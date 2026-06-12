---
title: "trouble manually installing SpiderOak"
date: 2016-08-20
forum: New to Ubuntu
---

### Post by dolly13 on 2016-08-20
I'm brand new to Ubuntu so I'm at the stage where I follow instructions in a very concrete way, without really knowing what I'm doing. I'm trying to manually install SpiderOak so I DDG'd some instructions. They seem simple enough: Open the terminal, type a command to install the downloaded file.

However, I keep getting the error that says no such file or directory. I'll attach a photo that shows exactly what I'm typing. I'm sure it's something very silly, like one character in the wrong place, but I can't figure it out.

Thanks in advance.

---

### Post by howefield on 2016-08-20
Try typing 

```
cd Downloads
```

which should move you into the Downloads folder, then you can run your install command

```
sudo dpkg -i spideroak.deb
```

---

### Post by dolly13 on 2016-08-20
That worked perfectly, of course, howefield. Thank you for taking the time to help with what I'm sure seemed like a ridiculous question! :)

My next task, which I hope to complete independently (!), is to figure out what the heck happened with my partitions when I installed Ubuntu. It looks like Windows kept almost all the disk space, and since I ultimately want to get rid of Windows (after I figure this out a bit better), that's not good...

Have a good day and thanks again.:)

---

### Post by howefield on 2016-08-20
You're very welcome.

Double clicking the .deb file would have initiated the installation of the application via the Software Manager, but it is good to be comfortable with using the terminal :) 

Good luck with the next task, messing with partitions can be risky so you know to post if you need to.

---

### Post by dolly13 on 2016-08-20
Oh I will post another thread if I get too badly stuck -- thank you! :)

BTW, I found that the Software Manager was not installing SpiderOak, and then I learned (via my reading online) that it had to be manually installed on the more recent versions of Ubuntu. Not sure why! But in any case it's a good little skill to learn. We all have to start somewhere, and I'm starting at the rock bottom. :)

It's been just a few hours, but I'm already enjoying Ubuntu and I'm looking forward to getting it all set up with everything I need, and giving Windows the boot.

---

### Post by Geoffrey_Arndt on 2016-08-21
Might also be good to install the package "gdebi" . . . it is excellent at unpacking and installing debs like this (I call them "stand-alone" debs . . . not in a repo or using Ubuntu Software or Synaptic package managers).   BTW, if "Synaptic" is not installed, highly recommend you install it.   Kinda old-school, but still the best all around gui package manager.

---

### Post by dolly13 on 2016-08-21
Thanks for the tips, Geoffrey! I will look into both of those. I really appreciate it.

And by the way I figured out my partition issues too -- so proud, lol.

---

### Post by kurt18947 on 2016-08-21
I'd recommend not being in too big a hurry to "give Windows the boot". There are a *few* tasks for which a viable linux alternative does not yet exist. For me, updating my Garmin GPS is one. Tax preparation software can be another. Updating firmware on a piece of hardware such as a printer might involve an .exe file. I find a Windows partition of around 50 GB. adequate, or something like current size + 25%. I haven't required Windows for everyday tasks in years but the surest way to discover the edge case is to delete Windows with no means to restore.

---

### Post by dolly13 on 2016-08-21
That sounds like wise advice, Kurt -- thanks!

---

