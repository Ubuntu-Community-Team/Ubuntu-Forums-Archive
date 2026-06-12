---
title: "RTlinux"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Maccabee on 2008-07-09
Can somebody help me with the installation of RTlinux in Ubuntu..[www.rtlinuxfree.com](www.rtlinuxfree.com)
There is a debian package rtlinux
[http://packages.qa.debian.org/r/rtlinux.html](http://packages.qa.debian.org/r/rtlinux.html)
from there i think its not maintained anymore can some body help me to figure out

the standard rtlinux installation as far as i know is by patching kernel n compiling it
so Wat is the purpose of this debian file??
wat does it do?
Will it patch thecurrent kernel n do everything automatically..??
please help

---

### Post by sdennie on 2008-07-09
To install the rt kernel on Ubuntu, just use:

```

sudo apt-get install linux-image-rt linux-headers-rt linux-restricted-modules-rt

```

When you next reboot, you will have the option to boot into the -rt kernel in grub (you may have to use <Esc> to get into the menu when grub starts to count down).

---

### Post by shantanuspathak on 2010-02-24
HI thanks,

i tried this but it says ... 
linux-image-rt not found
Plz help.

I have installed i386 package on my ubuntu 9.04.
But even after installing when i restart the ubuntu it does not give the
-rt boot option
do i have to try something else like compiling the kernel or something ?

---

### Post by lotharmat on 2010-02-24
What version of GRUB are you using?

GRUB2 will automatically add the new Kernel
GRUB1 will not - you will need to edit the menu.lst in /boot/grub
(I may have got the wrong location for this as since moving to GRUB2 I have forgotten a lot!!)

---

### Post by danger89 on 2010-04-20
Thanks!

---

### Post by ranmahs on 2010-07-15
HI.. 
After doing this i am able to boot the OS. When i am typing uname -a i am getting i am using the real time kernel. But i am not able to run not even a simple program. And I am also not able to find rtl.h and rtl.mk. Please help me

---

### Post by suhashgd on 2010-07-25
Hello everyone,

Even i am facing the same problem. I installed the RTLinux using the synaptic manager. The installation went fine and i am able to boot to RTLinux. But i cannot compile simple programs on it. I cannot find the rtl_ header files. I am using Ubuntu 10.04 and kernel version of RTLinux is 2.6.31-11-rt

Any sugesstion regarding this will be helpful.

Regards,
Suhas

---

### Post by suhashgd on 2010-07-27
Hello All,

I guess the problem is with the program that i am running. It uses rtl.h which is not present in the kernel 2.6.* . The program can only run on 2.4.* 

Does anybody know the new system calls for rt-linux or the proper way of accessing the real time feature of it....

Regards,
Suhas

---

### Post by koolkatkiwi on 2010-11-16
> **suhashgd said:**
> hello all,

i guess the problem is with the program that i am running. It uses rtl.h which is not present in the kernel 2.6.* . The program can only run on 2.4.* 

does anybody know the new system calls for rt-linux or the proper way of accessing the real time feature of it....

Regards,
suhas

bump

---

### Post by Highlander01 on 2011-01-02
I am getting stuck... on the first steps to get installed.
- I downloaded "rtlinux-3.2-wr.tar.bz2"
- I unzipped it..."tar -jxvf rtlinux-3.2-wr.tar.bz2"
 
- then I get stuck, what do I do next?
______________
-  i am trying::::  "./configure"  "make" "make install" etc...
-  nothing works.  I tried them with "sudo" also.  The [http://www.rtlinuxfree.com/](http://www.rtlinuxfree.com/) page does not tell me much.
______________
I have ubuntu 10.04 LTS lucid lynx installed.
Do I need some sort of patch to go with it.
uname -a ... returns that I have 2.6.32-122-rtai .... i686 GNU/Linux
rtai = real time linux but I do not believe this is RTLinux.

---

### Post by Highlander01 on 2011-01-03
Is linux-rt the same thing as RTLinux?  I am thinking yes.  I installed it from Synaptic Package Manager.  I think I need to run linux-rt from a boot option?  I have tried hitting esc and tab keys at boot but I am not get any boot options in ubuntu.  Are esc or tab the right keys?

---

### Post by gordie69 on 2011-01-03
I never heard of that linux but I tried kubuntu, liked the lay out but it had issues so I went back to ubuntu and been there since. The ubuntu 10 is very user friendly

---

### Post by HermanAB on 2011-01-03
Howdy,

Why do you want to run rt-linux?  The real-time mods are all in kernel-tmb, the multi-media optimized kernel.

---

### Post by Highlander01 on 2011-01-04
My goal is to pulse some stepper motor drivers thru a parallel port.  Also want to interface to RTLinux thru FIFO with Python GUI to control pulsing rates and speeds.

---

### Post by Highlander01 on 2011-01-04
I figured out my hang up.  I did not know that I was running Grub 2 with Ubuntu 10.04.  
(Sort of confusing that they made grub version 1.98 = Grub 2, would of thought it would have been 2.x something.)
 
The following web page is very helpful [[COLOR=#444444]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")
 
It explained one of my hang ups:    Hold down SHIFT to display the menu during boot (formerly ESC in GRUB legacy). 

Now after installing "linux-rt" from "synaptic package manager" I do see linux-rt option after pressing "shift" key during boot.

---

### Post by Bloque on 2011-02-12
Hello Everyone,

I am a newbie and I encountered problems installing rt-linux package on Ubuntu 10.10; the latest version as of this writing.  Please find the details of my attempt below. This is what I tried to run on terminal.

```

viswanathj@ubuntu:~$ sudo apt-get install linux-image-rt linux-headers-rt linux-restricted-modules-rt
[sudo] password for viswanathj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-rt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-image-rt' has no installation candidate
E: Unable to locate package linux-headers-rt
E: Unable to locate package linux-restricted-modules-rt


```

Thanks a lot in advance!

---

### Post by sukhoi1027 on 2011-07-07
Can we install RTLinux on a virtual machine??

---

### Post by marwenkachroudi on 2011-12-06
Hi I have also a problem .
To install rtlinux  on Ubuntu 10.4 I have taped the commend sudo apt-get install linux-image-rt linux-headers-rt linux-restricted-modules-rt

I have got this message "error"[COLOR=Red]Couldn't find package linux-restricted-modules-rt[/COLOR] "
please help

---

