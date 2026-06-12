---
title: "Debugging TIVA C launchpad using Openocd with eclipse Noen"
date: 2017-03-08
forum: Programming Talk
---

### Post by prithiviraj0v on 2017-03-08
Hi everyone here,
   I am working on TIVA launchpad. i would like to work in linux environment than windows. so i started using eclipse in linux for embedded development. Here, I'm using arm-none-eabi 4.8.3  toolchain for compilation. I'm able to build the bin, elf file with that. Now for debugging I'm using Openocd. while debugging i"m getting this error. Igoogled for solution also. but I'm not understanding what file they are asking me to modify only.


```
Open On-Chip Debugger 0.10.0+dev-00093-g6b2acc0 (2017-03-07-19:47)
Licensed under GNU GPL v2
For bug reports, read
    [http://openocd.org/doc/doxygen/bugs.html](http://openocd.org/doc/doxygen/bugs.html)
Info : The selected transport took over low-level target control. The results might differ compared to plain JTAG/SWD
adapter speed: 500 kHz
Started by GNU ARM Eclipse
Info : RCLK (adaptive clock speed)
Info : ICDI Firmware version: 9270
Info : tm4c123gh6pm.cpu: hardware has 6 breakpoints, 4 watchpoints
Info : accepting 'gdb' connection on tcp/3333
undefined debug reason 7 - target needs reset
adapter speed: RCLK - adaptive
target halted due to debug-request, current mode: Thread 
xPSR: 0x01000000 pc: 0x0000026c msp: 0x20007ffc
semihosting is enabled
adapter speed: RCLK - adaptive
target halted due to debug-request, current mode: Thread 
xPSR: 0x01000000 pc: 0x0000026c msp: 0x20007ffc, semihosting
target halted due to breakpoint, current mode: Thread 
xPSR: 0x61000000 pc: 0x20000042 msp: 0x20007ffc, semihosting
adapter speed: RCLK - adaptive
target halted due to debug-request, current mode: Thread 
xPSR: 0x01000000 pc: 0x0000026c msp: 0x20007ffc, semihosting
Error: gdb requested a non-existing register
Info : dropped 'gdb' connection
```

anyone suggest me some possible solutions
Thanks in advance.

---

### Post by DuckHook on 2017-03-08
*Thread moved to **Programming Talk** as the more appropriate forum.*

---

