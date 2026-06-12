---
title: "Opening &quot;/dev/ttyUSB0&quot; hangs C++ program"
date: 2015-07-29
forum: Programming Talk
---

### Post by BJ_Avery on 2015-07-29
I'm trying to create a C++ program which communicates over a serial interface with a motion controller. Unfortunately, my computer does not have a serial port so I am using a USB-to-RS232 converter cable. When I plug in the cable, everything appears to be recognized correctly. The command ```
ls -l /dev/ttyU*
``` gives me an output of ```
crw-rw---- 1 root dialout 188, 0 Jul 29 10:58 /dev/ttyUSB0
``` and communication in minicom works just fine, so I know the hardware is all working properly. The user I'm logged in as is in the dialout group so I believe I should have appropriate permissions to access the port. 

The problem comes in when I try to write a C++ program to communicate with this same serial port. Whenever I attempt to open the port, the program hangs. The open command doesn't "fail" per se, it simply never returns. Unfortunately, I don't have any hardware available to test if this  problem would still occur with a direct serial connection or whether  it's only with the USB cable.
The simplest code I've been able to use to replicate the problem is this:
```
cout << "Attempting to open port...\n";
int open_result = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY);

if(0 == open_result)
{
     cout << "Port Opened Successfully\n";
}
else
{
  printf("Port Failed to Open: %s.\n", strerror(errno));
}
cout << "Port Initialized\n";

```
This code will print "Attempting to open port...\n" but will never make it to any of the later print or cout statements. I tried a similar program using libserial with similar results. I found a proposed workaround for this problem of using the following commands:

modprobe -r pl2303
modprobe pl2303

(From [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661321](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661321))

However, this workaround did not work for me. I have the same effect before or after using this workaround.

I am using Ubuntu 14.04 LTS

Any help, insight, or suggestions would be greatly appreciated. Thanks very much.

---

### Post by dwhitney67 on 2015-08-01
Use std::endl to end an output statement?  For example:

```

std::cout << "Port opened successfully" << std::endl;

```


P.S.  If you really want to program in C++, avoid mixing your code up with C statements (e.g. printf).

---

### Post by xb12x2 on 2015-08-01
I suspect you do not need to do this:

*modprobe -r pl2303*
*modprobe pl2303*

The modprobe command loads a driver, in this specific case the pl2303 driver. You should not need to do this if, as you write, "*communication in minicom works just fine, so I know the hardware is all working properly.*" If the hardware was working then the correct driver was already loaded. 

Also, the pl2303 driver is for the most common type of USB-to-RS232 converter cable. However, there were other designs (though not common) and each design would need its own specific driver module.

To see the driver for your cable: 
First, without the USB-to-RS232 converter cable plugged-in, from the command-line, enter 

$ lsusb 

This will display the current, working usb hardware.

Then plug in the USB-to-RS232 converter cable (preferably without the controller plugged into the serial port of the cable) enter the command again and compare the output to the first time you ran it. You should see an new line added to the output, something like

**Bus 002 Device 006: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port**

That indicates the USB-to-RS232 cable was identified by the USB subsystem.

Now to prove that the driver module for the USB-to-RS232 converter is actually loaded, at the command line enter 

$ lsmod | grep -i pl2302

You should see something like

**pl2303    20480  0**


Okay, now for why your code is hanging:

First, the call to

*[COLOR=#000000][FONT=Ubuntu Mono]open_result = [/FONT][/COLOR]open("/dev/ttyUSB0", O_RDWR | O_NOCTTY);*


**open()** returns with -1 if Failed. 
If successful it returns a non-negative integer representing the lowest numbered unused file descriptor (almost guaranteed to be higher than 0). So you will have better luck if you initially check instead for a return value of -1 which indicates Failure, and accept any other value as the Successful return of the file descriptor of the opened port.

Next, I don't think you've shown enough of your code to be able to diagnose the problem. My guess is that the port is opened. However, your code is looping because it's waiting for hardware to be a certain state which never happens, possibly because the hardware is not initialized the way your code expects it to be. So check your code for loops waiting on a hardware state.

Another possibility is that the hardware is Interrupt-Driven and the moment the port is opened there is an interrupt (also because of uninitialized hardware). When the interrupt routine exits, the unhandled hardware condition that caused the interrupt causes yet another interrupt, and so on, again and again forever.

Good luck.

---

### Post by BJ_Avery on 2015-08-03
Thanks for the suggestions, here's what I've found so far:

Using the $ lsusb command, I have the following line added when the usb cable is plugged in:

Bus 006 Device 003: ID 05ad:0fba Y.C. Cable U.S.A., Inc. 

Using $ lsmod | grep -i pl2303 gives the following output:

pl2303                 19133  0 
usbserial              45014  1 pl2303

As for not showing enough of my code, here's my entire program, slightly modified to account for dwhitney67's advice of not mixing c/c++ code and using endl statements. (These modifications did not change the behaviour of the program, it still hangs on the open command.)

```
#include <iostream>
#include <errno.h>
#include <fcntl.h>
#include <string.h>

using namespace std;

int main(int argc, char** argv)
{
    cout << "Begin" << endl;
    cout << "Attempting to open port..." << endl;
    int open_result = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY);

    if(-1 == open_result)
    {
        cout << "Port Failed to Open: " << strerror(errno) << endl;
    }
    else
    {
        cout << "Port Opened Successfully" << endl;
    }
    cout << "Port Initialized" << endl;
    return 0;
}
```

As you can see, there are no loops to get stuck in, at least not within my code. This is obviously not the full program I intend to build, but while debugging a problem I find it's useful to reduce to the simplest possible program that will reproduce the error. I will begin looking into the issue of a looping hardware interrupt, but it's not an issue I've dealt with before. Do you have any advice or good links that could set me in the right direction for making sure I've properly accounted for hardware interrupts when the port opens? I've never heard of an interrupt being sent to a simple program just from opening a port, but I would like to learn more.

---

### Post by xb12x2 on 2015-08-04
-
It looks like the pl2303 driver module is the correct one for your [COLOR=#000000]Y.C. Cable (ID [/COLOR][COLOR=#000000]05ad:0fba). The header file for the pl2303 module shows support for it:

[/COLOR]***/* Y.C. Cable U.S.A., Inc - USB to RS-232 */***
#define [YCCABLE_VENDOR_ID]("http://lxr.free-electrons.com/ident?i=YCCABLE_VENDOR_ID")       0x05ad
#define [YCCABLE_PRODUCT_ID]("http://lxr.free-electrons.com/ident?i=YCCABLE_PRODUCT_ID")      0x0fba

Here's a link to the sources for the pl2303 module:
[http://lxr.free-electrons.com/source/drivers/usb/serial/pl2303.c](http://lxr.free-electrons.com/source/drivers/usb/serial/pl2303.c)


Question: Does your code only hang when the controller is connected? Or does it hang even without the controller and/or converter cable?

Since you've successfully tested with minicom, the converter cable and pl2303 module are most likely not the problem. But have you installed any code that came with the controller (application and driver)? If so you might try removing it. There might be a conflict between the controller's installed code and your code.

Another thing to try:
While your code is hanging, open another terminal and run dmesg to see if there are any error messages.
$ dmesg

You could try to narrow it down by 
$ dmesg | grep -i error

My guess is you'll have to start tracing your open() call and trying to figure out where it gets to, what code you're stepping through, where to find its sources, etc. Start by stepping through your code with the GNU debugger (gdb). There are tons of tutorials and examples online to learn how to use the GNU debugger.

And here's a link that will get you started using kernel symbols and sources on Ubuntu, in case your debugging leads you through kernel code.
[http://sysprogs.com/VisualKernel/tutorials/setup/ubuntu/](http://sysprogs.com/VisualKernel/tutorials/setup/ubuntu/)

---

### Post by BJ_Avery on 2015-08-11
The program only hangs when the cord is connected. If the serial/usb cable is unplugged, I get the following output:

```
Attempting to open port...
Port Failed to Open: No such file or directory
```

Which is what I would expect. dmesg did not provide any insight; while the program was hanging, the most recent messages were all about the cable being connected or disconnected.

last few lines of dmesg output:
```
[ 9726.641359] usb 6-2: New USB device found, idVendor=05ad, idProduct=0fba
[ 9726.641372] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 9726.641379] usb 6-2: Product: USB-Serial Controller
[ 9726.641386] usb 6-2: Manufacturer: Prolific Technology Inc.
[ 9726.644296] pl2303 6-2:1.0: pl2303 converter detected
[ 9726.656565] usb 6-2: pl2303 converter now attached to ttyUSB0
```

As for attempting to debug, I get a "no such file or directory" error for the file "syscall-template.S" when attempting to look into the source of the open64 command, which appears to be the function that is hanging.

```
Starting program: /home/bj/workspace/VelmexController/Debug/VelmexController 

Breakpoint 1, open64 () at ../sysdeps/unix/syscall-template.S:81
81    ../sysdeps/unix/syscall-template.S: No such file or directory.
(gdb) s
S
Breakpoint 1, open64 () at ../sysdeps/unix/syscall-template.S:81
81    in ../sysdeps/unix/syscall-template.S
(gdb) s

Breakpoint 1, open64 () at ../sysdeps/unix/syscall-template.S:81
81    in ../sysdeps/unix/syscall-template.S


```

I installed the linux source and debug symbols according to the tutorial that you linked, but this did not fix the problem. I am feeling very stuck about how to proceed with debugging this issue so any further insights would be greatly appreciated.

---

