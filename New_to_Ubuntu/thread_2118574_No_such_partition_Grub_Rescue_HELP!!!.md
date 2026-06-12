---
title: "No such partition Grub Rescue HELP!!!"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by FlyKoreanBoi on 2013-02-21
So recently I got a "new" computerfrom my brother. He got a new one so he gave me his old one. He said it was broken and he just said search the internet for a solution. Whenever I boot up the computer it gives me something like no such partition grub rescue. I searched it up and it said I had to make a system repair disk? What do I do? I just want Windows 7. He said Windows 7 was installed so I'm guessing he deleted Linux from what the internet said and I called him he said yes. He said something about deleting a partition? I HAVE NO IDEA WHAT IM DOING!! I just want windows 7 and only windows 7. Thank you. 

p.s. Please explain to me like I'm a noob at computers because I am.

---

### Post by oldfred on 2013-02-21
You can download this into an Ubuntu liveCD/DVD/Flash or download as a full repair ISO to install to a flash drive.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair: Then we can see what is where.
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
    
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

If Windows is otherwise working you may be able to fix it from your Windows 7 repair flash drive.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by JiuJitsu500 on 2013-02-21
OldFred is the master. Like boss.

Live CD/USB and re-install GRUB man... give linux a shot!

OR

Make a bootable USB for windows 7 or DVD and boot from that. Once you do, it'll take care of the install itself once you tell it to. Get bootable Windows 7 media first, then you can continue.

Legally, by the way.

---

### Post by Mark Phelps on 2013-02-22
> **FlyKoreanBoi said:**
> I just want windows 7 and only windows 7. Thank you.

If you're willing to spend a little money, you can download a Win7 repair disk image from the link below and burn it to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then, boot from that and run Startup Repair three times -- that's right, three times.  It sometimes takes all three passes to make all the repairs.

I would also suggest that for future Win7 questions, you visit the Win7 forums (sevenforums.com).  They have lots of forum sections and tutorials to help you make the maximum use of Win7.

---

### Post by grahammechanical on 2013-02-22
> **Mark Phelps said:**
> If you're willing to spend a little money, you can download a Win7 repair disk image from the link below and burn it to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then, boot from that and run Startup Repair three times -- that's right, three times.  It sometimes takes all three passes to make all the repairs.

I would also suggest that for future Win7 questions, you visit the Win7 forums (sevenforums.com).  They have lots of forum sections and tutorials to help you make the maximum use of Win7.


Or demand that your brother fix the machine that he broke!

---

