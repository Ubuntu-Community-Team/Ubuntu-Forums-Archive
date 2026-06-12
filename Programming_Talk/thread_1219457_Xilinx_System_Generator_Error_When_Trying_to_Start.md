---
title: "Xilinx System Generator Error When Trying to Start"
date: 2009-07-21
forum: Programming Talk
---

### Post by mju4t on 2009-07-21
Hello

I installed Xilinx System Generator (on Linux Mint, an Ubuntu Derivative) and am trying to start it.  I did the "source settings32.sh" and then I do "sysgen" and this is what happens:

ERROR: Could not find SysGen startup script at "/home/alexander/programs/xilinx/DSP_Tools/lin/sysgen/util/sysgen_startup.m".

Where do I get this script from?

Thanks!
Alex

---

### Post by tafkos on 2009-09-17
I was faced same error then trying to run sysgen. But solution was found:

At the page 26 of [http://www.xilinx.com/support/documentation/sw_manuals/xilinx11/sysgen_gs.pdf](http://www.xilinx.com/support/documentation/sw_manuals/xilinx11/sysgen_gs.pdf) was

[I]2. The following directory/file should exist under the DSP_Tools installation directory
   when installed under Linux. This will not show here under windows.
   <install_dir>/DSP_Tools/<OS>/install_logfiles/postinstall_<OS>.log
   <install_dir>/DSP_Tools/<OS>/sysgen/util/sysgen_startup.m
   <install_dir>/DSP_Tools/<OS>/common/bin/sysgen
[/I]
There was no first and second files. After examination of install logs in <install_dir>/.xinstall/install.log I've seen following :

[FONT=Courier New]Wed May 13 23:07:00 TZ 2009:: summary= /media/DATA-old/Xilinx/DSP_Tools/lin/common/bin/postinstall lin /media/DATA-old/Xilinx/DSP_Tools/lin/ sysgen 11.1 1666[/FONT]

It seemed that postinstall script failed during install process. It was confirmed then I manually tried to run next command:

[FONT=Courier New]$ postinstall lin /media/DATA-old/Xilinx/DSP_Tools/lin/ sysgen 11.1 1666
postinstall: 26: Syntax error: "(" unexpected[/FONT]

After adding **bash** at the beginning of last command postinstall script successfully finished, but some warnings were remained:
[FONT=Courier New]$ **bash** postinstall lin /media/DATA-old/Xilinx/DSP_Tools/lin/ sysgen 11.1 1666
Could not find good installation of matlab
Completed post installation script.  See /media/DATA-old/Xilinx/DSP_Tools/lin//install_logfiles/postinstall_lin.log for details.
A matlab startup function () has been created and placed into installation directory < /media/DATA-old/Xilinx/DSP_Tools/lin//sysgen/util/ > and < /home/tkhome/matlab > called[/FONT]

However, sysgen is now working:
[FONT=Courier New]$ sysgen[/FONT]

---

### Post by kylongmu on 2009-10-11
Support 64bit is the main reason to use ISE with linux64, and 0 pay for Ubuntu is why we use it.


Step 1: [FONT=Courier New]modify the first line of "./[/FONT][FONT=Courier New]DSP_Tools/lin64/common/bin/[/FONT][FONT=Courier New]postinstall"
#! /bin/bash
Step 2: modify the top settings64.sh
add this:
MATLAB_ROOT="you matlab too path"
export [/FONT][FONT=Courier New]MATLAB_ROOT
Step 3:
/opt/Xilinx/11/DSP_Tools/lin64/common/bin/postinstall lin64 /opt/Xilinx/11/DSP_Tools/lin64/ sysgen 11.1 1666
[/FONT][FONT=Courier New][/FONT]Step 4:
[FONT=Courier New]$ sysgen[/FONT][/quote]

----------------------------------
Make sure the matlab version is supportted by the correct System Generator

---

### Post by mju4t on 2009-11-30
Thank you for the responses!  Since my last post, I've upgraded to Ubuntu 9.10x64.  I have installed MATLABx64 but when I try to install ISE, it says linuxx64 is not supported.  I understand that 11.3 is compatible with 64 bits, and needs to be installed on top of 11.1.  HOWEVER, 11.1 is not compatible with linux64bit...so how am I to install ISE?

---

### Post by kylongmu on 2009-12-01
I installed ISE 11.1 onto Ubuntu 9.10amd64, without any error occours.
I tried with another way on Step 1:
no need change the file,
by change the "/bin/sh" to "/bin/bash,"
if you check the default link, the "/bin/sh" is link to "/bin/dash"
sudo ln -s /bin/sh /bin/bash
--------------------------------
:popcorn:My Ubuntu 9.10amd64 can't boot into X-Windows, because I upgraded my display card with HD5770 , the display driver can't work , I'm waiting for AMD to release HD5770 linux64 driver.
--------------------------------
If my display driver can work, I'll give more test on ISE under Ubuntu 9.10amd64

---

