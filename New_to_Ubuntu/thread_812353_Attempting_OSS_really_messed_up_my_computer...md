---
title: "Attempting OSS really messed up my computer.."
date: 2008-05-29
forum: New to Ubuntu
---

### Post by bm13084 on 2008-05-29
Hardy Heron...

I attempted the OSS 4.0 install instructions on this forum to get my mic working, but the directions stopped going right after step six... gave me some errors or something.  It wouldnt let me blacklist alsa or whatever because the file the directions said to blacklist didnt exist.   Anyhow, i tried to go back and install the default sound... and nothing but ubuntu recognized drivers for it.  it plays the boot up and shut down music, but amarok cant detect sound.. etc...

now when i try to boot up, i have more ubuntu install options in grub.  kernel 2.6.24-17 and 2.6.24-16.

neither work.  -17 shows where my top toolbar should be, but never loads it.  the programs (aside from terminal) dont load. -16 doesnt show my toolbar area at all and same problem with programs.

am i going to have to reformat? i hope not... this things a pain to get going...

---

### Post by Helgiks on 2008-05-29
Please post a link to that tutorial.

---

### Post by bm13084 on 2008-05-29
[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

---

### Post by bm13084 on 2008-05-30
anyone have a clue?

---

### Post by cheesypoof on 2008-05-30
I did that tutorial and it worked fine for my Creative X-Fi XtremeGamer. However, I ignored something in that tutorial. I did not remove alsa-base. If you do, it removes gnome-desktop also. So if you did remove these, you may want to try reinstalling them. "sudo apt-get install gnome-desktop alsa-base" I am on Windows right now so when i type names it is from my memory only. If you want to remove some of those startup entries, you can either download QGrubEditor or "sudo gedit /boot/grub/menu.lst".

---

### Post by bm13084 on 2008-05-30
im not sure that's it, since the higher numbered kernel doesnt let me open terminal, and the lower kernel looks normal, but doesnt open anything anymore....

---

### Post by cheesypoof on 2008-05-30
Try changing your session to failsafe on the login screen. Oh and by the way, in my previous post I think I meant to say ubuntu-desktop, not gnome-desktop.

---

### Post by bm13084 on 2008-05-30
failsafe boots, then crashes to a black screen with a white underscore.

booting into gnome causes the normal situation described before.

i tried to reformat, but since its on a partition, the install tried to shrink that partition and leave the broken ubuntu on also....

---

### Post by bm13084 on 2008-05-30
failsafe terminal allowed me to boot though... installed the desktop, but when i go back in things arent loading again... terminal freezes and programs dont open. 

but at least the top toolbar is back :(

---

### Post by bm13084 on 2008-05-31
still no clues?

how can i delete the ubuntu i have on there now then? i only want to delete one partition as the other two are windows and storage.

ill want to put ubuntu back on that partition also

---

### Post by cheesypoof on 2008-05-31
You should boot into Windows and use the Disk Management tool to delete the ubuntu volumes. Make sure once you are done, the space where ubuntu was, is now free space. With Vista I know from experience you can restore the windows bootloader by booting to the install cd. From there I believe you go to repair and then the command line.

> bootrec /fixmbr
bootrec /fixboot
bootrec /rebuildbcd
Remember, this is for vista. I do not know what the commands are for XP.

---

### Post by bm13084 on 2008-06-01
i have vista, but no boot cds... it came preloaded and it's the recovery partition i think.

Edit: I just deleted the partitions in disk manager and it worked fine.  It's listed as free space and I'm installing ubuntu again as we speak.

---

