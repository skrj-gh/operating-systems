# Operating Systems Lab Assignments
These are lab submissions done for CS344 Operating Systems Laboratory

### In this lab we used a UNIX based toy os called xv6 - created by MIT

## Assignment0 - Introduction and basics of assembly
- PC Boot Strap
  - X86 Assembly
  - Simulating x86
  - The PC’s Physical Address
  - The ROM BIOS
- The Boot Loader
- Loading the Kernel
- Link vs Load Address
- Adding a system call

## Assignment1 - Understanding system calls
- Sleep
  - Implement a user-level sleep program for xv6, along the lines of the UNIX sleep command. Your sleep should pause for a user-specified number of ticks.
- User Program to display animation
- Statistics
  - create a new system call wait2 which extends the wait system call:
      ```
      Input:
        int wait2(int *retime, int *rutime, int *stime)
        int * retime / *rutime / *stime ‐ pointers to an integer in which wait2 will assign:
        *retime : The aggregated number of clock ticks during which the process waited
        *rutime : The aggregated number of clock ticks during which the process was running
        *stime : The aggregated number of clock ticks during which the process was waiting for I/O (was not able to run).
      Output:
        Pid - of the terminated child process ‐ if successful
        1 ‐ upon failure
      ```

## Assignment2 - Process Management and Scheduling
- Add support for tracking the number of “tickets” in a process.
- Add a system call called *getprocessesinfo* with the following prototype
    ```int getprocessesinfo(struct processes_info *p);```
 where struct *processses_info* is defined as:
 ```
   struct processes_info {
    int num_processes;
    int pids[NPROC];
    int ticks[NPROC]; // ticks = number of times process has been scheduled
    int tickets[NPROC]; // tickets = number of tickets set by settickets()
  };
```
- Lottery Scheduling
- Hybrid scheduling algorithm
- Implement the system call getNumProc(), to return the total number of active processes in the system (either in embryo, running, runnable, sleeping, or zombie states)
- Implement the system call getMaxPid() that returns the maximum PID amongst the PIDs of all currently active (i.e., occupying a slot in the process table) processes in the system
- Implement the system call getProcInfo(pid, &processInfo). This system call takes as arguments an integer PID and a pointer to a structure processInfo
- Change the xv6 scheduler to take approximate process burst/running time into account.
  - Add new system calls to xv6 to set/get process burst time
  - `set_burst_time(n)`, the burst time of the process should be set to the specified value
  - `get_burst_time()` to read back the burst time just set
 
## Assignment3 - Memory management
- Lazy Memory Allocation
    - Eliminate allocation from sbrk()
    - Lazy Allocation
- Paging
    - Kernel processes
    - Swapping out mechanism
    - Swapping in mechanism

## Assignment4 - Features of modern file system
- Compare two modern file systems for their unique features
    - ZFS : Copy-on-Write
    - EXT4 : Journaling
- Use vdbench to create workloads to test the file systems
