---
title: "Rebuilding exisiting linux kernel on hardware(microzed zynq)"
date: 2015-09-28
forum: Packaging and Compiling Programs
---

### Post by bobdxcool on 2015-09-28
[FONT=Helvetica Neue] have xillinux OS (based on ubunutu 12.04.LTS) installed on my hardware (ZYNQ FPGA Board). I have done some hardware reconfiguration and I need to rebuild my kernel after editing the config-3.12.0-xillinux-1.3 file. My question is how do I rebuild the existing kernel on the hardware after making changes to the config file[/FONT]
[FONT=Helvetica Neue][http://www.wiki.xilinx.com/Uartlite+Driver](http://www.wiki.xilinx.com/Uartlite+Driver)[/FONT]
[FONT=Helvetica Neue]This is the page above that I am referring to where they say that:[/FONT]
[FONT=Helvetica Neue]To enable the uartlite driver in the linux kernel you either have to integrate it or build it as kernel module (.ko). You can enable it with:

[/FONT]
```
make menuconfig
---> Device Drivers ---> Character devices ---> Serial drivers ---> Xilinx uartlite serial port support
```


[FONT=Helvetica Neue]make menuconfig - I have to enter this command on the OS running on my hardware in the /root/boot/.config folder to enable it ?[/FONT]
[FONT=Helvetica Neue]What does , ---> Device Drivers ---> Character devices ---> Serial drivers ---> Xilinx uartlite serial port support THIS MEAN ? I have to change directory ?[/FONT]
[FONT=Helvetica Neue]The other option as per the link posted above is to add certain lines as below to the config file, for which I would use the nano editor and then save it with ctrl+X and then Y.

[/FONT]
```
# integrate into the kernel
CONFIG_SERIAL_UARTLITE=y
# build as loadable module
CONFIG_SERIAL_UARTLITE=m




```[FONT=Helvetica Neue]But they say that, "After that you of course have to rebuild the kernel and deploy it to your Zynq device."[/FONT]
[FONT=Helvetica Neue]Where zynq is the hardware I am running my OS on. What commands do I have to use to rebuild the existing kernel on my hardware after making changes to the .config file ?[/FONT]
[FONT=Helvetica Neue]So, after rebuilding the kernel with the changes above, I just reboot to observe the changes ?

I was referring to this link, 

[http://www.thegeekstuff.com/2013/06/compile-linux-kernel/](http://www.thegeekstuff.com/2013/06/compile-linux-kernel/)

So, in order to compile and build it, I edit the .config file in nano and save it.
 Then, I type "make"  in the same folder as config. 
Then, I type "make modules" in the same folder
Then I type make modules_install
Then I type make install
Then I reboot the system to see the new kernel installed.

Is this the right way of doing it ?

Currently in my boot directory, there are 4 files. One config file and 3 .dts files. After rebuilding the kernel, this might change ?

[/FONT]
[FONT=Helvetica Neue]

[/FONT]

---

