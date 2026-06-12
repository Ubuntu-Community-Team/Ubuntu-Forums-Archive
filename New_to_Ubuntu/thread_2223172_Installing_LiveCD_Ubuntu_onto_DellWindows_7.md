---
title: "Installing LiveCD Ubuntu onto Dell/Windows 7"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by john215 on 2014-05-09
Hello All, 

New to all things Linux. 

Recently bought "Hacking: The Art of Exploitation" which comes with LiveCD with Linux installed. 

I'm able to 'boot' Linux for the CD but invariably I get the following message:  

"Failed to start the X server (your graphical interface). It is likely that is is not set up correctly. Would you like it to view the X server output to diagnose the problem?"

I've contacted the company (NoStarch) and though extremely friendly, ostensibly there is no one there who can solve the problem. 

I've googled the above message and though initially I found some promising suggestions, ultimately none of the suggestions bore out for me. 

Some of the suggestions I have come across:

1) 

sudo dpkg-reconfigure xserver-xorg

rm ~/ config/monitors.xml

2)

sudo cp /home/ubuntu/xorg.conf.new  /etc/x11/xorg.conf

start x

3) 

sudo xorg ~configure

sudo cp /home/(username)/xorg.conf.new/etc/x11/xorg.conf

start x

The only command that would actually run was 

sudo dpkg-reconfigure xserver-xorg

but it took me through a whole series of questions that only lead me back to the command line. 

I would appreciate any help I can get in overcoming this hindrance as it seems the Linux gods are intent on suplexing me into uncle before I get started. 

Here is some info about my computer that might be helpful. 

Dell Inspiron 14R or Dell N4010 

Windows 7 Home Premium (7.2.0)

Generic PnP Monitor 

Intel (R) HD Graphics. 

Here is the only information I have about the Linux system I am trying to install, copied verbatim from a still shot. 

Current Operating System: Linux hacking 2.6.20-15-generic #2 SMP

Thanks in advance and I look forward to hearing from the community and finally being able to load this LiveCD.

---

### Post by TheFu on 2014-05-09
Welcome to the forums.

The best thing to do now is start out with the current LTS distro, released a few weeks ago - 14.04.
If your PC uses UEFI, then you'll want to carefully read the UEFI Ubuntu instructions before going any further.  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  It was much easier in the old days, pre-UEFI.

If the new release does NOT boot on the sytem, try booting any distro that will boot and running the boot-info script. It will create a URL with all the important data we need to help. More info about it is in my signature below.

---

### Post by john215 on 2014-05-09
Fu, 

thanks for the response. 

I'm currently on Ubuntu on a USB.  
 
I followed your instructions and ran the two sudo commnads but I got the following and was not able to proceed to the 3rd step. 

E: Some index files failed to download. They have been ignored, or old ones used instead.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair

I'll stay on the USB for as long as I can. 

Hope to hear from you soon.

---

### Post by JeQhdMD on 2014-05-10
Are you really trying to boot up an ancient linux CD using the 2.6.20  kernel ?   If you want a modern hacking (forensic) CD/DVD, check out distrowatch.com and get current edition of Tails iso, and burn it (or see any of several other modern security/forensic live distros).  

Your chances that your current hardware will work is much better.

---

### Post by TheFu on 2014-05-10
> **john215 said:**
> Fu, 

thanks for the response. 

I'm currently on Ubuntu on a USB.  
 
I followed your instructions and ran the two sudo commnads but I got the following and was not able to proceed to the 3rd step. 

E: Some index files failed to download. They have been ignored, or old ones used instead.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair

I'll stay on the USB for as long as I can. 

Hope to hear from you soon.

In order to help, we need to know exactly what you are doing. I cannot tell.
* which release is being used?
* which sudo commands?
* where is the boot-info URL? It is just a script.

---

### Post by coffeecat on 2014-05-10
This is the official forum for the Ubuntu family of Linux-based operating systems, not any OS that happens to use the Linux kernel, although users of other Linux distros are very welcome here. I haven't been able to find whether or not the Linux live CD included with the book Hacking, The art of Exploitation, is Ubuntu based, but that is moot because I found this on the publisher's website:

> This book will teach you how to:

[list][*]Program computers using C, assembly language, and shell scripts
[*]Corrupt system memory to run arbitrary code using buffer overflows and format strings
[*]Inspect processor registers and system memory with a debugger to gain a real understanding of what is happening
[*]Outsmart common security measures like nonexecutable stacks and intrusion detection systems
[*]Gain access to a remote server using port-binding or connect-back shellcode, and alter a server's logging behavior to hide your presence
[*]Redirect network traffic, conceal open ports, and hijack TCP connections
[*]Crack encrypted wireless traffic using the FMS attack, and speed up brute-force attacks using a password probability matrix[/list]

This from our forum [Code of Conduct](http://ubuntuforums.org/misc.php?do=showrules):

> **Cracking**: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

If you need help with Ubuntu, or with any of the official Ubuntu flavours, you are very welcome to post here, but we cannot support you with this CD.

Thread closed.

---

