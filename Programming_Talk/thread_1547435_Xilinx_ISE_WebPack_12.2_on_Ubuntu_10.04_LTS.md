---
title: "Xilinx ISE WebPack 12.2 on Ubuntu 10.04 LTS"
date: 2010-08-06
forum: Programming Talk
---

### Post by Stube on 2010-08-06
Hi,

I thought I could report this because I couldn't find one single guide for installing Xilinx ISE WebPack 12.2 on Ubuntu 10.04 LTS 64-bit system.

I finally succeeded in compiling a simple project using the ISE and programming it with iMPACT after completing the following steps to install the needed software. The following instructions assume that BASH is being used.

1. Download the software from [http://www.xilinx.com/support/download/index.htm]("http://www.xilinx.com/support/download/index.htm")

2. Untar the archive
```
cd /Path_to_the_archive
tar xvf Xilinx_ISE_DS_12.2_M.63c.1.1.tar
```

2a. Optionally burn the files inside the created directory to a DVD. This is not necessary, but it will allow you to delete the files from your hard disk.

3. Install the application
```
cd /Path_to_installer
sudo ./xsetup
```
-When asked to select edition to install, choose "ISE WebPACK".
-On the following page tick the box "Install Cable Drivers".
-I used the default directory suggested by the installer.

4. To make the application run correctly you need to type the following
```
source /opt/Xilinx/12.2/ISE_DS/settings64.sh

or

cd /opt/Xilinx/12.2/ISE_DS
source ./settings64.sh
```
Note the reference to the current directory, which is needed when using the second alternative. In the same directory there is also a file called "settings32.sh" for 32-bit systems.

The settings need to be run every time before invoking the application in a new console.

5. After the software has been installed it's time to get a license from Xilinx website ([http://www.xilinx.com/getlicense]("http://www.xilinx.com/getlicense")). After completing the form you should get a file called "Xilinx.lic". Copy this file to .Xilinx-folder inside your home directory:
```
cd /Path_to_license_file
cp Xilinx.lic ~/.Xilinx/
```
(The official instructions advise to use the license manager "xlcm", but for me it kept segfaulting, when I pressed the "Copy license..." button.)

At this point you should be able to start the design environment by running command "ise" in the console. If iMPACT doesn't find your cable, there are a couple of steps more to go.

The steps described below have been copied from the driver source files referenced at [http://groups.google.com/group/comp.arch.fpga/browse_frm/thread/f149e5b6028e2c70]("http://groups.google.com/group/comp.arch.fpga/browse_frm/thread/f149e5b6028e2c70"). The driver doesn't need to be compiled, but the udev rules are not created by the Xilinx installer.

6. Copy the udev rules and adapt the file to the new udev-version
```
sudo cp /opt/Xilinx/12.2/ISE_DS/ISE/bin/lin64/xusbdfwu.rules /etc/udev/rules.d/50-xusbdfwu.rules
sudo sed -i -e 's/TEMPNODE/tempnode/' -e 's/SYSFS/ATTRS/g' -e 's/BUS/SUBSYSTEMS/' /etc/udev/rules.d/50-xusbdfwu.rules
```
If your machine is running 32-bit Linux change 'lin64'->'lin' on the first line.

7. Copy the hex-files used by different Xilinx cables to /usr/share and make them readable by regular users
```
sudo cp /opt/Xilinx/12.2/ISE_DS/ISE/bin/lin64/xusb*.hex /usr/share/
sudo chmod 644 /usr/share/xusb*.hex
```
Again, 'lin64'->'lin' for 32-bit systems.

8. Install fxload, which is used by the rules, and libusb-dev, which is needed by iMPACT
```
sudo apt-get install fxload libusb-dev
```

9. Restart udev
```
sudo restart udev
```

10. To make planAhead work two script files must be edited.
```
sudo sed -i -e 's/#!\/bin\/sh/#!\/bin\/bash/' /opt/Xilinx/12.2/ISE_DS/PlanAhead/bin/planAhead
sudo sed -i -e 's/#!\/bin\/sh/#!\/bin\/bash/' /opt/Xilinx/12.2/ISE_DS/PlanAhead/bin/loader
```

If you now connect the cable to the computer, it should work as expected. I tested this with Spartan-3AN Starter Kit, which has an onboard USB programmer. When I connected the cable, the green LED next to the USB connector turned on to indicate that the driver was working correctly.


This is the first time I am able to program my Spartan-3AN Starter Kit using Ubuntu, and I hope this guide will help somebody else to achieve the same.

I am writing this at midnight after trying lots of stuff to get the software working. I might have forgotten a step or two, so please let me know, if you do or don't succeed in installing the software.

---

### Post by K.J. on 2010-08-24
I just followed this and it worked beautifully.  I haven't had a chance to actually connect my Nexys2 development board yet, so I'll let you know if it all went smoothly later when I get home.

Very helpful!

---

### Post by prox2far on 2010-08-25
Mine kept segfaulting as well, thanks for the .Xilinx tip.

---

### Post by Stube on 2010-08-25
Nice to hear that someone else is making progress with the ISE as well.

I have noticed that the FPGA Editor does not work because it is trying to use an outdated version of libstdc++.so. I haven't found the "right" solution for this yet...

---

### Post by liptonik on 2010-09-14
Stube,
I have done everything that you described and the green LED turned on. 
But I can't program my spartan 3E by Xilinx IMPACT, i get this errors:
```
GUI --- Auto connect to cable...
// *** BATCH CMD : setCable -port auto
AutoDetecting cable. Please wait.
PROGRESS_START - Starting Operation.
Reusing A0062001 key.
Reusing 24062001 key.
 OS platform = i686.
If you are using the Platform Cable USB, please refer to the USB Cable Installation Guide (UG344) to install the libusb package.
Connecting to cable (Usb Port - USB21).
Checking cable driver.
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
Reusing 78062001 key.
Reusing FC062001 key.
 OS platform = i686.
Connecting to cable (Parallel Port - parport0).
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module parport_pc is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
Reusing 79062001 key.
Reusing FD062001 key.
 OS platform = i686.
Connecting to cable (Parallel Port - parport1).
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module parport_pc is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
Reusing 7A062001 key.
Reusing FE062001 key.
 OS platform = i686.
Connecting to cable (Parallel Port - parport2).
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module parport_pc is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
Reusing 7B062001 key.
Reusing FF062001 key.
 OS platform = i686.
Connecting to cable (Parallel Port - parport3).
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
 Linux release = 2.6.35-gentoo-r4.
WARNING:iMPACT -  Module parport_pc is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
PROGRESS_END - End Operation.
Elapsed time =      4 sec.
Cable autodetection failed.
WARNING:iMPACT:923 - Can not find cable, check cable setup !
```

and of course I don't know what to do.

---

### Post by Stube on 2010-09-14
I investigated it a bit and might have found the solution.

Seems that for some odd reason impact needs the libusb development files.

So do```
sudo apt-get install libusb-dev
```and try it again.

---

### Post by martin.k on 2010-09-15
Just wanted to post above dependency on libusb-dev as well :) You were faster - nice job, Stube.

Other things I noticed with Xilinx ISE 12.2 (some components might not be licensed as part of the WebPack, though - I am using a full license):

1) the SDK (invoked by the command xsdk on the shell) needs ia32-libs installed, otherwise it can't verify the license:
```

sudo aptitude install ia32-libs

```Note that older versions of ISE and other commercial, pre-compiled software have numerous, well hidden dependencies on those 32bit libraries (many of them related to license management). So I am pretty sure other components of the ISE rely on ia32-libs as well. But once ia32-libs are installed, you will never know :)

2) Chipscope (invoked by the command analyzer on the shell) suffers from the same broken start scripts as planAhead, i.e. pointing to /bin/sh, but expecting bash functionality. 

I am sure more scripts are broken. Instead of touching the scripts in /opt/Xilinx/..., an alternative 'workaround' is:
```
sudo dpkg-reconfigure dash

```and point to bash. This is a 'dirty' quick-fix, which changes system settings, but 'fixes' the issues for all broken scripts. Not recommended, though. I think it is better to find and fix all the broken scripts (and tell us & Xilinx).

There were other caveats with ISE 12.1 (e.g. the SDK insists on gmake instead of make if compiling for microblaze, i.e. a symlink from make to gmake could fix this), I will report them as I am encountering them in 12.2.

Interesting enough, even without the 32bit libraries installed, my license manager never segfaulted so far, and allows proper 'copying' of the Xilinx.lic file. Stube, any idea what causes your license manager to segfault?

---

### Post by liptonik on 2010-09-15
I have installed it earlier and it's not working :/

---

### Post by Stube on 2010-09-15
According to the error message the problem is somehow related to libusb. The only way I am able to reproduce your error is by removing libusb-dev.

Just to double-check, is libusb-0.1-4 installed? Because libusb-dev depends on it, I assumed earlier that it will be. The only other possibly related packages (judging by the names) I have installed are libusb-1.0-0 and libusbmuxd1.

I'm afraid I might not be able to help much more as I do not have Gentoo installed on my computer...

---

### Post by liptonik on 2010-09-15
Your post give me clue that sth is wrong, because package dev-libs/libusb (in portage) depends on nothing. 
So I check again and there is another package called dev-libs/libusb-compat and it is dependent on dev-libs/libusb-1.0.8.

After emerging this everything seems to work fine :)

Thank you very much.

---

### Post by Stube on 2010-09-15
Glad to hear you got it sorted out. It helps to have the "right" development files and the binaries as well :)

[QUOTE="martin.k"]Interesting enough, even without the 32bit libraries installed, my license manager never segfaulted so far, and allows proper 'copying' of the Xilinx.lic file. Stube, any idea what causes your license manager to segfault?[/QUOTE]No idea. It only prints the OS only prints "Segmentation fault" to command line.

Thanks for the information about the other tools. I only have the free license which doesn't include SDK or Chipscope though, so can not comment on that. One thing that is not working in ISE is the FPGA editor. It gives the following error on the command line:```
/opt/Xilinx/12.2/ISE_DS/ISE/bin/lin64/_fpga_editor: error while loading
shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
``` In other words it requires an old version of libstdc++ which is no longer shipped with Ubuntu. I'm not sure, what would be the "clean" way to handle this.

Anyway, I will update the original post with the information about libusb-dev.

---

### Post by Vekin06 on 2010-09-22
Hi! 

I also have a problem with fpga_editor but with this error:

/opt/local/Xilinx/12.2/ISE_DS/ISE/bin/lin64/_fpga_editor: Symbol `_XtperDisplayList' causes overflow in R_X86_64_PC32 relocation
/opt/local/Xilinx/12.2/ISE_DS/ISE/bin/lin64/_fpga_editor: Symbol `_XtGetPerDisplayInput' causes overflow in R_X86_64_PC32 relocation

Does anyone can help???

Thanks

---

### Post by mr_etienne on 2010-10-11
Hi all!

First of all, thank you for this tuto Stube.

I am actully facing similar issues with the USB. I managed to install and use Xilinx ISE 12.2 on my 10.04, including SDK/EDK. But still blocked with the USB programmer (Digilent S3A board). I carefully dbl-checked the libs (libusb-0.1-4, libusb-1.0-0, libusb-dev) and the programmer firmware (r. 1030, green led on). Here is the log from iMPACT:

```

GUI --- Auto connect to cable...
AutoDetecting cable. Please wait.
PROGRESS_START - Starting Operation.
Reusing A0015DF2 key.
Reusing 24015DF2 key.
Connecting to cable (Usb Port - USB21).
Checking cable driver.
File version of /opt/Xilinx/12.2/ISE_DS/ISE/bin/lin64/xusbdfwu.hex = 1030.
 Using libusb.
Please  run `source ./setup_pcusb` from the  /opt/Xilinx/12.2/ISE_DS/ISE//bin/lin64 directory with root privilege to  update the firmware. Disconnect and then reconnect the cable from the  USB port to complete the driver update.
Cable connection failed.
Reusing 78015DF2 key.
Reusing FC015DF2 key.
Connecting to cable (Parallel Port - parport0).
 Linux release = 2.6.32-25-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
 Linux release = 2.6.32-25-generic.
WARNING:iMPACT -  Module parport_pc is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
Reusing 79015DF2 key.
Reusing FD015DF2 key.
Connecting to cable (Parallel Port - parport1).
 Linux release = 2.6.32-25-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
 Linux release = 2.6.32-25-generic.
WARNING:iMPACT -  Module parport_pc is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
Reusing 7A015DF2 key.
Reusing FE015DF2 key.
Connecting to cable (Parallel Port - parport2).
 Linux release = 2.6.32-25-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
 Linux release = 2.6.32-25-generic.
WARNING:iMPACT -  Module parport_pc is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
Reusing 7B015DF2 key.
Reusing FF015DF2 key.
Connecting to cable (Parallel Port - parport3).
 Linux release = 2.6.32-25-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
 Linux release = 2.6.32-25-generic.
WARNING:iMPACT -  Module parport_pc is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
PROGRESS_END - End Operation.
Elapsed time =      0 sec.
Cable autodetection failed.
WARNING:iMPACT:923 - Can not find cable, check cable setup !
```Note that iMPACT is using libusb! But then ask for this setup_pcusb script. As far as I understood, this script is only usefull for updating the programmer's firmware, which is already done…

Do you guys think that it may still come from a missing lib? Which one? If not, any other idea?

---

### Post by Stube on 2010-10-11
Hi mr_etienne,

That's interesting. What do commands```
ls -l /usr/share/xusb*

and

lsusb | grep 03fd
```print to the terminal?

---

### Post by mr_etienne on 2010-10-12
Hi Stube,
```
ls -l /usr/share/xusb*
-rw-r----- 1 root root  1971 2010-07-21 09:18 /usr/share/xusbdfwu
-rw-r----- 1 root root 21666 2010-10-08 08:51 /usr/share/xusbdfwu.hex
-rw-r----- 1 root root   965 2010-07-21 09:18 /usr/share/xusbdfwu.rules
-rw-r----- 1 root root  1288 2010-07-21 09:18 /usr/share/xusbdfwu.usermap
-rw-r----- 1 root root   913 2010-07-21 09:18 /usr/share/xusb_emb
-rw-r----- 1 root root 21708 2010-10-08 08:51 /usr/share/xusb_emb.hex
-rw-r----- 1 root root   913 2010-07-21 09:18 /usr/share/xusb_xlp
-rw-r----- 1 root root 21708 2010-10-08 08:51 /usr/share/xusb_xlp.hex
-rw-r----- 1 root root   913 2010-07-21 09:18 /usr/share/xusb_xp2
-rw-r----- 1 root root 22956 2010-10-08 08:51 /usr/share/xusb_xp2.hex
-rw-r----- 1 root root   913 2010-07-21 09:18 /usr/share/xusb_xpr
-rw-r----- 1 root root 20740 2010-10-08 08:51 /usr/share/xusb_xpr.hex
-rw-r----- 1 root root   913 2010-07-21 09:18 /usr/share/xusb_xse
-rw-r----- 1 root root 22956 2010-10-08 08:51 /usr/share/xusb_xse.hex
-rw-r----- 1 root root   913 2010-07-21 09:18 /usr/share/xusb_xup
-rw-r----- 1 root root 21666 2010-10-08 08:51 /usr/share/xusb_xup.hex


lsusb | grep 03fd
Bus 002 Device 005: ID 03fd:0008 Xilinx, Inc.

```Again, the version of the firmware seems to be fine (1030). I am more and more thinking at an access rights issue (basically because I don't have all the rights on this machine) and I have no clue regarding which rights should be set. Do you think iMPACT is lacking some access somewhere?

---

### Post by Stube on 2010-10-12
Yes, it certainly looks like that. The ID returned by lsusb tells that the firmware is loaded, indeed.

For some reason only root seems to have access to those hex-files on your system. Here's what I get:```
$ ls -l /usr/share/xusb*
-rw-r--r-- 1 root root 21666 2010-10-11 19:26 /usr/share/xusbdfwu.hex
-rw-r--r-- 1 root root 21708 2010-10-11 19:26 /usr/share/xusb_emb.hex
-rw-r--r-- 1 root root 21708 2010-10-11 19:26 /usr/share/xusb_xlp.hex
-rw-r--r-- 1 root root 22956 2010-10-11 19:26 /usr/share/xusb_xp2.hex
-rw-r--r-- 1 root root 20740 2010-10-11 19:26 /usr/share/xusb_xpr.hex
-rw-r--r-- 1 root root 22956 2010-10-11 19:26 /usr/share/xusb_xse.hex
-rw-r--r-- 1 root root 21666 2010-10-11 19:26 /usr/share/xusb_xup.hex
$
```
If I remove rights to read those files from group others, I get exactly same error that you reported earlier. So, a simple```
sudo chmod 644 /usr/share/xusb*
```should do the trick.

---

### Post by mr_etienne on 2010-10-13
…and it did the trick! USB programmer is running fine (I tried it from SDK and iMPACT).

Thanks a lot for you help Stube!

---

### Post by Stube on 2010-10-13
Nice to hear that!

I updated the first post with that piece of information.

---

### Post by chrisstankevitz on 2010-11-08
Thank you for this post!  How did you figure all of this out?

---

### Post by Stube on 2010-11-09
You're welcome!

It was a process of trial and error and, as I have learnt after the initial post, luck.
I think there would have been no way I would have figured out the libusb-dev dependency, if it had not been already installed on my computer...

---

### Post by riforifo on 2010-11-17
Hello,

Thank you for the tutorial. I have followed the steps and have everything almost running. My problem is that after Platform Studio successfully launches it does not recognize the license file. I have a 30 day system edition evaluation license and ISE recognizes it without problems. My computer is Asus A6jc and I have 32 bit Ubuntu 10.04. After reading Martin's post about SDK, being not able to verify license, I tried to install ia32-libs but Ubuntu refused to do so saying that I already have a 32 bit edition. 

Can you please guide me about this problem

thanks a lot
rifo

---

### Post by riforifo on 2010-11-18
In case you want to check the license, I paste it below

# ----- REMOVE LINES ABOVE HERE --------------------------
#
# This license is valid from Tue Nov 16 05:23:02 GMT+00:00 2010.
#
# This is license NODELOCKED to HOSTID=
# there is no need to run lmgrd for this license.
#
#
#  This license is valid for evaluation ( 30 days ) from Tue Nov 16 05:23:02 GMT+00:00 2010
INCREMENT System_Edition xilinxd 2011.11 17-dec-2010 uncounted \
7E89045BF499D \
VENDOR_STRING=  ,System_Edition,software,evaluation,_174912227_0_0_426 \
HOSTID=0016cb945f578 ISSUER="Xilinx Inc" START=16-Nov-2010 \
TS_OK
#
#
# ----------------------------------------------------------------------
#  The following PACKAGE definition is a REQUIRED part of this license:
#
PACKAGE System_Edition xilinxd 2011.11 E30D3F228C8F COMPONENTS="SDK \
ChipScopePro_SIOTK ChipscopePro ISE ISIM PlanAhead SysGen XPS" \
OPTIONS=SUITE
#
# ------------------------------------------------------------------------------
#
# ----- REMOVE LINES BELOW HERE --------------------------

---

### Post by riforifo on 2010-11-18
Hello again,
  
 I have solved the problem. It's my mistake (again :D ) The thing is, I  had downloaded ISE Webpack on another machine a couple of months ago.  When I iniated the license generation process for the system edition  evaluation version, Xilinx automatically automatically created the  license for the MAC address of my old machine (where I downloaded ISE  webpack) 
  
 I could have figured it out earlier but the thing is that when I  launched ise the first time, it complained about not finding a suitable  license and this complaints went away when I showed it the wrongly  configured (in terms of MAC address) license.
 y.sreekanth's post about generating a bitstream made me realize the problem. 
  
 So the morale of the story is,   double check the MAC address of your  license if you have downloaded different Xilinx products from different  machines.




One more important thing is, while looking for the license issue, I had came across this problem in launching planahead from ISE, the link below seemed to fix the problem


[http://www.c3a.de/wiki/index.php/ISE_Webpack_Ubuntu](http://www.c3a.de/wiki/index.php/ISE_Webpack_Ubuntu)


sudo apt-get install portmap




[LIST]
[*] **portmap**
[LIST]
[*] to fix the *Wind/U Error (248): Failed to connect to the  registry on server foobar - Cannot register service: RPC: Unable to  receive; errno = Connection refused* error (will work without but needs more time to start)
[/LIST]
 
[/LIST]
  
 thank you all for your time
 best regards
 rifo

---

### Post by jschaffn on 2010-11-22
Fantastic post, Stube! Many thanks.

I followed your directions, with slight modifications, for LabTools 12.3 on Ubuntu 10.04. When I connect the Platform Cable USB the LED lights. However, when I run "Cable Auto Connect" from iMPACT I get the following warnings and auto-connect fails:

"WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648."

I found that I COULD connect to the USB cable by going to "Cable Setup..." and selecting Platform Cable USB/II. So, I conclude that the warnings are caused by iMPACT still looking for windrvr6 to run the parallel cables during auto-detect.

I had good success installing and using Michael Gernoth's windrvr6 to libusb/ppdev wrapper that you alluded to in your post (see [http://groups.google.com/group/comp.arch.fpga/browse_frm/thread/f149e5b6028e2c70](http://groups.google.com/group/comp.arch.fpga/browse_frm/thread/f149e5b6028e2c70)). I installed the driver files at /opt/Xilinx/usb-driver and used the following export commands to get iMPACT to use the driver: export LD_PRELOAD=/opt/Xilinx/usb-driver/libusb-driver.so; export XIL_IMPACT_USE_LIBUSB=0.

I like the simplicity of your approach, using iMPACT's native libusb support. However, it's nice that with Gernoth's driver, both parallel and USB cable types are supported.

Thanks again,

Jake

---

### Post by Stube on 2010-11-23
Nice to hear that more people are having positive experiences with the Xilinx tools!

> "WARNING:iMPACT - Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648."

I get that same warning about windrvr6 at least when the USB cable is not connected. Intresting, that in your case auto connect fails where manual connection attempt is succesful... I included a logfile containing the messages printed by iMPACT when I have no cables connected to the computer. That might give you a clue, where the differences are.

> I like the simplicity of your approach, using iMPACT's native libusb support. However, it's nice that with Gernoth's driver, both parallel and USB cable types are supported.

Yes, I was trying to keep it as simple as possible because I myself find the windrvr6 wrapper quite confusing. Also, I do not have any way to test the parallel interface, so to me the most simple solution was also the best one.

---

### Post by gordwait on 2010-11-24
I just managed to get this working, I'm actually going back trying to retrace my many missteps and document it now.
I'm using labtools from Xilinx ISE 12.3

The last trick was to edit the udev rules file and change all the uppercase $TEMPNODE to $tempnode,
and I had to clear out all mention of XIL_IMPACT_USE_LIBUSB=n completely.

Found that tip on [http://forums.xilinx.com/t5/Installation-and-Licensing/Installing-usb-cable-driver-ubuntu/m-p/57845](http://forums.xilinx.com/t5/Installation-and-Licensing/Installing-usb-cable-driver-ubuntu/m-p/57845)


What a fiasco.


Here is what I have now working on Ubuntu 10.10 Kernel 2.6.35.22-generic
downloaded Xilinx_Labtools_12.3_M.70d.1.0.tar
unpacked it
sudo su
cd to /bin and:
mv sh bad_sh
ln -s ./bash sh
cd to the unpacked DIR and ran ./xsetup as root
fix the broken udev rules file:
edit /etc/udev/rules.d/xusbdfwu.rules and change all instances of $TEMPNODE to $tempnode
reboot
before running any Xilinx software (impact for example) do this:
source /opt/Xilinx/12.3/Labtools/settings32.sh
I made an alias to run the settings file before running impact..

Hopefully I didn't leave anything out in the multiple missteps I took to get to a working state.

---

### Post by thameera on 2010-12-07
Hello all, 
I applied most of the solutions given in the thread without no avail. The error I'm getting is:

```
// *** BATCH CMD : setMode -bs
// *** BATCH CMD : setMode -bs
GUI --- Auto connect to cable...
// *** BATCH CMD : setCable -port auto
AutoDetecting cable. Please wait.
PROGRESS_START - Starting Operation.
 OS platform = i686.
Connecting to cable (Parallel Port - parport0).
 Linux release = 2.6.35-23-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
 OS platform = i686.
Connecting to cable (Parallel Port - parport1).
 Linux release = 2.6.35-23-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
 OS platform = i686.
Connecting to cable (Parallel Port - parport2).
 Linux release = 2.6.35-23-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
 OS platform = i686.
Connecting to cable (Parallel Port - parport3).
 Linux release = 2.6.35-23-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
 OS platform = i686.
Connecting to cable (Usb Port - USB21).
Checking cable driver.
 Linux release = 2.6.35-23-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
 OS platform = i686.
Connecting to cable (Usb Port - USB22).
Checking cable driver.
 Linux release = 2.6.35-23-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
 OS platform = i686.
Connecting to cable (Usb Port - USB23).
Checking cable driver.
 Linux release = 2.6.35-23-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
 OS platform = i686.
Connecting to cable (Usb Port - USB24).
Checking cable driver.
 Linux release = 2.6.35-23-generic.
WARNING:iMPACT -  Module windrvr6 is not loaded. Please reinstall the cable drivers. See Answer Record 22648.
Cable connection failed.
PROGRESS_END - End Operation.
Elapsed time =      0 sec.
Cable autodetection failed.
WARNING:iMPACT:923 - Can not find cable, check cable setup !
```

I'm very helpless at this and need to get this working somehow, so can anyone please help?

---

### Post by Anindya29 on 2011-01-17
This worked beautifully ..... thanks a lot...

---

### Post by jobattle on 2011-02-08
I want to thank Stube for all the help in installing ISD Webpack on my home (32 bit Ubuntu 10.10) machine.  Your suggestions worked perfectly and I was able to program an S3E Demo Board using verilog and blink a few lights with a counter.  I was really happy lst night.

Unfortunately, when I did the same things to my work computer, also 32Bit Ubuntu 10.10, I was unable to program the board.  This is admittedly a "different" S3E board, but both were brand new.  Just in case, I will bring my other board to work tomorrow. 

When I run Impact,  I get a "Cable Notification: Impact: 923 - Cannot find cable. Check cable setup!" error.

The cable setup app seems to just hang when I try to switch to the USB mode.  I looked in all the instances of fileset.txt and none contained the string "summary=Parallel Cable Drivers...". as suggested in the help file.  Not sure why I needed Parallel .... anyway.

I re-installed ISE a second time and the error persists.  I dopn't know where to go from here. Any suggestions would be GREATLY appreciated.

Thanks

John Battle

---

### Post by jobattle on 2011-02-08
I accidentally left Impact running for a while and when I opened my terminal again I noticed several warnings on the screen:

[ ! ] 
Warning: Impact Module windrvr6 is not loaded.  Please reinstall cable drivers.  See answer record 22648 [OK]

Anybody know what that means?  How do I install the cable drivers?

John Battle

---

### Post by jobattle on 2011-02-09
I got home and realized I had a total of three S3E boards.  Tow of them have blue dots on IC3 and IC22 while the third has white dots on the IC3 and IC22. The one with white dots programs perfectly with both the built-in USB programmer and the external Platform Cable USB II programmer but the two boards with blue dots can only be programmed with the external Platform Cable USB II.

In all instances the green LD-G LED lights when the USB is connected. In the two "blue-dot" boards, however, the program finished light lights even without connecting the cable.

I wonder what could be wrong with the built-in programmer on these boards. Is it possible that the udev rules changed with different production runs of the boards and needs to be modified?  I believe these are "earlier" boards by about 2-3 years.

I have two Platform Cable USB II programmers and the both work perfectly with all the boards.

I will take the two suspect boards and the good board to work tomorrow to try them with my work computer, but I feel certain that the problem is in the boards themselves, esp the built-in programmer.

Anyone with any ideas???

Thanls in advance

John Battle N4OE
NASA Jet Propulsion Lab
4800 Oak Grove Dr
Pasadena, CA 91107 USA
818-281-6254 (c)

---

### Post by jobattle on 2011-02-09
When I  got home last night I realised I had a total of three S3E boards. Two of them have blue dots on IC3 and IC22 while the third has white dots on the IC3 and IC22. The one with white dots programmed perfectly with either the built-in USB programmer or the external Platform Cable USB II programmer but the two boards with blue dots could only be programmed with the external Platform Cable USB II. The built-in programmer always gave a Cable Notification error with these boards.

In all instances the green LD-G LED lights when the USB is connected. In the two "blue-dot" boards, however, the LD-D LED lights even without connecting the cable.

I wonder what could be wrong with the built-in programmer on these (blue dot) boards. Is it possible that the udev rules or driver changed with different production runs of the boards and needs to be modified? I believe these are "earlier" boards by about 2-3 years.

I took the two suspect boards to work today and, sure enough, they can indeed be programmed with the "Platform Cable USB II programmer" but still do not work with the built-in USB programmer.

What could be wrong with the built-in programmers on the "blue dot" boards.  I would really like to use them without the external programmer. 

Anyone with any ideas???

Thanks in advance

John Battle N4OE
Hairpuller 1st Class
NASA Jet Propulsion Lab
4800 Oak Grove Dr
M/S 169-506
Pasadena, CA 91107 USA
818-281-6254 (c)
818-393-7835 (o)

---

### Post by dhia on 2011-03-19
Hi,

I have a problem when I try to install XILINX ISE 12.2.
In fact, after downloading it, I can't execute xsetup, even when I print chmod +X xsetup to get it executable. I don't understand the reason of that, when I print ./xsetup or sudo ./xsetup, nothing is done, and I don't receive any error message or anything else.
Can someone help me please? thank you.

---

### Post by dhia on 2011-03-19
Hi,

I have a problem when I try to install XILINX ISE 12.2.
In fact, after downloading it, I can't execute xsetup, even when I print  chmod +X xsetup to get it executable. I don't understand the reason of  that, when I print ./xsetup or sudo ./xsetup, nothing is done, and I  don't receive any error message or anything else.
Can someone help me please? thank you.

---

### Post by lijing8898 on 2011-06-13
I followed all of your steps posted on the first page. But I still have the same problem similar to mr_etienne.
When I printed the commands you recommanded " ls -l /usr/share/xusb*" and "lsusb | grep 03fd". There are some files named “xub*.hex” listed, but no bus information are listed. The following is the code:

****************************************:
root@jing-SG45:~# ls -l /usr/share/xusb*
-rw-rw-rw- 1 root root 21666 2011-06-13 13:56 /usr/share/xusbdfwu.hex
-rw-rw-rw- 1 root root 21708 2011-06-13 13:56 /usr/share/xusb_emb.hex
-rw-rw-rw- 1 root root 21708 2011-06-13 13:56 /usr/share/xusb_xlp.hex
-rw-rw-rw- 1 root root 22956 2011-06-13 13:56 /usr/share/xusb_xp2.hex
-rw-rw-rw- 1 root root 20740 2011-06-13 13:56 /usr/share/xusb_xpr.hex
-rw-rw-rw- 1 root root 22956 2011-06-13 13:56 /usr/share/xusb_xse.hex
-rw-rw-rw- 1 root root 21666 2011-06-13 13:56 /usr/share/xusb_xup.hex
root@jing-SG45:~# lsusb |grep 03fd
root@jing-SG45:~# 
******************************************

What`s the problem? Could you help me to figure it out? 
ps: I use the this board "Digilent Atlys Spartan®-6 FPGA Development Kit". 
[LEFT] 			 		[/LEFT]



> **Stube said:**
> Hi mr_etienne,

That's interesting. What do commands```
ls -l /usr/share/xusb*

and

lsusb | grep 03fd
```print to the terminal?

---

### Post by venkatapraveen on 2011-07-15
SImply awesome... i searched many sites.. but this is so straight to the point > **Stube said:**
> Hi,

I thought I could report this because I couldn't find one single guide for installing Xilinx ISE WebPack 12.2 on Ubuntu 10.04 LTS 64-bit system.

I finally succeeded in compiling a simple project using the ISE and programming it with iMPACT after completing the following steps to install the needed software. The following instructions assume that BASH is being used.

1. Download the software from [http://www.xilinx.com/support/download/index.htm](http://www.xilinx.com/support/download/index.htm)

2. Untar the archive
```
cd /Path_to_the_archive
tar xvf Xilinx_ISE_DS_12.2_M.63c.1.1.tar
```2a. Optionally burn the files inside the created directory to a DVD. This is not necessary, but it will allow you to delete the files from your hard disk.

3. Install the application
```
cd /Path_to_installer
sudo ./xsetup
```-When asked to select edition to install, choose "ISE WebPACK".
-On the following page tick the box "Install Cable Drivers".
-I used the default directory suggested by the installer.

4. To make the application run correctly you need to type the following
```
source /opt/Xilinx/12.2/ISE_DS/settings64.sh

or

cd /opt/Xilinx/12.2/ISE_DS
source ./settings64.sh
```Note the reference to the current directory, which is needed when using the second alternative. In the same directory there is also a file called "settings32.sh" for 32-bit systems.

The settings need to be run every time before invoking the application in a new console.

5. After the software has been installed it's time to get a license from Xilinx website ([http://www.xilinx.com/getlicense](http://www.xilinx.com/getlicense)). After completing the form you should get a file called "Xilinx.lic". Copy this file to .Xilinx-folder inside your home directory:
```
cd /Path_to_license_file
cp Xilinx.lic ~/.Xilinx/
```(The official instructions advise to use the license manager "xlcm", but for me it kept segfaulting, when I pressed the "Copy license..." button.)

At this point you should be able to start the design environment by running command "ise" in the console. If iMPACT doesn't find your cable, there are a couple of steps more to go.

The steps described below have been copied from the driver source files referenced at [http://groups.google.com/group/comp.arch.fpga/browse_frm/thread/f149e5b6028e2c70](http://groups.google.com/group/comp.arch.fpga/browse_frm/thread/f149e5b6028e2c70). The driver doesn't need to be compiled, but the udev rules are not created by the Xilinx installer.

6. Copy the udev rules and adapt the file to the new udev-version
```
sudo cp /opt/Xilinx/12.2/ISE_DS/ISE/bin/lin64/xusbdfwu.rules /etc/udev/rules.d/50-xusbdfwu.rules
sudo sed -i -e 's/TEMPNODE/tempnode/' -e 's/SYSFS/ATTRS/g' -e 's/BUS/SUBSYSTEMS/' /etc/udev/rules.d/50-xusbdfwu.rules
```If your machine is running 32-bit Linux change 'lin64'->'lin' on the first line.

7. Copy the hex-files used by different Xilinx cables to /usr/share and make them readable by regular users
```
sudo cp /opt/Xilinx/12.2/ISE_DS/ISE/bin/lin64/xusb*.hex /usr/share/
sudo chmod 644 /usr/share/xusb*.hex
```Again, 'lin64'->'lin' for 32-bit systems.

8. Install fxload, which is used by the rules, and libusb-dev, which is needed by iMPACT
```
sudo apt-get install fxload libusb-dev
```9. Restart udev
```
sudo restart udev
```10. To make planAhead work two script files must be edited.
```
sudo sed -i -e 's/#!\/bin\/sh/#!\/bin\/bash/' /opt/Xilinx/12.2/ISE_DS/PlanAhead/bin/planAhead
sudo sed -i -e 's/#!\/bin\/sh/#!\/bin\/bash/' /opt/Xilinx/12.2/ISE_DS/PlanAhead/bin/loader
```If you now connect the cable to the computer, it should work as expected. I tested this with Spartan-3AN Starter Kit, which has an onboard USB programmer. When I connected the cable, the green LED next to the USB connector turned on to indicate that the driver was working correctly.


This is the first time I am able to program my Spartan-3AN Starter Kit using Ubuntu, and I hope this guide will help somebody else to achieve the same.

I am writing this at midnight after trying lots of stuff to get the software working. I might have forgotten a step or two, so please let me know, if you do or don't succeed in installing the software.

---

### Post by jobattle on 2012-10-18
I am running ISE Version 12.1 on Ubuntu 12.04 which uses the 3.2.0-32-generic kernel on a 64 bit machine.  When I recently upgraded to 12.04, XST stopped working.  I read enough on the internet to believe that the problem is probably glibc version but I don't know how to fix that without re-installing the operating system from scrattch so I just quit working with fpga's for a while, hoping I would someday find a solution. My consulting business suffered because I could no longer do FPGA work for my previous employer, JPL.

The other day I noticed that I also had the 32 bit version installed (I guess they were both installed together) so just for fun, I executed the 32 bit version and everything worked perfectly including xst.  I was able to build all of my previous projects again until I got to the part that uses impact to program the part.

When I tried to program a part, I received an error message stating that I could not execute the 32 bit version of impact on a 64 bit machine.  I read an article on the internet that suggested I "preload a 32 bit version of libusb" but I don't know what the author meant by "preloading" the library and, so far, I have been unable to cntact the author of the article.

I was wondering if anyone on this forum could shed any light on this problem for me.  It seems that I am very close to having my development system working again, but I don't know how to get past this small problem. 

Thank you for your help

John Battle
Caltech
[email]jobattle@caltech.edu[/email]
Tel: 626-709-6208
[http://www.n4oe.com](http://www.n4oe.com)

---

