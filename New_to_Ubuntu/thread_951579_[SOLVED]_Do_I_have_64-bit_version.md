---
title: "[SOLVED] Do I have 64-bit version?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by reginak on 2008-10-18
There should be a sub-forum for Absolute Beginners who are also Not Geeks! LOL, I feel like my 4-year-old niece always wanting to play with the 6-year-old nephews..... but you guys are so nice and helpful, thanks!

So: having Flash issues, I've been browsing around the forum, and thought maybe I'd go ahead and upgrade to Flash 10. Installation failed. I see there is no Flash 10 for 64-bit Linux. A neighbor installed Linux for me, which I guess was a mistake because I didn't pay close enough attention -- where can I look to see if I got the 64-bit version installed? I do have the 64-bit hardware, I'm sure, because there's a little sticker on my laptop that says AMD Turion 64 X2 Dual-Core ...............

It's the .swf files that are giving me trouble. And also whatever format CBS's shows are in, it just hangs up with "transferring data from track.cbs.com" in the status bar of the popup window. I tried disabling Adblock but no difference.

Thanks so much for your patience, everyone!

---

### Post by philinux on 2008-10-18
Terminal

uname -m

i686 = 32 bit

---

### Post by pdub on 2008-10-18
open a terminal window and type:

```
uname -a
```

You will see something like:

Linux ****** 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 **x86_64** GNU/Linux

I am running 64 bit as you can see in BOLD.

---

### Post by reginak on 2008-10-18
Thank you! I do have the 64 bit. I guess I'll go browse around the 64-bit forum threads some more and see if I can find a solution to my Flash problems.

Cheers,
Regina

---

### Post by bsharp on 2008-10-18
```
sudo apt-get install nspluginwrapper flashplugin-nonfree
```

Should do it.

---

### Post by reg4c on 2008-10-18
Hey, 

I have Intel Core 2 Duo, 2.0Ghz
Can I run 64 bit Ubuntu?

What are the bad/good points of having 64 bit OS?
Should I start a new thread?

Cheerio

---

### Post by bsharp on 2008-10-18
> **reg4c said:**
> Hey, 

I have Intel Core 2 Duo, 2.0Ghz
Can I run 64 bit Ubuntu?

What are the bad/good points of having 64 bit OS?
Should I start a new thread?

Cheerio

Yes you have 64-bit.

Decide for yourself:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by reg4c on 2008-10-18
> **bsharp said:**
> Yes you have 64-bit.

Decide for yourself:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

Awesome, thanks...

---

