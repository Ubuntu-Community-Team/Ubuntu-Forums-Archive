---
title: "[SOLVED] Vista seems faster than Ubuntu -why?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by mogsmar5 on 2008-09-27
I've always been under the impression that Linux managed resources better than Windows and so was much faster. However, I booted into windows recently and noticed that opening applications and completing tasks were much faster than on Ubuntu. Opening programs in Ubuntu that I would have thought ought to open in an install - e.g. the terminal - seem to take much longer to load than command prompt on windows. Why is this? Is there anything I can do to improve Ubuntu's performance?

---

### Post by wolfen69 on 2008-09-27
> **mogsmar5 said:**
> I've always been under the impression that Linux managed resources better than Windows and so was much faster.

yes, linux is generally faster, and your results are not typical. perhaps you can post your specs and we can go from there.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-09-27
hum I have know idea how to speed it up any more then it is
but i find it to be faster then my win xp and vista

and i just had a thought of something 
need to know some things first like how much ram do you have
and how big is your ubuntu install
ramdisk

---

### Post by aimpau on 2008-09-27
The command prompt of the XP/Vista is far different than the terminal in linux. Try going into your command prompt in XP and type

```

cd c:\windows\system [enter]
explorer

```

You'll notice it will say, "needs to be in Windows to run" or something similar. However, in linux, you can run almost anything from the terminal. You can even listen to music + surf the net + edit documents + download bittorrent + burn cd + edit videos (avidemux)!

Just to show you how I'm so greatful with my xubuntu's speed and memory management. As I'm typing this with FF, I'm also:

Rendering a video in Avidemux
Downloading torrent with rtorrent
Editing an image with Gimp
And when I need a 5 min break, I just alt+tab to Warzone 2100.

My specs:
512MB DDR2 RAM
Sempron LLE 1150
My HD is an old QUANTUM HD built from 1999: ATA 66
No video card, just a video chip from Nvidia with 64MB shared memory.

Uptime: 6hours.


Have you tried running Photoshop and Premiere together in XP?

---

### Post by starcannon on 2008-09-27
> **mogsmar5 said:**
> I've always been under the impression that Linux managed resources better than Windows and so was much faster. However, I booted into windows recently and noticed that opening applications and completing tasks were much faster than on Ubuntu. Opening programs in Ubuntu that I would have thought ought to open in an install - e.g. the terminal - seem to take much longer to load than command prompt on windows. Why is this? Is there anything I can do to improve Ubuntu's performance?

Need more input, viz. what are your system specs?, are you running a compositing desktop manager(compiz)?, which software is doing this (some/all)?, if any, what other desktop eye candy are you running(google widgets etc)? Do you have additional background daemons/services running, if so what are they? What version of Ubuntu, or distro of Linux are you using? There are many things, and or combinations of things that require ever more resources to operate. If you want it fast, stay default, if you are default, then perhaps some hardware issues are at hand? Anyway as stated before your results of a slower than vista system are atypical.

GL and have fun.

---

### Post by Crafty Kisses on 2008-09-27
My saying is: "A Linux box, is a more efficient box."

---

### Post by louieb on 2008-09-27
Wow, The only PC with Vista we have around is the wifes laptop. With a gig of ram it is just slightly faster than Ubuntu  booted from a live CD. Are you running Ubuntu from the Live CD?  Is it a wubi install? 

And like the other poster I would like to know the system specs.  Of course there are things that can be done to speed up any OS. 
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by misswham on 2008-09-27
my xp is twice as fast as linux, when i do a speed test.  i am getting 14mbps with xp but when i do the same speed test in linux i get 5mpbs.

---

### Post by JoshuaRL on 2008-09-27
What kind of test is this?  What app are you using?

---

### Post by akiratheoni on 2008-09-27
How long have you used Vista? If you've used it for awhile, there's a built-in feature called Prefetch that calculates your most used programs and then loads it into RAM on boot up so it loads faster. 

If you want Ubuntu to do the same, simply go to Applications -> Accessories -> Terminal and type:

```
sudo apt-get install preload
```

And your password when it prompts you to. Then Ubuntu will start caching your most used programs into RAM and it'll load faster.

---

