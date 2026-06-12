---
title: "Acer Aspire one AO751h - 12.04 32bit"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by LeDono on 2012-09-04
right, i managed to get 11.04 into a usable condition on my netbook, usable being the operative word.
I had graphics driver issues that meant rebooting if i wanted to watch video in full screen, after closing the lid. and occasionally windows would just break up into what i can only describe as digital noise. 

So i decided to upgrade to 12.04....
the live CD seemed to work, and installation seemed to go fine. Then when i boot up it decided to overlay the bottom half of the screen on top of the top half... the lower half would be black, or with code frozen on it.  This could be fixed by logging in and out again, until rebooted again.

I couldn't find any fixes on the internet, so i did a fresh install (not an upgrade) and now it boots up to a black screen. I here the sound of the log in box popping up, but thats it. no visuals. 
I rebooted and held down shift key, carried out the dpkg and then the 'resume' which simply resulted in the same half image problem. however on rebooting it goes to the black screen. 
HELP!! :cry:

I understand a bit, but will need step by step instructions....
Thanks in advance, 
LeDono

---

### Post by Bashing-om on 2012-09-04
LeDono; Hi ! welcome to the forum.

Your issue is not uncommon. Boot up to the grub menu (hold any key to do so)..and edit the kernel command line and try with the insertion of "nomodeset".

Here is a great tutorial in regards to this situation:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If the parameter works, the tutorial will instruct on the permanent fix.


[INDENT]hth <==BDQ

[/INDENT]

---

### Post by bodhi.zazen on 2012-09-04
You have to install a newer kernel.

See the wiki page for details:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by LeDono on 2012-09-04
> Post installation
Ubuntu 12.10 +

Starting with kernel 3.3.4 (Ubuntu 12.10), the gma500_gfx driver works without adding any boot options.

does this mean the simplest fix is to use 12.10 rather than 12.04?

---

### Post by GreatDanton on 2012-09-04
Ubuntu 12.10 is development release and it's not released yet. If you are not familiar with Linux, and if you don't want to spend time with bugs then DO NOT install 12.10.( I assume that you are pretty new here, so in your case I wouldn't install 12.10; correct me if I am wrong. ) Try what bodhi.zazen suggested you.

Regards.

---

### Post by LeDono on 2012-09-04
ok, so installed the new kernal, so there's no issue with logging on. but can i fix the suspend thing? when i close the lid, it suspends, but upon a key press black screens again :/

---

### Post by LeDono on 2012-09-05
now my mic and isn't working at all... and the sound out put is messed up. plugging in to the headphones doesn't stop the sound output, and when i use my usb headset, skype works through the headset, but when i opened up youtube it played through the speakers... now thats odd....

---

