---
title: "2 Issues (possibly related)"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by prenger745 on 2011-12-16
Hello,

I recently made the switch to Lubuntu and am trying to stick with it but a few issues I have are fairly big in my opinion.  Maybe there are work arounds:

1) I am using it on a computer that is shared with 3 other users.  When I am on my account and set the screen saver to require a password to log back in, it doesn't give me the option of switching users.  So if it locks down, and I am not here, my wife and kid can't log into their account.

2) I tried a work around by logging out every time I am finished. I am then brought to the main login page which is fine, but at that point no screensaver or monitor dimming happens which is not good for my monitor at all.

Any workarounds or settings I can do?

Thanks,
Dan

---

### Post by SteveDee on 2011-12-16
> **prenger745 said:**
> ...Any workarounds or settings I can do?
...

No, but your Lubuntu system should boot in less than 40 seconds and shutdown in less than 5 seconds....save power, switch it off when not in use.

---

### Post by prenger745 on 2011-12-19
I'm sorry but "turn off your computer" is not a work around nor something that I am going to do.

---

### Post by Bucky Ball on 2011-12-19
Unless you have a *very* old monitor the lack of screensaver will not make a jot of difference. ;)

---

### Post by JC Cheloven on 2011-12-19
EDIT: Oops, perhaps I missed the point. I was suggesting you to install gdm but not sure whether the screensaver will use the login manager at all... and that would install a lot of dependencies, pulseaudio among them, which is pretty much against the philosophy of a light desktop. Deleted it, as I'm unsure if that was good advice.

BTW, SteveDee's point is not that bad, in my opinion.

---

### Post by amjjawad on 2011-12-21
> **prenger745 said:**
> 1) I am using it on a computer that is shared with 3 other users.  When I am on my account and set the screen saver to require a password to log back in, it doesn't give me the option of switching users.  So if it locks down, and I am not here, my wife and kid can't log into their account.

See this and check the last post by me: [http://forum.lxde.org/viewtopic.php?f=8&t=31470](http://forum.lxde.org/viewtopic.php?f=8&t=31470)

It's similar case to yours and I wonder whether you were the same person who posted there ;)

Hope with Lubuntu 12.04, such issues will be fixed once and for all.


> 2) I tried a work around by logging out every time I am finished. I am then brought to the main login page which is fine, but at that point no screensaver or monitor dimming happens which is not good for my monitor at all.
ALL my tests are done on PC not laptop (I have ancient laptops and because it's slow, I can't use it on my tests which require a better machine). As far as I know, there are some packages/processes/daemons responsible to turn the monitor off in case of inactivity. When you log off, I don't think such stuff will be loaded in RAM but I'm not 100% sure. I must do some tests or ask someone who knows (who have tired that him/her self).

---

### Post by cmcanulty on 2011-12-21
see post #25 here note that I posted my values but you can set  whatever you like
[http://ubuntuforums.org/showthread.php?p=11553140#post11553140]("http://ubuntuforums.org/showthread.php?p=11553140#post11553140")

---

### Post by amjjawad on 2011-12-22
Because I do lots of tests, I keep a machine with Multi-Booting System which has many Linux Distributions installed on, one of these is Linux Mint LXDE 11. By default, it has GDM instead of LXDM. **Switch User** Feature works perfectly, just tested it.

[IMG]http://i40.tinypic.com/2ch4xar.jpg[/IMG]


After you switch back to your session, you'll see the lock/login window for XScreensaver, once you enter your password, you'll see you desktop. So, it does work.

Lubuntu 12.04 will not have LXDM. I hate to say that but it's true ... the development process is slow when it comes to LXDE.

Anyway, you can install GDM and replace LXDM. If you need some help, let me/us know.

Hope that helps!

---

### Post by amjjawad on 2011-12-22
Posting this from Lubutnu 11.04 installed [COLOR=Blue]**[sudo apt-get install lubuntu-desktop]**[/COLOR] within Xubuntu 11.04 (which I keep for testing ONLY) and I confirm that using GDM as a login manager will give you the ability to "Switch Users" easily.

So, go for it :)

---

### Post by JC Cheloven on 2011-12-22
> **amjjawad said:**
> Posting this from Lubutnu 11.04 installed [COLOR=Blue]**[sudo apt-get install lubuntu-desktop]**[/COLOR] within Xubuntu 11.04 (which I keep for testing ONLY) and I confirm that using GDM as a login manager will give you the ability to "Switch Users" easily.
So, go for it :)
Thanks amjjawad for giving a hand here :) I didn't have the time to test myself, and, in the doubt, deleted my suggestion of installing gdm from the post.
I'm still thinking in the dependencies, and in doubt of whether it's worth or not getting pulseaudio installed as a side effect... well, that depends on the user, I guess.

---

### Post by amjjawad on 2011-12-23
> **JC Cheloven said:**
> Thanks amjjawad for giving a hand here :) 

At your service, my friend :)

> I'm still thinking in the dependencies, and in doubt of whether it's worth or not getting pulseaudio installed as a side effect... well, that depends on the user, I guess.

IMHO, it depends on your machine. If your machine can handle more processes, then go for it. If your machine can't handle that, keep everything as it is. After all, Lubuntu mainly for old machines but as we both now, recently, many are using it on their new machines and you can count me as one of them :) I installed Lubuntu on Lenovo G570 Core i5 with 4GB RAM.

I'm now planning to install Lubuntu on this:

[IMG]http://ubuntuforums.org/picture.php?albumid=2136&pictureid=7114[/IMG]

Full story here: [http://ubuntuforums.org/showthread.php?t=1590614](http://ubuntuforums.org/showthread.php?t=1590614)

By the way, that old broken laptop does work and you'll be amazed if you see that yourself :D

Edit:
If you have an old laptop like the above one, of course you have to worry about each and every package you have or want to install. Otherwise, I don't think it really matters if you have a good PC.

In fact, I have P4 3GHz (L2 Cache 1MB) with 512MB RAM where I'm posting this now from (using Lubuntu 12.04). It's my test PC and it has many systems (Multi-Booting). Xubuntu 11.04 is giving me HARD time because it's slower than Ubuntu 10.04 and Lubuntu 11.04 and Lubuntu 11.10 and Linux Mint LXDE 11 ALL installed on the same machine. Even after I installed Lubuntu (lubuntu-desktop) as a second DE in Xubuntu, it's still the same. Not really off topic but my point is: as long as your system and machine can handle that, go for it. Otherwise, keep everything as it is :)

This is from my personal experience based on many tests.

---

### Post by JC Cheloven on 2011-12-26
> **amjjawad said:**
> 
Full story here: [http://ubuntuforums.org/showthread.php?t=1590614](http://ubuntuforums.org/showthread.php?t=1590614)


Wow, I see there that it's about a pc with 64 Mb ram... a real chalenge. But the photo shows Mint working... we have to believe :)

---

### Post by amjjawad on 2011-12-29
> **JC Cheloven said:**
> Wow, I see there that it's about a pc with 64 Mb ram... a real chalenge. But the photo shows Mint working... we have to believe :)

Not only 64MB of RAM but also a Pentium 2 with 366MHz only and there was no way to install unless connecting the HDD to another machine. I spent one month but learned a lot.

Yes, it's true that it has Mint but after all, it's LXDE :)


@OP
We never heard back from you anymore?

---

