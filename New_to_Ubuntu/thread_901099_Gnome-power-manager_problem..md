---
title: "Gnome-power-manager problem."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by goodbyewindows2008 on 2008-08-26
After installing Ubuntu 8.04 several weeks ago I noticed that the running on battery tab in gnome-power-management is not there.

I have searched google for the past couple of days and have not found a solution that works for me. One method which solved this for other people is this one [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413/comments/21](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413/comments/21), but it didn't help me.

I did find that running "acpi -v" and then killing and starting gnome-power-manager would make the battery tab show up. Although after a reboot the battery tab is missing again.

If I boot into my ubuntu 7.10 live cd the power-manager works fine. Does anyone know if I can use the acpi/gnome-power-manager files from 7.10 in 8.04? I have seen methods like this for older kernals.

---

### Post by uberdonkey5 on 2008-08-27
Sorry, couldn't get the link to work.

Have you tried right clicking on the panel/toolbar (where ubuntu icon, applications etc and icons are shown) and selecting 'add to panel'. Then add 'battery charge monitor'. When this is on the panel, right click on it and change settings by going into preferences. This should stay on when you reboot.

---

### Post by goodbyewindows2008 on 2008-08-28
I fixed the link.

I have the battery monitor(gnome-power-manager) but it does not show a battery tab unless I go through the steps in my first post.
[ATTACH]83096[/ATTACH]

---

### Post by pi.boy.travis on 2008-08-28
Very interesting. . . Could we get some system specs please?

---

### Post by goodbyewindows2008 on 2008-08-28
NEC Versa L2200
Ubuntu 8.04, Kernal Linux 2.6.24-19, Gnome 2.22.3
Anything else just ask.

---

### Post by nicedude on 2008-08-28
I vote your name as top name of 2008 :-)

---

### Post by goodbyewindows2008 on 2008-08-28
Umm... thanks.

---

### Post by goodbyewindows2008 on 2008-09-04
Sorry but I need an answer. Bump.

---

### Post by pi.boy.travis on 2008-09-04
I know this is a bad habit from my Windows days, but *A clean install fixes all!*

When all else fails, I burn a fresh CD, backup /home, make a list of my packages, and reinstall.

---

### Post by goodbyewindows2008 on 2008-09-06
Well I installed from a free CD I ordered from ubuntu.com so that shouldn't be the problem and ubuntu has never seemed to detect my battery but I didn't notice the battery management tab wasn't there for a couple of weeks.

Also booting into a live session the battery tab isn't there.

---

### Post by pi.boy.travis on 2008-09-06
How old is this battery?  How is it's capacity compared to it's first run?  the only thing I can think of is maybe you are having problems with an older, malfunctioning battery.

If the battery is in good shape. . . I will have to do some more digging around. . . 

Hope this helps

---

### Post by goodbyewindows2008 on 2008-09-06
The battery and laptop is brand newin January. I think the capacity is the same as when it was new.

---

### Post by goodbyewindows2008 on 2008-10-06
@pi.boy.travis
Have you managed to digg anythting up?

---

### Post by pi.boy.travis on 2008-10-06
This is a tough one. . . 

Have you tried out the Intrepid Ibex beta?  There is a link to the .iso on the Ubuntu homepage.  If the battery is detected there, your problem will be solved when you upgrade.  If you want to stick with 8.04. . . I'll keep looking on Launchpad.

---

### Post by goodbyewindows2008 on 2008-10-06
Im going to but I'm nearing my internet cap so it might take a while to download.

---

### Post by pi.boy.travis on 2008-10-08
I have searched every resource I can find. . .

You may want to file a bug on Launchpad.  It's very easy, just create an account if you don't already have one, the rest is self explanatory.  Just make sure you include as many specs and as much info as you can.  By filing a bug report, you benefit the entire Ubuntu user base!

Hope this helps!

---

### Post by goodbyewindows2008 on 2008-10-08
Thanks I'll do that this weekend.

---

### Post by goodbyewindows2008 on 2008-10-16
Just an update, I've booted into a live session of 8.10 beta and the problem is not only still there, it's worse, when i get it to recognize the battery it doesn't report correct values for it. Thanks for all your help.

Also what logs, configs, etc should I include in the bug report?

---

