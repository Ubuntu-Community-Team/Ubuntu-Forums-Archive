---
title: "Dual boot with Ubuntu?"
date: 2016-05-17
forum: New to Ubuntu
---

### Post by mike431 on 2016-05-17
Hey guys, someone approached me today with a problem, he just got a  new hp desktop pc with win10 but had a guy install a dual boot system  with Ubuntu. Now whenever he tried to log in he is having problems and wants to know what he can do to correct this situation.  I have never installed any linux system, I only use knoppix, Puppy  Linux and Parted magic to do data recovery or formatting e.t.c. 

This is the info he sent me:
  
 Once I turn on the computer at #1 this comes up:
  
 [http://imgur.com/9EW7Uc8](http://imgur.com/9EW7Uc8)
  
 I click on ubuntu and this is what comes up:
  
 [http://imgur.com/BVHsa7f](http://imgur.com/BVHsa7f)
  
 This is the message I get each time I press ENTER
  
 [http://imgur.com/HfrbaSz](http://imgur.com/HfrbaSz)
  
 He wants to drop off the pc here for me on Wednesday but since he  uses that pc for his work I will only have one day at the most to correct  this problem, any ideas please?

---

### Post by grahammechanical on 2016-05-17
May I suggest that the first thing you do is data recovery. The client may need it.

The second thing to try is at that first screen select Advanced options for Ubuntu. That will open a sub-menu that lists Linux kernels. There should be a kernel that has recovery mode as part of it boot parameter. Select that kernel and press enter. At the recovery menu select fsck - check all file systems. That is in line with the message, "the root file system /dev/sda6 requires a manual fsck." To find out if that works select Resume when back at the recovery menu.

I think that Wednesday is the day you are going to learn how to re-install a Linux distribution. The Ubuntu OS has a purple background to the Grub boot menu. That OS has a black background to the boot menu. That OS may be a flavour of Ubuntu or even a derivative of Ubuntu. Was the client given a DVD with the distribution on it?

You may find that there has been an update to Windows 10 and that has re-written the partition table and ignored the Linux partitions. You may also wish to add Boot Repair to your tool kit.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by yancek on 2016-05-17
You don't indicate if this 'dual-boot' system ever worked, did it?  Was your friend able to previously boot into windows and into Ubuntu?  Is the windows 10 as well as Ubuntu using UEFI?

---

### Post by mike431 on 2016-05-17
I just got off the phone with him, this is the rest of the situation. The tech had installed ubuntu and all was fine with going to either windows or unbuntu but Ronald had forgotten the password and the tech came back trying to crack or bypass the password and after that the problems started happening with ubuntu. Ronald then remembered the password and can now get into windows but the problem as stated with logging into ubuntu still exists, that's the whole shebang as I am being told.

---

### Post by mastablasta on 2016-05-17
is the Ubuntu part encrypted?

obviosuly they messed up the system the easiet way would be to reinstall.

for future reference there is no need to crack or bypass the passwrod. one can simply reset user password if they have physical access. : [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

encrpyted drive or home is another issue. 

you could try and run the live session, then fsck the disk (it's like running chkdsk in windows). i am sure the distros you are used to have it. 

fastest way  thoug - backup the data using live session and reinstall (you can let it overwrite the partition or do a clean one). it only takes about 15-20 mins to install linux.

---

### Post by grahammechanical on 2016-05-17
It sounds like full disk encryption. Forgetting the Ubuntu login password would not deny access to Windows. Likewise, having an encrypted Ubuntu home directory would only effect Ubuntu if the password was forgotten. For a forgotten password to effect access to Windows as well as Ubuntu there must be full disk encryption. As far as I can guess.

And he expected you to fix a problem without you knowing the password? Who knows what the tech person did to fix a forgotten password problem. Could this be a password that is set in the UEFI utility that has to be used before a boot loader will even run?

Regards.

---

### Post by mike431 on 2016-05-17
Ronald says since it's a brand new pc he doesn't have to do any data recover, if needed the can do a factory reset for windows 10. The tech did not give him a disk so I would first need to get a bootable ubuntu software, I found the instructions here which I will attempt to do now: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Yes as first option I would prefer to reinstall as opposed to trying to fsck to make sure he doesn't have issues later on. Does ubuntu have a reset [reinstall] function?

---

### Post by Geoffrey_Arndt on 2016-05-17
The boot-repair report would also be helpful to provide you the most reliable info to restore the proper dual-boot system.

---

### Post by grahammechanical on 2016-05-17
> Does ubuntu have a reset [reinstall] function?

No. But that boot menu does have a setup option under Advanced options. I do not know what that does as I do not see that on my machine. It could be something to do with UEFI. Which I do not have. I do not know.

To re-install Ubuntu over an existing install we run the live session. We select Install Ubuntu. And then we select Something Else. It is the same for all flavours of Ubuntu. This is from the Ubuntu Mate documentation. It shows the screens that you will navigate through.

[http://ubuntu-mate.community/t/install-ubuntu-mate-using-something-else-method/651](http://ubuntu-mate.community/t/install-ubuntu-mate-using-something-else-method/651)

See the third screen. It is where we select Something Else. The fourth screen shows the partition layout. It is where we select the partition to install Ubuntu to. It should be sda6. Based on that message to fsck /dev/sda6.

Click Change and in the dialog that appears fill it in as shown in the fifth screen. We do not know if the machine has a separate /home partition. So, the next section may not apply. A default install would not create a separate /home partition. The home folder would be part of the Ubuntu partition ( / ). So, look carefully at the partitioning layout.

Regards.

---

### Post by mike431 on 2016-05-17
In order to be prepared I am trying to simlulate ronald's repair on one of my own pc's so I created the flash drive with ubuntu and attempting to install it on a vista pc. First option I see is to "install alongside vista" so I am guessing that would be for a 'new' install?
So I choose 'something else' as you've directed and now I am at the "Installation Type" screen showing the partitions as can be seen here: [http://imgur.com/5WuikOG](http://imgur.com/5WuikOG)
Now please guide me from here, would I need to first create a new partition table to install ubuntu on so basically creating a separate partition for it?

---

### Post by yancek on 2016-05-17
You don't need to create a new partition table, just a new partition.  You have a little over 10GB on which to install which is pretty small but since this is just a test, it should be OK.
Click on free space in the main window then click the + in the lower left to add a partition, select to format it in the Edit partiiton windows and set the Mount point to /, the symbol for root.

---

### Post by mike431 on 2016-05-17
Thanks for the help but I need to go in slomo as first time and I don't only want to follow directions, I want to understand the basics as much as I can so please bear with me? if you can look at this screenshot please: [http://imgur.com/undRTAp](http://imgur.com/undRTAp)
I selected the / as the mount point but the "Use as" default option, is that the correct option?

---

### Post by mike431 on 2016-05-17
But first, wait a minute, 2 things, doesn't that 'free space' belong to the flash drive with unbuntu on it showing as sda1 Fat 16? Also back to the "create partition" window, the default option for 'Type for the new partition' is the Logical, shouldn't this be 'Primary' since a primary drive is needed to boot an OS?

---

### Post by mike431 on 2016-05-17
Sorry guys, please ignore the above posts. I installed ubuntu "alongside vista" on an older pc here as I figured this would be the easier way and it was. Now I need to pretend something is wrong with the ubuntu and attempt to reinstall it as I will need to do with ronald's machine. I will search the net for instructions on reinstalling, thanks.

---

### Post by mike431 on 2016-05-17
I insert the flash drive and power on, this time at the ubuntu screen  I choose the "Advanced" options, I am seeing 3 options [generic,  upstart and recovery mode]. Since I won;t be recovering ubuntu on his  pc, I am not understanding how to reinstall ubuntu all over again?

---

### Post by mastablasta on 2016-05-18
just boot into deskotp. click install icon, click "something else" option, install on same partition (the one with ext file system) and chose to overwrite it or format it (formatting will erase the data on it). set /swap (you cna use the same as it is now) then the rest should be easy.

---

### Post by mike431 on 2016-05-18
Oh, I had forgotten to boot from the flash drive again. Ok I am see the option no to reinstall, thanks.

---

### Post by mike431 on 2016-05-18
So I am guessing when you boot from the flash drive, Ubuntu recognizes that there is already an installation and that's why the default option is to 'Erase Ubuntu and reinstall", is this correct please?
Also, what's the advantage to using ubunto instead of windows?

---

### Post by pfeiffep on 2016-05-18
> So I am guessing when you boot from the flash drive, Ubuntu recognizes  that there is already an installation and that's why the default option  is to 'Erase Ubuntu and reinstall", is this correct please?
That's probably OK but I think mastablasta's response is the safer option
> just boot into deskotp. click install icon, click "something else"  option, install on same partition (the one with ext file system) and  chose to overwrite it or format it (formatting will erase the data on  it). set /swap (you cna use the same as it is now) then the rest should  be easy.
 > ]
Also, what's the advantage to using ubunto instead of windows?
[LIST]
[*]more secure
[*]less resources required
[*]it's free AND open source
[*]more customizable
[*]easier to maintain
[/LIST]
to name a few

---

### Post by mike431 on 2016-05-18
Thanks, yes I will try mastablasta's instructions when I get the pc. Seems only issue on his win10 machine would be to disable EUFI and choose legacy boot to boot off the USB?

---

### Post by pfeiffep on 2016-05-18
I have no experience with either Win10 or EUFI

---

### Post by Geoffrey_Arndt on 2016-05-18
Generally, most dual boots with Linux these days do not disable UEFI . . . . question - - why would you consider that even?

---

### Post by mike431 on 2016-05-18
> **Geoffrey_Arndt said:**
> Generally, most dual boots with Linux these days do not disable UEFI . . . . question - - why would you consider that even?

When working on win8 machines in particular, I have always had to boot from legacy to reinstalll the OS so I thought it would be the same with win10 when booting an OS from a flash drive. This article here should cover the win10 situation: 
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

---

### Post by Geoffrey_Arndt on 2016-05-18
Does the article talk about "reinstalling" at all or pros/cons of UEFI vs MBR?   I'd be very cautious of changing firmware mode on any Win10 machine.

---

### Post by oldfred on 2016-05-18
Generally you want all systems booting in same boot mode.
And since Windows only boots in UEFI mode from gpt or only in BIOS boot mode from MBR partitioned drives, you do not change Windows without a total reinstall and reformat of drive.
But Ubuntu can boot with either UEFI or BIOS from gpt partitioned drives. 
But UEFI and BIOS are not compatible. Once you start booting in one mode, you cannot switch. Or you cannot use grub to dual boot. You can use UEFI and start from that in one mode or the other.

HP is one vendor that is not dual boot compatible without special work arounds. HP violated UEFI spec that specifically says not to use description as part of UEFI boot and of course on valid description is "Windows Boot Loader". 

Depending on version and your configuration there are several work arounds. Pretty much same for all HPs. Most copy shimx64.efi to /EFI/Boot/bootx64.efi. That is a hard drive or fallback boot. Often bootx64.efi is just a copy of Windows own efi boot file. Then you boot hard drive entry in UEFI which boots Ubuntu/grub.

If you want more details see also link in my signature.

       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
      
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
    [URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

### Post by mike431 on 2016-05-18
Well I thought had the proper instructions but guess not so I am more confused now about the win10 ubuntu reinstall process.

---

### Post by oldfred on 2016-05-18
Both Windows & Ubuntu install in the same mode you boot install media.

So if you boot Windows in BIOS mode it will install in BIOS mode. And if drive is gpt it, totally converts to MBR. It may also complain drive is gpt and want that removed first. Have not installed Windows since XP so do not know from experience.

Ubuntu will also install in same boot mode as you boot install media, but can install either way to gpt. Best to only install in BIOS mode on MBR partitioned drive, but that may also work. Just not UEFI standard.

In UEFI boot menu should be two boot entries for a DVD or flash drive installer. One is normally clearly UEFI:name and the other (BIOS) is just name where name is label or brand of flash drive. You may be able to boot in a different boot mode than default in UEFI and then it may error out as it is in wrong boot mode and cannot find anything to boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by Geoffrey_Arndt on 2016-05-19
Mike431 . . nothing wrong with the instructions in your link, but from your post, . . but did you see if the writer (Gary Newell) enabled legacy boot mode before the install . . . if so, I didn't see it.  As OldFred indicated, the trickiest part of install may be to do the boot config workarounds in his links.   But - they may not be needed if HP has cleaned up their UEFI on very recent models (try it first as Gary writes, then do the workarounds as OldFred writes IF needed).  Be sure to have the boot-repair DVD or usb-stick at the ready . . . in case required.  

Read these:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

 [URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]Revised Guide



[/URL]

---

### Post by mike431 on 2016-05-19
If I would have had the pc here without any rush to get this done then this wouldn't have been an issue but because I will be pressed to do this quickly this is what's throwing me trying to be prepared. Alright, if I got it now, I will power on the pc with the USB drive and  select it as first boot then follow the instructions without trying to  disable UEFI and will take it from there. Will let you guys know how it goes, thanks for the help!

---

