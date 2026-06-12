---
title: "Easy Ubuntu &amp; Windows XP dual-boot install"
date: 2005-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Mechsus on 2005-08-13
[SIZE=6]How To Install Ubuntu 5.04 next to Windows XP.[/SIZE]
[SIZE=3]Mechsus - [COLOR=DarkRed]Thick as a Brick[/COLOR] tutorial®2005[/SIZE]
 

This walk through shows you how to easily install Ubuntu 5.04 next 
to Windows XP, so you have the option of a dual-boot system. Obviously, 
the assumption is you already have Windows XP installed onto the first 
partition of your HD.

This proceedure isn't difficult, but for the unwary it's easy 
to take a wrong turn, which will result in the disabling of 
your Windows XP boot option. Correcting that is a headache.

OK, on with the games:

1. _Boot_ from Ubuntu CD-ROM.
2. Press, [COLOR=Blue]Enter[/COLOR] at splash screen.
3. At **Configure the network** and **No network interfaces detected**, select [COLOR=Blue]Continue[/COLOR].
4. Enter your Hostname.
5. At **Partition disks** choose **Manually edit partition table**.
6. You should see something like this:
   
   #1. . .Primary. . . .6.3 GB **&#8224;**. . . .ntfs
. . . . .Pri/Log. . . .33.7 GB. . . . .FREE SPACE

 _Note_: The **&#8224;** represents the lightning bolt.


7. Scroll down to **Pri/Log** then press [COLOR=Blue]Enter[/COLOR].
8. Select **Automatically partition the free space** then press [COLOR=Blue]Enter[/COLOR].
9. You should see something like this:

    #1. . .Primary. . . . .6.3 GB. . . . . ntfs
    #2. . .Primary. . . . 32.3 GB **&#8224;**. . **&#920;**ext3
    #5. . .Logical. . . . . 1.4 GB. . . .**&#920;**Swap

  _Note_: The **&#920;** represents the Puppy. Notice the **&#8224;** has
        gone from #1 Primary.


10.Select **Finish partitioning and write changes to disk** then press [COLOR=Blue]Enter[/COLOR]. 
11.At **Write changes to disk?** select [COLOR=Blue]Yes[/COLOR].
12.At **Time Zone Configuration** select [COLOR=Blue]No[/COLOR] (unless you want GMT).
13.At **Time Zone Configuration II** select [COLOR=Blue]YES[/COLOR] (should be correct location).
14.Enter a name: "Ghengis Smith"
15.Enter a Username: "Smith"
16.Enter a password: "pillage" - now reenter it.
17.At **Install GRUB boot loader** choose [COLOR=Blue]Yes[/COLOR] (to install GRUB to MBR).
18.CD-ROM will eject. Remove.
19.Install will continue. About 10 -15 minutes to finish.
20.The End.

*As for the Road Warrior - that was the last we ever saw of him. He lives now, only in our memories...*

---

### Post by andlinux21 on 2005-08-13
cool i will try this when i get back from vacation I have a extra hard drive that i can install and just dual boot that way with XP \\:D/

---

