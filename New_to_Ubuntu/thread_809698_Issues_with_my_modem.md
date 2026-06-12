---
title: "Issues with my modem"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Sigfrodr on 2008-05-27
Hello all.  I'm a new Ubuntu, and Linux, user.  This is my first time dealing with either of the two, having been a Windows user since 98, maybe 95.  I recently bought a new laptop, a HP Pavilion dv6815nr Entertainment Notebook PC which, unfortunately, came bundled with Windows Vista.  I found Vista to be very awkward and unwieldy.  Not to mention a system resource hog.  I did some looking around and came upon Ubuntu which I downloaded and installed, albeit with a clean installation.  I completely wiped my hard drive whilst installing.  After lengthy battles with Ubuntu involving getting my screen resolution correct, I have now came upon the problem of getting my modem working.  I really need to have my dial-up working and so far it's been quite a daunting task.  I have installed GnomePPP and entered the correct information, however when I hit the connect button, I get the message "Cannot open modem".  After looking online about this issue I've found the "scanmodem" tool off of linmodems.org.  I find linmodems to be wanting in ease of use.  I've downloaded the scanmodem tool, however I can't do anything with it.  

With all that being said, will one of the fine members of this community help me out?  If at all possible could I get a detailed step-by-step guide to getting my modem to work?  I'd be super happy, as I truly do enjoy Ubuntu, it's quick, it looks great, I just really enjoy the flavor of it.  I just have this one last hurdle, and if I, or we can clear it, I'd be in nirvana.  Thanks in advance, for reading this, and hopefully, for helping me out.

---

### Post by bwhite82 on 2008-05-27
Please post the results of:

lspci (type it in a terminal)

Also, make model of modem. Also, what is the full package name you downloaded from linmodem?

---

### Post by Sigfrodr on 2008-05-27
Ah, therein lies the problem.  I have no idea the make and model of my modem.  When I installed Ubuntu, I wiped Vista and my hard drive completely.  Is there a place I can go to, in Ubuntu, to find the make and model.  I've attempted to search for it using the model of my laptop, but to no avail.  Most results merely state that it comes with a 56k modem.  

The package I have downloaded from linmodems.org is called,"scanModem.gz".  Hopefully this will help.  As I am in need of help.  :)  Seriously enough though, I hope I'm not up the proverbial creek without a paddle my wiping my HD first before installing Ubuntu.  



00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by bwhite82 on 2008-05-27
Alright, please post the results of another command:

lsusb

Also, that linmodem package needs decompressed (right click on it, extract here), then rename the file that is extracted: scanModem

Then, make it executable (from a terminal and make sure to type the full path to the shell script):

sudo chmod +x /path/to/scanModem

Then run it from the terminal with:

sh /path/to/scanModem

---

### Post by Sigfrodr on 2008-05-27
Here's the results of lsusb:
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

And I'm off to do the other things you just mentioned.  Thanks by the way for taking the time to help me out.

---

### Post by Sigfrodr on 2008-05-27
Hmm, the full path name to the file, I have it stored on my desktop.  When I click on the properties I see /home/william/Desktop.  Is that the full path?  
sudo chmod +x /path/to/scanModem
 would then become
sudo chmod +x /home/william/Desktop/scanModem  
right?

---

### Post by bwhite82 on 2008-05-27
> **Sigfrodr said:**
> Hmm, the full path name to the file, I have it stored on my desktop.  When I click on the properties I see /home/william/Desktop.  Is that the full path?  
sudo chmod +x /path/to/scanModem
 would then become
sudo chmod +x /home/william/Desktop/scanModem  
right?

Correct. Also, I'm not seeing your modem showing in either lspci or lsusb, I'm trying google to see what modem you have in it. Its a dial-up modem correct?

---

### Post by Sigfrodr on 2008-05-27
Correct, it's a dial up.

And the full path name thing, for some reason, and I get this type of roadblocks a lot, I get a reply from the Terminal of "chmod: cannot access `/home/william/Desktop/scanModem': No such file or directory" when I enter the command line "sudo chmod +x /home/william/Desktop/scanModem ". I've had untold amounts of difficulty so far, I suppose I just need to be patient.

---

### Post by bwhite82 on 2008-05-27
Alright, you have a:

'Conexant HDAudio Soft Data Fax Modem' according to HP.com.

Dell provides Linux Conexant drivers which may or may not work with your particular modem. Download the file here (to your desktop)

[http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb)

Double-click to install.

Reboot.

Attempt to connect with Gnome-ppp

---

### Post by Sigfrodr on 2008-05-27
Gaah!  So close yet so far.  :)  I, unfortunately, get an error message after double-clicking entitled Error:Wrong Architecture 'i386'  What can I do about that?

---

### Post by bwhite82 on 2008-05-27
Do you have an AMD 64 bit processor? Please post the result of yet another command:

uname -r

---

### Post by Sigfrodr on 2008-05-27
Here are the results:
2.6.24-17-generic

For what it's worth, I do have a sticker on my laptop that says AMD Turion 64x2.

---

### Post by bwhite82 on 2008-05-27
Alright lets go a different route. Move the previously downloaded package to the trash.

Download this package:

[http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09x86_64oem.tar.gz](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09x86_64oem.tar.gz)

Right click on it and select 'extract here'.

Open a terminal, type in:

sudo apt-get install build-essential

Then cd to the extracted directory:

cd /home/yourusername/Desktop/hsfmodem-7.68blahblahblah (if you type the first few letters, like hsf, then hit tab it will autocomplete the rest)

Then type:

sudo make install

Then, assuming no errors:

sudo hsfconfig

Then reboot.

Open Gnome-ppp, goto setup, hit the 'Detect' button. Save the settings and connect

---

### Post by Sigfrodr on 2008-06-02
Hey thanks for the help, I've gotten further than I thought I would.  However, I'm seemingly stuck, for a reason I'm not sure of.  When I get to the step where I change directories, I'm not able to hit "tab" to autocomplete.  After entering the filename myself, still no dice.  Here is a complete list of what I've done in the terminal, following your steps.  Any more help would be eternally grateful.  Here is how far I am:

william@william-laptop:~$ sudo apt-get install build-essential
[sudo] password for william: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 8179kB of archives.
After this operation, 33.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-17.31 [694kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [2538kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1217kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [3035kB]  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu5 [1446B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main patch 2.5.9-4 [97.8kB]           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main dpkg-dev 1.14.16.6ubuntu3 [559kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7070B]
Fetched 8179kB in 14s (551kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 112548 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-17.31_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu3_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Setting up linux-libc-dev (2.6.24-17.31) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu3) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu5) ...

Setting up build-essential (11.3ubuntu1) ...
william@william-laptop:~$ cd/home/william/Desktop/hsfmodem-7.68.00.09x86_64oem
bash: cd/home/william/Desktop/hsfmodem-7.68.00.09x86_64oem: No such file or directory
william@william-laptop:~$ cd /home/yourusername/Desktop/hsfmodem-7.68
bash: cd: /home/yourusername/Desktop/hsfmodem-7.68: No such file or directory
william@william-laptop:~$ cd/home/william/Desktop/hsfmodem-7.68.00.09x86
bash: cd/home/william/Desktop/hsfmodem-7.68.00.09x86: No such file or directory
william@william-laptop:~$

---

