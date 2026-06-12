---
title: "Problem with Nvidia drivers (I think?)"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Benbow on 2008-08-26
I have a Nvidia graphics card 3+ years old which is fine normally. However, when I turn on the "Nvidia accelerated graphics driver" so that I can use Compiz I notice an unevenness or jumpiness when I run videos from internet sites. I consequently have to turn off the accelerated graphics driver setting and the videos return to a normal smooth action. 
Is there any way that I can use Compiz and videos together without having to change the accelerated driver to do so?

---

### Post by nicedude on 2008-08-26
I would recommend that you try using envyng to update your Nvidia driver for you. It usually finds a better driver than the default Ubuntu one. It will do everything for you so you don't have to know anything about what you are doing etc.

COMMAND TO INSTALL ENVYNG

sudo apt-get install envyng-gtk

COMMAND TO START ENVYNG

sudo envyng-gtk

Now just select Nvidia and hit install driver and just say yes to anything it asks you. Once it is done then reboot and see if the driver it installs doesn't work better for you.

Hope this helps resolve your situation

---

### Post by Benbow on 2008-08-26
Thanks for the suggestion. I have done as you say but the result is the same - looks as though Ubuntu and Nvidia don't go together on my machine. This is a shame as it did work at first but subsequent Nvidia updates have spoiled a happy relationship.
I have been using Ubuntu for around 18 months now and have found all too frequently that updates, sometimes Ubuntu updates often sour an ideal situation. This is one of the problems with Windows and unfortunately also seems to affect Ubuntu. Probably the best way out would be to ignore any updates but then I suppose there would be other problems.

---

### Post by tuxxy on 2008-08-26
Make sure you remove any installed drivers first, search in synaptic for nvidia and remove them before running envy

---

### Post by xravexheavenx on 2008-08-26
Try diabling the one Ubuntu provides and going to the nVidia website and downloading their drivers on there.  However, watch out for any kernel updates because it will render your card useless and you will need to reinstall them again.  This reason is why Ubuntu now recognizes drivers for you.

---

### Post by alienexplorers on 2008-08-26
Use Envy and select to remove existing driver.  Then select manual install and use the 96.xx.xx driver.

---

### Post by nbayiha on 2008-08-26
Follow this thread . Use the Tricky Way.

[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

---

### Post by nicedude on 2008-08-26
I would suggest listening to [alienexplorers]("http://ubuntuforums.org/member.php?u=75896") and do what he just suggested. Also make sure the restricted drivers manager doesn't say it is controlling the graphics , System -> Administration -> Hardware Drivers . Although I just remove the restricted manager on all my boxes as I think it is lame to be installed by default and does more harm through confusion than good, its called "jockey" in synaptic if you ever want to just ditch it altogether. I have no use for it since all it manages is Nvidia or ATI ( use envyng instead ) & Wireless internet adapters ( use other means to enable if present since jockey wont give you the best driver anyway and fails to manage some adapters leaving people confused )

---

### Post by Benbow on 2008-08-26
OK, I have tried all these but still have the same problem. From past experience the only way to correct a serious update fault is to reinstall Ubuntu. This is a little severe and I don't particularly want to repeat an exercise which I have carried out too many times during the past 18 months, Windows may be bloated and slow but reinstalls are very rare.

This is the second major disappointment I have had during the last two months as I have also failed to find a user friendly video editor similar to Pinnacle or Windows own.

I may be in a better frame of mind in the morning but at this moment I feel like saying "goodbye Ubuntu". Linux, it appears, is still only for the technically proficient who can sort out problems from the command prompts.

---

