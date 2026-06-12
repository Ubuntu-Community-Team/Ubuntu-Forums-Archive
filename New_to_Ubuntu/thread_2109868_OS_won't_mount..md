---
title: "OS won't mount."
date: 2013-01-28
forum: New to Ubuntu
---

### Post by trexismeiamhim on 2013-01-28
This problem has lef me computerless. Let me preface this by saying it's completely my fault that this happened. Anyway, about a week ago, I went to Disk Settings or some such app and unchecked the box that uses that particular partition as the default boot. Now, it tells me that the OS won't mount at boot and I don't know how to fix this manually. Please help. I have online college courses that I don't want to take on my phone lol. Thanks.

---

### Post by frank604 on 2013-01-28
Ok so give us an idea of what is happening. When you power on your computer, does it show the grub menu? Or does it go straight to booting ubuntu?  In the grub menu, does it show ubuntu?  If you select it, what is the error message you see?

Best to either write the error message or take a pic and show us. Can you get to terminal?

---

### Post by blackbird34 on 2013-01-28
If it's too much fiddling to edit the right config file to get the OS to boot again properly (I believe this would be the kind of thing that shows up in /etc/fstab, but DON'T edit that file if you don't know what you're doing) I think it would be quicker to just boot up a live CD or live USB session, copy your home folder onto an external drive as backup and reinstall...
Do you know how to boot a live session?

---

### Post by trexismeiamhim on 2013-01-28
I get a full screen of purple. It says "GNU GRUB version 2.00-7ubuntu11 at the very top. It gives me four options: Ubuntu, Advanced options for Ubuntu, Mem test (186+) and mem test (186+, serial console 115200) i tried attaching a picture but I'm on my iphone so I'm unsure if it worked :( thanks for the speedy response!

---

### Post by trexismeiamhim on 2013-01-28
Dear blackbird,
No, I unfortunately do not know how to boot a live session. I do have the install cd for ubuntu in the cd drive, if that helps. I also did do the dual boot or dual install option so I still have windows on there somewhere. My original plan was to get back on windows, actually.  It mentions /etc/fstab/ ALL THE TIME when I try to manually enter something.

---

### Post by mansonfan78 on 2013-01-28
With the install cd in the drive, restart your computer and let it boot the cd.  When given the option select "try Ubuntu" and it will load a live session.  From there open nautilus and find the /etc/fstab file on your hard drive and open it with gedit.  Copy and paste the contents of it here so we can see what you've got (the live session will have firefox installed). Close the file without saving so you don't accidentally change anything.

---

### Post by trexismeiamhim on 2013-01-29
It won't boot from the cd drive. It just shoots right up to the purple screen. I'm pretty helpless when it comes to computers.

---

### Post by blackbird34 on 2013-01-29
Could you tell us what computer model you have? Then we can tell you how to boot from a CD - sometimes you need to press one of the function keys or the Esc key to get a more specialized menu.

For example I have a Compaq Presario, I press the Esc key when it boots, and get a menu that includes a "Boot device options" menu. I press F9 to get it, then I can choose to boot from a USB stick or a CD with Ubuntu on.

---

### Post by trexismeiamhim on 2013-01-30
I have an asus laptop. Hitting f9 during boot doesn't do anything D:

---

### Post by mansonfan78 on 2013-01-30
With an Asus (which is what I have) you hit the delete key at startup to get into bios settings.  You may have to press it repeatedly.

---

### Post by trexismeiamhim on 2013-02-03
NOW WE'RE GETTING SOMEWHERE!! What can I do now tha I am in the bios?

---

### Post by mansonfan78 on 2013-02-03
There should be a submenu (probably in a tab) for "boot".  From there you can change the boot order so that the cd drive boots before the hard drive.   I leave mine set to that all the time, if there's no cd in the drive it just skips to the next thing on the list.

---

### Post by trexismeiamhim on 2013-02-03
Is it possible to restore my computer directly from the bios?

---

### Post by mansonfan78 on 2013-02-03
No, the bios doesn't have write access to the entire hard drive.

---

### Post by trexismeiamhim on 2013-02-03
Is there any way I can ser windows as the default os to mount?

---

### Post by mansonfan78 on 2013-02-03
Not from bios.  That could only be done by editing grub (and you have to get Ubuntu working first to do that), or using the fixboot command from a Windows install cd's recovery mode - which would wipe the grub menu preventing access to Ubuntu at all (Ubuntu would still be on the drive, you just couldn't boot it).

---

### Post by trexismeiamhim on 2013-02-03
So, booting from cd drive and reunstalling ubuntu is a good idea?

---

### Post by mansonfan78 on 2013-02-03
It would be the easiest method.  Are there any important files in your Ubuntu installation?  When reinstalling there's always the risk of losing data.  If there's nothing important, go for it.

---

### Post by trexismeiamhim on 2013-02-03
I reinstalled. Now my mouse won't work. How can I set windows as my default os now that I'm back on ubuntu?

---

### Post by mansonfan78 on 2013-02-05
Have you tried plugging the mouse into a different port?  Or trying a different mouse?  If you don't have a way to move around the desktop it's going to be pretty hard to edit the grub configuration.  Check this thread on how to edit grub:  [http://ubuntuforums.org/showthread.php?t=2091152](http://ubuntuforums.org/showthread.php?t=2091152)

---

### Post by trexismeiamhim on 2013-02-06
I have a laptop with a track pad. I would consider my original topic resolved. I thank you all for your time. It really has helped me. I think I will open new threads to help me with my new problems. You all are the best! Thanks!

---

### Post by mansonfan78 on 2013-02-06
You're welcome.  Make sure you mark this thread as solved (should be in the "thread tools" dropdown}.

---

