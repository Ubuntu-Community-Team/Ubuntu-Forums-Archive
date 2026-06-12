---
title: "Paralysed after &quot;upgrading&quot; 10.10 to 11.04"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by swordsintoplowshares on 2011-12-08
I and a fellow Linux-newbie friend had been using a shared PC with Ubuntu 10.10 Maverick. Without getting help from someone with more Linux know-how, my fellow newbie tried to upgrade to 11.04 Natty (which I wouldn't have done because I read that 11.04 was buggy) after Ubuntu prompted him to upgrade. However, being a newbie, his decisions/choices during the upgrade must have been guesses. He said that there had been a message on screen that basically said the PC didn't have the hardware for Unity, but that it allowed him to keep Ubuntu Classic (Gnome).
And now, the PC is nearly paralysed—it's full of glitches and it's almost unusable.
When I try to click on anything—Applications, Places, etc., or an icon or shortcut for a file or folder—nothing happens, it just flickers for a second. Sometimes it will allow Firefox to run, but not for very long. 
Can anyone suggest a solution? Maybe I'll have to make a rescue disk or bootable USB flash drive, I don't know.
I appreciate any help you can give me, thanks.

---

### Post by swordsintoplowshares on 2011-12-09
(bump)

Should I try something like burning a CD for RIP Linux (Recovery Is Possible) or 
SystemRescueCD?

(I'm using a shared PC with Ubuntu pre-installed)

I appreciate any advice, thanks.

---

### Post by jerrrys on 2011-12-10
"full of glitches" is not much to go on.

Open a terminal and enter (one at a time):

**sudo dpkg --configure -a**
[B]sudo apt-get install -f 
 sudo apt-get upgrade -f 
 sudo apt-get dist-upgrade -f[/B] 

and post any errors

---

### Post by swordsintoplowshares on 2011-12-10
Thanks for answering.
I should have said that I had already run dpkg in recovery mode before I posted my question.

I entered the commands and it gave the same message that it gave me when I ran dpkg:

"The following packages were automatically installed and are no longer required: [It listed about 30 packages]
Use apt-get auto remove to remove them.
0 upgraded, 0 newly installed, 0 to remove, and 0 not upgraded."

As for glitches, the PC will only allow me to do a few things (without  using the command line), such as Ctrl-Alt-Delete, restart/shut down, and  open Firefox--but most of the time, it won't allow me to use Firefox.

Before, in recovery mode, I had run failsafeX (Run in failsafe graphic mode) and it said this:
"Ubuntu is running in low-graphics mode. Your screen, graphics card, and  input device settings could not be detected correctly. You will need to  configure these yourself."

---

### Post by yeats on 2011-12-10
> When I try to click on anything—Applications, Places, etc., or an icon or shortcut for a file or folder—nothing happens, it just flickers for a second. Sometimes it will allow Firefox to run, but not for very long. 

I would suspect that this has to do with your video driver.  I had a similar experience with an older ATI/Radeon card.  Do you know which video card you're running?  You can do

```
lspci | grep VGA
```

in a terminal to find out.

---

### Post by swordsintoplowshares on 2011-12-10
Thanks, it says:
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 2)

---

