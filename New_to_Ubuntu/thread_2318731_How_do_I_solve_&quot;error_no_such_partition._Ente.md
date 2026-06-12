---
title: "How do I solve &quot;error: no such partition. Entering rescue mode-grub rescue&gt;&quot;?"
date: 2016-03-28
forum: New to Ubuntu
---

### Post by duc_anh4 on 2016-03-28
Hi guys,
I hope.you could help me out I am really exhausted trying to fix this issue. I wanted to do a clean install of windows 10 and linux and just removed 
the linux partitions. Now when i boot up I get a black screen with the error message. i have tried the fixmbr command
In the command shell of the windows recovery shell. I ve also tried the ubuntu boot repair tool but nothing changed.
Here is my pastebin:
[http://paste.ubuntu.com/15547414/](http://paste.ubuntu.com/15547414/)

Sorry if there is any inconvenience I am just desperate and exhausted looking for help.

Regards, Duc

---

### Post by yancek on 2016-03-28
If you want to install windows, just boot the windows installation DVD or whatever you have.  Make sure you set the DVD drive or usb to first boot priority in the BIOS to boot the windows installation medium.  I'm not sure why you are trying to boot your hard drive if you want to do a clean install of both systems.

Your boot repair shows no Ubuntu on it which is expected because you deleted the partitions.  I imagine you were using the Ubuntu Grub bootloader to boot both systems.  Your problem is that you did things backwards.  If you want to remove Ubuntu and keep windows, you fix the mbr from windows first and then delete the Ubuntu partitions.  Since you did the reverse, you see the result which is the expected result.  Almost all the Grub boot files are on the partition you deleted so Grub isn't going to boot anything.  It's not there any more.

I don't think your windows recovery CD will be able to repair the MBR.  One usually needs the full install DVD from what I understand.  Do you have a windows installation DVD?  If so, just boot it and re-install windows.  Then if you want, you can re-install Ubuntu.

---

### Post by duc_anh4 on 2016-03-29
Hi yancek! Thanks for your reply. Unfortunately I dont have a windows recovery dvd. I always do the clean install with a usb stick with the iso file installed on it. What can I do now?
Actually I want to keep the bootloader and Ubuntu! I just did all that to move both OS to another drive.

---

### Post by buzzingrobot on 2016-03-29
If you correctly burned a Windows install image to that USB stick, then you should be able to tell the BIOS to boot into it.

If you're trying to set up a Windows+Ubuntu dual boot system (which it seems you've done before) the basic drill is to install Windows first, leaving sufficient room for the Ubuntu partition(s), then do the Ubuntu install. Linux bootloaders will accommodate Windows, while Windows will not accommodate any other OS.

---

### Post by duc_anh4 on 2016-03-29
Thanks for the help guys! I just went to a local IT Support they just wiped my drives. Now I am following your steps, start with installing windows again!
Best wishes, Duc

Edit: Now that I have installed windows I still get a blackscreen. It says MBR Error 1 Press any key to boot from floppy...
I always have to tell the bios manually from which drive I want to boot up, otherwise I get this blackscreen. I ve already tried fixmbr and fixboot nothing worked out :(

Can I just ignore it and install Ubuntu and it will eventually go away?
Please help, Duc

Edit edit: Problem solved. Just needed to change the bootorder TEMPORARELY. Damn that was exhausting &#55357;&#56832;

---

