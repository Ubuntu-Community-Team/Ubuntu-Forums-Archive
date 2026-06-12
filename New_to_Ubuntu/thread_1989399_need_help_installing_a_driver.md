---
title: "need help installing a driver"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by ridisempre on 2012-05-28
hi, i'm trying to install a driver on my sony vaio so that the webcam will work. i found a site that seems to have a driver. i downloaded the .tar.gz file and then extracted it. now i don't know what to do as i'm new to this. the website says:
[B]
Untar it and go inside the new created folder:
*tar xvfz r5u870-0.10.1.tar.gz*
*cd r5u870-0.10.1*
 With root privileges give this commands:
*make*
*make install*
 and then the command:
*modprobe r5u870*[/B]           

can anyone guide me through this in a simpler way? ie. what exactly i need to do. i would really appreciate it! :)

---

### Post by jtarin on 2012-05-28
You can get the files here.....there are two 32 and 64 bit....there is a driver and firmware. If you use the commands as they are and have the Linux Generic Kernel Headers installed....it should work.

---

### Post by linuxman94 on 2012-05-28
Could you post the result of this command?

```
lsusb
```

Paste the command into the terminal.  You can find the terminal by searching for it in the unity dash.  Paste the result in code tags (# sign in the editor).

---

### Post by ridisempre on 2012-05-28
> **jtarin said:**
> You can get the files here.....there are two 32 and 64 bit....there is a driver and firmware. If you use the commands as they are and have the Linux Generic Kernel Headers installed....it should work.

where can i get the files? how do i get the Linux Generic Kernel Headers installed?

---

### Post by ridisempre on 2012-05-28
> **linuxman94 said:**
>  Paste the result in code tags (# sign in the editor).

sorry, don't really know what this means...

these are the results:
Bus 005 Device 003: ID 0fce:d019 Sony Ericsson Mobile Communications AB VDC EGPRS Modem
Bus 005 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 [R5U870]
Bus 001 Device 002: ID 054c:0281 Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by linuxman94 on 2012-05-28
Are you using 32bit or 64bit? 

If 32bit, download [this]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.6-0arakhne0_i386.deb") and install it (double click and it will install with software center).

For 64bit, download [this]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.6-0arakhne0_amd64.deb") and install it.

Reboot after you have installed the correct package.

---

### Post by ridisempre on 2012-05-28
> **linuxman94 said:**
> Are you using 32bit or 64bit? 

If 32bit, download [this]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.6-0arakhne0_i386.deb") and install it (double click and it will install with software center).

For 64bit, download [this]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.6-0arakhne0_amd64.deb") and install it.

Reboot after you have installed the correct package.


it says: 

[COLOR=Red]ERROR: Dependancy is not satisfiable: ricoh-webcam-r5u870-firmware[/COLOR]

Ricoh r5u870 webcam kernel module
Linux driver for the Ricoh r5u870 webcams.
This package provides the source code for the Ricoh webcam kernel module. The ricoh-webcam-r5u870 package is also required in order to make use of these modules. Kernel sources or headers are required to compile this module.

---

### Post by linuxman94 on 2012-05-28
Ok, you need to install this package first:

[32bit]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb") [64bit]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_amd64.deb")

---

### Post by jtarin on 2012-05-28
> **ridisempre said:**
> where can i get the files? how do i get the Linux Generic Kernel Headers installed?Sorry forget to include the "url's".:P
You'll still need the headers.You can find them through Synaptic for your kernel. kernel and header versions should match. Install them first....then the other two you downloaded.

---

### Post by ridisempre on 2012-05-29
it works!!!:KS

thanks so much for your help linuxman- you made my day! now my mom can see my baby girl playing in her room and outside. :mrgreen:

thank you also jtarin for your input.

how do i mark this as solved? or does an admin do that?

---

### Post by mastablasta on 2012-05-29
top of the thread, on the right - thread tools  -> mark thread as solved.

---

### Post by jtarin on 2012-05-29
Glad you got it working!:P

---

### Post by esseppi on 2012-05-29
> **linuxman94 said:**
> Ok, you need to install this package first:

[32bit]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb") [64bit]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_amd64.deb")
Dear Linuxman, I have the same problem of Ridisempre.  I have followed your instructions to Ridisempre, and proceeded to download first:

[http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb](http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb)

No problem, went through.  And then:

[http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.6-0arakhne0_i386.deb](http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.6-0arakhne0_i386.deb)

However, as I tried to install the latter, I get this message:

PACKAGE OPERATION FAILED
The installation or removal of a software package failed

Details:
dpkg: regarding .../ricoh-webcam-r5u870_0.11.6-0arakhne0_i386 (2).deb containing ricoh-webcam-r5u870, pre-dependency problem:
 ricoh-webcam-r5u870 pre-depends on linux-headers-generic | linux-headers (>= 2.6.26)
  linux-headers-generic is not installed.
dpkg: error processing /home/stefo/Downloads/ricoh-webcam-r5u870_0.11.6-0arakhne0_i386 (2).deb (--install):
 pre-dependency problem - not installing ricoh-webcam-r5u870

Any suggestions?
Thank you!!

---

### Post by jtarin on 2012-05-29
> **esseppi said:**
> Dear Linuxman, I have the same problem of Ridisempre.  I have followed your instructions to Ridisempre, and proceeded to download first:

[http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb](http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb)

No problem, went through.  And then:

[http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.6-0arakhne0_i386.deb](http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.6-0arakhne0_i386.deb)

However, as I tried to install the latter, I get this message:

PACKAGE OPERATION FAILED
The installation or removal of a software package failed

Details:
dpkg: regarding .../ricoh-webcam-r5u870_0.11.6-0arakhne0_i386 (2).deb containing ricoh-webcam-r5u870, pre-dependency problem:
 ricoh-webcam-r5u870 pre-depends on linux-headers-generic | linux-headers (>= 2.6.26)
  linux-headers-generic is not installed.
dpkg: error processing /home/stefo/Downloads/ricoh-webcam-r5u870_0.11.6-0arakhne0_i386 (2).deb (--install):
 pre-dependency problem - not installing ricoh-webcam-r5u870

Any suggestions?
Thank you!!
Though not Linuxman, permit me to offer a suggestion(s). Read my post in this thread where I have already touched on this subject.

---

### Post by esseppi on 2012-05-29
> **jtarin said:**
> Sorry forget to include the "url's".:P
You'll still need the headers.You can find them through Synaptic for your kernel. kernel and header versions should match. Install them first....then the other two you downloaded.

Of course, thank's a lot Jtarin.  Unfortunately I do not know how to implement in practice some of the things you pont out.  I do not know what "headers" are, and the fact that I need to get them "through Synaptic for my kernel" (let alone the fact that they should "match") does not mean much because of my linux ignorance.

I would greatly appreciate your help in walking me through the steps to put in practice your suggestions.

Thank you very much for your time and help.

---

### Post by jtarin on 2012-05-29
First find "Synaptic" on your computer. What desktop are you using? You can probably just open a terminal and type ```
sudo synaptic
```or look for it in the menu. Once you find it do a search for "linux-headers-generic". The version number should be the same as the version number of your kernel. To find your kernel version open another terminal and type ```
uname -v
```. Once you have matched this with the headers in Synaptic right click on the selection then choose install. From the Synaptic toolbar click on "apply" this will download and install the headers. Once that is done return to the previous installation you were attempting to do. If you have any further error messages relating to this post back. The above is not a guarantee that it will work. It is what I would do under a similar situation.

---

### Post by esseppi on 2012-05-30
Thank you.  I did everything, get the same error message.

---

### Post by jtarin on 2012-05-30
> **esseppi said:**
> Thank you.  I did everything, get the same error message.
This line is the "gotcha"...._ricoh-webcam-r5u870 pre-depends on linux-headers-generic | linux-headers (>=[COLOR="Red"] 2.6.26[/COLOR])_.
The installation is calling for that version of headers but its an impossible situation because your kernel is....I'm guessing....about a3.x.x.x version.The only thing I can think of at this point is your going to have to compile it for your machine.
You will need to find the source code for these files.These need to be compiled. The outline and walk-through for this procedure is too lengthy for this post. I would suggest you start your own post post about compiling software. 
Heres a link with instructions for compiling generic software.
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Heres a link with instructions for compiling the r5u870 source and installing.
Be sure to read the entire page to make certain your looking for the right driver.
[http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)
> This Ricoh webcam driver is no more longer under development. It is provided for backward compatibility and source code examples.

---

### Post by linuxman94 on 2012-05-30
Are you sure you installed the kernel headers? I just tested this on my 64bit 12.04 install and it installed fine.  To make sure the kernel headers are installed, please run this in terminal. 
```
sudo apt-get install linux-headers-generic
```
 If they are installed it will say "linux-headers-generic is already the newest version."

---

### Post by esseppi on 2012-05-31
Jtarin, the procedure you suggest (compiling the files for the sourcecode) is definitely beyond my capacity... faced with that solution I will have to live without my camera in the Vaio... (btw, I have the 12.04 on 32bit)

Linuxman, I will be testing the headers installation tonight.  By the way, I have installed 12.04 at 32bit (question: do you think that by installing the 64bit version this problem would be overcome?).

Thanks guys!

---

