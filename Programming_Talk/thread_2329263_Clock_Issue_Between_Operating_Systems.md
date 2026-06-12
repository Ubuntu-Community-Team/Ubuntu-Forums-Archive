---
title: "Clock Issue Between Operating Systems"
date: 2016-06-29
forum: Programming Talk
---

### Post by llTheSoldierll on 2016-06-29
Hi,

I've set up Ubuntu alongside another OS and now have a trouble with clock settings.

I want to the clocks show different on my different Operating Systems. For example, when I open Ubuntu it shows me 10:00 am (as I selected the region for clock), and also it sets up this clock for BIOS and my other OS.

I want to stop this and use for my other OS different clock region, when I open other OS and choose different region for clock as you predict this time the BIOS is set up this clock region and for Ubuntu's clock.

What can I do for this? Is there a way to do?

- Thanks.

---

### Post by Dimarchi on 2016-06-29
Most likely there is a way to do it. It depends on what this other OS is, though. So, more info needed. As an example, I dual boot between Ubuntu (16.04) and Windows 10. Both are eager to mess up clocks - in my case Ubuntu did what it should and Windows 10 messed it up until I booted to Ubuntu again. I solved this by disabling some things in Windows and doing some registry editing. Now, Ubuntu does its stuff and Windows won't mess up the clock.

FWIW, this post is probably in the wrong forum...

---

### Post by llTheSoldierll on 2016-06-30
My other OS is also Win 10. Can you tell me too how you solved the problem on Win 10?

---

### Post by Bashing-om on 2016-06-30
llTheSoldierll; Hello;

What version of ubuntu have you installed ?.. As the procedure differs between systemd/upstart to effect the hardware clock interpretation; to make the match between how Windows/ubuntu utilize this clock. 

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by llTheSoldierll on 2016-06-30
I've installed ubuntu 16.04 LTS

---

### Post by Bashing-om on 2016-06-30
llTheSoldierll; Ho kay :

16.04 :
To check your settings:
```

timedatectl

```
To change RTC in local TZ:
```

timedatectl set-local-rtc 1

```
More info here: [http://manpages.ubuntu.com/manpages/xenial/man1/timedatectl.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/timedatectl.1.html)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Dimarchi on 2016-07-01
[This is the page]("http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html") I used as a guide to fix my issues. In short, I left Ubuntu alone, and did no modifications there. All that stuff took place in Windows 10. In other words, method B. Do make sure you can also revert the change should you need it.

---

