---
title: "Do I need another version of Ubuntu or Linux? It's rather slow..."
date: 2012-10-16
forum: New to Ubuntu
---

### Post by awesomedog on 2012-10-16
Hey, I have a HP Pavilion computer with a Pentium IV Processor rated at 2.8GHz, and 1.75GB RAM (it's about 7-8 years old). I am currently running Ubuntu 12.04, but it's rather sluggish, especially when viewing videos on YouTube, the videos lag a lot (esp. over 360p), I was wondering if my specs were enough to run this version of Ubuntu or if I need to downgrade or change my linux version?

I am running it alonside Windows XP. I intend to use Linux for browsing the web and basic editing of documents while playing old games on XP.

Thanks!

P.S. I have a Nvidia Geforce FX5500, and I am already running Unity 2D (I cannot support 3D in any case)

---

### Post by NikTh on 2012-10-16
Hi , 

first try to login from ubuntu-2d session. Its much lighter compared with Unity 3D session. 

Logout and at login box click the little Ubuntu icon and select "ubuntu-2d". 

Thanks

---

### Post by SlugSlug on 2012-10-16
I've just installed Debian squeeze on an older PC that struggled with graphics (HD playback mainly). 

It now runs great :)

---

### Post by TBABill on 2012-10-16
I would suggest looking at what type of video card you have and whether or not a proprietary driver may be available. The open source drivers are sometimes much less efficient and don't perform as well.

---

### Post by rishioid on 2012-10-16
try using cinnamon : [http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)  or use GNOME Classic while login.
Cinnamon is a new desktop environment and runs good as compared to unity.

---

### Post by puntigamer on 2012-10-16
Both Lubuntu and Xubuntu (LXDE and XFCE desktop environtments) are good lightweight alternatives for "normal" Ubuntu with Unity or Gnome Shell. Check out their homepage and try the one you like the most! :)

---

### Post by raja.genupula on 2012-10-16
+1

[http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu)
[http://en.wikipedia.org/wiki/Lubuntu](http://en.wikipedia.org/wiki/Lubuntu)

---

### Post by Gnawnsense on 2012-10-16
> **awesomedog said:**
> Hey, I have a HP Pavilion computer with a Pentium IV Processor rated at 2.8GHz, and 1.75GB RAM (it's about 7-8 years old). I am currently running Ubuntu 12.04, but it's rather sluggish, especially when viewing videos on YouTube, the videos lag a lot (esp. over 360p), I was wondering if my specs were enough to run this version of Ubuntu or if I need to downgrade or change my linux version?

I am running it alonside Windows XP. I intend to use Linux for browsing the web and basic editing of documents while playing old games on XP.

Thanks!

P.S. I have a Nvidia Geforce FX5500, and I am already running Unity 2D (I cannot support 3D in any case)

By no means am I a Linux guru. Relatively newbie still. But I've tried using off-and-on for a few years, only recently had success. Like you, I always suffered from sluggish performance on videos, screen transitions, and whatnot on my older machine. It was older, but by no means should it of been running Ubuntu so much worse than Windows.

It was an issue with my graphics card drivers. Sadly, I have no experience at all with Nvidia, always stayed with ATI. However, before switching versions, I'd try all possible options in making sure your card drivers were up to date, configured properly, and using the correct ones. Because you'll still have the same issues with the YouTube videos regardless of the version if it's a driver issue. And stepping back to older versions of Ubuntu never solved any of my driver issues; always were the same.

---

### Post by Mark Phelps on 2012-10-16
IF the lag is only serious during playing of videos, then it's the video drivers, not Ubuntu performance in general.

While another desktop might make a difference in general use, it's not going to affect video performance.

I've not used Nvidia chipsets in a long time, but with ATI chipsets, they dropped accelerated driver support for older chipsets a long time ago.  If this is the same situation for Nvidia chipsets, you're probably not going to see any improvement in video performance unless you're able to change the video chipset.

---

### Post by lykwydchykyn on 2012-10-16
Try this, before you go reinstalling another distro:

 - Open software center
 - Install the LXDE desktop
 - log out
 - Choose "LXDE" as your session
 - log in.

See if things perform better after that.  That's basically what Lubuntu is, Ubuntu with LXDE as a desktop; no need to reinstall to get it.

---

