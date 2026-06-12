---
title: "Rip cd's inp3?"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Axis on 2008-10-08
So I don't really care that much if my songs are ripped in mp3, however my girlfriend uses my computer to rip cds and put songs on her ipod sometimes and .ogg wont do.

So I have read I can use sound juicer to rip in mp3 but I can't find any up to day tutorials that work.

It says the mp3 profile is active, yet I can't select it?

---

### Post by Sef on 2008-10-08
Read this [HowTo]("http://ubuntuforums.org/archive/index.php/t-957.html").

---

### Post by Axis on 2008-10-08
Firstly thank you for your reply.

However as I mentioned all I can find are outdated tutorials that no longer work.
A newer one or some sort of a solution would be appreciated :)

Thanks,
Axis

---

### Post by gnuman on 2008-10-08
> **Axis said:**
> 
It says the mp3 profile is active, yet I can't select it?

Try exiting the program completely and restarting it.

Also, [read this ]("http://www.stchman.com/cd_rip.html")about setting the bitrate....

Good luck.

---

### Post by mazirian on 2008-10-14
It's not that simple.  Any profile that calls lame results in the following startup error:

** (sound-juicer:10778): WARNING **: Profile warning: no element "lame"

and will not be displayed as an option for selecting the output format.

Yes, lame is installed and is in my $PATH.

---

### Post by mazirian on 2008-10-14
Stupid of me.  I was simply missing a gstreamer plugin.  I was sure it was installed, but apparently not. :(

---

