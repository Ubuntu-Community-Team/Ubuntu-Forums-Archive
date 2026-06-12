---
title: "Ubuntu 14.04 - Updating to Synaptics 1.8 Touchpad Driver"
date: 2014-09-22
forum: New to Ubuntu
---

### Post by ts1971 on 2014-09-22
Hi,

Apologies in advance for what is probably a pretty basic question but I'm new to Ubuntu and trying to figure out how this all works.  In any event, I have recently installed Ubunut 14.04 on a Lenovo Thinkpad 540p.  Mostly, I'm loving it, with one really big exception. For some inexplicable reason, Lenovo decided to remove the two buttons dedicated to the trackpoint and now the only buttons available are the software buttons activatable through the touchpad.  Unfortunately, this works really poorly as I am constantly dragging my fingers across the touchpad as I type / manuever the trackpoint with the result that the cursor is all over the place.  It is *very* frustrating to say the least.  I am a long time Thinkpad user and my solution to this problem as always been to simply disable the touchpad.  Unfortunately, as the trackpoint no longer has it's own buttons that's no longer a possibility as things stand now.

However, I've done a bit of googling and at least as I read this [post]("http://who-t.blogspot.com.au/2014/03/xorg-synaptics-support-for-lenovo-t440.html"), it appears that synaptics 1.8 adds a lot of support for these new touchpads including the ability to disable them for scrolling without disabling their function as software buttons.  This is exactly what I need.  However, if I'm understanding the Ubuntu Software Center, it looks like I've only got xserver-xorg-input-synaptics 1.7.4-0ubuntu1 installed.  So, my question is, is it possible and or advisable to install 1.8 on my own?  If not, is there anyway to know when it might be available through the Software Center?

Thanks!

---

### Post by sandyd on 2014-09-22
> **ts1971 said:**
> Hi,

Apologies in advance for what is probably a pretty basic question but I'm new to Ubuntu and trying to figure out how this all works.  In any event, I have recently installed Ubunut 14.04 on a Lenovo Thinkpad 540p.  Mostly, I'm loving it, with one really big exception. For some inexplicable reason, Lenovo decided to remove the two buttons dedicated to the trackpoint and now the only buttons available are the software buttons activatable through the touchpad.  Unfortunately, this works really poorly as I am constantly dragging my fingers across the touchpad as I type / manuever the trackpoint with the result that the cursor is all over the place.  It is *very* frustrating to say the least.  I am a long time Thinkpad user and my solution to this problem as always been to simply disable the touchpad.  Unfortunately, as the trackpoint no longer has it's own buttons that's no longer a possibility as things stand now.

However, I've done a bit of googling and at least as I read this [post]("http://who-t.blogspot.com.au/2014/03/xorg-synaptics-support-for-lenovo-t440.html"), it appears that synaptics 1.8 adds a lot of support for these new touchpads including the ability to disable them for scrolling without disabling their function as software buttons.  This is exactly what I need.  However, if I'm understanding the Ubuntu Software Center, it looks like I've only got xserver-xorg-input-synaptics 1.7.4-0ubuntu1 installed.  So, my question is, is it possible and or advisable to install 1.8 on my own?  If not, is there anyway to know when it might be available through the Software Center?

Thanks!
It is already available in Ubuntu Utopic Unicorn (Development release). You can probably try to do a backport of that package to 14.04 or wait to see if it will be backported.

---

### Post by ts1971 on 2014-09-23
> **sandyd said:**
> It is already available in Ubuntu Utopic Unicorn (Development release). You can probably try to do a backport of that package to 14.04 or wait to see if it will be backported.

Thanks Sandy for that information.  I'm completely new to Ubuntu and don't really know how the development / version cycles work.  Will 14.04 one day be upgradable to whatever the Ubuntu Utopic Unicorn version is?  Or will that always be a seperate installation?  On a related note, is there somewhere that I could ask whether there is a planned backport to 14.04?

Thanks

---

### Post by sandyd on 2014-09-24
> **ts1971 said:**
> Thanks Sandy for that information.  I'm completely new to Ubuntu and don't really know how the development / version cycles work.  Will 14.04 one day be upgradable to whatever the Ubuntu Utopic Unicorn version is?  Or will that always be a seperate installation?  On a related note, is there somewhere that I could ask whether there is a planned backport to 14.04?

Thanks

Yes, 14.04 will be upgradable to the development version (which is Ubuntu Utopic, 14.10) once development has completed. That being said, Utopic will be released some time in October, so it is coming up.

---

