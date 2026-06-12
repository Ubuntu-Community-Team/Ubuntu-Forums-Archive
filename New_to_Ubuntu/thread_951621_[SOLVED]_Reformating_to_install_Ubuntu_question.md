---
title: "[SOLVED] Reformating to install Ubuntu question"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by nu2this2 on 2008-10-18
Hi all,

I had an old Dell Latitude laptop running w2ksp4 that was not working very well.I went onto one of the teckhelp forums and they really tried to help me but no one really solved my problem. Their solution was to reinstall windows. I can't really do this though as I got the laptop on EBay and recieved no discs at all, so I guess I'm stuck. I decided to install and use Ubuntu as a new OS.

I burned the iso image, matched the hash sums and inserted the disk. It suddenly seemed as though it was installing itself. I had not done anything as far as choosing a location, setting up a username, password etc.The screen turned black with white writing scrolling down informing me that certain actions had failed!--------------Oh well-----------The screen kept changing and suddenly I saw a number of actions with an OK next to them so I decided to let it do its thing. All of a sudden there is the Ubuntu screen asking me to log on and type my pssword. Of course I couldn't do this and my time ran out. I didn't know how to exit so I pushed the power down. When I rebooted A choice was given as to what OS system to use. I chose Ubuntu. Once again I was asked for my name and password which I had never been able to set up. Then, when I tried to boot up in windows I couldn't, the computer keyboard and mouse were frozen.

I really want to install Ubuntu correctly but feel a virus has corrupted my HD so I would like to reformat my drive. If I do this, will the live CD have all the required drivers and such to allow me to make a complete install or do I have to use the alternate CD version? 

Thanks for any input.

---

### Post by philinux on 2008-10-18
Just start again with the livecd and choose whole disk when the partitioner kicks in. It will format the drive.

I assume you've got data backup.

---

### Post by MunkyJunky on 2008-10-18
If you haven't told Ubuntu to install itself, it was the LiveCD loading to the desktop you saw. Removing the disk and booting up will stop this ;) The scrolling white text with [ OK ] and [ FAIL ] is Ubuntu loading its daemons (Unix services). 

And an install straight off the standard LiveCD will get your system up and running straight away. If you have restricted drivers (for example, nVidia drivers) Ubuntu will let you know, and you can choose to enable them.

---

### Post by nu2this2 on 2008-10-18
Thanks for getting back to me. I tried again and this time the Ubuntu desktop appeared. The bad part is that at copying files, at the 30% completed stage the cd was ejected and the keyboard froze. No mouse activity whatsoever. There was no indication (no rotating clock) of anything happening. I had to manualy shut down again and tried it all over. The install got to 34% and once again the cd ejected:confused:.

Any thoughts?

---

### Post by oldos2er on 2008-10-18
Did you run 'Check CD for defects' or md5sum on the cd?

---

### Post by philinux on 2008-10-18
Boot the livecd and at the first menu choose "Check CD for Errors".
Make a coffee it takes a few mins.

---

### Post by nu2this2 on 2008-10-18
Thanks,

I don't get that option, the program just starts to load.

---

### Post by Keen101 on 2008-10-18
I'd just reinstall. But I'd probably recommend the alternate install disk instead.

----

or if your feeling adventurous you could try the ubuntu 8.10 beta. But, i'd go for the alternate install disk first.

---

### Post by mkvnmtr on 2008-10-18
From what you are saying this is not acting like any of my installs. The live disk will not install itself. You have to start the install. Maybe you should tell us the specs for your machine. It is possible you lack enough ram or something and should go to the alt install disk. Or maybe another distro. Also explain exactly what you do when you insert the disk and begin the install. With this information someone can help you better.

---

### Post by ugm6hr on 2008-10-18
Where did you download Ubuntu from?

Which version?

There is clearly a problem with your installation disc, or the way you are using it.  It does not ask for a username until after installation.

Additionally, once installed, it does not ask you to choose an OS if it is the only OS on the HD.

> I burned the iso image, matched the hash sums and inserted the disk.

Did you install it inside Windows?  Or did you boot directly from the Ubuntu CD?

Basically, you need to start from the beginning, and describe **exactly** what you did, unless the questions I've asked above point you to an answer.

> I really want to install Ubuntu correctly but feel a virus has corrupted my HD so I would like to reformat my drive. If I do this, will the live CD have all the required drivers and such to allow me to make a complete install or do I have to use the alternate CD version?
The LiveCD will probably have the necessary drivers.  But you won't know unless you try the LiveCD (i.e. not within Windows).  In any case - it can't be any worse than an unusable computer.

---

### Post by oldos2er on 2008-10-18
> **nu2this2 said:**
> Thanks,

I don't get that option, the program just starts to load.

 Then something is seriously wrong. Try burning the ISO again at a slow speed, 4x or less.

---

### Post by nu2this2 on 2008-10-18
Thanks everyone. I reinstalled again and as they say here in the U.S. "The third times the charm"!! Everything seems to be working fine.

What a great bunch of folks here on this board. I'm sure I will be asking more questions very shortly and I look forward to learning how to use Ubuntu. The next thing I have to figure out is how to get my wireless up and running. I will check out the FAGS, TUTORIALS and SEARCH function for help along that line and see if I can work it out.

Once again thanks to all who made suggesstions, I appreciate your willingness to help a newbi.

---

