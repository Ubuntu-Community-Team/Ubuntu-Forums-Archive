---
title: "Lots of issues"
date: 2018-02-05
forum: New to Ubuntu
---

### Post by zebullonpike on 2018-02-05
I went from 17.04 to 17.10. A major downfall in my opinion. System won't reboot, to boot system I have do a recover boot to get it to come back up. System has a front end look of 17.04 but acts like 17.10. Thinking of dumping 17.10 and going back to 17.04, but I will lose a lot even if it's backed up. The video despite a lot of codec work to fix is still jerky like it's only resolving one in five frames. Any help there?

---

### Post by cariboo on 2018-02-05
17.10 was released in October, so it is no longer in development.

---

### Post by tinylagarto on 2018-02-05
Did you try to boot into into Wayland or Xorg? 

You can select that from the boot menu in the login screen.

---

### Post by kato223 on 2018-02-05
Unfortunately, Ubuntu 17.04 is no longer supported, so you would not be able to install it and get updates from it.  Ubuntu 17.10 will still be receiving updates until July 2018.  See:  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  If you're not that concerned about cutting edge or trying out the latest and newest, look into running a LTS release like Ubuntu 16.04 LTS or in April Ubuntu 18.04 LTS is scheduled for release.  They are supported in 5 year cycles, and they do have the ability for rolling updates to the kernel and stuff.  One thing to remember is that LTS is considered stable and applications can take a while before they are implemented into the release for full testing of the application.

---

### Post by Geoffrey_Arndt on 2018-02-05
Might consider not using the interim "beta" level releases like 17.04 and 17.10 (especially 17.10) as it uses the new and very unproven wayland display manager).

So, a good solution if you liked 17.04 is to do a full install (over 17.10) of Ubuntu 16.04.3.   Run it till about June or so and then if still wanting to get the newest  - - maybe try the very solld, easy to use and stable Ubuntu Budgie 18.04.    Budgie is super easy, looks good, more modern than xfce or mate and still has all the inherent advantage of Ubuntu proper.     Just my two cents (but an educated two cents).

PS:   Budgie is modern but still a traditional desktop gui.   IF, repeat, IF you need touch screen support, or other special user need, then might want the traditional main-line Ubuntu with Gnome3 in 18.04  . . . . either one is a winner (imho).

GGA

---

### Post by mörgæs on 2018-02-06
17.10.1 is a highly stable release and a good candidate for a reinstall (an upgrade from 17.04 can on the other hand break a system). 

17.10.1 contains all bug fixes which have been added to 17.10 from october. Just run it in Xorg mode (Wayland is experimental, Xorg certainly isn't).

---

