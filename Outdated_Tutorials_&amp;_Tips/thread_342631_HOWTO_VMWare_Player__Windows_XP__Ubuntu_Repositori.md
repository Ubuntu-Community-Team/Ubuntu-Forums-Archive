---
title: "HOWTO: VMWare Player / Windows XP / Ubuntu Repositories"
date: 2007-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by altonbr on 2007-01-20
For **VMWare Server**, please see this tutorial: [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

[B]Personal Note
[/B]As of May 5th, 2007, I've switched to using VMWare server. You can follow this tutorial almost verbatim but using "sudo aptitude install vmware-server" instead of "sudo aptitude install vmware-player" as in step 2. This is due to personal preference and the amount of virtual machines I run. One note: You have to register to receive a product-code for every vmware-server you install. That form can be found here: [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html). Anyone looking for a more advanced way to run their virtual machines, I suggest trying it. Good luck!

**A Note on Running XP on Ubuntu, through VMWare**
Running XP (or ANY operating system) on Ubuntu through VMWare presents NO security risks, no matter how insecure the OS is that is running through VMWare. The whole point of VMWare is that it's a *virtual* machine. The two can not directly communicate with each other without the means of Samba or SSH (Windows SSH program: [http://winscp.net]("http://winscp.net/")), just as you would have to communicate with a separate, physical machine.

XP will gain no security from running off a secure Ubuntu platform because the host has *nothing* to do with the VM OS. The only thing Ubuntu offers is the speed of which it is compiled with VMWare, and VMWare itself. Ubuntu also can only give it's VMs whatever peripherals it can read, so if Ubuntu can't read your printer, neither can XP.

If you get a virus in XP, you have a virus in XP and nothing else. It can not, and will not effect Ubuntu. You can have 3 instances of XP running, and only have 1 effected by a virus (unless it knows how to propagate). 

Lastly, if you're looking to ditch XP, but still hoping to play games, you CAN NOT through VMWare. You will have to dual-boot for that. Search through these forums for more on that topic. Installing VMWare Sever and then VMWare tools may give you a less-choppy effect for your graphics, but it still not recommended for games.

[B]Testing

[/B][SIZE=4]  [SIZE=2]Your kernel version:[/SIZE][/SIZE]```
uname -r
```Tested with:[LIST]
[*]Ubuntu 7.04 Feisty (on hard drive)
[*]VMWare[LIST]
[*]Player 1.0.2-2
[*]Server 1.0.2-2
[*]Server 1.0.3-1[/LIST] 
[*]QEMU  0.8.2+dfsg-0ubuntu1
[*]Ubuntu 6.06.1 LAMP Server iso
[*]Kernels:[LIST]
[*]2.6.20-15-386
[*]2.6.20-16-386[/LIST] [/LIST]and,[LIST]
[*]Ubuntu 6.10 Edgy (on hard drive)
[*]VMWare Player 1.0.2-2
[*]QEMU 0.8.2-0ubuntu1
[*]Windows XP Pro SP2 iso[/LIST]and,[LIST]
[*]Ubuntu 6.06.1 Dapper (on hard drive)
[*]VMWare Player 1.0.1-4
[*]QEMU 0.8.0-3ubuntu1
[*]Windows XP Pro SP2 iso
[*]Kernels:[LIST]
[*]2.6.15-23-386
[*]2.6.15-24-386
[*]2.6.15-27-386
[*]2.6.15-28-386 (working as of late March, 2007)[/LIST][/LIST]and,
[LIST]
[*]Xubuntu 6.06.1 Dapper (on hard drive)
[*]VMWare Server
[*]QEMU 0.8.2+dfsg-0ubuntu1-dapper1
[*]Ubuntu Dapper 6.06.1 Server
[*]Kernels:[LIST]
[*]2.6.15-23-386[/LIST][/LIST]**Here we go!**
I've noticed a couple tutorials that are quite long and convoluted so I've decided to make a simple tutorial using 10 easy steps.

[SIZE=4]**1] Update Ubuntu**[/SIZE]
```
sudo aptitude update && sudo aptitude upgrade
```[SIZE=4][B] 
2] Install VMWare Player[/B][/SIZE]
```
sudo aptitude install vmware-player
```[SIZE=4]** 3] Create a folder to store your Virtual Machines**[/SIZE]
```
mkdir ~/vmware
```[SIZE=4]
**4] Install QEMU**[/SIZE]
```
sudo aptitude install qemu
```[SIZE=4][B]
5] Create virtual drive using QEMU[/B][/SIZE]
```
qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10GB
```[LIST]
[*]the number '**[COLOR=DarkOrange]10GB[/COLOR]**' means that the virtual drive will be 10GB (so make sure you have enough room on you HD). You may change the number accordingly.
[*]The above is assuming you are using the folder "**[COLOR=Blue]~/vmware[/COLOR]**". Remove '**[COLOR=DarkOrange]vmware/[/COLOR]**' from the terminal command or change accordingly if necessary.[/LIST][SIZE=4]**6] Download the .vmx file**[/SIZE]
Supplied by help.ubuntu.com at: [https://help.ubuntu.com/community/VMware/Player?action=AttachFile&do=get&target=WindowsXPPro.vmx](https://help.ubuntu.com/community/VMware/Player?action=AttachFile&do=get&target=WindowsXPPro.vmx)[LIST]
[*]Or run gedit (or a similar editor),[/LIST]```
sudo gedit ~/vmware/WindowsXPPro.vmx
```[LIST]
[*]and copy and paste this:[/LIST]> #!/usr/bin/vmware
displayName = "Windows XP"
guestOS = "winxphome"

memsize = "64"
ide0:0.fileName = "WindowsXP.vmdk"
ide1:0.fileName = "WindowsXP.iso"

# DEFAULT SETTINGS UNDER THIS LINE
config.version = "8"
virtualHW.version = "3"

MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

uuid.location = "56 4d 34 58 fd 57 00 42-76 91 96 91 01 30 46 a5"
uuid.bios = "56 4d 34 58 fd 57 00 42-76 91 96 91 01 30 46 a5"

uuid.action = "create"
checkpoint.vmState = ""

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:30:46:a5"
ethernet0.generatedAddressOffset = "0"

usb.present = "FALSE"
sound.present = "FALSE"

scsi0.present = "FALSE"
scsi0.virtualdev = "lsilogic"
scsi0:0.present = "FALSE"
scsi0:0.deviceType = "disk"
scsi0:0.mode = "persistent"
scsi0:0.redo = ""
scsi0:0.writeThrough = "FALSE"
scsi0:0.startConnected = "FALSE"

scsi0:1.present = "FALSE"
floppy0.present = "FALSE"
ide0:0.present = "TRUE"
ide0:1.present = "FALSE"
ide1:1.present = "FALSE"

ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
ide1:0.startConnected = "TRUE"

ide0:0.redo = ""[LIST]
[*]Click save[/LIST][SIZE=4][B]7] If you are using a CD as an installer...
[/B][SIZE=2]If you are using a .iso file (possibly a Linux distrobution), then skip to step 7.[/SIZE][/SIZE]

This gives you the use of your cd-rom drive back:
```
sudo gedit ~/vmware/WindowsXPPro.vmx
```[LIST]
[*]*[line 7]** ide1:0.fileName*** = "**[COLOR=DarkOrange]auto detect[/COLOR]**"
[*]*[line 47] ****ide1:0.deviceType*** = "[COLOR=DarkOrange]**cdrom-raw**[/COLOR]"[/LIST][SIZE=4][B]8] Edit the .vmx file accordingly
[/B][/SIZE]```
sudo gedit ~/vmware/WindowsXPPro.vmx
```[LIST]
[*]*[line 2] ****displayName ***is simply the title of the VM window. This could be set to "**[COLOR=DarkOrange]Windows XP Pro[/COLOR]**", "**[COLOR=DarkOrange]Windows XP Home[/COLOR]**" or "**[COLOR=DarkOrange]Ubuntu Dapper LAMP Server[/COLOR]**". It's all up to you.
[*]*[line 3]**** guestOS*** uses pre-defined phrases to tell VMWare what type of Operating System you will be using. An excellent list I found for this is at: [http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php#oscodes](http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php#oscodes) . Bookmark this if you are using a lot of different OSes
[*]*[line 5] ****memsize*** is how much memory you would like your new OS to use. I have 3GBs on my computer, so I entered in "**[COLOR=DarkOrange]1024[/COLOR]**". The file you downloaded should say "64". ***[COLOR=Red]U[/COLOR]****[COLOR=Red]SE ONLY AS MUCH AS YOU THINK YOUR COMPUTER CAN HANDLE[/COLOR]***. If you want to multi-task between Ubuntu and Windows, tell it to use half your RAM and no more.
[*]*[line 6] ****ide0:0.fileName*** = "**[COLOR=DarkOrange]WindowsXPPro.vmdk[/COLOR]**" (change this to your filename)
[*]*[line 7] ****ide1:0.fileName*** = "**[COLOR=DarkOrange]WindowsXPPro.iso[/COLOR]**" (change this to your filename)
[*]*[line 28]* ***usb.present*** = "[COLOR=DarkOrange]**FALSE**[/COLOR]" to "**[COLOR=DarkOrange]TRUE[/COLOR]**" (only enable this if its needed)
[*]*[line 29]* ***sound.present*** = "[COLOR=DarkOrange]**FALSE**[/COLOR]" to "**[COLOR=DarkOrange]TRUE[/COLOR]**" (only enable this if its needed)
[*]*[line 41]* ***floppy0.present***= "**[COLOR=DarkOrange]FALSE[/COLOR]**" to "**[COLOR=DarkOrange]TRUE[/COLOR]**" (only enable this if its needed)[/LIST][B][SIZE=4]
9] Run VMWare Player and Install your OS
[/SIZE][/B]```
vmplayer ~/vmware/WindowsXPPro.vmx
```[LIST]
[*]or double-click the .vmx file
[*]or click *Applications >> System Tools >> VMware Player* and search for the .vmx using the file browser[/LIST][B][SIZE=4]
10] If you installed from an .iso: Get your CD-ROM back!
[/SIZE][/B][LIST]
[*]Edit your .vmx file to remove the .iso instance: refer to step 6[/LIST][B][SIZE=4]11] Enjoy :)

COMMUNICATE WITH WINDOWS
[/SIZE][/B][LIST]
[*]To transfer files from Windows to Ubuntu or visa versa, use a program called [WinSCP]("http://winscp.net") in Windows and install the SSH protocol for Ubuntu via this terminal command:[/LIST]```
sudo aptitude install ssh
```**[SIZE=4]RUNNING VMWARE USING WINDOWS AS THE HOST[/SIZE]**[LIST]
[*][SIZE=4][SIZE=2]I've been able to use a Feisty .iso, a Dapper LAMP server .iso & a SuSE .iso all inside Windows XP Pro using almost the exact same methods as described above. Simple differences with QEMU in Windows vs Linux is you'll have to download QEMU manually, extract it, and then using [/SIZE][/SIZE]"qemu-img.exe create -f vmdk feisty.vmdk 10GB". Notice the only difference is the ".exe" portion.
[*]The files (.vmx, .vdmk, .iso) are all "cross-platform" and therefore can simply be copied from one OS to an other and will still work. This is largely dependant on how advanced your configuration file is and the difference in version numbers of VMWare.[/LIST][SIZE=4][B] INCASE OF FAILURE
[/B][/SIZE][LIST]
[*]remove VMWare Player[/LIST]```
sudo aptitude purge vmware-player
```[LIST]
[*]clear the VMWare folder so that no previous versions are detected[/LIST]```
sudo rm -R /etc/vmware
```[LIST]
[*]compile VMWare Player from source by downloading the latest version from [http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)[LIST]
[*]```
tar -xzvf $filename
```
[*]```
cd $filename
```
[*]```
sudo ./vmware-install.pl
```[LIST]
[*]run through the steps to compile the proper vmware-kernel-headers and install VMWare Player[/LIST] [/LIST] [/LIST][SIZE=4]** REFERENCE AND (more advanced) TUTORIALS**[/SIZE][LIST]
[*][https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO](https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO)
[*][http://www.ubuntuforums.org/showthread.php?t=183209]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto")
[*][http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php](http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php)[/LIST]

---

### Post by Hanzerik on 2007-01-20
With the qemu command you should be able to specify a literal disk size, say 10G.

I have seem so many posts about using VMWare Server being used on a standalone machine, just to run a second OS. VMWare player is much simpler to use to do this. Sure, if you need headless server, then by all means run a VMWare server on a dedicated box. My VMWare Server is headless itself, running 3 different OS's, Ubuntu Host, with a Win2K Server VM, a Ubuntu Webserver VM, and a Slackware File Server VM.

But for my Laptop, I run WinXpPro as my main OS, with a Ubuntu 610 Desktop VM installed from scratch in VMWare Player. It achieves pretty much native speeds. Where as if you do it in a local VMWare server, you have more procceses running then you need to.

---

### Post by eoinmadden on 2007-01-22
Excellent tutorial, altonbr. Thanks.

---

### Post by altonbr on 2007-01-27
Glad it helped :)

---

### Post by keithpeter on 2007-01-28
Thanks for this clear tutorial; I'm now waiting for Office 2003 to install its updates to the updates to Service Pack 2 in that quaint way Microsoft have. I'm using XP home edition in a virtual machine with 5Gb of drive space and 256 Mb of RAM. The host computer has 512Mb of Ram and is a P4. Yes, I have another 512 Mb of RAM on order :D 

I'd just go so far as to clarify step 8 along the following lines

[LIST]Alter line 7 of the VMX file to read **ide1:0.fileName = "auto detect"**[/LIST]
[LIST]Alter line 47 of the VMX file to read **ide1:0.deviceType = "cdrom-raw"**[/LIST]

for people like me.

---

### Post by altonbr on 2007-01-28
> **keithpeter said:**
> Thanks for this clear tutorial; I'm now waiting for Office 2003 to install its updates to the updates to Service Pack 2 in that quaint way Microsoft have. I'm using XP home edition in a virtual machine with 5Gb of drive space and 256 Mb of RAM. The host computer has 512Mb of Ram and is a P4. Yes, I have another 512 Mb of RAM on order :D 

I'd just go so far as to clarify step 8 along the following lines

[LIST]Alter line 7 of the VMX file to read **ide1:0.fileName = "auto detect"**[/LIST]
[LIST]Alter line 47 of the VMX file to read **ide1:0.deviceType = "cdrom-raw"**[/LIST]

for people like me.

Yes, once Windows XP is done installing (which you said it has), and once the VM is shutdown, THEN edit the .vmx file and change those lines EXACTLY as you have them. Then you should be able to use your CD-ROM drive.

---

### Post by kikuman on 2007-01-28
Strange, gnomebaker fails to make .iso unless using gksudo :( 
readcd: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.

Lol, another thing that shocked me, wtf ...i have a legal copy windows that came with my laptop and it says "According to our record you have exceeded the number of activations" or something like that :D

---

### Post by keithpeter on 2007-01-28
> **kikuman said:**
> Strange, gnomebaker fails to make .iso unless using gksudo :( 
readcd: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.

I get the same but as I'm running Xubuntu I have to do sudo gnomebaker.. It is the same in K3b as well.

How do I get a USB thumb drive to recognise within my Windows XP virtual machine without any impact on permissions in Xubuntu? I would like to use the stick drive to transfer files between Xubuntu and the vmplayer Windows XP

I tried changing line 28 in the vmx file from

[LIST]usb.present = "FALSE"[/LIST]

to 

[LIST]usb.present = "TRUE"[/LIST]

and this resulted in Windows XP in vmplayer seeing my USB drives, but then permissions were changed so that the drives would not autoplay under my normal user in Xubuntu. pmount generated errors and I ended up re-installing Xubuntu as sudo chmod and sudo chown did not work.

---

### Post by altonbr on 2007-01-28
Well instead of using your USB disk as an intermediary drive, what about using SSH? In Windows, you can use a (stand-alone) program called WinSCP ([http://winscp.net/download/winscp382.exe]("http://winscp.net/download/winscp382.exe")) to talk between the two computers. That's how I transfer files, and since it's a LAN connection, it transfers at almost 5MB/s. 

On your Xubuntu machine, run this code:
```
$ sudo aptitude install ssh
```
Say yes to any prompts and let the program create some public and private encryption keys. Once it's done, open WinSCP in Windows, type in the Xubuntu IP address (ie: 192.168.2.100), your username and password (and save it if you'd like) and then you can browse through all your files. You can do the same on the Xubuntu end using the "Connect to Server..." function. 

If you don't know your IP address, run:
```
$ ifconfig
```

The output will be similar to this:
```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:6C:35:83
          inet addr:**[SIZE="4"]192.168.2.102[/SIZE]**  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe6c:3583/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1020592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:915864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:754495724 (719.5 MiB)  TX bytes:719841226 (686.4 MiB)
          Interrupt:177

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:129922 (126.8 KiB)  TX bytes:129922 (126.8 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.33.1  Bcast:192.168.33.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.182.1  Bcast:192.168.182.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
The bold, dot notation above is the IP address you're looking for.

Good luck! :D

---

### Post by altonbr on 2007-01-28
> **kikuman said:**
> Strange, gnomebaker fails to make .iso unless using gksudo :( 
readcd: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.

Lol, another thing that shocked me, wtf ...i have a legal copy windows that came with my laptop and it says "According to our record you have exceeded the number of activations" or something like that :D

Does this thread help any?: [http://www.ubuntuforums.org/showthread.php?t=217472](http://www.ubuntuforums.org/showthread.php?t=217472)

What about running GnomeBaker from the Application list? Or is that not a possibility?

---

### Post by loserboy on 2007-02-06
are the repos down or something, i can't install vmware playe, says missing files or something

Edit: more specifically when i run

> sudo apt-get install vmware-player-kernel-modules
it says
> Install these packages without verification [y/N]? y
Err [http://albertomilone.com](http://albertomilone.com) binary/ vmware-player-kernel-modules-2.6.17-10 2.6.17.8-1
  404 /drivers/edgy/nonlegacy/32bit/binary/vmware-player-kernel-modules-2.6.17-10_2.6.17.8-1_i386.deb
Failed to fetch [http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/vmware-player-kernel-modules-2.6.17-10_2.6.17.8-1_i386.deb](http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/vmware-player-kernel-modules-2.6.17-10_2.6.17.8-1_i386.deb)  404 /drivers/edgy/nonlegacy/32bit/binary/vmware-player-kernel-modules-2.6.17-10_2.6.17.8-1_i386.deb
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


---

### Post by altonbr on 2007-02-07
vmware-player-kernel-modules-2.6.17-10?? You must be in Edgy, correct? 2.6.15-10 is the version current for Dapper.

I would suggest running:

```
$ sudo aptitude update
$ sudo aptitude upgrade
```

But yes, it looks as though the VMWare repository is down for Edgy...

Also, what does your repository list look like? Copy and past this:
```
$ cat /etc/apt/sources.list
```

---

### Post by loserboy on 2007-02-07
I got it working, i just went ahead and intalled the server version and it works like a charm.

out of curiosity though, is there any advantage of having the player instead of the server

---

### Post by Saubazi on 2007-02-08
This sort of hints me that it did not go all right:

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

First I tried vmware server - uninstalled - and now this.
I am running 64bit edgy...

---

### Post by altonbr on 2007-02-08
> **loserboy said:**
> I got it working, i just went ahead and intalled the server version and it works like a charm.

out of curiosity though, is there any advantage of having the player instead of the server

There is no "advantage" for one over the other. It's purely preference. Use VMWare Player if you need to run a GUI and are simply running on your desktop, where as VMWare Server, is, well a server. The server should be used for headless operations.

> **Saubazi said:**
> This sort of hints me that it did not go all right:

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

First I tried vmware server - uninstalled - and now this.
I am running 64bit edgy...

Reading the release notes ([http://www.vmware.com/support/player/doc/releasenotes_player.html)](http://www.vmware.com/support/player/doc/releasenotes_player.html)), I can see that 64-bit IS supported.

This is the only page I could find discussing 64-bit VMWare: [http://ubuntuforums.org/showthread.php?t=315493&page=3](http://ubuntuforums.org/showthread.php?t=315493&page=3)
Specifically: [http://ubuntuforums.org/showpost.php?p=2035766&postcount=28](http://ubuntuforums.org/showpost.php?p=2035766&postcount=28)

I hope this helps :D

---

### Post by Saubazi on 2007-02-08
Well my problem is not uninstalling the player but installing player or server and what I described previously is the error I get trying to install the player.

---

### Post by groova on 2007-02-25
just a quick note of thanks from a linux-noob.

i'm installing windows as i write and i'm thrilled. this tutorial was easy, even for a point-and-clicker like me.

kudos.

---

### Post by kb3hkg on 2007-02-28
I have gotten VMware running XP before, however this time around your tutorial was the easiest and most helpful, thank you. Less effort and more functionality, I cannot complain a bit.

---

### Post by lvds on 2007-03-11
Hi,

Thank you very much for a so comprehensive document of vmware player.
The vmware works fine but i haven't found how to gain access to my real hardDisk.
Usually my harddisk is recognised as /dev/hda1, may you explain how to setup the vmware player to have it use the harddisk ? I have another disk at /dev/hdb1 also ; does the harddisks have to be NTFS or FAT32 or something else to be recognised ?

Best regards,
Laurent.

---

### Post by altonbr on 2007-03-11
> **lvds said:**
> Hi,

Thank you very much for a so comprehensive document of vmware player.
The vmware works fine but i haven't found how to gain access to my real hardDisk.
Usually my harddisk is recognised as /dev/hda1, may you explain how to setup the vmware player to have it use the harddisk ? I have another disk at /dev/hdb1 also ; does the harddisks have to be NTFS or FAT32 or something else to be recognised ?

Best regards,
Laurent.

VMWare is a Virtual Machine which means that there is a virtual layer between your real hardware and your virtual hardware. The two are not inter-connective. The only way it's possible to transfer files between VMWare and your real hard drive is by using SSH or when in Windows, WinSCP via the SSH protocol.

---

### Post by altonbr on 2007-03-13
> **groova said:**
> just a quick note of thanks from a linux-noob.

i'm installing windows as i write and i'm thrilled. this tutorial was easy, even for a point-and-clicker like me.

kudos.

> **kb3hkg said:**
> I have gotten VMware running XP before, however this time around your tutorial was the easiest and most helpful, thank you. Less effort and more functionality, I cannot complain a bit.

Thank you for the compliments.

---

### Post by JoxBG on 2007-03-19
Good How-To.

I just want to add a couple of things. Hopefully this adds to the ease of using vmplayer.

a. In lieu of step 2,3 and 4, use easyvmx.com. Click a few parameters and your vmx and vmdk files are created. And it offers option for any guest OS, plus no need to install qemu. You can browse and edit the vmx files if you want (specially for those who like to tweak certain settings, ie. printer port, sound cards, etc).

b. Skip creating an iso file, you can use the original CD of the operating system. Just load the vmx file into vmplayer (default settings normally is have CD-ROM active on startup). Load your Windows CD in your cd-drive (or any other OS installer) and during boot-up, vmplayer will find and load the installer. Remember that booting the vmx is like starting an actual machine with no OS. If there's a bootable CD in your drive, it will load that. I use this method to install any guest OS inside vmplayer. I only use the *.iso option if I downloaded an iso image to test a particular OS.

If you use the original CD, you can skip steps 5,7 and 9. And with easyvmx, 6 also.

So my steps are:
1. Have easyvmx create virtual machines files for any OS i want to try inside vmware.
2. If using iso (generally downloaded linux, solaris, freebsd images), I edit the vmx file to point to iso image. If using CD, go straight to next step.
3. If using CD, insert CD into drive, fire vmplayer using the vmx file created in 1. Follow OS installer prompts.
4. At end of install eject CD prior to reboot, or edit vmx file to detach iso image (if using iso).

HTH.

Jox

---

### Post by wushumofo on 2007-03-20
qemu-img create -f vmdk /mydir/Winblowsxp.vmdk 8192000
bash: $: command not found

um... I have qemu installed.

any ideas?

---

### Post by altonbr on 2007-03-20
> **JoxBG said:**
> 1. Have easyvmx create virtual machines files for any OS i want to try inside vmware.
2. If using iso (generally downloaded linux, solaris, freebsd images), I edit the vmx file to point to iso image. If using CD, go straight to next step.
3. If using CD, insert CD into drive, fire vmplayer using the vmx file created in 1. Follow OS installer prompts.
4. At end of install eject CD prior to reboot, or edit vmx file to detach iso image (if using iso).

Thanks for your input and the steps mentioned above, but this is so completely different, that it would need it's own HOWTO. This HOWTO is specifically for using WindowsXP (although any OS is supported) & VMWare from the repositories.

If you would like, just create a new post here: [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

But this is good to have if anyone wants a UI option (if that's what it is).

---

### Post by altonbr on 2007-03-20
> **wushumofo said:**
> qemu-img create -f vmdk /mydir/Winblowsxp.vmdk 8192000
bash: $: command not found

um... I have qemu installed.

any ideas?

It looks as though you copied and pasted this,

```
$ qemu-img create -f vmdk /mydir/Winblowsxp.vmdk 8192000
```

when the EXACT code you should copy is,

```
qemu-img create -f vmdk /mydir/Winblowsxp.vmdk 8192000
```

The "$" American Dollar sign is used to signify that the code goes into the terminal/BASH. Please omit the "$" from all of the code you copy and paste.

---

### Post by wushumofo on 2007-03-21
> **altonbr said:**
> It looks as though you copied and pasted this,

```
$ qemu-img create -f vmdk /mydir/Winblowsxp.vmdk 8192000
```

when the EXACT code you should copy is,

```
qemu-img create -f vmdk /mydir/Winblowsxp.vmdk 8192000
```

The "$" American Dollar sign is used to signify that the code goes into the terminal/BASH. Please omit the "$" from all of the code you copy and paste.


yup... I did copy and paste.... 

From... my... TERMINAL... to... the... BROWSER.
I know the $ is the symbol for the bash prompt.
and if you look at the number, I've altered it to an appropriate 8gig. (for my 9gig drive)
ALSO. I've changed the directory to "mydir" because I'd prefer not to show the full directory that I'm creating the virtual drive on. 

So now maybe you can help me with the fact that I have qemu installed... yet it says it's unable to find the command *qemu-img create -f vmdk /mydir/Winblowsxp.vmdk 8192000*

(you know... without... the $ infront.)

(Sorry for seeming like such a jackass, but sweet Lord. I thought people here would at least give me the benefit of the doubt and think... "hey... this guy's got to at least know how to handle a bash prompt.")

---

### Post by pirothezero on 2007-03-22
dumb question, do you have to have a nfts partition to set this up on or something? When it start copying files over just as it finishes it blue memory dumps with a file structure error, when I cross referenced with microsoft docs it said main cause is poorly configured ntfs file system.

Doesn't make sense though its a vm lol.

---

### Post by wushumofo on 2007-03-22
> **pirothezero said:**
> dumb question, do you have to have a nfts partition to set this up on or something? When it start copying files over just as it finishes it blue memory dumps with a file structure error, when I cross referenced with microsoft docs it said main cause is poorly configured ntfs file system.

Doesn't make sense though its a vm lol.

No, you shouldn't have to have an ntfs partition set up to run this. My question is how big did you make your virtual drive? That might have something to do with this issue...

---

### Post by dyrer on 2007-03-22
Running windows from vmplayer will recognize devices (printers, scanners) like a standalone windows installation?

---

### Post by JoxBG on 2007-03-22
> **altonbr said:**
> Thanks for your input and the steps mentioned above, but this is so completely different, that it would need it's own HOWTO. This HOWTO is specifically for using WindowsXP (although any OS is supported) & VMWare from the repositories.

If you would like, just create a new post here: [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

But this is good to have if anyone wants a UI option (if that's what it is).

I was just trying to help in your steps, you ask people to make an iso out of their WindowsXP CD. Why? You can install WindowsXP  from the CD direct, just insert it into CD-drive. The virtual machine will detect the CD-ROM. Also, I don't understand the UI option reference? What UI?

---

### Post by pirothezero on 2007-03-22
> **wushumofo said:**
> No, you shouldn't have to have an ntfs partition set up to run this. My question is how big did you make your virtual drive? That might have something to do with this issue...

Either 8 or 10 gigs. One of those I can't remember.

---

### Post by altonbr on 2007-03-23
> **wushumofo said:**
> yup... I did copy and paste.... 

From... my... TERMINAL... to... the... BROWSER.
I know the $ is the symbol for the bash prompt.
and if you look at the number, I've altered it to an appropriate 8gig. (for my 9gig drive)
ALSO. I've changed the directory to "mydir" because I'd prefer not to show the full directory that I'm creating the virtual drive on. 

So now maybe you can help me with the fact that I have qemu installed... yet it says it's unable to find the command *qemu-img create -f vmdk /mydir/Winblowsxp.vmdk 8192000*

(you know... without... the $ infront.)

(Sorry for seeming like such a jackass, but sweet Lord. I thought people here would at least give me the benefit of the doubt and think... "hey... this guy's got to at least know how to handle a bash prompt.")

Hahaha, no worries. I just assume lower understanding first, and then I work my way up. Sorry for the inconvenience as this takes longer if you know what I'm talking about.

Anyway, it honestly sounds like qemu isn't installed.

Just please run this again so I can confirm:

```
sudo aptitude install qemu
```

The only other thing I can think of is that you're in 6.10 (Edgy) and not Dapper and are therefore using Dash? But then again, your error says:
> bash: $: command not found

Which suggests to me that you did type in the "$" symbol at the beginning of the line because the error goes:

```
bash: *<program here>*: command not found
```

Those are my thoughts anyway, so I hope it helps :S

> **pirothezero said:**
> dumb question, do you have to have a nfts partition to set this up on or something? When it start copying files over just as it finishes it blue memory dumps with a file structure error, when I cross referenced with microsoft docs it said main cause is poorly configured ntfs file system.

Doesn't make sense though its a vm lol.

The .vmdk file you create is a blank drive and can be formatted to almost any structure you'd like. So when you're install Windows, you can install fat32 or ntfs; If Linux, then ext3, ext2, raiser, etc..

> **dyrer said:**
> Running windows from vmplayer will recognize devices (printers, scanners) like a standalone windows installation?

Yes, if you set up the .vmx file correctly. See "**]" after "10]" on my first post to see what lines to change to have USB recognized. Please remember that if your host OS can't recognize the peripherals, then neither will your VM OS.

> **JoxBG said:**
> I was just trying to help in your steps, you ask people to make an iso out of their WindowsXP CD. Why? You can install WindowsXP  from the CD direct, just insert it into CD-drive. The virtual machine will detect the CD-ROM. Also, I don't understand the UI option reference? What UI?

Yes, you're correct. You don't need to make a Windows .iso. That was just the way I was taught to do it. I'll try changing the tutorial around to suit both needs. I was trying to show that you can use ANY .iso, and it doesn't have to be Windows.. but maybe I should be more poignant.

Lastly, regarding easyvmx.com. Is easyvmx.com not a UI? It's a web interface for creating a .vmx & .vmdk file. If you prefer to use that, then sure, go right ahead. Maybe I'll add a link in my tutorial, but I think users get a better understanding of the files and structures of files when they can physically edit them themselves.

---

### Post by LCC on 2007-03-23
Beautiful how to thank you so much, I wish i knew how to put it all to a script, it`s a step closer to resolve Ubuntu bug number one.


Just two little, things the virtual machine online sees drive c: but I have others installed, and secondly the internet connection was down after starting windows on Vmware (reset the router and it was fine again), apart from that the whole thing works flawlessly

one last thing I never seen Windows running as fast as it did, maybe it`s because Windows have been "Ubunted" .

---

### Post by wushumofo on 2007-03-24
Thanks Alton...

I do have qemu installed.
and I am running 6.10.

but I have no clue why it's giving me this error.

I've also removed, and reinstalled quemu just to see... but still the same error.

---

### Post by altonbr on 2007-03-25
> **LCC said:**
> Beautiful how to thank you so much, I wish i knew how to put it all to a script, it`s a step closer to resolve Ubuntu bug number one.


Just two little, things the virtual machine online sees drive c: but I have others installed, and secondly the internet connection was down after starting windows on Vmware (reset the router and it was fine again), apart from that the whole thing works flawlessly

one last thing I never seen Windows running as fast as it did, maybe it`s because Windows have been "Ubunted" .

Lol, you're welcome.

As for the C: Drive... You can only see that one VMDK file, so unless you partioned that drive, you onle have 1. Because it's a *virtual* machine, it can only read it's own drive and nothing else. If you would like to transfer files, use a program called [WinSCP]("http://winscp.net") and the SSH protocol in Ubuntu.

---

### Post by altonbr on 2007-03-25
> **wushumofo said:**
> Thanks Alton...

I do have qemu installed.
and I am running 6.10.

but I have no clue why it's giving me this error.

I've also removed, and reinstalled quemu just to see... but still the same error.

Oh dear... maybe a screenshot, or a copy & paste of your whole terminal may be in order? (Starting from step 1 through to the error).

---

### Post by craigyjack on 2007-03-25
Hi,
I was following your steps, but after I installed VMWare Player with "sudo aptitude install vmware-player", there was no folder named "vmware" that was created in my home directory. The only thing in my home directory is just my user folder.

When I got to "qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10240000"
I got this error:
```
Formating 'vmware/WindowsXPPro.vmdk', fmt=vmdk, size=10240000 kB
qemu-img: Error while formatting
```

I followed your instructions just how they are. I don't understand why a vmware folder wasn't created. Was there supposed to be files in the folder, or should I create a blank folder? I don't know if anything else is wrong.

Could someone inform me on how to fix this so I continue with the installation because I do not know what to do - create a blank folder or if there needs to be vmware files in the folder and something more is wrong?

Thanks,
Craig

---

### Post by wushumofo on 2007-03-26
> **altonbr said:**
> Oh dear... maybe a screenshot, or a copy & paste of your whole terminal may be in order? (Starting from step 1 through to the error).


that's actually funny...

I boot my laptop up... type in the command to see if I can get the error...

and the damn thing works. LOL.

Thanks for your help alton.
Much appreciated.

---

### Post by wushumofo on 2007-03-27
ok, now it's not so funny, the vmware player isn't installed correctly.

I've removed, and re-installed... still the same issue. 

it tells me to run the vmware-config.pl script.

ARGH.

is there a way I can completely remove this thing... then re-install?
(without having to remove ubuntu-desktop?)

---

### Post by craigyjack on 2007-03-27
> **craigyjack said:**
> Hi,
I was following your steps, but after I installed VMWare Player with "sudo aptitude install vmware-player", there was no folder named "vmware" that was created in my home directory. The only thing in my home directory is just my user folder.

When I got to "qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10240000"
I got this error:
```
Formating 'vmware/WindowsXPPro.vmdk', fmt=vmdk, size=10240000 kB
qemu-img: Error while formatting
```

I followed your instructions just how they are. I don't understand why a vmware folder wasn't created. Was there supposed to be files in the folder, or should I create a blank folder? I don't know if anything else is wrong.

Could someone inform me on how to fix this so I continue with the installation because I do not know what to do - create a blank folder or if there needs to be vmware files in the folder and something more is wrong?

Thanks,
Craig

Any chance a could get some help on the install, I do not know what I am doing wrong....?

Thanks,
Craig

---

### Post by xboxSlayer on 2007-03-27
Same problem as the person above me. I'm using Ubuntu Ultimate edition which I'm pretty sure already has qemu installed but not vmplayer. Same question though, can we just create a blank folder or were there supposed to be files in the folder?

---

### Post by craigyjack on 2007-03-27
> **xboxSlayer said:**
> Same problem as the person above me. I'm using Ubuntu Ultimate edition which I'm pretty sure already has qemu installed but not vmplayer. Same question though, can we just create a blank folder or were there supposed to be files in the folder?

I created a blank folder in home called vmware, and redid the installation and still got the same error from qemu. i dont know what is wrong with it.

---

### Post by xboxSlayer on 2007-03-27
I created the folder as well and qemu worked fine for me. Now my problem is that the installation keeps crashing halfway through. I'm going to try installing the latest version of version of vmplayer, it  told me there was a newer version available when I first started it.

As long as you've named the folder correctly it should work. I've deleted and created the folder a couple of times now trying to get windows installed.

---

### Post by craigyjack on 2007-03-27
Okay, I got everything going and the install started, but now during windows setup t asks me to put in the install CD, although it loaded the XP iso..... so now i am confused about that.
I am using a .iso that I downloaded legally from my university (we get free xp's or vista's) but i dont understand why it would load the iso and then tell me to put in a CD?!?

So should I burn the .iso to a disc and then import it back with gnomebaker?
Or burn it to a cd and just use the cd to install it? EDIT: did that, and VM won't recognize the CD as bootable.

sigh, why wont it just use the .iso....

Thanks,
Craig

---

### Post by xboxSlayer on 2007-03-27
Did you put the .iso in the vmware folder? Also you have to remember to edit your WindowsXPPro.vmx and give it the name of your iso.

---

### Post by craigyjack on 2007-03-27
Ah, I think the XP I downloaded is just an upgrade version. I got a full version from a roomie would got it.
My bad.

Yay! The XP disc my roomie had worked fine, its all good now!

Thanks,
Craig

---

### Post by xboxSlayer on 2007-03-27
OK, I have no problems following the tutorial. Everything is installed fine and VMWare starts. But everytime I try to install Windows it always crashes part way through the installation. Most of the time it crashes and gives me a blue screen while it's copying files. The farthest I made it was the systems rebooted and WinXP was starting for the first time then I got a blue screen error. I've tried a couple different versions of Windows and I even tried Windows 2000. And I aways get a blue screen. Any suggestions?

---

### Post by altonbr on 2007-03-27
First off, I'd just like to say that was an entertaining chain of threads, but I'm glad everyone got their problems resolved.

> **xboxSlayer said:**
> OK, I have no problems following the tutorial. Everything is installed fine and VMWare starts. But everytime I try to install Windows it always crashes part way through the installation. Most of the time it crashes and gives me a blue screen while it's copying files. The farthest I made it was the systems rebooted and WinXP was starting for the first time then I got a blue screen error. I've tried a couple different versions of Windows and I even tried Windows 2000. And I aways get a blue screen. Any suggestions?

The first thing I think of when seeing the BSOD during installation, is you never left enough room on the VMDK file. Did you copy my line verbatim, or did you put in your own, custom number? Make sure that you have at least 4GB for the install. If that's not it, then can you write down what the error says and past it on here?

Sorry if that doesn't help.

---

### Post by xboxSlayer on 2007-03-27
It always says:

"A problem has been detected and windows has been shut down to prevent damage to your computer

TRAP_CAUSE_UNKNOWN"

Then VM player comes up with an error

*** VMware Player internal monitor error ***
vcpu-0:VMM fault: regs=0x5f34, exc=7, eip=0x6d17b

I've setup my .vmx file many different ways, with 64, 128, 256, and 512 for memory. Sometimes sound and usb on, sometimes off. I always use "qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10240000" to make a 10 gig drive. I've tried this a dozen times and so far no luck.

---

### Post by xboxSlayer on 2007-03-28
Well, I did a fresh install of Ultimate Ubuntu and made sure and installed the latest version of vmplayer. I still have the same problems, must be a conflict with one of the installed programs in Ultimate Ubuntu. Anyway, I was able to install windows using the qemu method. It would have been nice to get it working in vmplayer though. It's a good tutorial though, simple and easy to follow.

---

### Post by altonbr on 2007-03-29
> **xboxSlayer said:**
> Well, I did a fresh install of Ultimate Ubuntu and made sure and installed the latest version of vmplayer. I still have the same problems, must be a conflict with one of the installed programs in Ultimate Ubuntu. Anyway, I was able to install windows using the qemu method. It would have been nice to get it working in vmplayer though. It's a good tutorial though, simple and easy to follow.

Sorry to hear that, but that's a pretty cryptic error for me.

---

### Post by Mets on 2007-04-01
I am currently dual booting Ubuntu and XP and I ran across this post looking for ways to make my life easier.  I have a few questions if you guys don't mind me asking.

1)   I saw the attachment with internet explorer opened and it looked like the graphics were turned down a lot.  I'd like to be able to play my pc games - can it be made to look like a normal windows install, and would the resources required to run both virtual windows and a game be too taxing?

2)   I don't have the space available to transform my existing windows drive into a virtual drive.  I do have an external HD though.  Would it be possible to transform my existing windows partition to a virtual drive on my external, then erase the windows partition/increase Ubuntu partition size, and then move the virtual drive back?

Thanks a lot.  Looks like a great tutorial, hopefully I can give it a shot

---

### Post by altonbr on 2007-04-01
> **Mets said:**
> I am currently dual booting Ubuntu and XP and I ran across this post looking for ways to make my life easier.  I have a few questions if you guys don't mind me asking.

1)   I saw the attachment with internet explorer opened and it looked like the graphics were turned down a lot.  I'd like to be able to play my pc games - can it be made to look like a normal windows install, and would the resources required to run both virtual windows and a game be too taxing?

2)   I don't have the space available to transform my existing windows drive into a virtual drive.  I do have an external HD though.  Would it be possible to transform my existing windows partition to a virtual drive on my external, then erase the windows partition/increase Ubuntu partition size, and then move the virtual drive back?

Thanks a lot.  Looks like a great tutorial, hopefully I can give it a shot

1) No.
2) No.

Sorry for being so blunt, but you have to install a Windows on a blank VMDK and can not transfer an existing files. The graphics were only turned down because I'm sure you were looking at the Windows 2000 machine... you can have completely normal Windows XP graphics, just you can't play video games. The virtual video card can't be used fully by Windows and therefore, you'll loose A LOT of performance because of this.

What you CAN do though, is use your external drive to hold the VMDK file (which will hold Windows XP) and have Ubuntu/VMWare talk to it. That's the beauty of virtual machines: their hard drives are simply files, and not partitions.

And THEN you can erase your Windows drive and resize it back, but since you can't transfer settings (because you can't have both Windows open at the same time), and since you can't play games, I'll doubt you'll go through with this VMWare stuff.

But oh well eh? I guess it's just not what you're looking for at the moment.

---

### Post by Mets on 2007-04-05
aww shucks.  Thanks for being honest though, it sounded great heh.  I love Ubuntu more than windows, but I love my games a lot too, and I still have a few programs that just won't run on linux that I'm not ready to give up on.  One day I'll either be able to just run everything natively on linux or do something like you wrote with better performance.  Guess I'll just have to wait and keep dual booting.  Oh well...

---

### Post by SDF-1 on 2007-04-06
thank you very much for this tutorial. it took me a good 2 solid hours to get everything working. =) this tutorial should be recommended to others who wish to do this type installation

---

### Post by SDF-1 on 2007-04-06
okay im getting some problems now i dont know where i have gone wrong:

i put my USB in on vmware player and windows says that it cant recognise the usb, it may be malfunctioned. ubuntu was able to read the usb but windows couldnt. i checked my .vmx and the usb is shown as TRUE but still no suceess. i also noticed that another device popped up on my  toolbar on vmware player saying that it is running my USB a): (ASUStek Computer USB Device) and, b): (Syntek Semiconductor USB 2.0 Image Capture Controller). this doesnt make any sense of why its not working anymore. im running out ideas and about to get a bit frustrated. another odd thing is that my sound is working properly either. the sound adapter switches off because another device is using it. someone please help me :(

[[IMG]http://img462.imageshack.us/img462/4104/screenshotlo4.th.png[/IMG]](http://img462.imageshack.us/my.php?image=screenshotlo4.png)

[[img=http://img462.imageshack.us/img462/4104/screenshotlo4.th.png]](http://img462.imageshack.us/my.php?image=screenshotlo4.png)


   this is what i've got:

#!/usr/bin/vmware
displayName = "Windows XP Pro"
guestOS = "winxppro"

memsize = "1024"
ide0:0.fileName = "WindowsXPPro.vmdk"
ide1:0.fileName = "auto detect"

# DEFAULT SETTINGS UNDER THIS LINE
config.version = "8"
virtualHW.version = "3"

MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

uuid.location = "56 4d 95 2d 6f d9 c8 68-1e 86 93 a7 60 b8 0b b7"
uuid.bios = "56 4d 95 2d 6f d9 c8 68-1e 86 93 a7 60 b8 0b b7"

uuid.action = "create"
checkpoint.vmState = ""

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:b8:0b:b7"
ethernet0.generatedAddressOffset = "0"

usb.present = "TRUE"
sound.present = "TRUE"

scsi0.present = "FALSE"
scsi0.virtualdev = "lsilogic"
scsi0:0.present = "FALSE"
scsi0:0.deviceType = "disk"
scsi0:0.mode = "persistent"
scsi0:0.redo = ""
scsi0:0.writeThrough = "FALSE"
scsi0:0.startConnected = "FALSE"

scsi0:1.present = "FALSE"
floppy0.present = "FALSE"
ide0:0.present = "TRUE"
ide0:1.present = "FALSE"
ide1:1.present = "FALSE"

ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "TRUE"
ide1:0.startConnected = "TRUE"

ide0:0.redo = ""

tools.remindInstall = "TRUE"

sound.virtualDev = "es1371"

usb.autoConnect.device0 = "path:5/7 autoclean:1"

usb.autoConnect.device1 = ""

---

### Post by craigyjack on 2007-04-09
EDIT: Nevermind, I fixed my problem. Thanks for the great tutorial and help.

Thanks,
Craig

---

### Post by mikewhatever on 2007-04-09
While trying to install vmware-player on 6.10, I got several error messages. When I try to start it, there is an error message shown in the included screenshot. I'll post the whole deal, perhaps someone can help :lolflag: 
> sudo aptitude install vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libssl0.9.7 vmware-player-kernel-modules 
  vmware-player-kernel-modules-2.6.17-10 
The following NEW packages will be installed:
  libssl0.9.7 vmware-player vmware-player-kernel-modules 
  vmware-player-kernel-modules-2.6.17-10 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.3MB of archives. After unpacking 37.8MB will be used.
Do you want to continue? [Y/n/?] y

Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted vmware-player-kernel-modules-2.6.17-10 2.6.17.7-10.1 [141kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse vmware-player-kernel-modules 2.6.17.10 [23.7kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe libssl0.9.7 0.9.7k-3 [2282kB]     
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse vmware-player 1.0.2-2 [11.9MB]  
Fetched 14.3MB in 4m11s (57.0kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package vmware-player-kernel-modules-2.6.17-10.
(Reading database ... 116680 files and directories currently installed.)
Unpacking vmware-player-kernel-modules-2.6.17-10 (from .../vmware-player-kernel-modules-2.6.17-10_2.6.17.7-10.1_i386.deb) ...
Selecting previously deselected package vmware-player-kernel-modules.
Unpacking vmware-player-kernel-modules (from .../vmware-player-kernel-modules_2.6.17.10_i386.deb) ...
Selecting previously deselected package libssl0.9.7.
Unpacking libssl0.9.7 (from .../libssl0.9.7_0.9.7k-3_i386.deb) ...
Selecting previously deselected package vmware-player.
Unpacking vmware-player (from .../vmware-player_1.0.2-2_i386.deb) ...
Setting up vmware-player-kernel-modules-2.6.17-10 (2.6.17.7-10.1) ...

Setting up vmware-player-kernel-modules (2.6.17.10) ...
Setting up libssl0.9.7 (0.9.7k-3) ...

Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.92.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.165.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.238.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.37.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player



---

### Post by mikewhatever on 2007-04-10
[SIZE="6"][COLOR="Red"]The vmware version from the repositories does not work on the upgraded kernel 2.6.17-11-generic. One possible solution would be to manually install vmware using this how-to [https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)
Worked very well for me[/COLOR].[/SIZE]

---

### Post by altonbr on 2007-04-12
I posted the exact same problem here: [http://ubuntuforums.org/showthread.php?t=358275](http://ubuntuforums.org/showthread.php?t=358275)

The problem is due to a mismatch with the kernel and vmware-kernel-headers. Make sure to configure VMWare using the latest vmware-kernel-headers under the corresponding kernel version.

This can be accomplished by commenting out the boot lines in /boot/grub/menu.lst that correspond to NEWER (or mismatching) kernel to vmware-kernel-headers versions.

```
sudo gedit /boot/grub/menu.lst
```

Hope this helps :)

---

### Post by carusoswi on 2007-04-14
When starting my player, I get the message that WindowsXPPro.iso does not exist - but, I'm looking right at the file in my browser.  What have I done wrong, please?

Caruso

---

### Post by altonbr on 2007-04-14
Does your root directory have these three files? [http://ubuntuforums.org/attachment.php?attachmentid=23518&d=1169309836](http://ubuntuforums.org/attachment.php?attachmentid=23518&d=1169309836)

---

### Post by allforcarrie on 2007-04-15
that was easyer than i expected. its working quite well.

---

### Post by altonbr on 2007-04-15
Thanks.

I've been told to blog/digg it but I don't exactly have time at the moment. I'll get around to that this summer.

---

### Post by novus721 on 2007-04-17
Hi all, I just converted to ubuntu from xp so excuse me if this sounds obnoxious

I got stuck at step 2, as it starts to install but I end up with the attached output - [http://rafb.net/p/1QUuXW71.html]("http://rafb.net/p/1QUuXW71.html") - the cycle continuously repeats itself, and more so I cannot download any more packages because I must always get an error stating:confused: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

...and when I do so, it just goes back to the the vmware setup cycle. Please, any help would be greatly appreciated as I have very sensitive files to move ASAP and I need to be able to download ssh support in order to do it - thank you all so much!!!

---

### Post by novus721 on 2007-04-17
Nvm found the solution...got some outside help from a friend of mine that I'm still trying to understand, otherwise I'd post it - thank you all

---

### Post by altonbr on 2007-04-17
Good to hear you got it up an running novus21.

I'd like to point out that I've had a similar problem, and it was due to a mismatch in kernel headers (as seen by my post here: [http://ubuntuforums.org/showpost.php?p=2441822&postcount=60](http://ubuntuforums.org/showpost.php?p=2441822&postcount=60))

The best thing I found to do, is purge vmware-player (go into Synaptic Package Manager, search "vmware", and purge everything that has to do with vmware). Make sure to match the kernel and vmware-kernel-headers either by editing grub and loading an older kernel as stated in my link, or compile the newest version of vmware from source: [http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

---

### Post by altonbr on 2007-04-21
I've upgrade and expanded the article, including the suggestion made by JoxBG.

---

### Post by koma77 on 2007-04-22
I'm running XP inside VmWare player in Ubuntu and it works great!

Just one thing that puzzles me: the XP guest runs way to fast. The clock on the virtual machine gains 10 minutes per hour at least. Videos play at a really too high speed...

How can I get it to run more smoothly?

The virtual machine was once created on a XP machine running VmWare Workstation.

---

### Post by altonbr on 2007-04-22
> **koma77 said:**
> I'm running XP inside VmWare player in Ubuntu and it works great!

Just one thing that puzzles me: the XP guest runs way to fast. The clock on the virtual machine gains 10 minutes per hour at least. Videos play at a really too high speed...

How can I get it to run more smoothly?

The virtual machine was once created on a XP machine running VmWare Workstation.

Can you post your .vmx file?

---

### Post by Kotjze on 2007-04-24
> **koma77 said:**
> I'm running XP inside VmWare player in Ubuntu and it works great!

Just one thing that puzzles me: the XP guest runs way to fast. The clock on the virtual machine gains 10 minutes per hour at least. Videos play at a really too high speed...

How can I get it to run more smoothly?

The virtual machine was once created on a XP machine running VmWare Workstation.

I have this problem too, only I think mine might be going faster than yours, I seemed to be gaining 10 minutes every 10 minutes, if that doesn't sound weird.

As altonbr suggested, I guess I should post my .vmx file aswell.

---

### Post by altonbr on 2007-04-24
> **Kotjze said:**
> I have this problem too, only I think mine might be going faster than yours, I seemed to be gaining 10 minutes every 10 minutes, if that doesn't sound weird.

As altonbr suggested, I guess I should post my .vmx file aswell.

While I'm reading this, can you post these 3 files?

```
cat /proc/cpuinfo > cpuinfo-kotjze.20070424.txt
```
```
cat /proc/meminfo > meminfo-kotjze.20070424.txt
```
```
lspci -v > lspci-kotjze.20070424.txt
```

All three files should be in your home directory. If you're scared to do this, look at them before you post them. It's simply giving me an idea about what's on your computer.

---

### Post by altonbr on 2007-04-24
**_Kotjze_**

Can you try using this .vmx file?

> #!/usr/bin/vmware
displayName = "Windows XP Professional"
guestOS = "winxppro"

memsize = "256"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide1:0.fileName = "auto detect"

# DEFAULT SETTINGS UNDER THIS LINE
config.version = "8"
virtualHW.version = "3"

MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

uuid.location = "56 4d 56 7b e4 ea c1 e3-6f 75 d9 58 a5 75 53 b0"
uuid.bios = "56 4d 56 7b e4 ea c1 e3-6f 75 d9 58 a5 75 53 b0"

uuid.action = "create"
checkpoint.vmState = "windows-xp_pro.vmss"

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:75:53:b0"
ethernet0.generatedAddressOffset = "0"

usb.present = "TRUE"
sound.present = "FALSE"

scsi0.present = "TRUE"
scsi0.virtualdev = "lsilogic"
scsi0:0.present = "FALSE"
scsi0:0.deviceType = "disk"
scsi0:0.mode = "persistent"
scsi0:0.redo = ""
scsi0:0.writeThrough = "FALSE"
scsi0:0.startConnected = "FALSE"

scsi0:1.present = "FALSE"
floppy0.present = "FALSE"
ide0:0.present = "TRUE"
ide0:1.present = "FALSE"
ide1:1.present = "FALSE"

ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "TRUE"
ide1:0.startConnected = "TRUE"

ide0:0.redo = ""

tools.remindInstall = "TRUE"

Save it as "Windows XP Professional-edited-altonbr.vmx" or similar. Also, if you have enough space, or the .vmdk file fits on a DVD, I would suggest backing it up. It is HIGHLY unlikely my .vmx file will corrupt your Windows VM, but I don't want to be responsible if it does.

---

### Post by Kotjze on 2007-04-24
I tried the new .vmx file, and now it runs slower than it should (I even opened the clock to see, and each second takes roughly 3-4 real seconds). Also, the sound doesn't work, but I guess you removed that from the .vmx file. I also guess you added a thing for SCSI because when I booted the guestOS it asked to install it, but I didn't have any CD and it didn't find anything on the internet.

As per your other request, here are those three files:

UPDATE: I used your .vmx and added the sound device back, and when playing a song it runs the correct speed, but the reason I have XP in a virtual machine is so I can run some programs that Wine or CrossOver can't run good (like Guitar Pro 5). When I play tabs in Guitar Pro using your .vmx and the sound device added in, the system runs at a near-normal speed, so I think I'll leave it for now. It's much better now than it was yesterday. :)

---

### Post by Flavian on 2007-04-24
I get the following error, when I start vmwareplayer:

> 
VMware Player unrecoverable error: (vcpu-0)
Unexpected signal: 11.
A log file is available in "/media/data/vmware/vmware.log".  A core file is available in "/media/data/vmware/core.8978".  Please request support and include the contents of the log file and core file.  
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.


---

### Post by altonbr on 2007-04-25
**@Kotjze:** I believe you're having these problems because your processor & video card can't handle the extra operating system. I believe your system is near the minimum requirements for Windows XP let alone Ubuntu _and_ Windows XP. If things are running at 3/4 speed, I would guess this is the best you're going to get.

I've read that a MT-37 is supposed to run at 2000 MHz, why is your's only 800 MHz?

Lastly, I've also read that there have been some issues with the ATI Radeon Xpress 200M. Maybe search around for that too.

> **Flavian said:**
> I get the following error, when I start vmwareplayer:

Did you do what it asked you to do? I've never seen that error before. What do the logs say?

---

### Post by Repent on 2007-04-27
What can I do about this?

joe203@joe203-desktop:~$ sudo aptitude install qemu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
joe203@joe203-desktop:~$ qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10GB
Formating 'vmware/WindowsXPPro.vmdk', fmt=vmdk, size=10485760 kB
qemu-img: Error while formatting
joe203@joe203-desktop:~$ qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10GB
Formating 'vmware/WindowsXPPro.vmdk', fmt=vmdk, size=10485760 kB
qemu-img: Error while formatting
joe203@joe203-desktop:~$ 

Thanks

---

### Post by altonbr on 2007-04-27
> **Repent said:**
> What can I do about this?

joe203@joe203-desktop:~$ sudo aptitude install qemu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
joe203@joe203-desktop:~$ qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10GB
Formating 'vmware/WindowsXPPro.vmdk', fmt=vmdk, size=10485760 kB
qemu-img: Error while formatting
joe203@joe203-desktop:~$ qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10GB
Formating 'vmware/WindowsXPPro.vmdk', fmt=vmdk, size=10485760 kB
qemu-img: Error while formatting
joe203@joe203-desktop:~$ 

Thanks

Do you have a folder named "vmware" in your home directory? Maybe qemu isn't smart enough to create a directory for you.

Change the command to:
```
qemu-img create -f vmdk WindowsXPPro.vmdk 10GB
```
or create a directory called "vmware" in your home folder.

---

### Post by Pugwash on 2007-04-27
Thanks for the guide, works very well. Only problem is I have to reboot a couple of times to get my usb external hard disk working in ubuntu after loading it in vmplayer. I'll have to get the ssh thing sorted.

Cheers.

---

### Post by Flavian on 2007-04-28
> 
Did you do what it asked you to do? I've never seen that error before. What do the logs say?

Yepp, I did everything step by step like it was said in your first post! - I don't know either what the error message means :(
Maybe someone had the same issues like me and could fix them?

Thanks
Flo

---

### Post by Kotjze on 2007-04-30
> **altonbr said:**
> **@Kotjze:** I believe you're having these problems because your processor & video card can't handle the extra operating system. I believe your system is near the minimum requirements for Windows XP let alone Ubuntu _and_ Windows XP. If things are running at 3/4 speed, I would guess this is the best you're going to get.

I've read that a MT-37 is supposed to run at 2000 MHz, why is your's only 800 MHz?

Lastly, I've also read that there have been some issues with the ATI Radeon Xpress 200M. Maybe search around for that too.


Uh huh.... Well, first, my system meets more than the minimum requirements for Windows Vista Home Basic, and it runs Ultimate really well too (Ultimate's min. req. are higher), so I'm pretty sure it's able to run two operating systems at once, I've done it many times before on Windows.

Second, the processor is kind of random apparently. On Windows, when I go to System Properties, sometimes it says 1.99GHz and sometimes lower. VMWare Workstation for Windows also notifies me about what Windows says it is and what Workstation measured it as.

The speed of the virtual system varies, most likely because of the processor thing. As I said in my last post, things were running with a near-normal speed meaning sometimes it's fast and sometimes it's slow.

---

### Post by altonbr on 2007-04-30
> **Kotjze said:**
> Uh huh.... Well, first, my system meets more than the minimum requirements for Windows Vista Home Basic, and it runs Ultimate really well too (Ultimate's min. req. are higher), so I'm pretty sure it's able to run two operating systems at once, I've done it many times before on Windows.

Second, the processor is kind of random apparently. On Windows, when I go to System Properties, sometimes it says 1.99GHz and sometimes lower. VMWare Workstation for Windows also notifies me about what Windows says it is and what Workstation measured it as.

The speed of the virtual system varies, most likely because of the processor thing. As I said in my last post, things were running with a near-normal speed meaning sometimes it's fast and sometimes it's slow.

Your frequency is less than recorded because of CPU frequency scaling for laptops (it saves power for your battery). I should have know this, sorry.

If you are speaking of the mouse being "choppy" (maybe the 3/4 the speed you were speaking of), then that appears to be normal. This is what happens on my Intel 640 /w HT too. I haven't looked in on how to fix it so I couldn't tell you if there is a way.

Lastly, if your computer meets the "minimum" requirements, then it's not supposed to be running a second operating system, especially if it's not even at the "recommended" requirements.

But you said if ran VMWare in Windows, and it DIDN'T act like this? Can you elaborate on the differences between your Ubuntu VMWare experience and your Windows XP (or Vista) experience?

---

### Post by Unconscious on 2007-05-02
Help!!! I've been trying to get the vmware-player to load win 2k pro from my legal windows 2000 cd with no success. I've tried the vmware-player from synaptic,  and when that didn't work I downloaded the 1.0.4 version of the player form vmware, and installed that. Still no joy. 

The CD is sitting in the drive, I can read the files on it, but it appears that the VM never even looks at the drive. I changed the boot order via F2, when the VM starts up, but that didn't make any difference. It simply says "No operating system found". 

Perhaps I need to make a w2k pro ISO?

Here's my .vmx

```
#!/usr/bin/vmware
displayName = "Windows 2000 Pro"
guestOS = "win2000pro"

memsize = "192"
ide0:0.present = "TRUE"
ide0:0.filename = "Win2kPro.vmdk"

ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "TRUE"
ide1:0.startConnected = "TRUE"

floppy0.fileName = "/dev/fd0"
floppy0.startConnected = "FALSE"

config.version = "8"
virtualHW.version = "3"

MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

uuid.location = "56 4d 2c 54 f2 f8 07 79-f1 bc e3 c7 c1 d4 97 61"
uuid.bios = "56 4d 2c 54 f2 f8 07 79-f1 bc e3 c7 c1 d4 97 61"

# uuid.location = "56 4d 2c 54 f2 f8 07 79-f1 bc e3 c7 c1 d4 97 61"
# uuid.bios = "56 4d 2c 54 f2 f8 07 79-f1 bc e3 c7 c1 d4 97 61"

ethernet0.present = "FALSE"
usb.present = "FALSE"
sound.present = "FALSE"
sound.virtualDev = "es1371"
nvram = "Win2kPro.nvram"
ide0:0.redo = ""
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:d4:97:61"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
uuid.action = "create"
checkpoint.vmState = "Win2kPro.vmss"
tools.remindInstall = "TRUE"
fileSearchPath = "/home/scott/vmware/Win2kPro;." 

ethernet0.connectionType = "nat"

```

Thanks in advance for your help. If I can get this to work I can reclaim the machine I've had to waste as a windows box.

---

### Post by Unconscious on 2007-05-02
:popcorn: 
Ok. I figured out my problem (besides being somewhat dense)...

[LIST]
[*]I DID need to make a ISO from the CD. Right click on the CD-ROM icon on my desktop, Copy, and save it in .../vmware/Win2kPro
[*]I had to change ide1:0.deviceType to "cdrom-image"
[/LIST]

Now I need to figure out how to load the VMware tools, so I can do things between Ubuntu and W2k. Sorry, but the WinSCP thing is not gonna work for me.

Yay!!!

---

### Post by Aryra on 2007-05-11
Thankfully I have two Windows XP disks and licenses XD

One came with the PC and the other I bought 'cause I lost the original one...found it two weeks later in an envelope. I just hope that the serials will work :D

---

### Post by cisforcojo on 2007-05-11
Windows asks me to validate it. I am currently dual booting and often go back into Windows to play games.
If I activate with VMWare, will I again have to re-activate when I go back into Windows and so on? I can only activate 10x or so before MS flags the serial as stolen. 

Another question is that I may have COMPLETELY missed but I'd rather run my virtual drive off my external harddrive instead of my harddisk. Is this possible? I'd love to free up the space. I saw this briefly mentioned but I didn't catch an answer.

---

### Post by altonbr on 2007-05-12
> **cisforcojo said:**
> Windows asks me to validate it. I am currently dual booting and often go back into Windows to play games.
If I activate with VMWare, will I again have to re-activate when I go back into Windows and so on? I can only activate 10x or so before MS flags the serial as stolen. 

Another question is that I may have COMPLETELY missed but I'd rather run my virtual drive off my external harddrive instead of my harddisk. Is this possible? I'd love to free up the space. I saw this briefly mentioned but I didn't catch an answer.

A virtual Windows is the same as a Windows partition, so you'll have to use up an extra serial, yes. I wouldn't suggest dual-booting and then using the same serial for the virtual machine as their "Genuine Advantage" program may catch both and do it's thing.

Yes you can run the .vmdk from ANY spot on your computer. Just make sure to use absolute paths in your .vmx file (such as: "/media/external/vmware/windows.vmdk") instead of releative (such as "windows.vmdk"). If you can't get it working, give me a shout because I know you can do it :)

---

### Post by cisforcojo on 2007-05-12
I read somewhere that it's 'illegal' to use the same version of XP to have installed (dual-boot) AND use in a virtual machine. That's some bullshit right there. I can't even figure that one out legally how they justify it. Two computers I can see but it's not even two different computers. I love the irony of the name "Genuine Advantage".

---

### Post by altonbr on 2007-06-20
I guess that warning I have of VMware Server being recommended has scared people away...

---

### Post by Tony D'Ambrosio on 2007-06-30
It is my experience that experimentation is worth 50% of tutelage's value.  So it was in this instance, of following your wonderful, helpful, and essential instructions.

First:  Last night, at about 1PM or so, I installed Windows XP on a virtual machine on my Feisty system.  The problems were numerous:
1.  Couldn't resolve all kinds of repository issues; pretty much nothing in your list of commands ran properly or completely.  Solution.  Reinstall Ubuntu.  Since I've only been using it a few weeks, this was not a great sacrifice.  However, it was a long time realizing the problem.  Then, once reinstalled, to immediately do a complete update.  About 32 packages failed to install.  Redo the update (and just in case with my firewall off this time) and they all came along.  By the way, my access is via dialup (perforce, as I'm in the sticks), and over a proxy to a PC running America Online.  How's that for an environment many Linux devotees would sneer at?  The download and update/install took only some 7-9 hours.  But then it was done, and EVERYTHING worked.

2.  Second problem: at the end of the download/install of VMWare, there's a notification about the license.  It should be noted that, even though it didn't say to (there was nothing to click at this point indicating acceptance; it was just a notification, and did not require action), YOU MUST close this window before proceeding.  I didn't; instead I opened another Terminal and tried to execute the Qemu install.  It didn't complete properly.  Solution:  I looked up the command and removed the VMWARE directory (so things, hopefully) would be back where they ought to be; closed the notification window; went to the Synaptic Package Manger and installed Qemu from there.  Proceeding from that point, your tutorial worked swimmingly.

3.  For some reason (probably something I did wrong) I ended up with a file name (and or place) the VMWare program didn't like.  I had to work to get the file it works off of into the proper directory (found it in the VMWARE directory in my Home Folder (clicking on Places) alongside of Desktop and Examples, but working with the editor I managed to straighten this out.

4.  Somehow misinterpreted the directions and ended up without a CD-ROM machine; got it back (per your tutorial's directions) and sure enough the Windows CD installation proceeded and worked beautifully!!!

5.  The virtual machine's screen only occupied about 1/4 of my monitor.  It was pretty, but not usable.  Went to bed and figured I'd deal with that in the morning.  Did.  Solution:  Using the Windows XP Display Properties (a double click on the right button) changed Settings to up the resolution from 600x800 by one click to the next higher setting.  The display showed the screen getting smaller, but I persisted with a click to Apply, and, Lo!, the screen actually ended up a little bigger.  Did this twice more until virtually the entire actual screen is filled, just as it would be if Windows were the only thing running.

Thanks to your WONDERFUL TUTORIAL, I am about 75% towards my goal of making all my Windows software available.  The only things I really want are my Corel Draw, my AOL, and Windows access to my HP Scanner.  Perhaps time will allow me to drop some of these, but until then I couldn't consider moving over to Linux ... I just need these things too much at this point.

Anyway, thanks so much for the excellent job.  If any of my experiences can help others that will be great.

Tony

Tony D'Ambrosio

---

### Post by altonbr on 2007-07-02
Tony,

Thanks for your wonderful review. I'll look into making a complete re-write of this tutorial. I started it in December of '06 and have been adding to it and modifying it ever since. I will be looking into re-writing it for my personal website and I will post the new edition up here.

Hope your transition to Linux is as easy and peaceful as mine!


Brett

---

### Post by Gary.M on 2007-07-19
My experience today, for assistance if anyone needs it...

I followed this exactly but ran into a problem because my grub boot list had two kernels listed. I ended up with an install that failed and which I couldn't remove. I spent a couple of hours using the forum to find my way to a solution that allowed me to remove vmware-player. Messy!

It would be great if the note on the need to comment out any unused kernel entries in the grub menu was at the beginning of this thread. Then vmware installs the right stuff.

Once I got the player installed and running with WinXP Pro installed I noted it didn't load a driver for the graphics (exclamation mark in device manager) and the mouse was jerky. Read a bit and learn that I should install the windows tools from Vmware. (I don't think it is mentioned in this thread?). Downloaded the full Linux tar server install from vmware and extracted the windows.iso file that has the tools install.

Loaded that iso in the virtual machine and installed the tools. Now the graphics driver is there and the mouse is smooth.

Perhaps this can be added to the initial entry in this thread too?

Also to get access to and from the virtual machine I used a samba share I created in my home folder and mapped that within the virtual XP to a suitable drive letter. Now files can easily go in and out.

Now all is well.

---

### Post by FDPOD on 2007-07-30
I'm glad I stumbled across this thread ... 
Nice work on the howto Brett 

A couple of questions also from my side though:
1.) Since I have installed my VMWin2k from the CD directly - there is no .iso file in the vmware -folder. Also the is no .vmx file ..... Everything seems to work as expected right now as well.
Do I need to have a .vmx file in the vmware folder ? What benefit do I get from it ?

2.) This WinSCP prog to exchange data btw Ubuntu<>VMWin looks very nice but asks me a s***load of questions to make a connection. 
For me that's way too many parameters I can screw up on ....:confused:
Now, when I had VMWare Server installed - It already somehow has a connection set up via SAMBA !
So I see in my VM-Windows a mapped network drive.
Have a look here : [ATTACH]39390[/ATTACH]

Originally the plan was to have a USB drive accessible both from Ubuntu & VMWindows.

However if I plug a USB drive in - Ubuntu recognizes it, mounts and opens a file browser window - and then when VMWindows also tries to connect  to the USB drive - it disconnects it in an "unsafe" way from Ubuntu.

So, now my "idea/hope/expectation" would be to leave full control over the USB drives in Ubuntu and SAMBA -Network into the USB-Drives then from VMWindows (instead of connecting the USB Drives as devices to VMWindows). 

Does that makes sense ?

Any chance you can figure out how this SAMBA thingy works ?!
Would make a great extension to the HowTo ;)

Any hints would be greatly appreciated ?

Tx
Frank

---

### Post by Gary.M on 2007-07-31
Frank... my 2c having moved on a week or so. I wanted more than I was getting from Vmware player from the repositories. I removed it by reversing the process and then downloaded the tar installer file from the Vmware site for Player V2. I then followed the instructions for install found in the documents on the player also on the Vmware site. No probs... just keep hitting enter on all the prompts to accept the defaults.

Vmware 2 is much better than the version this guide installs from the repositories... this puts in only 1.0.2. Vmware support tell me that this version was never certified for use with Feisty...

If you go to [http://www.easyvmx.com/](http://www.easyvmx.com/) and use the V2 machine creator, d/l it and install your OS you'll be away.

I now have USB V2 that works. Even my scanner that isn't supported under Linux can be used now in the VM.

I don't use shared folders. Just use NAT networking in the VM and map some samba shared folders from the host machine. Easy...

---

### Post by altonbr on 2007-08-18
> **Gary.M said:**
> My experience today, for assistance if anyone needs it...

I followed this exactly but ran into a problem because my grub boot list had two kernels listed. I ended up with an install that failed and which I couldn't remove. I spent a couple of hours using the forum to find my way to a solution that allowed me to remove vmware-player. Messy!

Are you taking about your VM or your base Ubuntu installation?

> **Gary.M said:**
> It would be great if the note on the need to comment out any unused kernel entries in the grub menu was at the beginning of this thread. Then vmware installs the right stuff.

Please elaborate and then I'll consider adding this comment.

> **Gary.M said:**
> Once I got the player installed and running with WinXP Pro installed I noted it didn't load a driver for the graphics (exclamation mark in device manager) and the mouse was jerky. Read a bit and learn that I should install the windows tools from Vmware. (I don't think it is mentioned in this thread?). Downloaded the full Linux tar server install from vmware and extracted the windows.iso file that has the tools install.

Loaded that iso in the virtual machine and installed the tools. Now the graphics driver is there and the mouse is smooth.

VMware Tools is available in VMware Server and possibly for download on their website as you mentioned. If Windows couldn't pick up the VMware video driver, then I would have to guess you're using SP1 and not SP2?

> **Gary.M said:**
> Perhaps this can be added to the initial entry in this thread too?

Will do.

> **Gary.M said:**
> Also to get access to and from the virtual machine I used a samba share I created in my home folder and mapped that within the virtual XP to a suitable drive letter. Now files can easily go in and out.

Now all is well.

Great! I'm glad you know how to do so!

> **FDPOD said:**
> I'm glad I stumbled across this thread ... 
Nice work on the howto Brett 

A couple of questions also from my side though:
1.) Since I have installed my VMWin2k from the CD directly - there is no .iso file in the vmware -folder. Also the is no .vmx file ..... Everything seems to work as expected right now as well.
Do I need to have a .vmx file in the vmware folder ? What benefit do I get from it ?

The .vmx file is your settings file so all of the files that are created by VMware are created in the same spot. If you have it in your home directory, more than likely all of the VMware files such as *.vmmem are in your home directory. Does that make sense? I'm sure you could change some absolute paths around, but that's how I do it.

~/vmware/win_xp_pro/win_xp_pro.vmx
~/vmware/win_xp_pro/win_xp_pro.iso
~/vmware/win_xp_pro/win_xp_pro.vmdk
etc.

> **FDPOD said:**
> 2.) This WinSCP prog to exchange data btw Ubuntu<>VMWin looks very nice but asks me a s***load of questions to make a connection. 
For me that's way too many parameters I can screw up on ....:confused:
Now, when I had VMWare Server installed - It already somehow has a connection set up via SAMBA !
So I see in my VM-Windows a mapped network drive.
Have a look here : [ATTACH]39390[/ATTACH]

Originally the plan was to have a USB drive accessible both from Ubuntu & VMWindows.

However if I plug a USB drive in - Ubuntu recognizes it, mounts and opens a file browser window - and then when VMWindows also tries to connect  to the USB drive - it disconnects it in an "unsafe" way from Ubuntu.

So, now my "idea/hope/expectation" would be to leave full control over the USB drives in Ubuntu and SAMBA -Network into the USB-Drives then from VMWindows (instead of connecting the USB Drives as devices to VMWindows). 

Does that makes sense ?

Any chance you can figure out how this SAMBA thingy works ?!
Would make a great extension to the HowTo ;)

Any hints would be greatly appreciated ?

Tx
Frank

You're right, SAMBA would be a great addition to my HOW-TO, but I have absolutely no experience with it yet. I'm sure it's just like NFS, so just know that Ubuntu has the ability to see Windows shared folders. Try going to System > Administration > Shared Folder and/or Places > Network to see the Windows shared folder.

> **Gary.M said:**
> Frank... my 2c having moved on a week or so. I wanted more than I was getting from Vmware player from the repositories. I removed it by reversing the process and then downloaded the tar installer file from the Vmware site for Player V2. I then followed the instructions for install found in the documents on the player also on the Vmware site. No probs... just keep hitting enter on all the prompts to accept the defaults.

Vmware 2 is much better than the version this guide installs from the repositories... this puts in only 1.0.2. Vmware support tell me that this version was never certified for use with Feisty...

If you go to [http://www.easyvmx.com/](http://www.easyvmx.com/) and use the V2 machine creator, d/l it and install your OS you'll be away.

I now have USB V2 that works. Even my scanner that isn't supported under Linux can be used now in the VM.

I don't use shared folders. Just use NAT networking in the VM and map some samba shared folders from the host machine. Easy...

I really think you guys should just run VMware Server. More than likely your suit if you want to use Windows as a secondary OS. VMware Tools will get rid of the choppy screen and help with general performance. Plus, no editing .vmx files.

---

### Post by Gary.M on 2007-08-18
>Are you taking about your VM or your base Ubuntu installation?

The base Ubuntu grub boot options menu in my case had two kernel options listed  .....15 and .....16 (sorry can't recall the rest of the kernel identifier) and I was running .16 which was the most recent. (These entries a result of Ubuntu Feisty's repository kernel upgrade) When I followed your instructions I ended up with Vmplayer compiled for the .15 kernel. It didn't run of course.

Of note is that if you run the vmplayer config separately in the console it asks you where the current kernel version is found so you get a chance to check and correct.

All that is needed anyway is to edit grub's menu.lst /boot/grub/menu.lst and comment out the unwanted kernel lines.


>VMware Tools is available in VMware Server and possibly for >download on their website as you mentioned. If Windows couldn't >pick up the VMware video driver, then I would have to guess you're >using SP1 and not SP2?


No, My Windows XP install is a slipstreamed SP2 install. You still need to find and install the tools to make things really work well.


>I really think you guys should just run VMware Server. More than >likely your suit if you want to use Windows as a secondary OS. >VMware Tools will get rid of the choppy screen and help with >general performance. Plus, no editing .vmx files.

What I like about the player, and I'm now running Player V2, is the USB 2.0 support. I don't think server has that.

---

### Post by altonbr on 2007-08-18
> **Gary.M said:**
> >Are you taking about your VM or your base Ubuntu installation?

The base Ubuntu grub boot options menu in my case had two kernel options listed  .....15 and .....16 (sorry can't recall the rest of the kernel identifier) and I was running .16 which was the most recent. (These entries a result of Ubuntu Feisty's repository kernel upgrade) When I followed your instructions I ended up with Vmplayer compiled for the .15 kernel. It didn't run of course.

Of note is that if you run the vmplayer config separately in the console it asks you where the current kernel version is found so you get a chance to check and correct.

All that is needed anyway is to edit grub's menu.lst /boot/grub/menu.lst and comment out the unwanted kernel lines.

Yes, I had that as part of my tutorial until problem resolved itself. I thought it had resolved itself, so I removed it. As you can see, that one Dapper kernel didn't have VMware support until a month or so after the new kernel release.

I'll see if I can add this back in without confusing other users.

> **Gary.M said:**
> >VMware Tools is available in VMware Server and possibly for >download on their website as you mentioned. If Windows couldn't >pick up the VMware video driver, then I would have to guess you're >using SP1 and not SP2?


No, My Windows XP install is a slipstreamed SP2 install. You still need to find and install the tools to make things really work well.

Sorry, I'll have to research that again.

> **Gary.M said:**
> >I really think you guys should just run VMware Server. More than >likely your suit if you want to use Windows as a secondary OS. >VMware Tools will get rid of the choppy screen and help with >general performance. Plus, no editing .vmx files.

What I like about the player, and I'm now running Player V2, is the USB 2.0 support. I don't think server has that.

Again, I'll have to research that. I've heard about it not having USB 2.0 support, but it seems silly to me that in 2007, they wouldn't have USB 2.0 support.

---

### Post by gpmiii on 2008-06-12
After entering "qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10GB", I get an error - 

"Formatting 'vmware/WindowsXPPro.vmdk', fmt=vmdk, size=1048576 kB
qemu-img: Error while formatting".

I have tried changing the size to 5GB and 1GB, with out any success.

Any suggestions?

Thanks

---

### Post by altonbr on 2008-06-13
> **gpmiii said:**
> After entering "qemu-img create -f vmdk vmware/WindowsXPPro.vmdk 10GB", I get an error - 

"Formatting 'vmware/WindowsXPPro.vmdk', fmt=vmdk, size=1048576 kB
qemu-img: Error while formatting".

I have tried changing the size to 5GB and 1GB, with out any success.

Any suggestions?

Thanks

Becareful of where it says "vmware/WindowsXPPro.vmdk". If you never created a folder called vmware and you're not currently in your home directory, that command will fail.

Try:```
qemu-img create -f vmdk $HOME/WindowsXPPro.vmdk 10GB
``` instead. This should create it as /home/<username/WindowsXPPro.vmdk

---

### Post by OisinT on 2008-08-22
edit: solved

---

### Post by cardpogi on 2009-03-26
I get an error message when it is checking virtual machine memory monitor, im running on linux4one, aspireone 160GB version,this is the log file content.
```
Mar 26 10:30:38.580: app| Log for VMware Workstation pid=9015 version=6.5.1 build=build-126130 option=Release
Mar 26 10:30:38.581: app| Host codepage=UTF-8 encoding=UTF-8
Mar 26 10:30:38.581: app| Logging to /tmp/vmware-root/setup-9015.log
Mar 26 10:30:47.934: app| Extracting the sources of the vmmon module.
Mar 26 10:30:47.997: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/usr/src/linux-headers-2.6.28.7v45aspire1/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.2.4
Mar 26 10:31:10.509: app| Extracting the sources of the vmmon module.
Mar 26 10:31:10.533: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/usr/src/linux-headers-2.6.28.7v45aspire1/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.2.4
```

---

### Post by altonbr on 2009-03-29
> **cardpogi said:**
> I get an error message when it is checking virtual machine memory monitor, im running on linux4one, aspireone 160GB version,this is the log file content.
```
Mar 26 10:30:38.580: app| Log for VMware Workstation pid=9015 version=6.5.1 build=build-126130 option=Release
Mar 26 10:30:38.581: app| Host codepage=UTF-8 encoding=UTF-8
Mar 26 10:30:38.581: app| Logging to /tmp/vmware-root/setup-9015.log
Mar 26 10:30:47.934: app| Extracting the sources of the vmmon module.
Mar 26 10:30:47.997: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/usr/src/linux-headers-2.6.28.7v45aspire1/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.2.4
Mar 26 10:31:10.509: app| Extracting the sources of the vmmon module.
Mar 26 10:31:10.533: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/usr/src/linux-headers-2.6.28.7v45aspire1/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.2.4
```

What's the error? That error log just gives me some debugging info, but it doesn't say anything went wrong!

---

### Post by cardpogi on 2009-03-29
> **altonbr said:**
> What's the error? That error log just gives me some debugging info, but it doesn't say anything went wrong!

The error message is, unable to build Kernel Module.

---

### Post by mazid on 2009-04-24
> **cardpogi said:**
> The error message is, unable to build Kernel Module.
i've get the same error with the ~same log 
any help :)

---

### Post by altonbr on 2009-05-09
> **mazid said:**
> i've get the same error with the ~same log 
any help :)

Honestly, just install virtualbox-ose or go to [http://virtualbox.org](http://virtualbox.org) and download their .deb package from there. The -ose package in the repositories uses only open source software while the package on their website has proprietary extensions.

---

### Post by canam101 on 2009-09-15
Thanks for an excellent tutorial. I have the player installed, but have not yet installed windows xp. You say:

Run VMWare Player and Install your OS
Code:
vmplayer ~/vmware/WindowsXPPro.vmx


I can run the player, but how do I install windows xp?

If I put the windows xp disk in my cd drive and click on setup.exe, will that somehow create WindowsXP.vmdk, because that seems to be what vmplayer wants?

Or do I have vmplayer browse to the CD, and do something?

Or what?

I know this is probably so obvious that it didn't seem necessary to spell it out, but some of us don't get it unless it is spelt out.

Thanks

---

