---
title: "Back, and back to stay."
date: 2020-04-16
forum: New to Ubuntu
---

### Post by Rockwell32001 on 2020-04-16
Hi, again.  I've been around for a while, but now I'm back, and back to stay.  I had an absolutely horrible, horrible experience with Windows 10.  My sound stopped working, mysteriously, discord would just randomly not work, and I was watching the news about how many patches Microsoft was having to roll back.  And, I've had enough.  When my system stopped working, randomly, for the second time in two weeks, during a pandemic when school was shut down, and blue screened three times in one day, (that week) I nuked and paved.  

However, I didn't plan the best.  I pulled out a 3 TB hard drive before I reformatted and am having some trouble.    It had important data on it, and I couldn't keep the OS stable enough, long enough, to move it over to the external.  How should I proceed about migrating it?  Thanks a million.

---

### Post by Impavidus on 2020-04-16
So you had some trouble with a hard drive. What kind of trouble?

---

### Post by ajgreeny on 2020-04-16
If you pulled out the 3TB drive from a Windows machine that had crashed I would expect that you will not be able to mount, read or do anything with that drive until it has been attached to a Windows machine and repaired, probably running chkdsk (or whatever it's called; I don't have Windows any more) and then removed properly, not just unplugged or detached.

Is this an external or internal drive?  Do you hace a drive caddy you can use to attach it with USB if necessary?

---

### Post by Rockwell32001 on 2020-04-17
Hi.  Sorry it took so long.  I&#8217;m on my tablet.  I couldn&#8217;t get the computer to boot this morning.  The other hard drive is waiting to be reformatted, no problem there.  Windows was the problem.  I don&#8217;t know what&#8217;s wrong.  First, it wouldn&#8217;t boot, then I couldn&#8217;t log in.  I&#8217;m running AMD hardware, not sure if that is the problem.  Help?

---

### Post by Impavidus on 2020-04-17
Ubuntu woks well on AMD hardware, but if the hardware is recent (less than a year on the market), it may be best to use Ubuntu 20.04. It will be released next week, but I've read that the beta is good for daily use already.

If you've a concrete problem with Ubuntu, we can probably help, but we may need some information on your hardware, your Ubuntu version, its configuration and what you want to accomplish. So far we only know that you've got a computer with a broken Windows 10 system, some AMD hardware and a 3TB harddrive and want to install Ubuntu.

---

### Post by Rockwell32001 on 2020-04-17
My apologies for not being clear.  My hardware is as follows:  MSI Mobo, X470 chipset.  Ryzen 5 processor, RX 570 Video card.  I have successfully (finally) managed to reinstall Ubuntu.  The 3 TB hard drive is a red herring at the moment;  I can reformat it at will and everything should be fine.  The stability problem was a Windows problem, nothing to do with a hard drive.  I THINK my initial  install may have had a driver problem, but I can't and don't know how to confirm that at the moment.  My local hackerspace is shut down for the time being.  In the meantime, I need to confirm drivers before I get too carried away.  So, how do I do that?

---

### Post by Impavidus on 2020-04-18
Only once have I installed drivers on Ubuntu and those were printer drivers. Assuming you installed 20.04, 19.10 or 18.04 using the 18.04.4 live disk, all AMD drivers should be built-in. You could check the "additional drivers" utility, which can show you if proprietary drivers are available for your hardware. But if everything works, don't worry about drivers.

---

