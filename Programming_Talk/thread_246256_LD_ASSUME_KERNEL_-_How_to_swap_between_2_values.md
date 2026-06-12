---
title: "LD_ASSUME_KERNEL - How to swap between 2 values?"
date: 2006-08-29
forum: Programming Talk
---

### Post by angandas on 2006-08-29
Hi All,

I have tried out all possible ways (kudos to google) to solve my problem but am unsuccessful at the end of the day. I seek your help.

I am running a C++ program which calls Matlab and HSpice (a circuit simulation program) through the 'system' commands inside the program. The versions are:
Linux : 2.6.15-26-386 (Ubuntu 6.06)
Matlab: 7.0.0 (R14) 
C++ compiler: g++

Since I have a windows version of Hspice, I have installed 'wine' (version: 0.9.19) through the Synaptic Package manager. To test if it runs fine or not, when I run ($ wine hspice.exe) at the command prompt, it runs perfect. 

Now, regarding Matlab, I need to do symbolic analysis. On getting errors, I saw that I need to change the variable LD_ASSUME_KERNEL ($ export LD_ASSUME_KERNEL=2.4.1) in the same shell where I invoke Matlab. Then Matlab runs fine. But when I run hspice again from the same shell (terminal), then it fails. Changing back to LD_ASSUME_KERNEL=2.6 makes hspice run smoothly (as before), but screws up matlab.

How do I switch between the two values of LD_ASSUME_KERNEL? I can do it manually on the command prompt before invoking the tools individually, but as you understand, I cannot do it (inside my program) while executing (the program has a loop calling matlab and hspice alternatively).

Two of the things I have tried are:

1) Inside my program, 
system("export LD_ASSUME_KERNEL=2.6 && wine hspice.exe");........
system("export LD_ASSUME_KERNEL=2.4.1 && matlab);.......
2) Tried by doing the same thing in .alias file for the two commands. 
In the .bash_aliases file,
alias command_1='export LD_ASSUME_KERNEL=2.6 && wine hspice.exe'
alias command_2='export LD_ASSUME_KERNEL=2.4.1 && matlab'
Inside the program, 
system("command_1");....
system("command_2);.....

They were of no use. Might be one cannot change the LD_ASSUME_KERNEL in runtime.

I eagerly look forward to your help in this regard.

P.S. :
1) The error in 'wine hspice' with LD_ASSUME_KERNEL=2.4.1 was:
..."wine: Unhandled page fault on write access to"......
2) The error in 'matlab' with LD_ASSUME_KERNEL=2.6 was:
..."Unable to load mex file: $Matlab7/toolbox/symbolic/maplemex.mexglx".....

Thanks,
Angan

---

### Post by LordHunter317 on 2006-08-29
The correct way to do it is to use setenv() before calling system.

---

