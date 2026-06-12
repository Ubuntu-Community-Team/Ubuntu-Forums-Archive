---
title: "Ubuntu 14.04 LTS won't turn off"
date: 2016-04-23
forum: New to Ubuntu
---

### Post by giogio3 on 2016-04-23
Hi everyone!

I'm having some troubles with shutting down the machine after installing Ubuntu 14.04 lts (Only Ubuntu, no other OS, previously I had Win 10).
This is what I get when I try to shut down:

[ATTACH=CONFIG]268558[/ATTACH]

I've already tried to change the configuration of the grub file several times, and also tried other ways found on other threads but nothing seems to work with me.
As far as I understood it is related to the Bios that comes with Acer Aspire Laptop (in my case it is an Acer Aspire E 15 Start / ES1-512-C162).

Another problem is that in that case the combination of keys REISUB/O doesn't work, so I have to turn it off with the power button.

Could someone help me figure this out? Any hint would be really appreciated !

Thanks in advance, have you all a nice day ;)

---

### Post by RobGoss on 2016-04-23
Hello welcome to the forum, I was currently a 14.04 user but since moved on to 16.04, when I wanted to shut down my system I always used Cairo docks short cut and it work very well it would add a red tab with a number of shut down options

There's a shut down tab at the top right of 14.04, if I can remember correctly when I wanted to shut my machine down and used this option it would take me to the login screen and there it would give me to options Shut down or Restart my machine

Is this what you see when you use the shut down tab at the top of your desktop?

---

### Post by giogio3 on 2016-04-23
I'm currently using GNOME Flashback metacity as desktop version, so i just get this simple form:
[ATTACH=CONFIG]268560[/ATTACH] 
otherwise I would get this (i took the image from internet, but was the same)
[ATTACH=CONFIG]268561[/ATTACH]

I should also say that I've already tried to shut down through command line with sudo shutdown -h now or others similar, but nothing.
I noticed that sometimes with certain configuration of the grub file it hangs after saying will now halt.

---

### Post by RobGoss on 2016-04-23
> **giogio3 said:**
> I'm currently using GNOME Flashback metacity as desktop version, so i just get this simple form:
[ATTACH=CONFIG]268560[/ATTACH] 
otherwise I would get this (i took the image from internet, but was the same)
[ATTACH=CONFIG]268561[/ATTACH]

I should also say that I've already tried to shut down through command line with sudo shutdown -h now or others similar, but nothing.
I noticed that sometimes with certain configuration of the grub file it hangs after saying will now halt.


Yes this is the options I have as well but  for me this seems to work ok.

Is this a new installation of 14.04? I've learned when trying to install and distro and things don't work the way they should it worn't hurt to do yet another clean installation because in most cases for me it will fix any issues I might be having.

I also think it might be the [COLOR=#000000]**Flashback metacity** environment your using that may be causing this, try using the **default **desktop  ENV and see what happens[/COLOR]

---

### Post by giogio3 on 2016-04-23
Already tried, unfortunately it didn't work.
What could I do in case it is a bios related problem with acer aspire´s laptops?

---

### Post by RobGoss on 2016-04-23
I don't know much about Acer's but I would have to it's not your bios yet something else 

Take a look at this thread there're having the same issues as you maybe you can find a fix in this post

[http://ubuntuforums.org/showthread.php?t=2217602](http://ubuntuforums.org/showthread.php?t=2217602)


Question? is this a new installation of 14.04?

Have you considered giving 16.04 a go it's pretty smooth just a suggestion....

---

### Post by giogio3 on 2016-04-25
Sorry for the late response, I'll probably try to put 16.04 these day, hope will be not too late, it has been weeks that I turn it of with the power button

---

