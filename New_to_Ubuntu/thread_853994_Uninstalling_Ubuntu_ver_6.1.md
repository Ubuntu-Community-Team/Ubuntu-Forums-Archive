---
title: "Uninstalling Ubuntu ver 6.1"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Ant01 on 2008-07-09
I've loaded ubuntu 6.1 on a older pentium 3 and want to upgrade to version 8.04 but it seems that my pentium 3 cant handle version 8.04. 

I want to uninstall Ubuntu but keep my windows boot up partition without having to reload windows and all the updates and then install version 8.04 on another machine, can someone please help?

---

### Post by Elfy on 2008-07-09
~You will need to fixmbr either with your win dosc or download supergrub disc - burn it as an iso and boot with it. It has a fixmbr for win on it.

---

### Post by wannadumpwindows on 2008-07-09
You can use EasyBCD to fix your windows bootloader. It's a windows program that you install and use from windows. It's easy as pie. And better yet, it's free.

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

And after that, just use you partition tool of choice to delete the Ubuntu partition.

---

### Post by Ant01 on 2008-07-09
> **wannadumpwindows said:**
> You can use EasyBCD to fix your windows bootloader. It's a windows program that you install and use from windows. It's easy as pie. And better yet, it's free.

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

And after that, just use you partition tool of choice to delete the Ubuntu partition.

Thanks, I'll try it

---

### Post by wannadumpwindows on 2008-07-09
No problem. Just make sure you keep an eye on which one you're going to reinstall. There's options for Vista and XP. Use the one for your version, and you should be fixed in a matter of minutes, if not seconds.

---

### Post by Ant01 on 2008-07-09
> **wannadumpwindows said:**
> You can use EasyBCD to fix your windows bootloader. It's a windows program that you install and use from windows. It's easy as pie. And better yet, it's free.

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

And after that, just use you partition tool of choice to delete the Ubuntu partition.

The program doesn't work, I get a error the application failed to initialize properly (0x0000135) Click OK to terminate

---

### Post by bumanie on 2008-07-09
If you only want to change one ubuntu version for another, you should not have to worry about the mbr as long as you don't alter windows. The 'new' ubuntu install, as long as you put it over the old one, should correctly install grub to windows mbr - you could be unlucky and have windows mbr corrupt with the changes, but  in theory, that should not happen. Do manual at the partitioning stage and ensure the 'new' ubuntu is installed over the old ubuntu and grub should take care of itself. You could try 7.04 ubuntu it can run on 256mb ram, alternatively if you want to use 8.04, you could use Xubuntu with the fxce desktop environment that will work on 128mb (I think, although needs 194mb to install off a live cd, but the alternate xubuntu cd can install on as little as 64mb ram). Because you are not reinstalling windows, the mbr should not be an issue.

---

### Post by Ant01 on 2008-07-09
I initially tried to reinstall ver 7.1 over 6.1 but seemed to have a problem with my petium 386 running on 1 gig ram. 

I want to remove it and install it o a different machine.

---

### Post by wannadumpwindows on 2008-07-09
> **Ant01 said:**
> The program doesn't work, I get a error the application failed to initialize properly (0x0000135) Click OK to terminate

What version of windows are you using?

---

### Post by Ant01 on 2008-07-09
> **forestpixie said:**
> ~You will need to fixmbr either with your win dosc or download supergrub disc - burn it as an iso and boot with it. It has a fixmbr for win on it.

Where can I download the supergrub disc from or do you have a torrent I can use

---

### Post by wannadumpwindows on 2008-07-09
You can get it here:

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by Ant01 on 2008-07-09
> **wannadumpwindows said:**
> What version of windows are you using?

Windows XP

---

### Post by wannadumpwindows on 2008-07-09
> **Ant01 said:**
> Windows XP

Odd. Must be something specific to your set-up. Personally, I've used it on XP and Vista and had no troubles. Easiest way I've found to do it. Sorry it didn't work for you.

Supergrub Disc should solve your problem also, as mentioned. I provided the download link in my last post.

---

### Post by Ant01 on 2008-07-09
Loaded Super Grub, very confused please help not sure what to do...

---

### Post by Elfy on 2008-07-09
Hit enter until you get to language choice - choose language

enter until you get menu - choose windows - enter until menu and then choose fixboot, then using menu - go back until menu with quit appears and quit

---

### Post by Ant01 on 2008-07-09
> **forestpixie said:**
> Hit enter until you get to language choice - choose language

enter until you get menu - choose windows - enter until menu and then choose fixboot, then using menu - go back until menu with quit appears and quit

Followed everything to the T but it still boots up in Ubuntu, feel very stupid

---

### Post by Elfy on 2008-07-09
Maybe you'll need to delete the ubuntu and then run the fixboot from supergrub, but it worked ok for me when I needed it to. Once you'd got to the new menu you picked the right option I assume WIn2k, XP - assuming you've not got 95 or 98

Instead of trying the basic windows, go advanced and then miscellanea - fix partition of boot of windows - I have never used this option though so can't say what happens.

---

### Post by artir on 2008-07-09
Your pc is slow for Ubuntu, but not for Xubuntu or Fluxbuntu. Try them! Just format your old ubuntu partition and install xubuntu on that space.

---

### Post by Ant01 on 2008-07-09
> **forestpixie said:**
> Maybe you'll need to delete the ubuntu and then run the fixboot from supergrub, but it worked ok for me when I needed it to. Once you'd got to the new menu you picked the right option I assume WIn2k, XP - assuming you've not got 95 or 98

Instead of trying the basic windows, go advanced and then miscellanea - fix partition of boot of windows - I have never used this option though so can't say what happens.

Thanks, I used the advanced tab and it seems to have worked. I will now install it on my other PC...

---

