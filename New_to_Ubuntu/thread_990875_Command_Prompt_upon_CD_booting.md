---
title: "Command Prompt upon CD booting"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by msbealo on 2008-11-23
Hello,

I'm keen to move across from Windows, but I'm having a problem.

When I boot from the CD I get to choose my language and then start to boot 8.10. The progress bar goes backwards and forwards for some time and then the progress bar starts to fill. It fills, I then see a shell, a few messages pop up and go before I can see them and then I'm simply left with the Linux command prompt. 

There is no obvious error message that I can see. It tells me where to find the documentations and also something about running commands in administrator mode and that's it.

I can type commands but that's about it. 

Is there anyway for me to find out what the problem is or any suggests on what I should do next? I've tried to look at the documentation but couldn't find anything that covered CD booting problems.

Again, all I'm trying to do it boot from the CD and I'm not even trying to install it yet.

System Specs: Mobile Athlon XP 2600+
              448MB of RAM
              26 megs free HD space

Thanks,

---

### Post by insane_alien on 2008-11-23
try selecting the check disk integrity option.

it is possible you have a bad burn

---

### Post by Michael.Godawski on 2008-11-23
> System Specs: Mobile Athlon XP 2600+
              448MB of RAM
              26 megs free HD space

really only 26 megs free space?:)
 but i cannot imagine that has something to do with your CD not working. 

A good way to avoid burning errors is to follow psychocats instructions:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by -Zeus- on 2008-11-23
it shouldn't, but the 26mb free could be the problem...

---

### Post by Michael.Godawski on 2008-11-23
hi Zeus
do you think Ubuntu is somehow checking the free disk space to make sure there is enough space for a future installation? Could be. But I am not 100% sure.

---

### Post by fooman on 2008-11-23
boot the live cd and after you choose language...press f4

choose safe graphics mode and see if you can get to the desktop.

---

### Post by Dr Small on 2008-11-23
Sounds like a problem with the graphics card. Probably is missing the drivers for it, so X isn't starting. The vesa drivers should work for it, though.

---

### Post by msbealo on 2009-01-18
Guys,

Thanks for your replies. I've only just seen that anyone did reply as I didn't receive a message letting me know. 

I sorted the problem out quite quickly after a little more digging. 

xorg.0.log was complaining that it couldn't find any suitable screen resolution and was therefore failing to find a screen.

I simply changed my xorg.cong file to include:  

```

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	31-51
	VertRefresh	50-70
EndSection
```

For the confused beginner out there, I did this by opening the xorg.conf file using

```

sudo nano /etc/X11/xorg.conf
```

This somehow does the trick and my X windows starts up every time using the openchrome driver.

Just so people know, I have an old Acer Aspire 1350. 

Also.. I think I had 23 gigs available at the time of my previous post. Now I only have Ubuntu installed and quite a bit more space.

Thanks.

---

