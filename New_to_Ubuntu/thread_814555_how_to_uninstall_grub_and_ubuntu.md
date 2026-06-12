---
title: "how to uninstall grub and ubuntu?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by b2379 on 2008-05-31
I need to uninstall ubuntu and the grub loader.
How do I do this the correct way?

If I uninstall it the wrong way then grub will not find ubuntu at startup and probably won't even let me boot to any OS.

---

### Post by kansasnoob on 2008-05-31
Glad you asked. Look through this list of tutorials. If you're still unsure post back being specific about what other operating systems you have installed and we'll try to help.

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You are right about losing GRUB and becoming unbootable unless GRUB or another boot loader is installed/modified.

---

### Post by b2379 on 2008-05-31
> **kansasnoob said:**
> Glad you asked. Look through this list of tutorials. If you're still unsure post back being specific about what other operating systems you have installed and we'll try to help.

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You are right about losing GRUB and becoming unbootable unless GRUB or another boot loader is installed/modified.
Thanks for that list of methods, but which do you think would be the quickest and easiest for me since I will never use grub again on this hard drive?

After deleting Ubuntu I will only have Windows XP on this hard drive, so will I still need a boot loader? If not, then I don't really want one, so how do I delete grub completely?

---

### Post by IHATEDLINK on 2008-05-31
> **b2379 said:**
> I need to uninstall ubuntu and the grub loader.
How do I do this the correct way?

If I uninstall it the wrong way then grub will not find ubuntu at startup and probably won't even let me boot to any OS.

Before thinking of uninstalling you may want to consider keeping Ubuntu as a emergency OS, when Windows fails, Ubuntu will be there. It's also a very safe partition to put your data onto.

Well, if there's nothing I can do for you to stay...

Are you dual-booting with Windows?
If so, you may want to restore MBR (Windows' GRUB ;)).
To do this you will need your XP or Vista installation disk.
If you don't have one don´t panic! Try to borrow a friend's or even download a copy from a torrent client.

If your CD/DVD and windows installations is a vista one:
1.	Put the Windows Vista installation disc in the disc drive, and then start the computer.
2.	Press a key when you are prompted.
3.	Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4.	Click Repair your computer.
5.	Click the operating system that you want to repair, and then click Next.
6.	In the System Recovery Options dialog box, click Command Prompt.
7.	Type Bootrec.exe, and then press ENTER.
8.      Type Bootrec.exe /FixMbr

The /FixMbr option writes a Windows Vista-compatible MBR to the system partition.

If your disk and windows installation is an XP one:
1. Boot from the CD
2. Wait until the setup loads and press ´R´ to enter recovery console.
3. Select the "Windows Installation" you want to repair. (1 by default)
4. Enter your administrator password.
5. Type fixmbr.

Hope I helped!
If this post was useful to you remember to thank me by clicking the little star button at the bottom right of the post. ;)

---

### Post by IHATEDLINK on 2008-05-31
> **b2379 said:**
> Thanks for that list of methods, but which do you think would be the quickest and easiest for me since I will never use grub again on this hard drive?

After deleting Ubuntu I will only have Windows XP on this hard drive, so will I still need a boot loader? If not, then I don't really want one, so how do I delete grub completely?

Yes, you will ALWAYS need a bootloader. Windows bootloader is MBR.

---

### Post by kansasnoob on 2008-05-31
Just put in your Windows XP install CD, and boot into the recovery console and use the so-called 'FIXMBR' command.

After that you can boot the Ubuntu Live CD and use Gparted (partition editor) to delete the Ubuntu partition(s) and give that space back to XP.

---

### Post by b2379 on 2008-05-31
Yes, I am currently dual-booting windows xp with ubuntu. They are on seperate hard drives.

I want to uninstall Ubuntu on this hard drive because I am going to take it out of my computer and put it in an external enclosure to transfer my files between computers.
I will be installing Ubuntu on my newer and larger hard drive. :)

**Am I supposed to delete grub and then write mbr in the empty space? Or am I supposed to just overwrite grub with mbr?**

I have my Windows XP Installation CD but it would take some time for me to look around to find it.

**Does this program do exactly what the XP Installation CD repair feature would do for me:** [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by IHATEDLINK on 2008-05-31
> **b2379 said:**
> **Am I supposed to delete grub and then write mbr in the empty space? Or am I supposed to just overwrite grub with mbr?**

The "fixmbr" command just writes a windows-compatible MBR to system partition. There may be still traces of GRUB around when you finish uninstalling.

> **b2379 said:**
> Does this program do exactly what the XP Installation CD repair feature would do for me: [http://www.users.bigpond.net.au/herm...htm#MbrFix.exe](http://www.users.bigpond.net.au/herm...htm#MbrFix.exe)

I guess it does, I haven't tested it my self. But it does seems like the simplest way to do this. So... use it under your own risk!
Hope I helped somehow... :)
Remember to post your results when you finish!

---

### Post by greglcl on 2008-06-01
Hello I just finish installing Ubuntu 8.10 Fr - Here is my conf :
1 HDD 120 Window XP -
DVD Boot ubuntu Live 8.10
1 USB Maxtor 40 Go Drive

I made my ubuntu install to the usb Maxtor Drive then I had un Grub loader to my primary boot partition -

I don't want to have multiboot on this first partition.

How can I uninstall the mbr ? Do I have to follow the FIXMBR utilitys as show in this forum  ?

thank's for the help.

---

### Post by sweeneytodd on 2008-06-01
you could try " fdisk mbr"

---

### Post by IHATEDLINK on 2008-06-01
> **greglcl said:**
> Hello I just finish installing Ubuntu 8.10 Fr - Here is my conf :
1 HDD 120 Window XP -
DVD Boot ubuntu Live 8.10
1 USB Maxtor 40 Go Drive

I made my ubuntu install to the usb Maxtor Drive then I had un Grub loader to my primary boot partition -

I don't want to have multiboot on this first partition.

How can I uninstall the mbr ? Do I have to follow the FIXMBR utilitys as show in this forum  ?

thank's for the help.

OK, let me see if I understand, It's not that easy when your not a native English speaker! Are you French? Cause in any other language Go would be GB. ;)

You installed Ubuntu onto a external USB drive, but GRUB is on your main windows drive?
If GRUB is in C: you can use all of the options mentioned above.
If it isn't and I misunderstood you, just use [MbrFix.exe]("http://www.users.bigpond.net.au/herm...htm#MbrFix.exe") and place it on your external drives´s letter on windows. If windows doesn't see your Ubuntu HD try installing the [fs-driver]("http://www.fs-driver.org/") to make windows see ext2/ext3 formated drives.

---

### Post by georgegerm on 2008-07-27
choices are choices but having tried ubuntu on my new pc with a partition for xp (games and some other progs) i will never erase what takes few space workds cool and cost not a dime..
thanks to all who make it possible for idiots like me
ubu 4 ever
but i respect ur choice

---

### Post by Operator8 on 2008-12-19
Just wanted to give a thanks to Ihatedlink, your posts are still helping!!!

---

