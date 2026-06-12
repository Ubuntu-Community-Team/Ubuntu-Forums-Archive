---
title: "Dell Inspiron 710m, non-PAE: Kernel Panic while Installing Xubuntu 12.04"
date: 2013-12-15
forum: New to Ubuntu
---

### Post by xSCCMx on 2013-12-15
I have this old Dell Inspiron 710m notebook that does not support pae but found Xubuntu 12.04 

I installed b43 broadcom drivers on the live cd and when I decided to install, it panicked I assumed and spat out all of these lines with no gui.

So I rebooted and tried again thinking I am going to install b43 after I'm done with the CD. It did it again.

Does anyone know what I could do? This laptop is only going to be used for websurfing and I need something a little lighter than Windows XP.

Thanks :)

---

### Post by mörgæs on 2013-12-15
Are you able to install Xubuntu 12.04, apply all updates and have a stready system through a couple of reboots, all with wired internet access?

---

### Post by xSCCMx on 2013-12-15
> **mörgæs said:**
> Are you able to install Xubuntu 12.04, apply all updates and have a stready system through a couple of reboots?


I wasn't able to go past the screen that asks, "Is your computer plugged into a power source, connected to internet, has xx GB available" When I push continue, it locks up and panics.

---

### Post by mörgæs on 2013-12-15
Here are some options for dealing with the [PAE]("https://help.ubuntu.com/community/PAE") problem.

---

### Post by xSCCMx on 2013-12-15
I got past PAE, it boots perfectly into a live session... It's the broadcom chip that screws everything up.

---

### Post by mörgæs on 2013-12-16
You didn't answer how it worked with wired internet access.

---

### Post by xSCCMx on 2013-12-16
So I connected it directly via cable without tinkering with the wifi card on live cd and the same thing happened.

---

### Post by amanchesterman on 2013-12-16
I had a similar problem a while back: trying to install Xubuntu on an old laptop (also one which needs b43 drivers installed), it ran beautifully from the live CD and then crashed in the same way as yours when I tried to install.

In my case, the problem was down to the fact that I had ticked the boxes to 'install third party software' and 'update packages while installing'. [I can't remember the exact wording but they are two boxes that appear on a screen very early during the installation process.] When I tried to install **without** ticking the boxes, there was no problem; I just had to update the packages and install the restricted extras when everything was working OK.

At the time, someone here commented that it's always best not to tick those boxes when doing an installation, so evidently it's not an uncommon problem. Just mentioning it in case it's relevant to your situation.

---

### Post by xSCCMx on 2013-12-16
I remember exactly checking the boxes... 
I'll try again.

did you install b43 before or after the OS installation completed?

---

### Post by xSCCMx on 2013-12-16
I went on with the installation, everything works perfectly! I've been testing it for nearly two hours now. No kernel panics and updates came flawless.

Thank you both for help.

---

### Post by mörgæs on 2013-12-16
You are welcome. Now your turn to help people :-)

Please mark the thread solved.

---

### Post by xSCCMx on 2013-12-17
Done.

---

