---
title: "error: no such partition  grub rescue&gt;"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by SUPERFITTER on 2013-03-03
I installed ubuntu 12.04 64bit on an empty hard drive. Install went ok, but I cannot get it to go on line. I formatted the disk, by making it an external drive and using another computer to format this drive. I reinstalled the hard drive in the computer and put the disk in the CD drive. I started the computer and got this on a black screen: 
error: no such partition  grub rescue>

I cannot boot off of the disk, and the hard drive is empty.  What should I do?

Thank you

---

### Post by oldfred on 2013-03-03
When you installed from the other computer did you make sure grub was installed to the external (now internal drive) or does it have an old copy of grub that cannot find its old install to boot.

You may be able to manually boot.

       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

You may be able to update grub in MBR.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Or you may be able to bypass your grub and just boot:
      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by SUPERFITTER on 2013-03-04
Hi oldfred

I read the different threads, but I could not find a solution for a hard drive that was formatted and does not contain an operating system. Is there a way to format and bring the drive back to an empty state so I can reinstall Ubuntu? All I get now is: 

error: no such partition  grub rescue>

when I use the install CD on the empty hard drive.  I can not boot from the CD now. The computer only contains the one hard drive. Sorry if I missed something.

Thank You

---

### Post by oldfred on 2013-03-04
If you get grub rescue then BIOS is seeing harddrive and is trying to boot from it. 

Some systems seem to lock up after multiple boot errors. Try full power shutdown and if laptop remove battery. Maybe wait a bit before putting battery back in.
Some have key combinationsto drain residual power, to make sure you are restarting from a total cold reboot.

---

### Post by SUPERFITTER on 2013-03-04
I found the problem, I made drive an external again and found that I missed a small partition. I formatted the section and merged it with the rest of the drive. I reinstalled Ubuntu 12.04 and got that to install.  Now I cannot get the wired connection to work. I ran this in the terminal:

dennis@dennis:~$ sudo lshw -C network
[sudo] password for dennis: 
  *-network [COLOR=#a52a2a]UNCLAIMED[/COLOR]     
       description: Ethernet controller[COLOR=#0000ff][/COLOR]
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d3ffff ioport:d000(size=128)
dennis@dennis:~$ arch
x86_64
dennis@dennis:~$ uname -r
3.2.0-29-generic
dennis@dennis:~$ cd Desktop
dennis@dennis:~/Desktop$ sudo dpkg -i *.deb
Selecting previously unselected package build-essential.
(Reading database ... 140394 files and directories currently installed.)
Unpacking build-essential (from build-essential_11.5ubuntu2_amd64.deb) ...
Preparing to replace linux-headers-generic 3.2.0.29.31 (using linux-headers-generic_3.2.0.38.46_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not installed.
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not installed.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-38-generic; however:
  Package linux-headers-3.2.0-38-generic is not installed.
dpkg: error processing linux-headers-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential
 linux-headers-generic
dennis@dennis:~/Desktop$ 

I downloaded and transferred these to my desktop:

 [http://packages.ubuntu.com/precise/build-essential](http://packages.ubuntu.com/precise/build-essential) 

 [http://packages.ubuntu.com/search?ke...se&section=all]("http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all")

I don't no what to do now.

Thank You

---

### Post by oldfred on 2013-03-04
I do not know Ethernet issues, but with nVidia you have to install headers first with 12.10 and 12.04.2.
       sudo apt-get install linux-headers-generic
    
There are a lot of threads on your Atheros drivers and how to install, but I do not have any links to them.

---

