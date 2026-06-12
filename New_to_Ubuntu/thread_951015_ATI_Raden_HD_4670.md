---
title: "ATI Raden HD 4670"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by swoop_ubu on 2008-10-17
I tried to boot ubuntu 8.10 beta on my HTPC featuring ATI HD 4670 video card and the booting somehow hung up. I belive, when I tried the same (but with 8.04.1) while using onboard intel G3100 everything was fine.

Is HD 4670 known to not working properly or not having stable drivers? The same thing repeated when I tried XBMC (uses ubuntu) while specifically selecting ATI driver. Any hints?

cheers

---

### Post by swoop_ubu on 2008-10-18
I tried to boot live version of XBMC (Media center). Its using ubuntu 8.04.1 as host OS and the same thing happened. Although I chose the nVidia drivers at boot-time, as it has this option.

Does anyone know what is the problem with Radeon HD 4670?
I will try to boot Mandriva One 2009.0 and post the result here.

Cheers

edit: the word "nVidia" should be "ATI", of course. it's just that I have 2 computers, one with nVidia and one with ATI card...

---

### Post by phidia on 2008-10-18
Take a loook at the thread [here]("http://ubuntuforums.org/showthread.php?t=515573") on enabling drivers for ATI cards-the 1st link in that thread provides a guide for installing the driver from the ATI site.

I overlooked that you are using the testing release. A testing release is expected to have issues. 
You're better off using 8.04 or asking this question in the development forum.

In your second post here you say you tried to boot another distro(?) based on 8.04 selecting the nvidia driver for an ati card doesn't seem likely to work.

---

### Post by swoop_ubu on 2008-10-19
> **phidia said:**
> In your second post here you say you tried to boot another distro(?) based on 8.04 selecting the nvidia driver for an ati card doesn't seem likely to work.
that's right. let me rephrase my problem:

- booting live ubuntu 8.04.1 not successful
- booting live ubuntu 8.10 beta not successful
- booting live XBMC (based on ubuntu 8.04.1) - at boot stage selected "use ATI drivers" - not successful
= it seems they all hang at the start of X

my configuration is Shuttle HTPC SG33G5M (D'VO Series) + ATI Radeon HD 4670. the rest is onboard.

I started this thread because on ATI drivers page I downloaded the latest drivers package for XP and that one, how strange that might sound, doesn't contain drivers for HD 4670. thus, I thought it is a known issue that there is no appropriate driver for linux too.

any comments?

---

### Post by Lycosid on 2008-10-19
I'm running an ati radeon hd 4670 as well and using 8.04.1 I was able to fully boot into ubuntu, but the card isn't recognized by ubuntu. When I try to install drivers and reboot the system hangs when gnome is loading. Are we stuck waiting on ati to put out linux drivers for the 4670?

If anyone solves this and is ever near of Gettysburg, PA, I will buy them a beer.

---

### Post by PilotJLR on 2008-10-20
I have an HD 4670 working under 64 bit Ubuntu 8.04.1. I had to use the ATI provided driver, though.

Download the driver here:
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

Then follow the instructions here:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29)

After install, I rebooted (though restarting X is probably all you need).

The PROBLEM is that, once the gdm screen appears, my monitor says "No Signal" and goes to sleep. I found that I can workaround this by toggling to a virtual terminal (Ctrl + Alt + F1), and then toggle back to X (Ctrl + Alt + F7).

I've not tried to find a real fix for this issue yet... once done toggling and logged in, the card works GREAT.

If I find a real fix, I will post back. If anyone else does, please tell me!!

---

### Post by Lycosid on 2008-10-20
Thanks Pilot! I had tried the wiki's advice to no avail until I noticed that I downloaded Catalyst 8.9, but the next two lines read:

sudo chmod -x ati-driver-installer-8-10-x86.x86_64.run
sudo sh ati-driver-installer-8-10-x86.x86_64.run

I had to change them to this:

sudo chmod -x ati-driver-installer-8-9-x86.x86_64.run
sudo sh ati-driver-installer-8-9-x86.x86_64.run 

Then there was much rejoicing, as well as bouncy windows.

---

### Post by spudgunner on 2008-10-28
I just installed one of these today, after taking an nVidia 8600GT out... it doesn't like my computer at all... colour is severely screwed up and the resolution is really low, so i can barely tell what I'm doing... couldn't find this catalyst thing in the repositories. I'm looking for any suggestions.

Also, I'm think of ripping it out and using the mobo graphics just to get this stuff installed. I'm gonna try what PilotJLR said, although I have a 32-bit installation, so I'm gonna try the 32-bit driver.

Thanks all,

Josh

[EDIT]

I figured it out using the above the method prescribed by PilotJLR. I looked through the website and got what it said was the 32-bit version of Catalyst. The only problem I had was executing this code:

```
$ sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb
```

It kept complaining about xorg-driver-fglrx_8.542-0ubuntu1_i386.deb missing the fglrx-kernel-source dependancy, and kept wanting to install the one from the repos, which didn't work. Eventually I figured out the connection (that the installing line is in the wrong order) so I used this code instead:

```
$ sudo dpkg -i fglrx-kernel-source_8.542-0ubuntu1_i386.deb xorg-driver-fglrx_8.542-0ubuntu1_i386.deb  fglrx-amdcccle_8.542-0ubuntu1_i386.deb
```

and it worked.

Also note that because I basically couldn't see anything, I did everything up to configuring the xorg.conf file before putting the card in, when I turned it off, put it in, and turned it on, it was all good. I had to edit it after to stop the video from flickering (which I discovered using Skype), but it all seems good now.

Just my two cents, but I hope it helps someone.

---

### Post by lingenfr on 2008-11-01
I downloaded and upgraded the latest Intrepid 32-bit today. I downloaded the latest catalyst drivers also and followed the instructions, but no joy. It gives me an error message about needing a DKMS build first. But the bottom line is that it does not correctly build the fglrx.ko. Has anyone figured out how to get around that? I googled around and saw some patching going on for other linux versions. Looks like you all have been able to get it to work, so I can figure out why I can't.

---

### Post by lingenfr on 2008-11-02
Bump

---

### Post by PilotJLR on 2008-11-02
You need to follow the instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method)

That link will tell you what you need to install as dependencies.

In other words:
```

$ sudo apt-get update
$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r) 

```

If you have already done this, then something is amiss... a copy-paste of the error message would help. But it sounds like you're just missing dependencies, which this code will take care of.

---

### Post by lingenfr on 2008-11-02
Thanks for the reply. Actually, I followed these:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)

since I'm running Intrepid rather than Hardy. I checked the line in question and it is the same anyway.

When I execute the command in step 5 (32-bit) I get the following:

--------------------------------------------------------------------------
lingenfr@MPC-MBR:~/ati$ sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 97510 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.542-0ubuntu1_i386.deb) ...
dpkg - warning: downgrading fglrx-kernel-source from 2:8.543-0ubuntu4 to 2:8.542-0ubuntu1.
Preparing to replace fglrx-kernel-source 2:8.543-0ubuntu4 (using fglrx-kernel-source_8.542-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.542-0ubuntu1_i386.deb) ...
Setting up fglrx-kernel-source (2:8.542-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.542/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-7-generic (i686) first.
Done.

Setting up xorg-driver-fglrx (2:8.542-0ubuntu1) ...
Installing new version of config file /etc/ati/signature ...
Installing new version of config file /etc/ati/authatieventsd.sh ...
Installing new version of config file /etc/ati/atiogl.xml ...

Processing triggers for man-db ...
Setting up fglrx-amdcccle (2:8.542-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
--------------------------------------------------------------------------

/var/lib/dkms/fglrx/8.542/build/make.log really says nothing, but /var/lib/dkms/fglrx/8.542/build/make.sh.log says:

lingenfr@MPC-MBR:/var/lib/dkms/fglrx/8.542/build$ more make.sh.log 
ATI module generator V 2.0                                         
==========================                                         
initializing...                                                    
build_date =Sun Nov 2 19:41:03 EST 2008                            
uname -a =Linux MPC-MBR 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i68
6 GNU/Linux                                                                     
uname -s =Linux                                                                 
uname -m =i686                                                                  
uname -r =2.6.27-7-generic                                                      
uname -v =#1 SMP Thu Oct 30 04:18:38 UTC 2008                                   
uid=0(root) gid=0(root) groups=0(root)                                          
.                                                                               
drwxr-xr-x 32 root root 4096 2008-11-01 18:47 /usr/include                      
.                                                                               
total 12                                                                        
drwxr-xr-x  2 root root 4096 2008-11-02 19:40 fglrx-8.542                       
drwxr-xr-x 22 root root 4096 2008-11-01 18:24 linux-headers-2.6.27-7            
drwxr-xr-x  7 root root 4096 2008-11-01 18:24 linux-headers-2.6.27-7-generic    
.                                                                               
file /lib/modules/2.6.27-7-generic/build/include/linux/agp_backend.h says: AGP=1
OsVersion says: SMP=1                                                           
file /proc/kallsyms says: SMP=1                                                 
file /lib/modules/2.6.27-7-generic/build/include/linux/autoconf.h says: SMP=1   
file /lib/modules/2.6.27-7-generic/build/include/linux/autoconf.h says: MODVERSI
ONS=1                                                                           
.                                                                               
CC=gcc                                                                          
cc_version=                                                                     
found major but not minor version match for gcc and the ip-library              
ls -l ./libfglrx_ip.a                                                           
lrwxrwxrwx 1 root root 18 2008-11-02 19:41 ./libfglrx_ip.a -> libfglrx_ip.a.GCC4
.                                                                               
cleaning...                                                                     
patching 'highmem.h'...                                                         
assuming new VMA API since we do have kernel 2.6.x...                           
def_vma_api_version=-DFGL_LINUX253P1_VMA_API                                    
 Assuming default VMAP API                                                      
 Assuming default munmap API                                                    
doing Makefile based build for kernel 2.6.x and higher                          
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.542/bu
ild modules                                                                     
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'           
  CC [M]  /var/lib/dkms/fglrx/8.542/build/firegl_public.o                       
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;__ke_printk&#8217;:     
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:1915: warning: format not a stri
ng literal and no format arguments                                              
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;__ke_flush_cache&#8217;:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:2791: error: too many arguments 
to function &#8216;smp_call_function&#8217;                                                 
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;__ke_vm_phys_addr_
str&#8217;:                                                                           
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3522: warning: return makes poin
ter from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3523: warning: return makes poin
ter from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3524: warning: return makes poin
ter from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3526: warning: return makes poin
ter from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;KCL_enable_pat&#8217;:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:4063: error: too many arguments
to function &#8216;smp_call_function&#8217;
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;KCL_disable_pat&#8217;:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:4082: error: too many arguments
to function &#8216;smp_call_function&#8217;
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: At top level:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:5774: warning: initialization fr
om incompatible pointer type
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:5800: warning: initialization fr
om incompatible pointer type
make[2]: *** [/var/lib/dkms/fglrx/8.542/build/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.542/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
--------------------------------------------------------------------------

I am over my head here. Any help appreciated.

---

### Post by lingenfr on 2008-11-02
OK, I remembered that after the last failure, I was offered an upgrade on the three packages and because it wasn't working, I tried it. So, I went back and did a:

sudo apt-get remove fglrx-kernel-source 

and went back through the steps again. When I tried step 5 again, here is what I got:

---------------------------------------------------------------------------
lingenfr@MPC-MBR:~/ati$ sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb
(Reading database ... 97631 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 2:8.542-0ubuntu1 (using xorg-driver-fglrx_8.542-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace fglrx-kernel-source 2:8.542-0ubuntu1 (using fglrx-kernel-source_8.542-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-amdcccle 2:8.542-0ubuntu1 (using fglrx-amdcccle_8.542-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Setting up fglrx-kernel-source (2:8.542-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.542/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-7-generic (i686) first.
Done.

Setting up xorg-driver-fglrx (2:8.542-0ubuntu1) ...

Processing triggers for man-db ...
Setting up fglrx-amdcccle (2:8.542-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
--------------------------------------------------------------------------

and make.sh.log says:

--------------------------------------------------------------------------
lingenfr@MPC-MBR:/var/lib/dkms/fglrx/8.542/build$ more make.sh.log
ATI module generator V 2.0                                        
==========================                                        
initializing...                                                   
build_date =Sun Nov 2 20:01:34 EST 2008                           
uname -a =Linux MPC-MBR 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i68
6 GNU/Linux                                                                     
uname -s =Linux                                                                 
uname -m =i686                                                                  
uname -r =2.6.27-7-generic                                                      
uname -v =#1 SMP Thu Oct 30 04:18:38 UTC 2008                                   
uid=0(root) gid=0(root) groups=0(root)                                          
.                                                                               
drwxr-xr-x 32 root root 4096 2008-11-01 18:47 /usr/include                      
.                                                                               
total 12                                                                        
drwxr-xr-x  2 root root 4096 2008-11-02 20:01 fglrx-8.542                       
drwxr-xr-x 22 root root 4096 2008-11-01 18:24 linux-headers-2.6.27-7            
drwxr-xr-x  7 root root 4096 2008-11-01 18:24 linux-headers-2.6.27-7-generic    
.                                                                               
file /lib/modules/2.6.27-7-generic/build/include/linux/agp_backend.h says: AGP=1
OsVersion says: SMP=1                                                           
file /proc/kallsyms says: SMP=1                                                 
file /lib/modules/2.6.27-7-generic/build/include/linux/autoconf.h says: SMP=1   
file /lib/modules/2.6.27-7-generic/build/include/linux/autoconf.h says: MODVERSI
ONS=1                                                                           
.                                                                               
CC=gcc                                                                          
cc_version=                                                                     
found major but not minor version match for gcc and the ip-library              
ls -l ./libfglrx_ip.a                                                           
lrwxrwxrwx 1 root root 18 2008-11-02 20:01 ./libfglrx_ip.a -> libfglrx_ip.a.GCC4
.                                                                               
cleaning...                                                                     
patching 'highmem.h'...                                                         
assuming new VMA API since we do have kernel 2.6.x...                           
def_vma_api_version=-DFGL_LINUX253P1_VMA_API                                    
 Assuming default VMAP API                                                      
 Assuming default munmap API                                                    
doing Makefile based build for kernel 2.6.x and higher                          
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.542/bu
ild modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /var/lib/dkms/fglrx/8.542/build/firegl_public.o
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;__ke_printk&#8217;:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:1915: warning: format not a stri
ng literal and no format arguments
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;__ke_flush_cache&#8217;:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:2791: error: too many arguments
to function &#8216;smp_call_function&#8217;
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;__ke_vm_phys_addr_
str&#8217;:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3522: warning: return makes poin
ter from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3523: warning: return makes poin
ter from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3524: warning: return makes poin
ter from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3526: warning: return makes poin
ter from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;KCL_enable_pat&#8217;:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:4063: error: too many arguments
to function &#8216;smp_call_function&#8217;
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function &#8216;KCL_disable_pat&#8217;:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:4082: error: too many arguments
to function &#8216;smp_call_function&#8217;
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: At top level:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:5774: warning: initialization fr
om incompatible pointer type
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:5800: warning: initialization fr
om incompatible pointer type
make[2]: *** [/var/lib/dkms/fglrx/8.542/build/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.542/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
--------------------------------------------------------------------------

Let me know if there is anything else I can do to troubleshoot. Thanks.

---

### Post by lingenfr on 2008-11-03
Bump

---

### Post by lingenfr on 2008-11-04
And again. Help please.

---

### Post by PilotJLR on 2008-11-05
lingenfr,
I missed that you're running Intrepid... I've only done this build on Hardy amd64, so I don't think I'll be able to help, since I can't reproduce your problem.

But... based on the error messages you posted, I'm wondering if the ATI driver simply won't compile against the 27 kernel in Intrepid. I do NOT know that as a fact - it's just my hunch. 

I don't have a solution for you. Maybe someone else here can confirm or deny if this driver works in Intrepid right now?


Personally - I got fed up with some other bugs in the ATI driver and replaced the card with an nvidia 9800GT.

---

### Post by lingenfr on 2008-11-06
Pilot, me too. I started with nvidia but it would not work with my nvidia motherboard.

---

### Post by lingenfr on 2008-11-08
Bump, still need help.

---

### Post by rmbell on 2008-11-09
> **lingenfr said:**
> I downloaded and upgraded the latest Intrepid 32-bit today. I downloaded the latest catalyst drivers also and followed the instructions, but no joy. It gives me an error message about needing a DKMS build first. But the bottom line is that it does not correctly build the fglrx.ko. Has anyone figured out how to get around that? I googled around and saw some patching going on for other linux versions. Looks like you all have been able to get it to work, so I can figure out why I can't.



try installing the "dkms" package and the "build-essential" package.

---

### Post by lingenfr on 2008-11-09
I have read every post I can find and it seems that the 42 version of the Catalyst drivers that are available at the ATI website are not the right ones. The ones in the repository are newer (43) and intended to work with intrepid and the newer version of X. I have tried them and the ati driver and I can't get either to work. My card is an ASUS EAH4670 HDMI. Before anyone starts, I am connecting to the SVGA 15-pin connector, not the HDMI connector. When everything is installed per the directions, the system boots to the point of saying 'Checking battery state'. The screen flashes once or twice like it is going to bring up the GUI and then nothing. The computer is not locked up. If I hit the power button or ctrl-alt-del the computer shuts down in an orderly fashion. I am stumped.

---

### Post by lingenfr on 2008-11-09
OK, so I think that I am following the intended method. I used the KDE restricted driver manager and installed the ATI drivers from the repositories. The installation seems to complete successfully. When I reboot, all seems to be well, but instead of a login screen, it drops to a screen of text and the last entry (under Starting kdm) is Checking battery state. The screen will flash once or twice like it is trying to start, but no joy. All I can do is ctrl-alt-del and let it shutdown, then restart in recovery mode and use the fix graphics option then resume. Posted below is my /var/log/Xorg.0.log from one of the failed sessions:
--------------------------------------------------------------------------
z
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux MPC-MBR 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  9 13:26:14 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xfebf0000/0, I/O @ 0x0000e000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.54.3
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 02@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.543.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 10 2008 21:37:39
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x9490) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x9669a60
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 2 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(II) fglrx(0): PCS database file /etc/ati/amdpcsdb not found
(II) fglrx(0):   Creating PCS database from initial defaults instead
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 4670" (Chipset = 0x9490)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x0268)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(EE) fglrx(0): No valid linear framebuffer address
(EE) fglrx(0): PreInitConfig failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
SetVBEMode failed
(II) UnloadModule: "fglrx"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
--------------------------------------------------------------------------

In order to try something different this time, rather than connecting to the HD15/SVGA connector, I used the DVI->HD15 adapter and connected to the DVI port on the card. Same results. Help.

---

### Post by lingenfr on 2008-11-10
Bump.

---

### Post by lingenfr on 2008-11-11
Bump bump.

---

### Post by spudgunner on 2008-11-11
I'd like to help you out, as I have the exact same video card, but I need my computer for school and don't really have the time to play around with it for now. However, if this problem still isn't solved by the beginning of December, I'll have some free time to upgrade Ubuntu, play around with my computer, and possibly help you out.

I know it's not that soon, but nobody else appears to have a solution this far. I'll do my best, but hopefully someone else will figure it out before then.

Josh

---

### Post by lingenfr on 2008-11-15
Well, my DVI-D cable arrived and as could be expected, I got the same results. As this is an affordable card, I would think that others have it and have it working. If you have either the 4670 or the 4650 working with hardware accelerated 3D under *buntu (or any linux for that matter) please post the following:

1) Version (i.e. Hardy 32 or 64-bit, Intrepid, etc)
2) Drivers (Drivers from Restricted Driver manager, from ATI website, etc)
3) Card type (Brand, model)
4) Your xorg.conf
5) Any special tweaks, etc. to get it working

Thanks.

---

### Post by ilovesocks on 2008-11-17
I've got an HD 4670 (made by HIS) set up with the radeonhd drivers on Xubuntu 8.04. It works okay, as I can set the resolution as I want, but there is no video acceleration, so I have to use the x11(XImage/Shm) driver in mplayer instead of X11/xv (or it lags a lot and uses lots of CPU), which means no full-screening.

I've been trying to configure the proprietary drivers, but as others have said, it hangs when X starts and then starts up in low-graphics mode, after which I just change the drivers back to radeonhd. I've tried both the repository and manual installations, and it happens both ways. Here's the xorg.conf that aticonfig comes up with:

```
Section "ServerLayout"
  Identifier     "Default Layout"
  Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
  Option      "AIGLX" "Off"
EndSection

Section "InputDevice"
  Identifier  "Generic Keyboard"
  Driver      "kbd"
  Option      "XkbRules" "xorg"
  Option      "XkbModel" "pc105"
  Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
EndSection

Section "Monitor"
  Identifier   "Samsung T260HD"
  HorizSync    30.0 - 81.0
  VertRefresh  56.0 - 75.0
  ModeLine     "1920x1200" 204.9 1920 2024 2272 2744 1200 1200 1203 1244
EndSection

Section "Device"

# Driver      "radeonhd"
  Identifier  "ATI HD4670"
  Driver      "fglrx"
  Option      "UseFastTLS" "1"
  BusID       "PCI:1:0:0"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device     "ATI HD4670"
  Monitor    "Samsung T260HD"
  DefaultDepth     24
  SubSection "Display"
    Depth     24
    Modes    "1920x1200_60.00"
  EndSubSection
EndSection

Section "Extensions"
  Option      "Composite" "Off"
EndSection

```

Just an account of another person who can't get fglrx working with an HD 4670.

---

### Post by lingenfr on 2008-11-17
I would be interested in your posting the xorg.conf that you have working with the radeonhd driver. Thanks.

---

### Post by whocarez on 2008-11-17
As far as I know the HD4000-series are not supported by the fglrx driver (8.543) currently in the repository, so I wouldn't bother messing with it. Newer drivers from ATI/AMD supposedly support this card, but then again, as far as I know, they do not support Xorg 1.5.x yet.

I guess your only choice for the moment being would be the radeonhd-driver. You won't get DRI (3D support). I think the 1.2.1 driver in the repositories do not support RV7xx cards, so you might need to follow this howto:

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by lingenfr on 2008-11-26
I have been camping on Phoronix as they seem to provide the latest on this issue. Some news today:

[http://www.phoronix.com/scan.php?page=news_item&px=Njg3OA](http://www.phoronix.com/scan.php?page=news_item&px=Njg3OA)

---

### Post by titicaca on 2008-11-29
I also have the HD4670 but it now works for me in ubuntu 8.10 (intrepid), you need to install the latest AMD driver v8.11 released on Nov. 12, 2008.

Ubuntu 8.10 came with xorg v7.4 and amd's previous driver only supported 7.3.  

The latets driver from amd now supports 7.4.  Download the driver and install it and you're good to go..

---

### Post by quarkster on 2008-12-02
After a few days of tweaking and reading other forums about the HD4670 and Ubuntu 8.10, this is what I came up with for my xorg.conf file:


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "Xinerama" "off" # may or may not need this
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dbe"
	Load  "freetype"
	Load  "extmod"
	Load  "glx"
	Load  "dri"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "TexturedVideo" "off"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "off"
	Option	    "TexturedXrender" "off"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
	Option	    "mtrr" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection


Only problems I have as of now are with some of the OpenGL apps like some screen savers.  Other than that, compiz works great!  I can have a DVD playing with either totem or VLC on one desktop, while playing some other video (mpg, mov...etc) on another desktop, and watching some youtube videos on yet another with the desktop cube spinning around.  No jitters or tearing of any of the videos.

Pentium D 935 3.2GHz
GA-P35-DS3L
Kingston 2GB ram
WD SATA 500GB
*ATI Radeon HD4670*

Using the ATI driver from EnvyNG 8.543
And, if anyone has any suggestions, I'd be happy to try them.
I'm a major tweaker not afraid of crashing out the entire system and having to do a complete reinstall.

---

### Post by spudgunner on 2008-12-04
I did say I was gonna work on it come December... unforunately, I forgot my laptop at the g/f's, and I can't afford to mess up this computer as I have exams to study for. Sorry.

---

### Post by lingenfr on 2008-12-04
Quarkster, thanks for the information. I am reluctant to fool with EnvyNG, but I will give it a shot. I will probably try restricted manager again with your xorg.conf first. I also don't care about compiz and spinning cubes, but I will try it to see if I can replicate your results. I just want to get 3D working adequately. Like you, I can reload mine completely if I have to. Over at the kubuntu forums, one fellow said that he got his working using MEPIS. MEPIS (and LinuxMint) wouldn't even load on mine.

spud, thanks for the update...

---

### Post by quarkster on 2008-12-04
Just as a side note, I did try it with the ATI/AMD proprietary FGLRX drivers from the System >Administration >Hardware Drivers and the results are the same.  It also will add one extra line in the xorg.conf file

Section "Module" 
        Load "GLcore"

Just add all the other info from my xorg.conf file and the graphics should run identical with the EnvyNG driver.

---

### Post by lingenfr on 2008-12-05
I tried the restricted manager last night and no joy. It is still giving me errors and x pukes without starting. I will try your xorg.conf and see what that does for me. I am getting the bad feeling that my ECS motherboard is part of the problem. Thanks for the additional feedback.

---

### Post by spudgunner on 2008-12-05
I figure since I'm not directly working on it (for now), I'll post up that stuff you wanted... maybe it'll help:

Version: Hardy 32-bit

Driver: The one off the ATI website, version 8.10 (for Linux x86)

Card Type: Asus EAH4670

xorg.conf

```
 Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"off"
	Option		"OpenGLOverlay"	"on"
	Option		"TexturedVideo"	"off"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
EndSection 
```

---

### Post by ulletal on 2008-12-11
I have been able to install and enable restricted drivers for the 4670 and aparently have fglrx running. I can now set the resolution up to what i want and it looks fine, but some features of Compiz-fusion are not working properly (just tried it to test if drivers were working fine) and I cant play web videos in sites like youtube although having the plugins installed (it just gets blank before playing). When I change my xorg.cong to some of your proposals, ubuntu is not able to start up properly after reboot (does not even let me switch to other terminals with ctl+alt+f.. nor ask for account names and pw).

My xorg.conf is as follows:


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dbe"
	Load  "freetype"
	Load  "extmod"
	Load  "glx"
	Load  "dri"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	 "Composite" "Enable"
EndSection



Anyone has any ideas why this is happening?
Thanks in advance.

---

### Post by lingenfr on 2008-12-11
In konsole if you type:

glxinfo|grep direct

Does it say 'Direct Rendering: Yes'? If you get any errors, post them. You might also want to try:

glxgears 

and check the average FPS.

---

### Post by ulletal on 2008-12-12
when typing glxinfo|grep direct it says: 

direct rendering: Yes

with no error, and with glxgears it shows the gears spinning and gives:

304 frames in 5.0 seconds = 60.719 FPS
301 frames in 5.1 seconds = 59.526 FPS
303 frames in 5.0 seconds = 60.505 FPS
300 frames in 5.0 seconds = 59.948 FPS
300 frames in 5.0 seconds = 59.999 FPS
300 frames in 5.0 seconds = 59.944 FPS
300 frames in 5.0 seconds = 59.955 FPS

---

### Post by spudgunner on 2008-12-12
I did a clean install of Ubuntu today to figure this out... turns out ATI released another version of their driver on the 10th, which I wasn't aware of until about 10 min ago, but anywho... it works perfectly. Here's my setup:

Ubuntu 8.10 32-bit
Driver: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
Card Type: Asus EAH4670
xorg.conf:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

I followed instructions here work:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

I used the "Installing the restricted drivers manually" section to install the drivers, and also did the configuration, since on a clean install of Ubuntu, I haven't used fglrx previously.

Video from YouTube works flawlessly (no flicker). Compiz rotating cube and fire writing works (just used these ones to test). And watching YouTube while rotating the cube works flawlessly (again, no flicker).

I hope this is able to help some people out.

Josh

---

### Post by lingenfr on 2008-12-12
> **ulletal said:**
> when typing glxinfo|grep direct it says: 

direct rendering: Yes

with no error, and with glxgears it shows the gears spinning and gives:

304 frames in 5.0 seconds = 60.719 FPS
301 frames in 5.1 seconds = 59.526 FPS
303 frames in 5.0 seconds = 60.505 FPS
300 frames in 5.0 seconds = 59.948 FPS
300 frames in 5.0 seconds = 59.999 FPS
300 frames in 5.0 seconds = 59.944 FPS
300 frames in 5.0 seconds = 59.955 FPS

Your FPS are so low as to be worthless. I expect that accounts for your 3D problems. Others may be able to assess your xorg.conf and see a setting you need to change.

---

### Post by lingenfr on 2008-12-12
> **lingenfr said:**
> I tried the restricted manager last night and no joy. It is still giving me errors and x pukes without starting. I will try your xorg.conf and see what that does for me. I am getting the bad feeling that my ECS motherboard is part of the problem. Thanks for the additional feedback.

Well after further testing and research, I have determined that my ECS GF7050VT-M motherboard is a piece of !@#$%^. I broke down and ordered a Gigabyte GA-EP45-UD3P which from all my research appears to be a board that will work. I am glad that folks are having some luck with their 4670's.

Follow-up. I got the new board. It is great (but required a different PS than the ECS). I went back to my Nvidia 9600GSO that I wanted to use in the first place. Thanks for everyone's help.

---

### Post by spudgunner on 2008-12-12
Turns out there is one problem... Webcam flickers...

---

### Post by Israphel on 2008-12-14
What about the 8.12 Catalyst Drivers released on December 10th, are they better for the 4870?

---

### Post by spudgunner on 2008-12-14
> **Israphel said:**
> What about the 8.12 Catalyst Drivers released on December 10th, are they better for the 4870?

I'd assume so... the driver I used to get my 4670 working is actually the 48xx driver. Follow the instructions at the link I posted earlier and you should be good.

---

### Post by Israphel on 2008-12-15
I made a mistake. 4670, not 4870. I'll try the steps in that Wiki.

---

### Post by ulletal on 2008-12-17
I tried the instructions in the wiki several times and with some clean ubuntu installs ang got no luck, so I decided to try the installer instuctions in the download link: 

[http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

It basically says to type the command:

```
sh ./ati-driver-installer-8-12-x86.x86_64.run
```

and select between a couple of choices. This solution worked for me and is much easier and shorter than the offered in the wiki.

Now my xorg.conf looks like:


[PHP]Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "es"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
[/PHP]

I later realised that the problems I had with the flash players where due to some other issues that were solved by following the instructions in this link:

[http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")


I think I forgot to say in previous posts that all this has been done and works in a 64 bit installation of Hardy 8.04. Now Compiz works fine and I havn't found any errors yet, but i will check if the webcam image flickers. Thank you for your help.

---

### Post by oklopnik on 2008-12-25
Hi. I'm planning to buy this card. I would like to know how it works with 8.12 drivers and are there some problems (eg, right now I have HD 3450 and have a problem with slow scrolling in applications when compiz is active, which I was unable to solve).

---

### Post by ilovesocks on 2009-01-06
> **lingenfr said:**
> I would be interested in your posting the xorg.conf that you have working with the radeonhd driver. Thanks.

Sorry for the late reply, I forgot about this thread. Here's my xorg.conf, which works with radeonhd. Note that I'm on Xubuntu 8.04, not 8.10.

```

Section "InputDevice"
  Identifier  "Generic Keyboard"
  Driver      "kbd"
  Option      "XkbRules"  "xorg"
  Option      "XkbModel"  "pc105"
  Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
EndSection

Section "Device"
  Identifier    "ATI HD4670"
  Driver      "radeonhd"
# Driver      "fglrx"
EndSection

Section "Extensions"
  Option      "Composite" "Off"
EndSection

Section "ServerFlags"
  Option      "AIGLX" "Off"
EndSection

Section "Monitor"
  Identifier    "Samsung T260HD"
  HorizSync     30-81
  VertRefresh   56-75
  Modeline "1920x1200" 204.95  1920 2024 2272 2744  1200 1200 1203 1244
EndSection

Section "Screen"
  Identifier    "Default Screen"
  Device        "ATI HD4670"
  Monitor       "Samsung T260HD"
  DefaultDepth  24
  SubSection "Display"
    Depth   24
    Modes   "1920x1200_60.00"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
EndSection

```

---

### Post by spudgunner on 2009-01-06
Turns out DVD video seems to flicker as well on mine... maybe it's only flash video that works, I don't know, I'll test some more when I get back home... anybody have any ideas of how to fix the flicker?

---

### Post by ilovesocks on 2009-01-06
Wow! Just installed the 8.12 ATI Proprietary Drivers and they work like a charm!

The steps I followed:
[LIST]
[*]Download the driver from ATI (in my case, the x86_64 version)
[*]chmod +x on the file and sudo execute it
[*]Go through the installation
[*]Do sudo aticonfig --initial --input=/etc/X11/xorg.conf (backup your original xorg.conf first, of course)
[*]Edit /etc/X11/xorg.conf to make sure there are no remnants of the original xorg.conf (see below)
[/LIST]

aticonfig didn't do such a great job editing my xorg.conf - I had to comment out a lot of the original configuration:
```

Section "ServerLayout"
  Identifier     "Default Layout"
  Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
  Option      "AIGLX" "Off"
EndSection

Section "InputDevice"
  Identifier  "Generic Keyboard"
  Driver      "kbd"
  Option      "XkbRules" "xorg"
  Option      "XkbModel" "pc105"
  Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
EndSection

#Section "Monitor"
# Identifier   "Samsung T260HD"
# HorizSync    30.0 - 81.0
# VertRefresh  56.0 - 75.0
# ModeLine     "1920x1200" 204.9 1920 2024 2272 2744 1200 1200 1203 1244
#EndSection

Section "Monitor"
  Identifier   "aticonfig-Monitor[0]-0"
  Option      "VendorName" "ATI Proprietary Driver"
  Option      "ModelName" "Generic Autodetecting Monitor"
  Option      "DPMS" "true"
EndSection

#Section "Device"

# Driver      "fglrx"
# Identifier  "ATI HD4670"
# Driver      "radeonhd"
#EndSection

Section "Device"
  Identifier  "aticonfig-Device[0]-0"
  Driver      "fglrx"
  BusID       "PCI:1:0:0"
EndSection

#Section "Screen"
# Identifier "Default Screen"
# Device     "ATI HD4670"
# Monitor    "Samsung T260HD"
# DefaultDepth     24
# SubSection "Display"
#   Depth     24
#   Modes    "1920x1200_60.00"
# EndSubSection
#EndSection

Section "Screen"
  Identifier "aticonfig-Screen[0]-0"
  Device     "aticonfig-Device[0]-0"
  Monitor    "aticonfig-Monitor[0]-0"
  DefaultDepth     24
  SubSection "Display"
    Viewport   0 0
    Depth     24
  EndSubSection
EndSection

Section "Extensions"
  Option      "Composite" "Off"
EndSection

```

It started right up at 1920x1200 resolution, I can use x11/Xv drivers in mplayer (fullscreen movies!), and Flash video and DVD playback all work fine!

EDIT: I don't use Compiz.

---

### Post by spudgunner on 2009-01-07
I tried using some of the settings according to your xorg.conf file. Video works great now, however, desktop effects are broken, even after I've restored my original xorg.conf (and the video still works)... I'm working on that now, but if anyone has suggestions, let me know.

Reinstalling compiz didn't work either... keeps telling me the desktop effects can't be enabled, with no explaination

---

### Post by ilovesocks on 2009-01-07
Oh, I don't use Compiz - can't help you there.

---

### Post by markbuntu on 2009-01-07
You need Composite "on" and AIGLX "on" for compiz to work. These are turned on by default. You can return the driver to defaults by running

aticonfig --initial -f

Many options that people use in xorg.conf do not work for all cards and some that used to work will break the newer drivers.

To fix a lot of problems with video playback you can go to System/Preferences/Multimedia Systems Selector/Video/Default Output/Plugin/X Window System (No Xv) and then change vlc etc to use gstreamer. For the rest just turn off compiz.

---

### Post by spudgunner on 2009-01-08
Thanks for the advice, it is looking that way to me. I tried turning textured video off as per the Hardy instructions but it just went blank screen for me, and by screwing around I've found the compiz is causing the problems. Thanks for your help.

---

### Post by grant937 on 2009-01-10
I use Hardy and upgraded the kernel when notified by the upgrade manager.  I have a ATI 4670 graphics card and when I boot with the new kernel I get a black screen and the system freezes.  A total freeze, not able to toggle to another screen.  I read some posts and can I uninstall the ATI Driver on the previous kernel, which works and uses ATI's 8.12 driver, and reinstall it to get the system to work with the new kernel. 

Thanks

---

### Post by grant937 on 2009-01-11
> **grant937 said:**
> I use Hardy and upgraded the kernel when notified by the upgrade manager.  I have a ATI 4670 graphics card and when I boot with the new kernel I get a black screen and the system freezes.  A total freeze, not able to toggle to another screen.  I read some posts and can I uninstall the ATI Driver on the previous kernel, which works and uses ATI's 8.12 driver, and reinstall it to get the system to work with the new kernel. 

Thanks

Solution:  Maybe this will help someone who upgraded the kernel and lost the screen.  I booted the machine in recovery mode under the new kernel, went to the root terminal, then to my home directory where I saved the ATI Catalyst™ 8.12 Proprietary Linux x86 Display Driver.  I installed the driver and the normal login procedure works.  I don't know this as a fact but from what I read until the new driver is in the Ubuntu Repositories anytime a new kernel is installed you have to install the ATI Driver.  Maybe someone can verify this.

---

### Post by spudgunner on 2009-01-23
There have been a few X.org updates lately, and they seem to fix flickering video with Compiz enabled, so make sure you are up to date if your video is flickering.

---

### Post by Randomperson_1000 on 2009-02-19
Seems like people have this card working now but i still can't. I'm a noob so plz bare with me.

I've tried the 8.12 drivers but at boot i get a message saying that screens have been found but none have a usable screen configuration. I've tried editing the xorg.conf file and removing any remnants of the old configuration.

Has anyone had the same problem? I was thinking of manually editing the xorg.conf file and adding a line with my monitors supported resolution.

plz som1 help iv spent hours trying to get this to work i get the feeling im doing something wrong since every1 has the drivers working. Also the 9.1 drivers dont seem to help either.

---

### Post by Randomperson_1000 on 2009-03-01
bump

anyone with any ideas?

I was going through my xorg file I noticed that my screen isnt detected it just says generic could that be the problem. I've noticed my computer has a problem with linux and x. Im actually lucky when other distros manage to boot with a gui.

---

### Post by Sir Prospect on 2009-04-13
So how do i install The driver of Ati Sapphire HD4670 on Ubuntu 8.10?

---

### Post by Randomperson_1000 on 2009-04-14
[QUOTE=ilovesocks;6507630]Wow! Just installed the 8.12 ATI Proprietary Drivers and they work like a charm!

The steps I followed:
[LIST]
[*]Download the driver from ATI (in my case, the x86_64 version)
[*]chmod +x on the file and sudo execute it
[*]Go through the installation
[*]Do sudo aticonfig --initial --input=/etc/X11/xorg.conf (backup your original xorg.conf first, of course)
[*]Edit /etc/X11/xorg.conf to make sure there are no remnants of the original xorg.conf (see below)
[/LIST]

Just follow these instructions posted by ilovesocks. It wasnt the solution for me i had some other weird problem but i have the drivers working now.

remeber to rnu the commands in a terminal and you will need to be root for some of the commands

---

### Post by carrizo88 on 2009-12-31
Hello I have LInux tenog Miny 8 Elena and an ATI HD 4670 I do not recognize the video card can install the drivers not to drop internet ATI official page and not understand the last post that theoretically explains the problem as I am new at this and have not much idea.
I do not speak English so I use google translator: S if they could make more clear the last post to see if I can solucianarlo


HELP!! PLZ HELP!!!

---

### Post by kronictokr on 2010-01-06
should be same series as mine, if youre running 64 bit try this, you do need internet though.

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

[COLOR="black"][COLOR="Green"]**Install the fglrx Driver from ATI Catalyst 9.12 For Ubuntu 9.10 Karmic**[/COLOR][/COLOR]


We have to create a folder to enable the instalation process
          location  filename
            VVVV       VVV
create /usr/share/ati "ati"

to do this, enter in a terminal the following command

sudo nautilus

then click "file system" from the left side of the window, then double click the file "usr" and the same with "share". once inside the "share folder, right click on a blank space, click create file, name it "ati".  

leave the nautilus window open while you do the next step

download the 64bit driver from this link
VVVVVVVV
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run)

now copy the downloaded file, or drag it into the file you created , (/usr/share/ati  <location reminder )still open in your nautilus window.

when you have placed the "ati-driver-installer-9-12-x86.x86_64.run" file into /usr/share/ati , close your nautilus window, and type the next command into a terminal.

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

this will take a couple minutes as it gathers the proper pakages for your ati gpu. it will create debs and a change log , that will install with the following method

sudo dpkg -i *

there will be missing dependancies, go to SYSTEM>>>SYNAPTICS , and select edit top left , scroll down to and click on fix broken pakages. the click on apply, and lastly click on reload.

now go back to your terminal (to ensure ALL neded pakages are installed, and correctly follow this process exactly)
so, like i was saying, in your terminal, enter the following commands

sudo dpkg -i *

sudo aticonfig --initial

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic


sudo dpkg -i *

sudo aticonfig --initial

sudo reboot

MAKE SURE TO COMPLETE ALL THE STEPS BEFORE YOU REBOOT!!

AFTER YOU REBOOT
vvvvvv
to confirm , in a terminal type

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 3.2.9232

if you get errors, 
do this again, but i suggest you get it right the first time

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

sudo dpkg -i *

sudo aticonfig --initial

sudo reboot



references
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf)

---

### Post by patryck on 2010-05-12
Hi, I have an ATI Radeon HD 4670 (over HDMI) on my HTPC, but inside the XBMC when running .mkv ou mpg4 files I can see only a flash of various colour when I play something, the audio and subtitles work fine. Even if I play something in VLC I can see all that I want. I don't understand the XBMC problem. 

I have the last driver of vendor drivers for ATI HD 4000 Series adapter. This can be some bug of ATI driver or XMBC config error, I have installed Ubuntu 10.04 on my HTPC.


Someone knows this problem?

---

