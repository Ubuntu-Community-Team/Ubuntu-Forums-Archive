---
title: "Run a Native Windows Installation on Ubuntu with Vmware Player"
date: 2007-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by inapad on 2007-03-10
I found this tutorial in this web page **[*here*]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")** I resided to give it a try and it work perfectly. Now i can start my native windows without having to reboot and without needing to create a virtual machine.
I only did some minor edits to the tutorial.



Running existing Windows installation on Ubuntu is piece of cake. What you need is Vmware player and 10 minutes of spare time.


There are two ways you can get your existing Windows installation to run in Vmware player:

1. Vmware Conventer - It converts you existing physical Windows installation into virtual machine - means; if your Windows installation is 30 GB big, you will need another 30 GB of free space to store it somewhere. Not an option in my case.

2. To setup Vmware player to use physical Windows installation. Don't worry, you will still be able to boot and use your Windows like you used to do.

Let's start with the dirty work:

I will save you a lot of trouble with creating necesarry .vmdk and .vmw files. These are files that contain your virtual machine information and are used by Vmware player. Download [**windows.vmdk**]("http://www.advicesource.org/ubuntu/files/windows.vmdk") and [**windows.vxm**]("http://www.advicesource.org/ubuntu/files/windows.vmx") but don't just fire 'em up yet. Read on.

Open console. You will use program "parted" to get some of your disk information and modify windows.vmdk file. Parted is already there in Ubuntu by default.
Strat parted with "sudo parted", (or if you have several disks "sudo parted /dev/hdx" where x the letter of the disk containing Windows installation) and type: "unit s" then "print". You will get something like this:
[IMG]http://www.advicesource.org/ubuntu/images/parted1.png[/IMG]



Note the underlined number. Now type: "unit cyl" and "print". You will get this:
[IMG]http://www.advicesource.org/ubuntu/images/parted2.png[/IMG]



Again, note the underlined numbers.

Open windows.vmdk file with text editor and find this part of file:

[IMG]http://www.advicesource.org/ubuntu/images/vmdk.PNG[/IMG]

Underlined values should be replaced with the values given by parted but there is a catch. Note that second RW value from vmdk file is not the same as the one you got from parted "Disk /dev/hda/". Thats because first partition on disk is master boot record or MBR which points to boot files of operating systems. It's lenght in this case is 63, and as far as I know, it is pretty standard value.

We will use copy of MBR so actual start point of Windows parititon is parted's value "Disk /dev/hda" 240121727 minus 63.

240121727 - 63 = 240121664 <- result goes to vmdk file

Now, you do the same for your values and modify vmdk file. Don't forget about "ddb.geometry.heads" and "ddb.geometry.cylinders".

Type "quit" in parted and make copy of MBR. Copy-paste this command into console:
"dd if=/dev/hda of=windowsxp.mbr bs=512 count=63"
If it doesn't let you do it, then try as root, write this in a terminal  "sudo -i" and then the previous command. the file wil now go to "/root". remmember that cose you will need it later.

Ubuntu part of work is done but DON'T run Vmware player yet. Put vmdk and vmx files together with copy of MBR windowsxp.mbr which is already in your home directory. (or in /root)

Now reboot into Windows and set up another hardware profile for Vmware.
Start-> Control Panel-> System, click on Hardware tab and Hardware profiles. You will find Profile 1 (Current), highlight it and click Copy, give it new name, Vmware for instance and move it up.While at Hardware tab in System properties, you can disable driver signing.

One more thing to do. As you may know, work in Vmware machines is easier with Vmware tools. I took Vmware tools installation out of Vmware Server to spare you of downloading 100 MB + file and you can download it **[here]("http://www.advicesource.org/ubuntu/files/windows.rar")**. Unpack archive and put it somewhere on Windows partition.

If you don't trust me, go to Vmware web site and download whole Vmware Server package for Linux. You will find Vmware tools for Windows inside windows.iso file.

Finally, boot back to Ubuntu, run windows.vmx, choose newly created hardware profile at prompt and install Vmware tools once in Windows.

Oh and, windows.vmx contains some of virtual machine properties like amount of RAM or enabled or disabled peripherals so scroll thru it with text editor and customize it with your own needs.


Troubleshooting:

- I you get ""Cannot open the disk" error, add your user to "Disk group";  [PHP]$ sudo adduser USERNAME* disk[/PHP]
*write your user name

- If you have Windows that requires activation, be sure to know what are you doing. I'm not familiar with Windows Activation procedures and rights so I can't help you with that;

- If you get 0x000000xx BSOD in Windows upon boot, google for that error. One of the most common problems are hidden or restore partitions on brand-name/laptop computers;
you can also try [**here**]("http://support.microsoft.com/kb/324103").I had to do what says **[here]("http://support.microsoft.com/kb/314082/")** to make it work

- Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0". error: Turn off Beryl of Compiz and try again.

just in case here is (again) the page where i found this tutorial
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

---

### Post by Sethiano on 2007-03-11
Hi!

I've followed the guide, but get an error from Grub while it starts in vmware: "Error 17".
Does any one have a solution?

It didn't say anything about grub (or similar boot manager) in the guide, so I though that the present of grub was implicit, because grub is necessary to be able to dual boot between Ubuntu and Windows.

---

### Post by lopop on 2007-03-13
Hi,

Currently i'm dual-boot (Edgy - XP). And i'm trying this guide so that I can run my XP in Ubuntu.

But I've this problem when trying to boot Windows in VMPlayer. When windows loading it went to this BSOD. (Stop 0x0000007B error) 

Can anyone help me on this. I'm really stuck in here.  :confused: 

My .vmdk file

> #!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

uuid.location = "56 4d 77 00 91 40 73 73-88 7d 44 4f 20 ab e7 2c"
uuid.bios = "56 4d 77 00 91 40 73 73-88 7d 44 4f 20 ab e7 2c"

uuid.action = "create" 
checkpoint.vmState = "windowsxp.vmss"

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxphome"
numvcpus = "1" 
memsize = "128" 
paevm = "TRUE" 
sched.mem.pshare.enable = "TRUE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "TRUE" 
tools.remindinstall = "TRUE"
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "TRUE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:ab:e7:2c"
ethernet0.generatedAddressOffset = "0"

usb.present = "TRUE" 
usb.generic.autoconnect = "TRUE" 

sound.present = "TRUE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windowsxp.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "TRUE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE" 

floppy0.present = "FALSE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "FALSE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"

Thanks in advance.

---

### Post by inapad on 2007-03-13
lopop, finish reading the post, there is a trobelshot section :P

tray with what it says here "http://support.microsoft.com/kb/314082/" it fix that problem  for me

---

### Post by lopop on 2007-03-14
thanks..  i'll try the method from the links  :guitar:

---

### Post by crysys on 2007-03-14
Well, I've tried this twice now and keep encountering the same problem.  Even after adding myself to the disk group I get this error:

```
Cannot open the disk '/home/crysys/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```

I tried this with my normal desktop using VMWare server but I figured my problem was the use of a SATA disk so I've moved over to a fresh Kubuntu install on an older box with VMWare player and a PATA drive yet the same problem crops up.  I've gone so far as setting all the files permissions to 777.  Am I missing something obvious? :confused:

---

### Post by insub2 on 2007-03-15
> **inapad said:**
> Put vmdk and vmx files together with copy of MBR windowsxp.mbr which is already in your home directory. (or in /root)

what does that mean?  dump it all in my home dir?  make a new dir for it?  how-to's for "absolute beginners" should be less ambiguous.

i'm gonna jsut put them together in my ~/ and hope it works.  Thanks for the how-to by the way.  If this works, it should be a pretty good free alternative to parallels.

---

### Post by PaulFXH on 2007-03-16
I have used the original [guide]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html") by BlackMH to run a virtual version of my existing Windows XP from Ubuntu.
Yes, it does work and is much more convenient than rebooting to get from one OS to another.
However, it is unfortunately not all that straightforward and there are quite a number of problems. 
In addition, the guide as written above, which is essentially just taken straight from BlackMH's original, is just not up to the standard which is normal for guides/tutorials in Ubuntu forums. Certainly, the howto part needs to be clarified as it doesn't work everytime straight out of the box.
I don't make any claims to being an experienced computer user but there are certainly many people who are considerably less experienced. As the procedure under discussion is fraught with traps for the unwary that could end up in serious damage to existing installations (both Ubuntu and Windows XP) this guide needs serious re-working before it is unleashed on unsuspecting Ubuntu beginners.
I will mention some of the difficulties I came across in the hope that inapad may think about upgrading this guide into something which may be of benefit to the type of person who is most likely to use guides in this forum (i.e. home user/enthusiast, not a computer professional)

1. USB devices
VM Player does not support USB 2.0 so all USB connections become 1.1
Not only that but a maximum of two USB devices can be connected to the virtual Windows XP at a time. 
So if your physical Windows XP has a USB printer, an external HD and a camera hooked up to it, and you need all three at once, you're going to have a problem.

2. Windows activation
Because the virtual Windows XP will be operated with a different Hardware Profile, it will need to be re-activated when first used. Now while this is just a minor inconvenience if it only happens once, it can become a major pain in the neck if you intend to occassionally boot into your physical Windows XP in addition to using your virtual Windows XP from Ubuntu. Everytime you boot to Windows you will have to re-activate it. After something around 10 re-activations, your CoA key becomes inactive and you need to call Microsoft to re-activate over the phone. This can take about 10 minutes.
It is not clear to me how many times Microsoft will go on allowing the same version of Windows XP to be re-activated. Therefore, the possibility that your Windows may become permanently inactive must be faced.

3. Virtual Machine boot errors
Because nearly everybody who wants to try this will have a dual boot system, they should be aware that launching VM Player will load your usual boot menu. Two things can go badly wrong here:
i) you boot to a virtual Ubuntu instead of Windows XP in error. This will badly mess up your Ubuntu installation to such an extent that you may have to re-install it.
ii) you select the wrong Hardware Profile when booting to your virtual Windows XP. This will badly mess up your Windows installation (although I have no personal experience of this myself)

4. Virtual Windows XP is illegal?
Apparently, it is not legal to use one licensed version of Windows XP as both a physical OS and a virtual OS on the same computer. It's got to be one or the other.
So, if you like the convenience of operating a virtual Windows XP from Ubuntu for small tasks but need to boot to the physical version of Windows for more serious work, then you've got a problem (in addition to the re-activation difficulties mentioned earlier).

It is not my intention to completely turn anybody against the proceedure outlined here but be aware of the problems before setting off.
There is an alternative that avoids many of the re-activation and illegality difficulties mentioned here although it doesn't give you a virtual version of your physical Windows XP. This is outlined in this [guide]("http://www.ubuntuforums.org/showthread.php?t=342631&highlight=virtual+windows") and gives you enough Windows in Ubuntu to do anything you want but is particularly suitable for small tasks (I like to use a VM Windows to access Skype from Ubuntu as SkypeOut calls just don't work well in Ubuntu in my experience).

I think this is a matter of putting all the cards on the table so that everybody knows what they may be letting themselves into. I hope others will share their good or bad experiences so that a more comprehensive all-embracing guide can be assembled.

---

### Post by ArtInvent on 2007-03-19
I would thank PaulFXH for the above. He brings up some additional points that had never occurred to me - I never got far enough to discover these drawbacks. As someone who tried this howto, found it vague in key spots, and nearly ruined both the Ub. and XP existing installs, I would caution people against this until it's been enlarged upon and made more robust. If you are familiar with the procedures and it all makes perfect sense to you, then fine. But for me, having never set up a virtual machine before, it was not good. I also got blue screen errors and never got XP to boot. 

It does seem like there should be some very easy and safe way to identify and boot an existing install in a VM. Until I find that method, I will continue to dual boot and futz with Wine. I've also discovered the almost trivially easy way to get a remote session on a nearby Ubuntu machine using XDMCP and the Windows program Xming, a setup which seems much better and more responsive than 'remote desktop' or VNC. Quite pleased with that. This way I just leave Windows on the laptop yet can still use any Linux program or the full Ubuntu desktop on it at will, at least while on my home network. Linux is truly amazing.

---

### Post by atd85 on 2007-03-19
i'v tried the guide and when i try loading the windows.vmx i get the following error..

VMware Player cannot find the virtual disk "/home/tony/vmware/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/home/tony/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

i have the windows.vmdk, windowsxp.mbr, and windows.vmx all in the same directory and it is in the /home/tony/vmware directory.. i dont know why it says it cant find it

---

### Post by Shampyon on 2007-03-22
> **atd85 said:**
> i'v tried the guide and when i try loading the windows.vmx i get the following error..

VMware Player cannot find the virtual disk "/home/tony/vmware/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/home/tony/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

i have the windows.vmdk, windowsxp.mbr, and windows.vmx all in the same directory and it is in the /home/tony/vmware directory.. i dont know why it says it cant find it

I'm using VMWare Server, so it might be different, but I think the Virtual Machines are stored in /var/lib/vmware
Open up terminal/konsole and type *sudo nautilus* to navigate your folders as root.

I'm having a few problems getting this to work too. I've followed the instructions, even going so far as to temporarily reinstate the Windows MBR so I could copy it into the VM folder. For some reason I'm still getting a GRUB Error 22...

If I get it working, I'll come back and let you know how it was done.

---

### Post by atd85 on 2007-03-22
i got it to boot.. but nothing works in it.. my mouse, usb, dvd drive.. nothing works at all and half the time it crashes my entire computer.. i posted another thread in the beginners forum about it

---

### Post by raintheory on 2007-03-22
[QUOTE=VMware Server]GRUB Loading stage 1.5


GRUB loading, please wait...
Error 21[/QUOTE]

sigh...

---

### Post by ejos on 2007-03-22
> **crysys said:**
> Well, I've tried this twice now and keep encountering the same problem.  Even after adding myself to the disk group I get this error:

```
Cannot open the disk '/home/crysys/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```

I tried this with my normal desktop using VMWare server but I figured my problem was the use of a SATA disk so I've moved over to a fresh Kubuntu install on an older box with VMWare player and a PATA drive yet the same problem crops up.  I've gone so far as setting all the files permissions to 777.  Am I missing something obvious? :confused:

Run it with sudo.

---

### Post by Shampyon on 2007-03-23
Well I've managed to get it partway there. It's starting to boot, but once that Windows boot screen starts up, the booting fails. It just restarts. I'm gonna try a few different settings to see if it works.

Oh, and putting the windows mbr in the folder (a pre-GRUB version - I'd already partitioned the drive  long before installing Ubuntu) did nothing. Strange...

---

### Post by PaulFXH on 2007-03-23
As I mentioned in an earlier post, I got this to work using BlackMH's original [guide]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html"). I had just a few easily rectifiable problems as well as some longer term issues that I mentioned in my previous post.

As so many people seem to be having issues with this howto, I'm going to provide here a little more detail on exactly what I did to get this working. The steps all refer to BlackMH's guide:

1. In Ubuntu, install VMplayer from Synaptic including the creation of a new folder "vmware" in ~/.
2. Download windows.vmdk and windows.vmx to ~/vmware
3. Change windows.vmdk as detailed by BlackMH. Note that if you have another partition between the MBR and the start of your Windows partition, you will have to subtract a number greater than 63. In my case, my Dell computer has a Dell Utilities partition between the MBR and Windows partition so I had to subtract 64260 (rather than 63) from the value Parted gives for "Disk /dev/hda". Save windows.vmdk
4. Change windows.vmx appropriately. Here are the changes I made:
i) guestOS = "winxphome"
ii) memsize = "512"  [determines how much RAM memory you want in your VM windows. I have 1 GB of RAM so I chose half this for the VM Windows]
iii) usb.present = "TRUE" [if you want your usb devices (maximum 2) to be picked up]
iv) sound.virtualdev = "es1371" ["sb 16" didn't work for me]
5. Check that your Windows partition is owned by the Disk group. Assuming it is, make sure you are a member of the Disk group (sudo adduser *your username* disk)
6. Make copy of MBR and place in ~/vmware along with windows.vmdk and windows.vmx
7. Reboot to your physical Windows and create the new Hardware Profile
8. Download and install vmwaretools from BlackMH's guide

Now you should be ready to try out your VM version of your physical Windows XP. However there's a couple of things that can go wrong and really mess up either your Ubuntu or Windows installations. These are:

1. When you launch VMplayer and select the windows.vmx file, you should be brought to your normal boot menu. Make sure that you DO NOT boot to a virtual Ubuntu. To avoid this, I found it best to increase the timeout in /boot/grub/menu.lst to 30 seconds so you don't get taken by surprise if your timeout is only a few seconds (as mine was). Also, the Ctrl-G and Ctrl-Alt commands didn't always work for me on the VM boot menu. I found it best to mouse click on the menu and that always seems to grab the control for me allowing me to safely select Windows XP to boot.
2. When you boot into Windows XP (VM), you will be asked to choose the Hardware Profile. Make sure you choose the correct one (Give the two of them completely different names as advised by BlackMH so you don't get mixed up and make sure you don't forget).

When you get to your VM Windows XP, make sure vmware tools is running (there should be an icon in your notification area and you can check in the running processes if it is really running)

Finally, you're probably going to have to activate your Windows XP so make sure you have the CoA key available.
Note, however, that if you decide to boot to your physical Windows XP again, you will again need to activate this. In my case, my CoA became invalid after about 10 re-activations so that from now on I must phone Microsoft to re-activate my Windows XP as required. This takes about 10 minutes on the phone.

Obviously, I can't be sure how well this is going to work for anybody else, but this is what got it going for me.
Good luck

Paul

---

### Post by atd85 on 2007-03-23
lots of great info.. but does anyone have any idea why that it hard locks my computer 97% of the time.. either on bootup and when i try to shut it down (the vm windows) .. and also none of my hardware works at all.. except the keyboard.. so it makes it pretty much useless.. sorry for being such a newb :(

---

### Post by PaulFXH on 2007-03-23
@atd85
It's a little difficult to make any serious diagnosis of your problem when you're not giving too much away.
My experience with this guide is restricted to one computer only. Therefore, if you did everything that I did and it still doesn't work, I really can't suggest anything.

However, given that you are by your own admission,a n00b, I really think it is a bad idea to launch your virtual adventures from this guide. As written it is definitely not for newbies.
Why don't you try this [guide]("http://www.ubuntuforums.org/showthread.php?t=342631&highlight=virtual+windows") instead.
While this won't give you a virtual version of your physical Windows, it does provide a very workable version of the same Windows (assuming you have the installation disk) that will provide a Ubuntu user with almost everything they need Windows for.

In addition, you will be able to boot to your physical Windows without having to re-activate.
The guide is very well written and there is really no downside other than that you wont get all of the crap that's included in your physical Windows. But do you really need all that stuff?

However if this doesn't work, now you've got a problem!

Good luck

---

### Post by 5thgendriver on 2007-03-24
ok so i followed this tutorial and im now stuck at this point

Cannot open the disk '/home/nick/vmrun/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The file specified is not a virtual disk.


my best guess is that im copying the mbr and it has grub on it not a win mbr - so im now going to restore the win mbr boot up in live cd perform this mbr copy again and see what happens...

---

### Post by PaulFXH on 2007-03-24
@5thgendriver
I don't believe your problem is related to Grub. It seems to me to be more likely that your windows.vmdk file has been wriiten with incorrect values.
I would therefore suggest going through BlackMH's [guide]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html") again and make sure the underlined numbers in this file are correct for your computer and Windows partition. 
A potential problem here will arise if your Windows partition is NOT directly after the MBR partition. In this case, you will need to use a number other than 63 to subtract.

---

### Post by kakabobo on 2007-03-24
i manage to reach grub screen for Os selection and after i chose Winxp, it tried to boot and get struck at the starting up screen.

any idea to fixed this ?

---

### Post by PaulFXH on 2007-03-24
You would help yourself a lot more by providing some more information on what exactly you did when setting this up. In particular, what changes did you make to the windows.vmx file?

However, if I was forced to make a guess at your problem, I would say you just might be running into a RAM problem if your Windows boot freezes before it finishes.
Did you change this line in windows.vmx?
> memsize = "128"
If not, and assuming you have enough available RAM, try moving this up to 256 or better to 512. Note that this number refers to the MB of RAM you want to devote to your virtual Windows.
Good luck
Paul

---

### Post by kakabobo on 2007-03-25
below is my windows.vmx file.
i have running on 2gig ram.
IBM X41 laptop.
it boot ok and i manage to reach the grub screen. right after the selection to boot winxp all just stop at the starting up screen.
any ideas?



#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

uuid.location = "56 4d cc d8 08 89 99 78-a5 4c 24 fa 30 b4 4f 90"
uuid.bios = "56 4d cc d8 08 89 99 78-a5 4c 24 fa 30 b4 4f 90"

uuid.action = "create" 
checkpoint.vmState = ""

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "512"
paevm = "FALSE" 
sched.mem.pshare.enable = "FALSE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "FALSE" 
tools.remindinstall = "TRUE"
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "FALSE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:b4:4f:90"
ethernet0.generatedAddressOffset = "0"

usb.present = "FALSE" 
usb.generic.autoconnect = "FALSE" 

sound.present = "FALSE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "FALSE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE" 

floppy0.present = "FALSE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "TRUE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"

---

### Post by PaulFXH on 2007-03-25
@kakabobo
I found 6 lines in your windows.vmx file that are marked as FALSE when they should be TRUE.
However, I cannot say whether any of these would cause the problem you describe. Nevertheless, it is worthwhile changing them all to TRUE and trying again.
The lines are:

usb.present = "FALSE"
sound.present = "FALSE"
ethernet0.present = "FALSE"
paevm = "FALSE"
sched.mem.pshare.enable = "FALSE"
tools.syncTime = "FALSE"

If this doesn't work, I would strongly recommend that you try this [guide]("http://www.ubuntuforums.org/showthread.php?t=342631&highlight=virtual+windows") which I have suggested already in post #18 of this thread. It is a much more Newbie-friendly guide and gives you practically everything you're going to get here with infinitely less problems.

---

### Post by maddentim on 2007-03-31
@PaulFXH

Great extra info.  I think I understand what needs to happen.  The activation part has been unclear up til now.  Can you confirm if I have it correct, if I do this VM with my physical windows, I will need to "activate" it again.  Also, if (or really when) I (or my kid) goes back into the physical windows, I would need "activate" again and then again if I went back to the virtual windows and so on...  Hence, this is why you burn through 10 activations...  Do I have it correct?  Seemed like a good idea, but now...  may be unworkable...

Thanks

---

### Post by sethmo on 2007-03-31
I get stuck at the very beginning of this tutorial.  When I open parted it says:
```

Warning: Unable to open /dev/hda read-write (Read-only file system).  /dev/hda
has been opened read-only.
GNU Parted 1.7.1
Using /dev/hda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)    
```

I only have one hard drive on this laptop, it has a few partitions as I am duel booting to XP.

---

### Post by PaulFXH on 2007-03-31
@maddentim
> if I do this VM with my physical windows, I will need to "activate" it again
Certainly in my case, I had to activate Windows when I launched the VM version of the physical Windows the first time.

> Also, if (or really when) I (or my kid) goes back into the physical windows, I would need "activate" again and then again if I went back to the virtual windows and so on
Again, in my case, Yes to all of your questions. When I emailed the original author on this point (Blackmh), he told me he was unaware of this as he had no experience with a version of Windows requiring activation. Hmmm...
> Hence, this is why you burn through 10 activations... Do I have it correct? Seemed like a good idea, but now... may be unworkable.
Again I can only refer to my own experience. After something around 10 activations, my original CoA became inactive and from then on, I had to phone Microsoft to activate over the phone which takes about 10 minutes each time.

As I have mentioned a number of times already, unless you specifically need a VM version of your physical Windows, you can save yourself an awful lot of problems by using this [guide]("http://www.ubuntuforums.org/showthread.php?t=342631&highlight=virtual+windows"). However you do need to have a re-install CD and you will have to activate the VM Windows the first time you use it but only this one time.

---

### Post by 5thgendriver on 2007-03-31
after very little effort i just decided i dont need windows anymore anyways and also i have found that i can remote desktop to other windows boxes on my network and run programs that i cant emulate in wine - but thanks for the help anyways

---

### Post by trey504 on 2007-04-21
[IMG]http://i36.photobucket.com/albums/e43/gchutz1/part.jpg[/IMG]
sorry for the shitty image
I could not get vmware to boot it just goes to a black screen and closes.
Could someone tell me if i used the right values?
I was not sure what i had to replace because mine does not start with 63 so for the MBR i used
dd if=/dev/hda of=windowsxp.mbr bs=512 count=96390

# Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 96390 FLAT "windowsxp.mbr" 0

RW 156205097 FLAT "/dev/sda" 96390 



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "ide"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "9729"

---

### Post by srhlefty on 2007-04-22
> **ArtInvent said:**
> I've also discovered the almost trivially easy way to get a remote session on a nearby Ubuntu machine using XDMCP and the Windows program Xming

I've tried this, both with XMing and Cygwin/X, but it hasn't worked for me.  Did you have to do any special configuration, unblocking of things in xp, etc?  I've already enabled remote login in System->Administration->Login Window, and I can get to the login window remotely, but never to my desktop.

---

### Post by lucky2 on 2007-04-22
Hi I have this all working OK but I have a storage ide drive(d:)(/dev/hdb) as well as a main hard drive(c:) I have it mounted with fstab and can access it using nautilus or whatever but vmware player will not see it for Windows, Ie tried guess and added * ide1:1.fileName = "/dev/hdb" * and similar to the windows.vmx, but an error is thrown saying something like 'this is not a virtual sidk' and wont mount it, any help? cheers. And I agree with that guy before up in the thread, this is not a good way to run windows apps in ubuntu, the need for 2 licences alone is enough. gg

---

### Post by PaulFXH on 2007-04-22
@trey504
I believe you need to change the count in
> dd if=/dev/hda of=windowsxp.mbr bs=512 count=96390
back to 63.
All of your other inputs seem fine to me.
Be aware, however, that if this works for you, you're going to have to re-register your CoA code everytime you switch from the VM Windows to your real Windows and vice versa.

---

### Post by trey504 on 2007-04-22
Stilll have not had any luck it does the same thing the screen goes black then it just closes a short time after. I made a few more changes but any aditional help would be greatful. Also im trying to do this with Vista Enterprise  so im not worried about CoA if this does not work im just going to delete it and reinstall in vmware but this would be nice. Does this work with vmware server? or do i need the player
dd if=/dev/sda of=windowsxp.mbr bs=512 count=63     

RW 63 FLAT "windowsxp.mbr" 0
RW 156205097 FLAT "/dev/sda" 96390 

ddb.toolsVersion = "6530"

ddb.adapterType = "scsi"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "9729"

---

### Post by PaulFXH on 2007-04-22
> Also im trying to do this with Vista Enterprise
Well, now you've left me way behind. My experience with this is limited to WinXP and VMPlayer.
However, if you're trying this with Vista, it sure doesn't seem right calling the copied mbr file "windowsxp.mbr".
Maybe you should try contacting the author of the original guide [here]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html"). to see if he has made any moves towards extending his guide to Vista.

---

### Post by xmrcivicboix on 2007-04-22
Hey! thanks for a great guide. I'm running Ubuntu on my external drive while my windows is on my main drive. Following this guide, I was able to run Windows perfectly in VMWare Player. :guitar:

---

### Post by PaulFXH on 2007-04-23
@xmrcivicboix
> I'm running Ubuntu on my external drive while my windows is on my main drive
That's an interesting concept. It might be useful to others if you were to post some further details of your experiences with this. For example,

1) Why do prefer this to the same internal drive dual-boot system?
2) How fast is your Windows when you use it through VMPlayer on an external drive. I imagine it must be significantly slower than your real physical Windows.
3) How have you overcome the need to re-activate your physical Windows when you need to go back to it? (or perhaps you don't).
4) Any unexpected upsides/downsides?

---

### Post by trey504 on 2007-04-23
I got mine up to the BSD with error 0x0000007e. I assume the problem is because ubuntu "says" I have scsi and I really only have ide. Is there anyway to change that?

[http://i36.photobucket.com/albums/e43/gchutz1/vistaerror.png](http://i36.photobucket.com/albums/e43/gchutz1/vistaerror.png)       - cap of the error


I used this to get to where im at. Select use entire disk
 [http://www.vmware.com/support/ws55/doc/ws_disk_scsi_linux.html](http://www.vmware.com/support/ws55/doc/ws_disk_scsi_linux.html)

---

### Post by PaulFXH on 2007-04-23
@trey504
This [article]("http://support.microsoft.com/kb/330182") from MS gives a number of reasons for the 0x000007e STOP error that you're seeing. 
The most likely seems to shortage of disk space. You need to look into this.

---

### Post by grinias on 2007-04-24
Thanx!!! I correctly configured the vmplayer, following your guide. But, I had to set 
 ```

sound.virtualdev = "es1371"

```
in windows.vmx 
and first run with
```

sudo vmplayer

```
and then as a simple user.

And I had to raise the capture using alsamixer in order to speak to others (and hear me) in WinXP skype. By the way my usb camera works too with skype!!!

---

### Post by starfry on 2007-04-27
> **raintheory said:**
> 
GRUB Loading stage 1.5


GRUB loading, please wait...
Error 21

I get this too. I think this happens because your Ubuntu is on hdb and your Windows is on hda. You get this when Windows is installed first followed by Ubuntu. When the VM boots, it loads from the MBR of hda but this wants to look in /boot on hdb. The Virtual Machine does not have access to hdb.

What you need is to have a "real" Windows MBR in the file "Windowsxp.mbr". The problem you have is that your Ubuntu install over-wrote that with Grub!

You can restore your Windows MBR, take a copy of it and then restore Grub but it is fiddly. Here's what I did:

(a) boot your PC using the WIndows XP install CD
(b) elect to "Repair" an existing system
(c) get to the C:\windows prompt (you'll need to enter the Amdinistrator password)
(d) run "FixMBR" - this will re-write the MBR to the root of hda
(e) exit
(f) place the Ubuntu CD in the drive, reboot into Ubuntu LiveCD
(g) run up a terminal
(h) do the following to save a copy of the windows MBR
       # dd if=/dev/hda of=windowsxp.mbr bs=512 count=63
(i) do the following to reinstate the grub MBR:
       # sudo su -
       # grub
       # find /boot/grub/stage1
(h) this will report the location of your grub boot stages (for me this is hd1,0). Issue the following commands:
       # root (hd1,0)
       # setup (hd0)
       # quit
(i) reboot

Now, when you start VMWare you'll get past the grub error, on to the next one which, in my case is a Windows blue screen of death, but I followed the Microsoft support fix at [http://support.microsoft.com/kb/314802](http://support.microsoft.com/kb/314802) as suggested in an earlier post above and that worked fine. 

The other point worth mentioning is that, for sound to work you need to change "sb16" to "es1371" in windows.vmx.

---

### Post by daveyyan on 2007-05-08
> **kakabobo said:**
> below is my windows.vmx file.
i have running on 2gig ram.
IBM X41 laptop.
it boot ok and i manage to reach the grub screen. right after the selection to boot winxp all just stop at the starting up screen.
any ideas?



#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

uuid.location = "56 4d cc d8 08 89 99 78-a5 4c 24 fa 30 b4 4f 90"
uuid.bios = "56 4d cc d8 08 89 99 78-a5 4c 24 fa 30 b4 4f 90"

uuid.action = "create" 
checkpoint.vmState = ""

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "512"
paevm = "FALSE" 
sched.mem.pshare.enable = "FALSE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "FALSE" 
tools.remindinstall = "TRUE"
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "FALSE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:b4:4f:90"
ethernet0.generatedAddressOffset = "0"

usb.present = "FALSE" 
usb.generic.autoconnect = "FALSE" 

sound.present = "FALSE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "FALSE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE" 

floppy0.present = "FALSE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "TRUE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"


I have the same question with feisty + vmware server 1.0.2.
After the selection to boot winxp in grub, it stop with a black screen(worse than BSOD?), and the host cpu rich near 100%.
Any help?

---

### Post by kilou on 2007-05-10
Hi,

I'm interested in running my existing windows install in Ubuntu but have a few questions about that:

1) Since XP is installed on an NTFS partition, if I run it in a Virtualmachine following this HowTo, will I be able to write on the XP disk (NTFS) while in the virtual machine or do I need the NTFS driver in Ubuntu for this to work?

2) Is there any speed difference between running XP on its own NTFS drive (like this HowTo) or do an XP install in a virtual machine from scratch (what most people do)? 

3) Is this possible to achieve the same as this HowTo but using VirtualBox instead of VMPlayer??? I'd like to use VirtualBox because it has a built in folder sharing capability.

Thanks

---

### Post by PaulFXH on 2007-05-10
@kilou
1. Yes, you can write to the NTFS formatted disk without installing any special drivers
2. I have used VMPlayer to run both WinXP native and as a "fresh" install (from the install CD) and I don't notice any difference in speed or operability. Make sure you have VMWare tools installed as without this your speed will suffer.
3. I have no experience with Virtual Box. Perhaps someone else can help you with this.

---

### Post by kilou on 2007-05-10
Thanks for the update PaulFXH! I've heard many people saing VirtualBox is slightly faster than VMWare. It also comes with a builtin share folder capability but I know it is still quite buggy for now although some workarounds exist. I think VMWare can onl share folders through Samba, which is much slower than what VirtualBox proposes.

---

### Post by kleuber on 2007-05-10
I´ve tried this and after read this forum for some little problems, it worked very well.


But now I´d like to know if it´s possible to do exactly the opposite: Run Existing Ubuntu Instalation on Windows with Vmware Player?




P.S.: My primary partition is Windows XP.

---

### Post by kilou on 2007-05-10
Normally you should be able to do it exactly the same way. I also have a dualboot system and when I start my existing XP install in VMPlayer from Ubuntu it first goes to Grub and I can select which OS I want to start. With this I can even start my existing Ubuntu from itself (quite weird and pretty useless:lolflag:  but it does work). So I see no reason why it wouldn't work from XP.

---

### Post by PaulFXH on 2007-05-10
> With this I can even start my existing Ubuntu from itself
I inadvertently did this too, and it resulted in a number of corrupted files. I have seen other references to this also, all of which have been very negative.
So, based on this, it is something that should not be recommended or made light of.
However, if you have another experience, it really might be interesting to hear some more, despite the fact that, as you say, it's pretty useless.
Did you really do this and came out of it unscathed?

---

### Post by kleuber on 2007-05-10
> **kilou said:**
> Normally you should be able to do it exactly the same way. I also have a dualboot system and when I start my existing XP install in VMPlayer from Ubuntu it first goes to Grub and I can select which OS I want to start. With this I can even start my existing Ubuntu from itself (quite weird and pretty useless:lolflag:  but it does work). So I see no reason why it wouldn't work from XP.


Unfortunatelly it doesn´t work. In Windows VmWare gives me this:

[i]
Cannot open the disk 'd:\Meus documentos\My Virtual Machines\windows.vmdk' or one of the snapshot disks it depends on.
Reason: O sistema não pode encontrar o caminho especificado.[/i]

---

### Post by kilou on 2007-05-11
@kleuber:

I'm confused: you're not supposed to open windows.vmdk. You want to open Ubuntu and you have to redo something similar to the tutorial on page 1 for Ubuntu BUT you'll have to use a vmdk file that is made for Ubuntu/linux, not the one done for Windows. I don't know if this file would have the same structure as the one for windows but it shouldn't be that different I guess. You can install VMWare server and create such a file for a Ubuntu/Linux system and then modify it. You probably cannot launch Ubuntu with a vmdk file made for windows......but I'm not sure about this one since I could boot my Ubuntu partition from Ubuntu with a windows vmdk file :?

One thing that may be "problematic" though is that Ubuntu has no different hardware profiles. I'm not sure Ubuntu needs that but this the only difference I can see.

@PaulFXH

your right, it's not recommended to run Ubuntu from itself.  Actually I did that by mistake first because my dualboot prompt timeout (when you choose which OS starts default) is set to 1 sec. As I did not click on the Virtual machine window after launching it the keystroke were not recorded so after only 1 sec it automatically booted on Ubuntu. However I was just mentionning that although ridiculous it appeared to work but I did not boot completely in Ubuntu. I just saw that the boot screen was loading properly so I assumed it was possible to boot Ubuntu from itself but maybe it didn't get far enough to corrupt anything.

---

### Post by Steve H on 2007-05-11
Thanks very much for this thread, it has helped me out loads. But I am just having one problem, Ihave followed the instructions carefully and now i just keep getting the following

```
GRUB Loading stage 1.5

GRUB Loading, please wait......
Error 21
```

Now I know that error 21 is grub not recognising / finding the disks listed but I don know how to edit the virtual GRUB. I have even tried the fix that involves booting in to XP Recovery Console via the Install disc in VMPlayer, But that didn´t work either.

Any one got any ideas??

:)

---

### Post by starfry on 2007-05-11
> **Steve H said:**
> 

Now I know that error 21 is grub not recognising / finding the disks listed but I don know how to edit the virtual GRUB. I have even tried the fix that involves booting in to XP Recovery Console via the Install disc in VMPlayer, But that didn´t work either.

Any one got any ideas??

:)

You're right about the disks not being found. See my earlier post on this subject (Number 40, above) I think it was.

---

### Post by Steve H on 2007-05-12
Thanks for the heads-up, starfry. I have managed to get past the GRUB error by doing as you suggested, once I worked out where the MBR was being put by the Live CD. Now I´m getting the BSOD, as you did, but when I followed the link in your thread, it doesn´t exist anymore, MS have moved the article.

I´ve dug around the other threads and someone else suggested it was a lack of disk space.....but it can´t be that as I have about 60Gb free on the Windows partition. I can´t even get into Safe Mode.

Any suggestions??

---

### Post by PaulFXH on 2007-05-12
If you're getting a BSOD, you must also be getting a Stop error ( a bunch of numbers).
You can Google these (particularly the first one which should be something like 0x0000058c).
This will provide some information as to what exactly is troubling your computer.

---

### Post by Steve H on 2007-05-12
I´m getting a 0x0000007B error which is listed as INACCESSIBLE_BOOT_DEVICE, which is similar to changing the motherboard. I have tried booting natively in to Windows and altering the hardware profile so it has Standard Dual Channel PCI IDE Controller, but that didn´t change anything, still getting the error.

Then I noticed that I had Daemon tools loaded in Windows, which install a virtual SCSI driver, so I uninstalled that as well just to be sure.

I have googled this to death now......still no joy.

HELP?!?!?

:)

---

### Post by PaulFXH on 2007-05-12
@Steve H
Unfortunately, I don't have an answer to what your problem is but it seems more of a Windows difficulty than an Ubuntu problem. Yoy might consider posting to one of the MS groups as it is likely they will be able to diagnose your Stop Error problem better than anyone here.
Another option is to try a modified approach and use this [guide]("http://ubuntuforums.org/showthread.php?t=342631&highlight=virtual+windows") to get into a VM version of WinXP.
I have already posted that I think the guide in this thread is much better written and explained than the one in the thread we're in right now. The only thing is it doesn't give you your native Windows. But, do you really need it?
In addition, as I have already explained, it avoids many of the problems associated with the method you are grappling with now.

---

### Post by Steve H on 2007-05-12
Thanks anyway PaulFXH, I´ll just have to keep plodding away at it. It is kind of annoying that I can natively boot into XP, but not through VM. I only want to keep the XP install, as I´ve had it for years, and I´m sure there is stuff on there that I´ll need as soon as I´ve wiped the disk.....sod´s law rules my life!!

Thanks again.

:)

---

### Post by PaulFXH on 2007-05-12
@Steve H
Another option is to talk to the author in the original guide on which this Howto is based. You can email him through the "contact me" link [here]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html").
I got in touch with him because of some problems I had at the time and found him to be very helpful.
Additionally, you might consider taking out everything you've done so far and starting over from scratch. You never know what kind of minor error crept into your .vmx file or whatever that might be messing you up now.
I haven't read your earlier posts, but are you sure your Windows partition starts exactly where the original guide assumed it started? When I did this, I was using a Dell computer which had a small Dell Utility partition between the mbr and the Windows partition which meant I had to make substantial changes to the numbers  in the .vmdk file
Good luck
Paul

---

### Post by Steve H on 2007-05-14
Thanks for the help but I have given up with my old windows installation. It was flakey at the best of times and so I ditched it.

I have now setup a 10 gig partition, which I used to install a fresh XP, through VMPlayer. It now boots and works fine. I did try everything to get my old install to work, but cut my losses on Saturday, I backed up all the stuff I thought I might need (or just moved it over to my Ubuntu install anyway). I only need a native XP for 2 programs (Stackz list editor & Nokia PC suite), so I was happy to free up 68gig of useless space which the XP partition was hogging. I am now trying to get the VM-XP to share files through a SAMBA share, but for some reason it "has network difficulties" when trying to authenticate itself to SAMBA. ho-hum.

Thanks to everyone for your help anyway.

:)

---

### Post by kilou on 2007-05-14
I think that the new VMPlayer 2.0 has a built in feature to share folder between host/guest, something similar to what Virtualbox does. You shouldn't need Samba anymore.

---

### Post by starfry on 2007-05-14
> **Steve H said:**
> I´m getting a 0x0000007B error which is listed as INACCESSIBLE_BOOT_DEVICE

SteveH - go take a look at [http://support.microsoft.com/kb/314082](http://support.microsoft.com/kb/314082) for the solution to that problem.

---

### Post by Steve H on 2007-05-14
@starfry, cheers for the link, but I did try all that and to no avail! but thanks anyway.

@kilou, I have noticed the shared folders section in VMPlayer, but I'm stumped how to get it working. If I share a folder on either XP or Ubuntu, nothing appears in the box, and there is no way to add a new folder in there.

I'll have a look around on that function, see what i can find!!

Thanks again guys

:)

I´ve got it all sorted now. I´ve got my SAMBA share working and all is well with the world again....

Thanks for all the help guys. This thread really helped.

:)

---

### Post by awreneau on 2007-05-15
I'm having the stop error 0x0000007b also.

I'm able to boot the XP installation w/o any problems from grub as the only OS running.  However XP will fail if running thru ubuntu.

I also used BlackMH's guide.

I'm guessing this is due to the SCSI vs. ide drive emulation, not sure.

I've uploaded  both files, had to append .txt in order to do so, in the .vmdk file I access my HD as a scsi device /dev/sda.

In the vmx file its listed as a ide device.

Is this the problem?  Im not convinced it is, but maybe its a lead.

---

### Post by kilou on 2007-05-16
Have you tried that (look into "More information"):

[http://support.microsoft.com/kb/314082/](http://support.microsoft.com/kb/314082/)

---

### Post by Steve H on 2007-05-16
> **awreneau said:**
> I'm having the stop error 0x0000007b also.

I'm able to boot the XP installation w/o any problems from grub as the only OS running.  However XP will fail if running thru ubuntu.

I also used BlackMH's guide.

I'm guessing this is due to the SCSI vs. ide drive emulation, not sure.

I've uploaded  both files, had to append .txt in order to do so, in the .vmdk file I access my HD as a scsi device /dev/sda.

In the vmx file its listed as a ide device.

Is this the problem?  Im not convinced it is, but maybe its a lead.


From my experiences trying to get it to work, it would appear that it is an issue were XP thinks it has a different hardware setup to the one listed in the HAL. I couldn't find a way around it except to reinstall through the VMware Player, there by giving it the opportunity for the XP setup to probe the "Virtual" motherboard for it's "Virtual" chipset. I think in some cases people have had this working by changing the real IDE controller to a generic Dual Channel PCI IDE controller driver and then rebooting in to Ubuntu and trying again. But I had no success with this. 

This problem is somewhat similar to chnaging a motherboard in XP, if that gives you any ideas for looking....

Good Luck

:)

---

### Post by Flavian on 2007-05-16
Btw: I found a pdf file on the vmware site itself that tells you how to set up a native windows install propperly. It also talks about certain bugs and stuff and how you can fix them.

The upload limit here doesn't allow me to upload that file though :(
So I've uploaded it on mine: [http://www.orcinus-orca.org/~Uriel/doc/ws_6.0_dualboot.pdf](http://www.orcinus-orca.org/~Uriel/doc/ws_6.0_dualboot.pdf)
enjoy

---

### Post by Steve H on 2007-05-16
That was a good find, Flavian. I'vve had a quick look through it and found this:

> [B][U]IDE Drivers in Windows 2000, Windows XP, or Windows Server 2003
Virtual Machines[/U][/B]
If you install Windows 2000, Windows XP, or Windows Server 2003 on a computer, and then try
to run that same installation of the operating system as a virtual machine that uses a physical
disk, the virtual machine might fail with an error message reporting an inaccessible boot device.
The problem occurs because the physical computer and the virtual machine require different
IDE drivers. The Windows Plug and Play feature, which handles drivers for many hardware
devices, does not install new IDE drivers.
If you encounter this problem, VMware recommends that you install your Windows 2000,
Windows XP, or Windows Server 2003 guest operating system in a virtual disk, rather than
running it from a physical disk.
If you encounter this problem but it is important for you to run the virtual machine from the
existing physical disk configuration, you can set up separate hardware profiles (as described in
Defining Hardware Profiles for Windows Guests on page 4) and manually update the IDE driver
in the profile for the virtual machine. For a detailed description of this workaround, see the
VMware knowledge base article titled “Error INACCESSIBLE_BOOT_DEVICE (Raw Disk).”

So it doesn't look like it is very easy to do.....nevermind. I ditched my partition and started again anyway.

:)

---

### Post by Matthaeus on 2007-05-16
When trying to run vmware tools on windows via vmware i get the following error:

Error 1327
Invalid Drive: F:\


Any thoughts? What is/does vmware tools do?

Thanks, Matt.

---

### Post by PaulFXH on 2007-05-16
What VMWare tools did for me was to speed up significantly the operation of the vm WinXP (under Ubuntu), smoother movement of the mouse pointer in the vm as well as permitting drag and drop of files between Ubuntu and the vm WinXP.
Worth having for sure.

---

### Post by Steve H on 2007-05-16
> **Matthaeus said:**
> When trying to run vmware tools on windows via vmware i get the following error:

Error 1327
Invalid Drive: F:\


Any thoughts? What is/does vmware tools do?

It looks like vmware hasn't mapped your drives properly so it is looking for a drive that isn't there. It might be worth looking at [_this _]("http://www.vmware.com/community/message.jspa?messageID=331114")thread from the VMware forums. It looks like quite a common error with XP using VMware.

VMware tools basically allows better communication between host and guest, also allows the cursor to just wander off the guest window instead of having to use the ctrl-alt to escape the focus.

Hope this helps.

:)

---

### Post by Matthaeus on 2007-05-16
Thanks Steve H - that page had the following post which fixed it.
Feels a lot smoother now.
[QUOTE=damage] I discovered what the problem is: Windows. It sucks.

C:\> mkdir foo
C:\> subst H: C:\foo

... retried installing VMWare Tools... works fine.

Gotta love Windows. cripes... [/QUOTE]

Just a couple of quick questions - I have 3 sata HDDS in my computer - 1 contains  NTFS windows xp boot partition + NTFS storage partition +  ubunutu & swap partions, while the other 2 are just NTFS storage drives.

Under windows (vmware) the windows boot drive + the storage partition on the same drive are visible under my computer, but the other two drives are not. Nor are the other drives visible under device management, or HDD management.

I have a number of files on these drives which i would like to directly access through vmplayer windows - and not have to copy them to one of the visible HDDs. Is there a way of doing this?

Thanks, Matt.

---

### Post by awreneau on 2007-05-17
kilou

Merging the registry information worked!

Thanks alot!

---

### Post by Clodaus on 2007-05-22
Well, I've tried everything suggested from multiple sites, including that registry patch, with no luck. I still get the 0x0000007B error. Does anyone have any other suggestions? I've been messing with it for hours and I'm not giving up on this yet :)

---

### Post by blackjackel on 2007-05-24
I get the error:

"File not found: windows.vmdk

This file is required to power on this virtual machine.  If this file was moved, please provide its new location."

Even though I followed the guide to the point and placed the .vmdk with the .vmx along with the mbr file ...

Even when I BROWSE to the file and point it to it, it still gives me that error, its as if that file dosen't even exist.

---

### Post by PaulFXH on 2007-05-24
> **blackjackel said:**
> I get the error:

"File not found: windows.vmdk


Are you sure the file is truly named "windows.vmdk" and not something YOU might think is the same but the computer doesn't?
For example, if your file is called "Windows.vmdk", you will get this error.

---

### Post by strungoutfan78 on 2007-05-25
So I finally got my vmware player to actually boot and not crash with a stop 0x0000007b error.  Too easy.  All i had to do was follow the guide which has been referred to in this thread numerous times originally poted by **altonbr**.

My problem now is,** I HAVE NO MOUSE**.  The mouse cursor is stuck in the middle of the screen and i cant get it to move.  Possibly a quick edit in .vmdk?  I know that only 2 usb devices are useable so I unplugged everything but my mouse and it still doesn't work.  Any ideas?

Oh and on another note.  I read somwhere else in this thread not to allow vmware player to boot your ubuntu partition or bad things will happen.  YES THEY WILL.  I can attest to this as i just had to reinstall last night.  I accidentally let it happen and it did all kinds of nasty things to the file system that fsck couldn't fix.

---

### Post by codeslicer on 2007-05-25
> **blackjackel said:**
> I get the error:

"File not found: windows.vmdk

This file is required to power on this virtual machine.  If this file was moved, please provide its new location."

Even though I followed the guide to the point and placed the .vmdk with the .vmx along with the mbr file ...

Even when I BROWSE to the file and point it to it, it still gives me that error, its as if that file dosen't even exist.

That file might exist, but another file might not. Make sure that you have a "windows.vmdk", a "windows.vmx", and a "windowxp.mbr", all in the correct case. That's what happened to me - I had windowsXP.mbr instead of windowsxp.mbr :)

---

### Post by codeslicer on 2007-05-25
Well, I have 2 hard drives on my PC. 1 of them has the Windows XP setup (/dev/hdb1) and the other has Ubuntu(/dev/hdd3) on it along with a swap(/dev/dhh2) and a My Documents partition(/dev/hdd1). Windows was installed first, then Ubuntu. Anyways, Grub was installed in the MBR on the Windows hard drive, while the settings were installed on /boot/grub of my Ubuntu partition. When I followed the tutorial, and started VMWare Player, I had a Grub Error 21. Reading a suggestion in Post #40, I decided to use the [MBRFix]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php") utility for Windows to restore the MBR. After that, I used savembr or something like that to save the MBR to the disk, and then restored my original GRUB MBR from a file using the MBR command. Now, I used the Windows XP mbr instead of the grub one, and it is called windowsxp.mbr (exactly the same as the grub partition). I have tried many solutions I have found on the Internet, but none of them work. If more info is needed, I will post it. Oh yeah, in the log file, one of the suspicious things in there is:
```
May 25 17:32:16: vmx| DISKLIB-FLAT  : "/home/codeslicer/VMWare Player/windowsxp.mbr" : failed to open (15): Size of extent in descriptor file larger than real size.
May 25 17:32:16: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
May 25 17:32:16: vmx| DISKLIB-LINK  : "/home/codeslicer/VMWare Player/windows.vmdk" : failed to open (The file specified is not a virtual disk).  
```

Thanks in advance, codeslicer

---

### Post by palino on 2007-05-25
> **blackjackel said:**
> I get the error:

"File not found: windows.vmdk

This file is required to power on this virtual machine.  If this file was moved, please provide its new location."

Even though I followed the guide to the point and placed the .vmdk with the .vmx along with the mbr file ...

Even when I BROWSE to the file and point it to it, it still gives me that error, its as if that file dosen't even exist.

I ve got the same problem, all files are named correctly (due to the [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html))

---

### Post by greew on 2007-05-26
> **palino said:**
> I ve got the same problem, all files are named correctly (due to the [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html))

Same problem here... I even tried to create windows.vmdk from scratch, but it didn't help.

Anyone has an idea of how to solve this?

---

### Post by codeslicer on 2007-05-26
Note that when I had my original GRUB mbr, everything worked, except I got an error 21, but now, it just says that it's not a virtual disk ???

---

### Post by palino on 2007-05-26
i think our prob is because of using the incorrect vmx file, however we have SATA disk.. (in the manual he told us to edit just .vmdk file not to .vmx) 

i think the mistake is in these lines:

ide0:0.present = "TRUE" 

ide0:0.fileName = "windows.vmdk" 

ide0:0.mode = "independent-persistent" 

ide0:0.deviceType = "rawDisk" 

ide0:0.redo = "" 

ide0:0.writeThrough = "FALSE" 

ide0:0.startConnected = "TRUE" 



ide1:0.present = "TRUE" 

ide1:0.fileName = "/dev/cdrom" 

ide1:0.deviceType = "atapi-cdrom" 

ide1:0.writeThrough = "FALSE" 

ide1:0.startConnected = "TRUE" 

simple replace ide >> scsi doesnt help so im lookin for some other solutions, but if this information helps others and know the solution, plz past it, thx a lot

---

### Post by palino on 2007-05-27
sorry about posting also cdrom-lines, before..

i think the simple replace from ide to scsi helps but now i have suspicion on the .vmdk file he uses (on that how-to) because I can open the file in text editor, but the other vmdk files on the internet (i found) are not openable (for unknown encoding).. 

i tried to download one, and it really helps, the virtual machine opened, but it was not the vmdk i wanna and i dont have any data there (nor any operating system, just floppy, cdrom, usb etc.) but it works, so i know the vmdk on the website is bad (or it needs to be converted somehow)

any ideas?

---

### Post by palino on 2007-05-27
finally i solved it

1. i wrote, if u use SATA replace ide for scsi, so NO, IT HAS TO STAY "ide" as it was.. 

2. u need to add user [you] to group "disk"

there s one more problem, while u  creatin it, it can seem nothin happen, also after reboot, i check the groups and there were no group called "disk" so i rather do it in terminal

sudo adduser [you] disk

but it just return "user [you] is already member of group disk" so..

i hope it helps ya all

---

### Post by greew on 2007-05-27
> **palino said:**
> finally i solved it

1. i wrote, if u use SATA replace ide for scsi, so NO, IT HAS TO STAY "ide" as it was.. 

2. u need to add user [you] to group "disk"

there s one more problem, while u  creatin it, it can seem nothin happen, also after reboot, i check the groups and there were no group called "disk" so i rather do it in terminal

sudo adduser [you] disk

but it just return "user [you] is already member of group disk" so..

i hope it helps ya all

Yeah.. helped me too.. thanks a lot!

Now I only have a problem with the mouse.. when I touch my mouse pad, the mouse jumps everywhere in Vista.. really annoying.. but I'll look into it!

---

### Post by jperez on 2007-05-27
Hi all,

Okay, I got it to work flawlessly from the get go.  I made a copy of my Win2000 Pro install and it worked, everything booted well, but now I need to know how to get the video drivers working perfectly.  I have an nVidia GeForce 6200-LE and I wanna know what to do to get the video drivers working in my VMWare copy of WIn2000 Pro.  Thanks!

Jesse~

---

### Post by PaulFXH on 2007-05-28
> **greew said:**
> 
Now I only have a problem with the mouse.. when I touch my mouse pad, the mouse jumps everywhere in Vista.. really annoying.. but I'll look into it!
My mouse was very jumpy (but in XP, not Vista) until I installed the VMware tools from [here]("http://www.advicesource.org/ubuntu/files/windows.rar").

---

### Post by codeslicer on 2007-05-28
I don't know, nothing works for me yet. I think it might be something wrong with my windowsxp.mbr file from windows, not the grub one. Because when I use the grub mbr, it works but i get an error 21, when i use the "Windows" version of windowsxp.mbr, I get an error saying that windows.vmdk is not a virtual disk. Help ???

---

### Post by codeslicer on 2007-05-28
LOL, everything started working when I put my 3 files in my home directory and ran it as root. :)

---

### Post by codeslicer on 2007-05-28
> **inapad said:**
> lopop, finish reading the post, there is a trobelshot section :P

tray with what it says here "http://support.microsoft.com/kb/314082/" it fix that problem  for me

The page is gone, but luckily it's still there on web.archive.org:

[http://web.archive.org/web/20050317080752/http://support.microsoft.com/kb/314082]("http://web.archive.org/web/20050317080752/http://support.microsoft.com/kb/314082")

If that link doesn't work then go to archive.org and in the take me back box enter:
[http://support.microsoft.com/kb/314082](http://support.microsoft.com/kb/314082)

Then click on the latest link. HTH! :)

---

### Post by Clodaus on 2007-05-30
Okay, I finally got this working. Getting rid of my one I customized through VMWare Workstation and just following the tutorial worked like a charm.

Note for users after upgrading Ubuntu on May 30th:

After upgrading Ubuntu today it upgraded the kernel. Before my hard drive was mounted on /dev/sda for whatever reason, but now it's mounted on /dev/hda. I had been getting the error from vmplayer stating the vmdk file could not be found, even when running as sudo. So I ran parted again, figured out it was mounted on /dev/hda, changed that in the file, and it worked properly.

---

### Post by cawill on 2007-06-02
I get this error message:

Cannot open the disk '/home/crysys/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.

I have opened vmware with 'sudo vmware' but the same error is given. I have full read/write permissions on windows.vmx, windows.vmdx and windowsxp.mbr

How do I fix this?

---

### Post by PaulFXH on 2007-06-02
> **cawill said:**
> I get this error message:

Cannot open the disk '/home/crysys/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.

I have opened vmware with 'sudo vmware' but the same error is given. I have full read/write permissions on windows.vmx, windows.vmdx and windowsxp.mbr

How do I fix this?
I got the same error when I tried this first. The solution was to make myself a member of the Disk Group (which is the owner of the HD where your physical Windows is installed).
BTW, I had also tried "sudo vmware" to overcome this difficulty but it actually produced another problem in that the ownership of the "Permissions" file in ~/vmware had changed to Root. I had to revert this ownership back to me to overcome the resulting problems.

---

### Post by cawill on 2007-06-02
Ok, added my user to the disk group and it works now, thanks for your help.

---

### Post by dimmanramone on 2007-06-14
It was a while ago that i found this guide about using the existing installation of windows with vmware, so after some thinking and reading around the net, i decided to give it a try today...but i got a problem that seems a lot of people to have...when i'm trying to run the VM i'm getting

```
Cannot open the disk '/path/to/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```

1. I used the guide and made everything
- made the vmdk and vmx
- copied the windowsmbr
- change the numbers using parted
- change the memory that is going to be used

2. I add user my username in the disk group

but still getting the same error

here are coming my vmdk and vmx files

vmdk
```
# Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 63 FLAT "windowsxp.mbr" 0

RW 488397104 FLAT "/dev/hda" 63 



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "ide"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "30401"
```

vmx
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"

uuid.location = "56 4d 42 68 cb cf 36 23-d5 49 c6 cf b7 e6 b4 6a"
uuid.bios = "56 4d 42 68 cb cf 36 23-d5 49 c6 cf b7 e6 b4 6a"

uuid.action = "create" 
checkpoint.vmState = "" 

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "640" 
paevm = "TRUE" 
sched.mem.pshare.enable = "TRUE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "TRUE" 
tools.remindinstall = "FALSE" 
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "TRUE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:59:aa:eb" 
ethernet0.generatedAddressOffset = "0" 

usb.present = "TRUE" 
usb.generic.autoconnect = "FALSE" 

sound.present = "TRUE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = "" 
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "TRUE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom"
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE"

floppy0.present = "TRUE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "TRUE"

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"

priority.grabbed = "normal"
priority.ungrabbed = "normal"

snapshot.disabled = "TRUE"

sound.startConnected = "TRUE"
```

I have 3 os (win,ubuntu and suse) in my system all in hda and windows are in the first partition of the disk (hda1) using grub from suse...

someone that can help me, with that?

---

### Post by dimmanramone on 2007-06-14
oh I forgot to write that i created one VMware hardware profile in windows...so hopefully i have everything :)

---

### Post by dimmanramone on 2007-06-14
I realized that i had to change the permissions in windowsxp.mbr file...i change them...getting grub...getting the menu for the hardware profile...and of course BSOD...i went to the link that i found in this thread about receiving the errot Stop 0x0000007B ([http://support.microsoft.com/kb/314082](http://support.microsoft.com/kb/314082)) ...but i don't really understand what i have to do :S ... anyone that can explain in more plain words?

---

### Post by dimmanramone on 2007-06-15
Finally i boot normally in windows with the VMware hardware profile, followed the instructions from the link on the microsofts site that i mentioned before...and then tried again to run windows with vmware...it worked...

thx for the guide...finally it was not so difficult as i thought in the beggining...

i just have one more question...hopefully there is someone to help me with that...

i cannot see my sata hdd in windows when i'm running it through vmware, do i install the normal drivers of my sata hdd or there is specials drivers from VMware that i have to install?

thx in advance

---

### Post by sab0403 on 2007-06-27
Alright, I tried the guide already, and I ran into a few problems... I solved them and it's running now, however, so I'd like to share what I did with you...

FIRST and foremost, I did everything as the guide said. Some ambiguous points cleared up:

- All three files (windowsxp.mbr, windows.vmdk, windows.vmx) apparently have to be housed somewhere in the native linux partition(s). Home directory works fine because you already have all permissions for it. However, you CAN NOT put the files in any other partition (I know this because I tried to put them in the secondary Windows partition, not the one I have the OS on, but the one I keep all my data on, and the VM wouldn't run). Just in case you were wondering. Oh, and yes, **they do have to be together**.

- When you're editing the windows.vmdk file you're told to modify this part:

```
# Extent description
RW *63* FLAT "windowsxp.mbr" *0*
RW **240121664** FLAT "/dev/hda" *63*
```

and this part:

```
ddb.geometry.sectors = "**63**"
ddb.geometry.heads = "**255**"
ddb.geometry.cylinders = "**14946**"
```

With your own numbers. Notice that the bold is the ONLY thing you have to modify, UNLESS the Windows partition you're trying to boot from is not the first partition displayed here:

[IMG]http://www.advicesource.org/ubuntu/images/parted1.png[/IMG]

Then you'd have to substitute what's on *italics*, as well as the bold on the first part of the windows.vdmx file, with different numbers. The bold you substitute with the substraction indicated on the guide, but I have no idea what you substitute the *italics* with. Perhaps someone who has could PM me and then I'll edit this post :D.

- If your disk is Serial ATA (check the blue screen above and see if yours says **/dev/sda** instead of **/dev/hda** on the second line), you have to modify the windows.vmdk file further (skip this whole step if yours is an IDE drive). You have to change the line

```
RW 240121664 FLAT "**/dev/hda**" 63 
```

and modify the bold so it reads "**/dev/sda**". The guide says that you should also modify this line:

```
ddb.adapterType = "**ide**"
```

so now the bolds read "**scsi**". HOWEVER, as soon as I did that, I ran into the problem previously described in this thread - a Blue Screen of Death that appeared as soon as Windows started booting:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=27274&d=1173765063[/IMG]

and so I had to follow [this Microsoft guide]("http://support.microsoft.com/kb/314082") (which requires you to boot into Windows) to fix it. A few people here report this worked for them; for me, it didn't (though it might still be a required step nonetheless), and after fiddling with windows.vmdk for a while, I ended up restoring the ddb.adapterType line back to "ide". So you might want to try the guide's recommended steps first, then consider switching that line back (remember this step applies ONLY if your disk is Serial ATA).

- To correct the "not enough permission" error, as well as another error which I cannot remember (regarding permissions or accessing the virtual disk), I added myself to the disk group:

```
sudo adduser *myusername* disk
```

and also I had to change ownership of the windowsxp.mbr file (which is owned by root initially). I tried to use

```
sudo chown *myusername* windowsxp.mbr
```

but for some reason it didn't work for me, so I ended up copying it to another file, erasing windowsxp.mbr, then renaming that other file to windowsxp.mbr (that other file was created by me, so I had full permissions over it). However (once again) the chown command is reported to work, so try that first.

- Finally, the "mouse doesn't work problem". That's fixed rather easily. We're now going to modify the windows.vmx file. Since my mouse is USB, I had to modify the following lines:

```
vmmouse.present = "FALSE"
```

and

```
usb.present = "FALSE" 

usb.generic.autoconnect = "FALSE"
```

as you're probably guessing, we have to change every "FALSE" into "TRUE". However, if your mouse is not an USB, just modify the first line, and you can leave the second and third alone (though any USB devices won't work, obviously).

Then, and only then, I had a chance to boot to XP. The first boot was incredibly slow, however, and it took my PC about five full minutes to boot completely. The mouse and keyboard didn't respond immediatly after the login screen showed up (they took about a minute), so give it time. I had to reactivate my XP copy indeed, and I'm still fiddling with the video driver in XP (it doesn't show me the resolution I need), but at least it works now.

I hope this helps anyone who still has any doubts. If you see something wrong with this post, please PM me and I'll make the pertinent changes.

---

### Post by stianalm on 2007-06-28
Sab: 
That's really helpful! Thanks for posting your findings.

---

### Post by sab0403 on 2007-06-28
No problem. If you run into some more trouble, or if you find any innacuracies, please PM and I'll make the changes as needed.

---

### Post by the8thstar on 2007-07-04
I have three problems:

1 - How am supposed to copy the MBR? No instructions or command line are given!!!

2 - > the8thstar@the8thstar-laptop:~$ sudo -i dd if=/dev/hda of=windowsxp.mbr bs=512 count=63
Password:
/bin/dd: /bin/dd: cannot execute binary file

How can I fix this?

3 - Also, whenever I launch VMWare Player, I get the following message:
> 
VMware Player cannot find the virtual disk "/home/the8thstar/vmware/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/home/the8thstar/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

But the file IS there... Stupid program :(

---

### Post by sab0403 on 2007-07-05
> **the8thstar said:**
> I have three problems:

1 - How am supposed to copy the MBR? No instructions or command line are given!!!

2 - 

How can I fix this?

3 - Also, whenever I launch VMWare Player, I get the following message:


But the file IS there... Stupid program :(

1) Actually, the code given in 2) is the code that copies the MBR. but you shouldn't have to use sudo -i, considering you're running it on your home directory... 

2) It does sound, however, like your dd command doesn't want to run. I don't know enough to help you there, but that's the problem here...

3) That has to do with the error in 2). Since you don't have windowsxp.mbr, the VM can't run.

Remember that you MUST have all three files (windows.vmx, windows.vmdk, windowsxp.mbr) in the same directory.

Hope this helps.

---

### Post by grantkelly on 2007-07-06
Try running
```
sudo /usr/bin/vmplayer windows.vmx
```

For some reason vmplayer is giving the error message that it can't find the .vmdk file, when really it just doesn't have the right permissions for something else.

---

### Post by don_xvi on 2007-07-07
Hey, great thread it contained about all the information I needed.  I have a dedicated hard drive I wanted to continue running my WinXP off of and it's going now.  As noted, I had to change the audio emulation, and I'm still having to run it with sudo, etc.  

What I have to add is about the network adapter, I couldn't see my Windows network with the virtual machine until I went into the .vmx file and changed 

ethernet0.connectionType = "nat" to "bridged"

That allows the virtual machine to use the network adapter directly and see the rest of the network instead of appearing behind a NAT where it could still see the internet, but not the Windows workgroup.

---

### Post by ElemonGW on 2007-07-07
After some errors that i finally manage to fix, I am at the last step where I run windows.vmx. I get this error
```
VMware Player cannot find the virtual disk "/home/elemongw/Desktop/vmware/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/home/elemongw/Desktop/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.
```
I added my user to disk group with
```
 $ sudo adduser USERNAME* disk
```
but still nothing. Any help?
PS: Yes, I replaced USERNAME* with mine username.

EDIT: Yes, I have all the files in the same folder :)

---

### Post by ElemonGW on 2007-07-07
Managed to fix that too, now I get a blue screen of death. Let's see what we can do for that.....
EDIT: I attached the image which shows exactly the error i get. I get it when windows try to boot. The boot screen appears for a second and before it completely appears this error is encountered and after no time it restarts (i was lucky that i was able to capture the error :) ). Hope that somebody can help me......
EDIT2: I have a SATA drive. Also my CPU has to processors (because I found a setting in windows.vmx about it but when I tried to set it to 2 it gave me this error
```
This product allows you to run virtual machines with at most 1 virtual processor.  Your virtual machine has 2 processors configured, which exceeds this limit.
```

---

### Post by the8thstar on 2007-07-07
**sab0403**

> 1) Actually, the code given in 2) is the code that copies the MBR. but you shouldn't have to use sudo -i, considering you're running it on your home directory... 

2) It does sound, however, like your dd command doesn't want to run. I don't know enough to help you there, but that's the problem here...

3) That has to do with the error in 2). Since you don't have windowsxp.mbr, the VM can't run.

Remember that you MUST have all three files (windows.vmx, windows.vmdk, windowsxp.mbr) in the same directory.

Hope this helps.

Well, my problem was that my hard disk is not listed as 'hda' but as 'sda' by Ubuntu, hence the problem. I just changed the command line and altered windows.vmx accordingly. And voila, XP runs on VMWare!

I have three problems to sort out before I can be completely happy with my config.

1 - I installed NTFS-3G but I'm still unable to modify or create files on my Windows partition from Ubuntu. Why is that?

2 - After I installed rdesktop in Ubuntu and seamlessrdp in Windows, I ran the following command line:

> rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Windows Media Player\wmplayer.exe" <ip>:3389 -u administrator -p password

but it's not working still. Why? Which IP should I input?

3 - Is there a way to config the network with VMWare to allow Windows and Ubuntu to actually 'see' one another? I have it configured to NAT right now. Should I change it to Bridged?

---

### Post by superFerra on 2007-07-10
WORKS!!! 

i had to follow the procedure indicated into Microsoft Knowledge base id: 314082 because of SATA controller. 

Well i'm usign my windows installation on p P4 2.8GHz proc ASUS mobo and 512MB ram but it seems to me to be much slower than my full virtualization performed by VMWare Server on an Athlon XP 2400 (ASUS mobo but 2Gb RAM)

Do you know if VMWare server is faster than Player?

@the8thstar:

1- Install NTFS-config from Synaptic to enable Write support to your NTFS partitions BEWARE!!!: Do not write on NTFS disks while windows is using 'em (personal experience :) ) Yuo shoul umount them first

---

### Post by ElemonGW on 2007-07-11
> **superFerra said:**
> WORKS!!! 
i had to follow the procedure indicated into Microsoft Knowledge base id: 314082 because of SATA controller. 

Can you please specify what you did???

---

### Post by n8bounds on 2007-07-11
If you don't have to join a domain with your XP, you might like to give this a try after you get a VM working:

[http://www.ngbnet.org/seamlessrdp](http://www.ngbnet.org/seamlessrdp)

cheers

---

### Post by kalekseishaken on 2007-07-12
My problem is strictly a permissions issue.

I can run the VM. It will log into Windows2000pro and will let me open files but will not let me write anything from inside of the VM.

The partition is owned by 'root' it is an NTFS partition that I have full 'create/delete' permissions to as setup with ntfs-3g.

The funny thing is that if you try to write a file, you don't get an error. But if you check to see if the file is there, it is not.

---

### Post by kalekseishaken on 2007-07-12
I keep seeing comments about the 'disk' group on my computer. I don't see any such group listed on my Feisty install.

Since the Windows 2000 VM will run, could it theoretically be something inside of my install of Windows 2000? Though I have to admit that the Windows 2000 install appears to work fine when I am in it natively.

Ciao . . . C.Joseph

---

### Post by kalekseishaken on 2007-07-13
I looked at my earlier message and it may not have been clear where my problem lies at.

I installed VMPlayer. I created the VM.

When I run the VM using;

  sudo vmplayer ~/.Windows200/windows.vmx

The VM runs. I get to Windows 2000, and it lets me log-in.

I then load the toolkit ISO, and that where the problem comes in. It copies the files and then it says 'Starting services'. There are 5 bars on the progress bar then I get the following message;

   Error 1920.Service VMTools (VMTools) failed to start. Verify that 
   you have sufficient privileges to start system services.

The VM does everything I need except I have to have the higher screen resolution which is I am running the toolkit ISO.

I tried doing a search for this error and did not come up with a solution. I do have one question when I start the VM, should the partition that holds the Windows 2000 native install be mounted? I used ntfs-3g to mount the partition with full 'create/delete' rights.

The problem with being able to write to the disk is solved. I can open NotePad and make a file and save it and it works fine.

Any help on solving the above quoted error would be appreciated.

Ciao . . . C.Joseph

---

### Post by superFerra on 2007-07-17
> **ElemonGW said:**
> Can you please specify what you did???

i followed the instructions from inapad:
-prepared vmware player (did the parted trick)
-created an hardware profile in windows (copy)

firsti time i booted windows from VMWare (of course choosing VMWare hardware profile) the BSOD came to me ... 
then i followed these instructions:
[http://support.microsoft.com/?scid=kb%3Ben-us%3B314082&x=14&y=10](http://support.microsoft.com/?scid=kb%3Ben-us%3B314082&x=14&y=10)
0-Rebooted into windows (vmware hardware profile!)
1-Created the megaide.reg file (copy and paste)
2-verified that Atapi.sys, Intelide.sys, Pciide.sys, and Pciidex.sys files were into %SystemRoot%\System32\Drivers folder
Merged the .reg file to the registry
3- rebooted in ubuntu

4-enjoy

I'VE A LITTLE PROBLEM:
i changed network from nat to bridged but i'm having problems with domain authentication. Is there a way to fix it??

---

### Post by superFerra on 2007-07-17
SOLVED!

i had to force winxp to not change it's workstation password then rejoin my domain

now it's working like a charm except that semms to me incredibly slow! (worst than on my home pc that is an amd 2400+)

---

### Post by Likenota on 2007-07-17
umm yea this may seem like a dumb question.. but it seems to me that the parted thing doesnt recognize the command print for me... ?

---

### Post by superFerra on 2007-07-17
> **kalekseishaken said:**
> I keep seeing comments about the 'disk' group on my computer. I don't see any such group listed on my Feisty install.

Since the Windows 2000 VM will run, could it theoretically be something inside of my install of Windows 2000? Though I have to admit that the Windows 2000 install appears to work fine when I am in it natively.

Ciao . . . C.Joseph

'disk' group exists and it's an ubuntu (debian) users group. It's like an hidden/system group and you can add your user to that group only by terminal issuing the command
```

sudo adduser <you_user_name> disk 

```

---

### Post by SlowAde on 2007-07-18
I experience an error 21 problem with grub when I try to boot my windows xp installation with vmplayer.

I followed [these instructions]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html"). I tried to follow them as faithfully as I could but maybe I missed something..

My parted output is as follows :-

Disk /dev/sda: 312499999s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 63s 112454s 112392s primary fat16
2 112455s 305684819s 305572365s primary ntfs boot
3 305684820s 312496379s 6811560s primary fat32


Disk /dev/sda: 19452cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 19452,255,63. Each cylinder is 8225kB.
Partition Table: msdos

Number Start End Size Type File system Flags
1 0cyl 6cyl 6cyl primary fat16
2 7cyl 19027cyl 19021cyl primary ntfs boot
3 19028cyl 19451cyl 424cyl primary fat32

-- snip --


My vmx file is as follows :-

--- snip ---

# Disk DescriptorFile
version=1
CID=9428f535
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "windowsxp.mbr" 0
RW 312499936 FLAT "/dev/sda" 63

# The Disk Data Base
#DDB

ddb.geometry.cylinders = "19452"
ddb.geometry.heads = "255"
ddb.geometry.sectors = "63"
ddb.virtualHWVersion = "4"
ddb.adapterType = "scsi"
ddb.toolsVersion = "0"

floppy0.present = "FALSE"
floppy0.fileName = "/dev/fd0"
floppy0.startConnected = "FALSE"

--- snip ---

It would be great If anyone can spot anything I have got wrong or missed, or is able to suggest something I might try.

Thanks,

Adrian.

---

### Post by Hasen_A on 2007-07-18
> **lopop said:**
> Hi,

Currently i'm dual-boot (Edgy - XP). And i'm trying this guide so that I can run my XP in Ubuntu.

But I've this problem when trying to boot Windows in VMPlayer. When windows loading it went to this BSOD. (Stop 0x0000007B error) 

Can anyone help me on this. I'm really stuck in here.  :confused: 

My .vmdk file



Thanks in advance.

Just curious as to how you managed to pause the screen to stay at the BSOD?

---

### Post by kalekseishaken on 2007-07-21
I've got everything running.

My problem is that I don't have enough permission to run VMTools. When I run the ISO from within Windows2000, it gets to the point where it is supposed to start services, and I get an error 1920.

How do you get VMPlayer to allow you to run VMTools.

The 'native' VM works fine, but I must have a screen resolution of 1024 x 768. I was told that I have to run VMTools to do that.

I tried to install VMWorkstation but it consistently aborts the install.

If anyone knows how to make VMTools install I would really like to know.

Thanks,
C.Joseph

---

### Post by Likenota on 2007-07-21
i get to the command print and it doesnt work... any ideas guys ?


[PHP]
]likenota@likenota-desktop:~$ sudo parted /dev/hda1
GNU Parted 1.7.1
Using /dev/hda1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            
Error: Can't have a partition outside the disk!                           
(parted) unit s                                                           
(parted) unit s print                                                     
Error: Can't have a partition outside the disk!                           
(parted)     
[/PHP]

---

### Post by kalekseishaken on 2007-07-21
Hi All,

I solved the problem of doing a 'custom' install of VMTools and had it only load the SVGA and mouse drivers.

The system now works perfectly. I will probably not have to boot into the 'native' Windows ever again . . . assuming that Ubuntu doesn't crash on me.

Ciao . . . C.Joseph

---

### Post by Likenota on 2007-07-21
Delete this post..

---

### Post by Likenota on 2007-07-21
please delete message.

---

### Post by Likenota on 2007-07-21
please delete message.

---

### Post by Likenota on 2007-07-22
sorry for double posting ... i got it working and everything but i cant seem to get the drive to be read.... any ideas guys ?

---

### Post by superFerra on 2007-07-23
> **Likenota said:**
> i get to the command print and it doesnt work... any ideas guys ?


[PHP]
]likenota@likenota-desktop:~$ sudo parted /dev/hda1
GNU Parted 1.7.1
Using /dev/hda1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            
Error: Can't have a partition outside the disk!                           
(parted) unit s                                                           
(parted) unit s print                                                     
Error: Can't have a partition outside the disk!                           
(parted)     
[/PHP]

You're trying to use a specific partition "/dev/hda**1**". I think you've to issue "sudo parted /dev/hda" without any trailing number...

---

### Post by Hasen_A on 2007-07-23
I've gotten farther :). Now the booting process works and windows comes to the screen where it is loading it's OS with the blue bar going from left to right. Sadly, it crashes after a few seconds without any error messages. 

I have created a 2nd profile, but I didn't install the **VMTools** before booting into that profile. Is that a must?

---

### Post by Likenota on 2007-07-23
you have to install vmtools while you are in the virtual system.. ;)  

also my sata drive isnt being read when i get into the virtual machine any ideas ? my primary hard drive is ide and my secondary is sata where my files such as psds and music are..

---

### Post by Hasen_A on 2007-07-25
> **Likenota said:**
> you have to install vmtools while you are in the virtual system.. ;)  

also my sata drive isnt being read when i get into the virtual machine any ideas ? my primary hard drive is ide and my secondary is sata where my files such as psds and music are..
thats what I did under vmware server. am I perhaps mistaken, when I want to boot my physical c:\ partition?
why does the system crash on the windows load screen, any thoughts?

---

### Post by Lorek on 2007-08-06
I don't know if its been mentioned before but if you don't get the correct MBR it'l load grub instead of windows straight off the bat. If grub in vmware accidently loads linux it'l screw your bootup pretty badly. I just barely got things fixed without having to do a complete reinstall. Really messed up the filesystem when you try and have linux running in vmware and outside vmware at the same time.

---

### Post by Lorek on 2007-08-06
> **Hasen_A said:**
> Just curious as to how you managed to pause the screen to stay at the BSOD?

I believe you can pause the screen by hitting the pause break key on your keyboard. I know that it allows you to pause the bios post when you hit it, should do the same thing with BSOD's.

---

### Post by Hasen_A on 2007-08-06
Well my BSOD used to stay for only a quarter of a second, not enough time for me to pause break.

---

### Post by Lorek on 2007-08-06
I've just about got everything running perfectly with vmware now. Running VMplayer 2.0. I was messing around with the settings in the vmx file i noticed there was an option to allow more then 1 cpu for multi core systems. However it seems there's a huge performance hit for using it. I'm only down to the annoyances now which is kinda nice.

So, does anyone know where to look for the windowsxp mbr so I can completely bypass grub. Already made the mistake of accidently booting into linux twice now, real nasty both times cause it totally corrupts the file system.
I have multiple partitions on one hard drive but it boots straight to grub first
/dev/hda
1.HDA1       WinXPPro    NTFS      +Boot
2.HDA2       Data             NTFS
3.HDA3        root              ext3
4.HDA4        swap           swap

Also for some reason file's i've copied over to the ntfs drive using the 3g driver don't show up in my vmware os even though they are there. Anyone know how to fix that w/o samba.

And for the other thing, does anyone know if there's a way to get directx to work. Nothing that's really required for games, but i'd like to be able to watch my anime fansubs with decent quality and the display in vmware seems to show up kinda grainy with the standard codec pack from CCCP. I'm figuring its prolly the svga driver and no directx support.

---

### Post by NoSmokingBandit on 2007-08-08
When i go to run the xp machine it says it cant find the file windows.vdmk, but its in the same directory as the .mbr and .vmx files. When i choose to browse for the location of it and choose the file it says the same thing again...

---

### Post by David Valentine on 2007-08-08
OK, I'm stuck and I can't find an answer elsewhere in the forums.  Help!  When I attempt to launch vmplayer, I get the following errors:  > $ vmplayer
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:19523): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

(vmplayer:19523): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)Any ideas?

---

### Post by superFerra on 2007-08-09
@David Valentine: How did you install vmware player?
Do you have libpng installed? 

@NoSmokingBandit: Are you member of 'disk' group? Where is .vmdk file stored? On an NTFS disk? It doens't work from there.

@Hasen_A: I think your system isn't recognizing your IDE/SATA controller follow there instructions: [http://support.microsoft.com/kb/314082/](http://support.microsoft.com/kb/314082/)

---

### Post by David Valentine on 2007-08-09
Thanks for your response.
> **superFerra said:**
> @David Valentine: How did you install vmware player?
Do you have libpng installed? 
I installed VMWare player from the repos, and at one point I had it working nicely--I'm wondering if maybe an update messed with it somehow?  I tried uninstalling and reinstalling, again from the repos--I got no error for installation, but still got the errors I quoted.  And yes, libpng12-0 is installed.

Could kiba-dock or compiz-fusion be causing a conflict?  I'll try removing them...
UPDATE:  Nope, they're not the problem.

---

### Post by Ellzinhand on 2007-08-14
I have had that problem with the libraries before.  Just remove the file from the folder (put it somewhere safe in case I'm wrong), or rename the file.  In stead of using the vmware libraries, it uses your own, and thus it works.

---

### Post by David Valentine on 2007-08-15
> **Ellzinhand said:**
> I have had that problem with the libraries before.  Just remove the file from the folder (put it somewhere safe in case I'm wrong), or rename the file.  In stead of using the vmware libraries, it uses your own, and thus it works.
I renamed both /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1 and /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0.  Now attempting to execute vmplayer yields no errors--and indeed, no response whatsoever.  I'll try rebooting to see if that helps.

UPDATE:  Rebooting changed nothing.  > $ vmplayer
$then nothing happens.

---

### Post by dimmanramone on 2007-09-08
I have followed this guide and everything worked perfect for me...I just reinstalled ubuntu and i would like to do make maybe a dum question, but i'm going to make it...what if I make one copy of the mbr with first choice in the operating systems to be windows and then change the order of the operating systems in the grub....am I going to have a problem?

With way I can have like a default choice the windows in the grub...and Ubuntu like default choice in my actuall grub...

Is it possible?It would be great to know that everytime i'm loading windows from VMware is not any change to destroy my Ubuntu installation and everytime that I am restarting my PC to start directly with Ubuntu without getting in the trouble to choose it...

thx in advanced

---

### Post by pakku on 2007-09-14
> **lucky2 said:**
> Hi I have this all working OK but I have a storage ide drive(d:)(/dev/hdb) as well as a main hard drive(c:) I have it mounted with fstab and can access it using nautilus or whatever but vmware player will not see it for Windows, Ie tried guess and added * ide1:1.fileName = "/dev/hdb" * and similar to the windows.vmx, but an error is thrown saying something like 'this is not a virtual sidk' and wont mount it, any help? cheers. And I agree with that guy before up in the thread, this is not a good way to run windows apps in ubuntu, the need for 2 licences alone is enough. gg


Hi,
Did you ever get this answered?  More by accident than design I managed to get this working but have the same issue- two distinct hard disks and the virtual Windows can't see/access the 2nd hard 
disk.  

I have no idea what all the changes I made were, I blindly followed instructions.

Given all the possible horror scenarios, I might just pack this in and create a virtual machine using qemu and reinstall windows in that. It is just that I have a fair bit of programs installed on the windows side I didn't want to have to redo it!

---

### Post by LeonI on 2007-09-23
> **NoSmokingBandit said:**
> When i go to run the xp machine it says it cant find the file windows.vdmk, but its in the same directory as the .mbr and .vmx files. When i choose to browse for the location of it and choose the file it says the same thing again...

I'm having this exact problem. Did you have any luck?

EDIT: nevermind... found the solution earlier in this same thread, it's the same permission problem thingie everyone's having

---

### Post by benlooi on 2007-10-10
I had the problem when starting parted and got:
/dev/hda opened as read-only. (blah blah).

The solution to this is

sudo parted /dev/sda

because my partitions are sda1, sda2, sda3 etc....
 Hope this is useful to anyone out there. I googled around but couldn't find a solution...

---

### Post by benlooi on 2007-10-10
Sigh...still having no luck in getting Windows running...got to the Windows XP loading screen, blue bar runs left to right for a few secs...then BSOD again...it seems to run a little longer now though...
Anywa I've been going through this thread and have solved a few problems I encountered along the way...hope this could be useful to someone.
The problem of a possible error you might face is with the windows.vmdk figures you plug in. Yeah, this howto says MINUS 63 from the "parted -> unit s -> print result. HOWEVER, for those people like me with a hidden rescue partition (i'm using a Dell Vostro), you will see the return values as such:
0 [Your MBR details  Start=0 End=63]
1[Your HIDDEN/RESCUE partition Start=63 End=XXXXXX]
2[You WINDOWS partition START=XXXXXX+1 end=YYYYYY]
3 ....
4 ....

So, instead of subtracting 63 from your returned result line that says:
RW = [somenumber] blahblah 63

you subtract the XXXXX+1, i.e., the start of your WINDOWS partition from the [somenumber] figure, and put this into the appropriate place/line in your VMDK file.

It should work. Worked for me, now onto my other problems...

---

### Post by luistorresmx on 2007-10-10
Hi guys! I have a problem that i think it might be simple to solve.

I did everything according to the tutorial, but when I pick Windows Xp Professional from the GRUB it takes me to a screen that says: "Starting up." which is very similar to the one that is shown when loading Ubuntu, and it stays there.

I don't want to corrupt my Ubuntu system, so, is there any clue about what i got wrong in order to having that issue?

My files are:

windows.vmdk

# Disk DescriptorFile
version=1
CID=a19f6330
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "windowsxp.mbr" 0
RW 117210176 FLAT "/dev/sda" 63 

# The Disk Data Base 
#DDB

ddb.toolsVersion = "6530"
ddb.adapterType = "ide"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "7296"

and my windows.vmx

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

uuid.location = "56 4d 94 98 e0 47 46 ac-a3 f5 05 80 a2 b6 3b 40"
uuid.bios = "56 4d 94 98 e0 47 46 ac-a3 f5 05 80 a2 b6 3b 40"

uuid.action = "create" 
checkpoint.vmState = "windows.vmss"

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "512"
paevm = "TRUE" 
sched.mem.pshare.enable = "TRUE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "TRUE" 
tools.remindinstall = "FALSE" 
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "TRUE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:b6:3b:40"
ethernet0.generatedAddressOffset = "0"

usb.present = "True" 
usb.generic.autoconnect = "false" 

sound.present = "TRUE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "False" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "False" 

floppy0.present = "False" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "False" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"

I'm on a HP Compaq Tc4200.

Thanks for the help!

---

### Post by benlooi on 2007-10-12
Aha! More success! but not there yet....

After googling around for tips, I finally got past my starting up screen. I went as far as the activation stage, then my mouse got stuck.

Anyway I think I know what went wrong earlier. Here's what I did today:
When I ran vmplayer in terminal, it showed some error msg about the /usr/lib/libpng12.so.1 and the vmplayer/lib/libpng12.so.1 file. Just copy the one in the /usr/lib one to the directory where the vmplayer/lib/ is.

Also, I did a reinstall of vmplayer and went through the tutorial again. I know now that it had something to do with the SATA disk that I have, so after changing the vmdk figures with the result from parted [total_no_of_sectors - no_sectors_in_sectors_before_ntfs_sectorstart], I did the copy and paste of the mbr file. But WAIT!! the 'dd ...." command from the tutorial used "/dev/hda", so I need to change it to "/dev/sda" to create the correct image.

It worked fine and it as a free run to the activation part....then I ran the process again because internet didn't work in guest operating sys, then my virtual mouse never moved anymore. Any ideas?

---

### Post by luistorresmx on 2007-10-12
I think you have to active your mouse on your VMX file. Where it mentions the mouse put "TRUE".

---

### Post by sebadigri on 2007-10-13
Help Please!
--------------------------------------------------------------
NOTE: I have 1 sata disk with 4 partitions (2 ntfs, 1 ext3 and 1 swap)

-ntfs (sda2) (size: more than 100gb) it's the primary boot  partition with all windows boot files....(with xp "boot" archive redirecting to partition number 4 (sda5)

-ntfs (sda5) (size: aprox 45gb) it's the partition where the Xp it's installed...

-swap...(size aprox: 2gb)

-ext 3 (size 15gb's Ubuntu linux 7.04)
----------------------------------------------------------------
I cant print from "sudo parted" "unit s" "print" because its "only read":


sebastian@sebastian-ubuntu:~$ sudo parted
Warning: Unable to open /dev/hda read-write (Read-only file system).  /dev/hda
has been opened read-only.
GNU Parted 1.7.1
Using /dev/hda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            
Error: Unable to open /dev/hda - unrecognised disk label

---------------------------------------------
So i used "Sudo parted /dev/sda" "unit s" "print" and i have this:

sebastian@sebastian-ubuntu:~$ sudo parted /dev/sda
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            

Disk /dev/sda: 390721967s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number       Start                      End                Size                Type            File system  Flags
 1                   16065s             83891429s     83875365s   extended                           lba  
 5                   16128s             83891429s     83875302s   logical          ntfs              
 2                   83894272s      357787647s  273893376s  primary       ntfs                boot 
 4                   357799680s    361687409s  3887730s      primary       linux-swap        
 3                   361687410s    390716864s  29029455s    primary       ext3       

(parted) unit cyl                                                         
(parted) print                                                            

Disk /dev/sda: 24321cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 24321,255,63.  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start     End       Size      Type      File system  Flags
 1      1cyl      5221cyl   5221cyl   extended               lba  
 5      1cyl      5221cyl   5220cyl   logical   ntfs              
 2      5222cyl   22271cyl  17049cyl  primary   ntfs         boot 
 4      22272cyl  22513cyl  242cyl    primary   linux-swap        
 3      22514cyl  24320cyl  1807cyl   primary   ext3              
--------------------------------------------------
And in "windows.vmdk" file i have this:


# Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 63 FLAT "windowsxp.mbr" 0

RW 390705839 FLAT "/dev/sda" 16128 (***changed hda for sda***)



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "ide"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "24321"
---------------------------------------------------
***FIXED***
When i start the "windows.vmx" file i got this: 

VMware Player cannot find the virtual disk "/home/sebastian/Desktop/untitled folder/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/home/sebastian/Desktop/untitled folder/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.
--------------------------------------------------
UPDATE:
I have "GRUB ERROR 17"!
---------------------------------

What i need to correct?

note2: I don't understand this line:
"dd if=/dev/hda of=windowsxp.mbr bs=512 count=63" 
I used also this line..haha
"dd if=/dev/sda of=windowsxp.mbr bs=512 count=63" (modifing hda with sda)

note3: Im newbie with linux i installed this week :p so i dont understand too much but im learning... 

thank's  you all i'll waiting for your unswers!!

Sebastián.

---

### Post by sebadigri on 2007-10-15
Finally i can fix it!..and all works ( i think ) fine...
-----------------------------------------------------------------------
1)I corrected the values in windows.vmdk like this:

# Disk DescriptorFile
version=1
CID=1e8d3306
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 16128 FLAT "windowsxp.mbr" 0
RW 390705839 FLAT "/dev/sda" 16128

# The Disk Data Base 
#DDB

ddb.toolsVersion = "6530"
ddb.adapterType = "ide"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "24321"
-----------------------------------------------------------------
2) I created another windowsxp.mbr with this command:

"dd if=/dev/sda of=windowsxp.mbr bs=512 count=16128" ( changed hda for sda and 63 for 16128 )
-----------------------------------------------------------------

---

### Post by the8thstar on 2007-10-18
I solved my problem too: I formatted the hard drive and installed Windows XP. It works very well now. Maybe I'll reinstall Ubuntu one day... :lolflag:

---

### Post by KillaB7 on 2007-10-18
Howdy folks, new member here ;)

I'm moving from XP to Gutsy for the Compiz experience and to immerse myself in Linux once and for all.  I know I won't be able to go without Windows completely so I'm planning on running XP on one of my workspaces.

I currently run RAID0 for the performance boost in application launching and boot times and just wondered if the following scenario would work:
```

   2 HD's in ICH7 RAID0 Array                          
 -----------------------------------------------------------------
|     WinXP       |                 Ubuntu Partitions             |
 -----------------------------------------------------------------

```
Pretty simple in theory, I'm just wondering if it will cause problems when I'm trying to access infomation from both partions on the same array at the same time?

Maybe I'm better off running XP on one HD and Ubuntu on the other but I'd rather give up more space to Ubuntu.

EDIT:  I'm also wondering if I should make my XP partition NTFS or FAT32.  I'm under the impression that 7.10 can read and write to NTFS partitions but not sure how VMWare handles this?

---

### Post by ericderace on 2007-10-21
Hi all,

I've been trying to get this to work as well.  My hard drive is SATA (/dev/sda).  I've followed the instructions and I get to the point where grub boots, then I choose Windows XP Pro and then it stays stuck at Starting up ...  The CPU is also at 100%.  

Any help?

---

### Post by ericderace on 2007-10-23
I have some more info on my issue,


Using Partition Magic 8, i shrunk the windows NTFS partition to make space for Ubuntu. I then installed Ubuntu on the freed space.
I can boot in both Ubuntu and Windows XP but I wanted to try the VMWare native thing, within Ubuntu. I could not get it to work, and here's what I found out:
--------------------
TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63, sector size=512

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
Partition Start End Size in sectors
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
1 * HPFS - NTFS 0 1 1 4864 239 63 78155217 [SYSTEM]
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
2 P HPFS - NTFS 4864 240 1 10156 59 63 85004640 [DATA]
3 P Linux 10157 0 1 12070 254 63 30748410
4 E extended 12071 0 1 12160 254 63 1445850
5 L Linux Swap 12071 1 1 12160 254 63 1445787
-------------------

Here's what testdisk tells me. I believe what happened is that Partition Magic screwed up the partition table, probably from using a different driver when it shrunk the partition.

Now... Both systems work now, I would like to fix that, without deleting the partitions (if possible). Partition #2 is my data partition, where all my documents is and it's already backed up.

Any help ?

---

### Post by leicester on 2007-10-24
hi! can someone help me?
i followed this guide but i keep getting the error below:

File not found: windows.vmdk

This file is required to power on this virtual machine.  If this file was moved, please provide its new location.

when i browse and choose my my vmdk file in /home/myusername/vmware i would still get the same error. I have the mbr, vmx and vmdk in this folder but it still would result in the same error message. 

im using vmware player 2.0.2 build-59824 (64bit), i installed it from the tar.gz file

im running gutsy64bit

thanks in advance for the help

---

### Post by boast on 2007-10-25
> **leicester said:**
> hi! can someone help me?
i followed this guide but i keep getting the error below:

File not found: windows.vmdk

This file is required to power on this virtual machine.  If this file was moved, please provide its new location.

when i browse and choose my my vmdk file in /home/myusername/vmware i would still get the same error. I have the mbr, vmx and vmdk in this folder but it still would result in the same error message. 

im using vmware player 2.0.2 build-59824 (64bit), i installed it from the tar.gz file

im running gutsy64bit

thanks in advance for the help


I have the same problem

edit; uhg

"As far as I know, this does NOT work with SATA drives. VMware cannot directly read physical (RAW) partitions from a SATA drive. And there is no timeline for such SATA RAW support."

---

### Post by ephman on 2007-10-25
> **leicester said:**
> hi! can someone help me?
i followed this guide but i keep getting the error below:

File not found: windows.vmdk

This file is required to power on this virtual machine.  If this file was moved, please provide its new location.

when i browse and choose my my vmdk file in /home/myusername/vmware i would still get the same error. I have the mbr, vmx and vmdk in this folder but it still would result in the same error message. 

im using vmware player 2.0.2 build-59824 (64bit), i installed it from the tar.gz file

im running gutsy64bit

thanks in advance for the help

had the same issue a while ago.  can't promise your issue is the same as mine was, but i'll give you my fix.  if you go take a look in the windows.vmdk file, there's a line that should look something like this.

> RW 240121664 FLAT "/dev/hda" 63

you might want to change that to /dev/hda to /dev/sda and give the .vmx file another shot.

thanks for your bandwidth,

ephman

---

### Post by ephman on 2007-10-25
hey,

ok i have a 2 questions i'll throw into one post.

1) no way to run vmware under xgl right?  i've searched everyplace to figure how.  any thoughts? i just get a blank screen after i select my vmware profile

2) i'm running my native xp partition as guest, and can't get on the 'net.  i installed vmtools and my network card shows it's a "VMware Accelerated AMD PCNet Adapter" under device manager.  as well i've bridge connected the ethernet.  and no network.  can't even ping out.  any ideas what i can do???

thanks for your bandwidth,

ephman

---

### Post by leicester on 2007-10-26
ephman:
but isnt that for sata drives only???

---

### Post by ephman on 2007-10-26
> **leicester said:**
> ephman:
but isnt that for sata drives only???

yes i have a sata drive in my dell inspiron 6000.  82801FBM (ICH6M) SATA Controller with a WDC WD800VE-75HD hard drive.  i'm not sure i understand your question.

thanks for your bandwidth,

ephman

---

### Post by thetimekeeper on 2007-11-17
I'm having a rather strange error...after putting everything in, it boots, but gives me a network boot screen:

[http://img526.imageshack.us/img526/7696/vmwareww9.png](http://img526.imageshack.us/img526/7696/vmwareww9.png)

I've tried googling, but it seems like I'm the only one with this issue?

---

### Post by maxxum on 2007-11-18
> **boast said:**
> I have the same problem

edit; uhg

"As far as I know, this does NOT work with SATA drives. VMware cannot directly read physical (RAW) partitions from a SATA drive. And there is no timeline for such SATA RAW support."
I had the same issue then I tried running vmplayer as root and it worked. (sudo vmplayer, then open the vmx file from the player window, not by clicking on it).
It works on sata drives. I replaced all entries that said 'ide' to 'scsi' and 'hda' to 'sda. Hope this helps.
My issue is however that I cannot get vista to boot. It starts to boot and then I get the blue screen with error but it reboots immediately so I cannot read the error number. I replaced the atapi.sys, intelide, pciide and pciidex.sys files where the original howto wanted me to. Vista also has those files but it didn't work so I put the xp versions of those files after backing up the vista ones. I have vista enterprise version, which should be an almost full featured version.
I guess I'll put xp pro and try it. 
I was able to boot the other linux installation on the hard drive under the vmplayer. I also accidentally booted the same ubuntu installation which I was running the vmplayer from (not a great idea I believe)  and it booted. However upon reboot I had a number of filesystem errors and X-server would not start. I had to manually do the fsck to fix the errors of lost sectors, dual ownership etc. I'm back up and now looking to put XP pro and forget about vista altogether.

---

### Post by bobbrrz on 2007-11-21
I've read through this forum, and I've tried to bring up my Windows XPPro partition about fifty times, to no avail.  I always get the same
error.  

I get the grub menu, I choose Windows XP Pro, the entry from
/boot/grub/menu.list appears on the screen, and then stays there.
There's no windows error message, and vmware.log doesn't really 
have a lot of information in it.  

I have an SATA drive, running VMplayer from Gutsy.

---

### Post by wtruong on 2007-11-23
I was wondeirng, can you do the other way around?  Running native linux installation on windows vmware?

---

### Post by briwood on 2007-11-24
> I get the grub menu, I choose Windows XP Pro, the entry from
/boot/grub/menu.list appears on the screen, and then stays there.

You need to do this: 
[http://ubuntuforums.org/showpost.php?p=2546498&postcount=40](http://ubuntuforums.org/showpost.php?p=2546498&postcount=40)

---

### Post by lvleph on 2007-12-04
> **leicester said:**
> hi! can someone help me?
i followed this guide but i keep getting the error below:

File not found: windows.vmdk

This file is required to power on this virtual machine.  If this file was moved, please provide its new location.

when i browse and choose my my vmdk file in /home/myusername/vmware i would still get the same error. I have the mbr, vmx and vmdk in this folder but it still would result in the same error message. 

im using vmware player 2.0.2 build-59824 (64bit), i installed it from the tar.gz file

im running gutsy64bit

thanks in advance for the help

If you don't have SATA and you already tried
```
sudo adduser <username> disk
```
and that didn't work, like it didn't for me, try 
```
sudo chmod 777 windows.*
```
in the folder where your vmdk is located.

---

### Post by MaximumFish on 2007-12-06
I'm getting a weird error before I can even start this process:

"VMware Player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

Surely i386 is the most common form of installation? This seems absolutely crazy. Any thoughts?

---

### Post by brawa on 2007-12-06
> **MaximumFish said:**
> I'm getting a weird error before I can even start this process:

"VMware Player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

Surely i386 is the most common form of installation? This seems absolutely crazy. Any thoughts?

I get the same answer...I assumed this meant no support (as weird as that is), but am interested to see if that's not the case.

---

### Post by Nevel on 2007-12-09
vmware nagging about your system seems to be an Gutsy Gibbon problem. For a fix, please check Komputes' comment over here:

[http://www.uluga.ubuntuforums.org/showthread.php?t=581414&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=581414&page=2)

Worked like a charm for me. :)

One thing I can't get working, though, is the skipping of the MBR. I did change the necessary configs (according to this manual: [http://advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)).
Still, whenever I run my WinXp VM, I still get the grub GUI.

Could it be that my MBR got screwed up along the way? Or doesn't each MBR consist of 63 cylinders? Or? 8-[

---

### Post by slimx3m on 2007-12-15
> **grantkelly said:**
> Try running
```
sudo /usr/bin/vmplayer windows.vmx
```

For some reason vmplayer is giving the error message that it can't find the .vmdk file, when really it just doesn't have the right permissions for something else.

thnx for this info.  now i will try to get rid of the 0x0000007B error

---

### Post by slimx3m on 2007-12-15
> **brawa said:**
> I get the same answer...I assumed this meant no support (as weird as that is), but am interested to see if that's not the case.

download the code *.tar.gz from vmware website and do this
```

tar xvzf VMware-player-VMware-player-2.0.2-59824.i386.tar.gz
cd vmware-player-distrib
./vmware-install.pl
```

and leave everything by default

hope it helps

---

### Post by slimx3m on 2007-12-15
*OLD: ok guys, i finally got rid of x0000007B error, but now when i boot another error comes up.  the problem is that the problem doesn't even give me time to catch this new error message.*

**EDIT: i haven't got rid of x0000007B error message.  and i merged the registry just like MS said in the tutorial, but still no outcome**

here it is my *.vmx values

```

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"

vuuid.location = "56 4d 56 4a 7b d7 4c 30-f5 80 d6 8b c4 59 aa eb" 
uuid.bios = "56 4d 56 4a 7b d7 4c 30-f5 80 d6 8b c4 59 aa eb" 

uuid.action = "create" 
checkpoint.vmState = ""

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxphome" 
numvcpus = "1" 
memsize = "256" 
paevm = "TRUE" 
sched.mem.pshare.enable = "TRUE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "TRUE" 
tools.remindinstall = "FALSE" 
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "TRUE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:59:aa:eb" 
ethernet0.generatedAddressOffset = "0" 

usb.present = "FALSE" 
usb.generic.autoconnect = "FALSE" 

sound.present = "TRUE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "TRUE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE" 

floppy0.present = "TRUE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "TRUE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"

extendedConfigFile = "windows.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"

uuid.location = "56 4d df 88 81 6f 33 5f-24 1d ac 85 08 98 c9 11"

```

i have all three things (windows.vmdk, windows.vmx, windowsxp.mbr) on the same folder.  and whenever i'm going to run the windows.vmx, i have to sudo it.

---

### Post by wwarsin on 2008-01-09
nevermind
--edit--
i found it is ALOT easier to do this in VirtualBox, take a look at its manual i believe its 9.9 that tells you how to do this... 
although i do have to say you might have to do that boot MBR thing, im using 2 drives 1 hda 1 sda i have windows installed on the sda  drive w/ ubuntu (the drive is partitioned, but ubuntu's grub is on hda, windows MBR is on the sda drive... maybe im wrong but i didnt have to do anything with the MBRs

---

### Post by David Mulligan on 2008-03-23
I am very interested in running my existing Windows XP installation (partition) from within VMWare Player on Gutsy with the option to boot into XP occasionally.  This is mainly for a game, a rc simulator and my Canon all in one scanner/printer.  Damn Canon for not supporting linux!

I was following the first post in this thread up to the point where I ran parted to find my hard disk info.  Unfortunately all of the images and vxm and vmdk files are missing because the original referenced article (or site?) has been pulled down.  Where can I find this information or an archived copy of the article?

Thank you,
David

---

### Post by codeslicer on 2008-04-28
The new version of VMWare Server allows you to configure hard drive access right from its gui, so this is no longer needed. Just use the Physical Disc option when creating a new virtual machine.

---

### Post by KingWilliam on 2008-05-08
I tried with vmware server and my native windows vista. but when booting (during the ugly little green scrolling bar) I get a bsod...

anyone?

---

### Post by hasufell on 2008-06-05
> **KingWilliam said:**
> I tried with vmware server and my native windows vista. but when booting (during the ugly little green scrolling bar) I get a bsod...

anyone?
same here with WinXP, bsod

does any1 have the files from the thread-starter?

---

### Post by KingWilliam on 2008-06-06
> **hasufell said:**
> same here with WinXP, bsod

does any1 have the files from the thread-starter?

Hi, I fixed the probelm with the bsod a few days ago. What i did was editing the config files of the vmx and vmd so it uses IDE instead of SCSI for the harddrive. Which lines to change where I found somewhere on the forums of OSX68. 

If I have some spare time I'll look for it and post it here.

---

### Post by hasufell on 2008-06-15
i'v changed the following lines in vmx

> ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide0:0.deviceType = "rawDisk"
ide0:0.redo = ""
ide0:0.mode = "independent-persistent"


and these in vmdk

> ddb.adapterType = "ide"

[http://www.informatik-forum.at/showthread.php?t=56924](http://www.informatik-forum.at/showthread.php?t=56924)
[http://forums.gentoo.org/viewtopic-p-4224409.html?sid=5edd7697ca4b641078c497b3cb8e15de](http://forums.gentoo.org/viewtopic-p-4224409.html?sid=5edd7697ca4b641078c497b3cb8e15de)

it works now

---

