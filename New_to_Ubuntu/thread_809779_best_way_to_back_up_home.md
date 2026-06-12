---
title: "best way to back up /home ???"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-27
i have had ubuntu running now for 2 weeks and most eerythi gis looking pretty good over all.

so i want to bakc up my /home directory..   its 3.4 gigs large....

so i tried nautilus's ... create archive  from the menu and picked the /home/user directory and set it for a tar.gz  one hour later im think WTF my cup is going full tilt and my drive is running and nothing is done
thats a lot of time to archive only 3.4 gigs..

so i try 7ziping it..  no better
and just tar ing it  still no better,,

i can rar or zip up 4 gigs when im in windows in 45 mins tops..

what im i doing wrong here???
i tried it as a normal user and i tried it as a sudo command

i back it 2.4 gig last week and that could not have been 1/2 hour and now i waited 2 hours and its still working on 3.4 gigs..

am i asking too much?

nutz

---

### Post by Zacariaz on 2008-05-27
you may want to investigate the "dd" command:
(in console)
```
man dd
(and/or)
info coreutils &#8217;dd invocation&#8217;
```

It may be a bit advanced, but it works.

---

### Post by sayakb on 2008-05-27
Why are you even creating an archive? Just copy your /home/yourname folder to some other storage media..

---

### Post by john_markh on 2008-05-27
Check out this thread: [http://ubuntuforums.org/showthread.php?t=791431]("http://ubuntuforums.org/showthread.php?t=791431")

---

### Post by Duck2006 on 2008-05-27
Some info on the DD commands.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

---

### Post by Paqman on 2008-05-27
> **LinuxIsInnovation said:**
> Why are you even creating an archive? Just copy your /home/yourname folder to some other storage media..

I agree. Then after that just use grsync every once in a while to keep the backup up-to-date.

Compressing 3.4GB into a single archive is always going to be slow, and you'll probably only save a few hundred MB on your destination.

---

### Post by Monicker on 2008-05-27
It shouldn't take all that long.  

The quickest is probably just to go to a console and do

```
tar czvf /tmp/home.tar.gz /home/username
```


This will put the archive in /tmp.

---

### Post by Zill on 2008-05-27
SBackup (Simple Backup) works for me...
Menu: System, Administration, Simple Backup Config/Restore

---

### Post by nutpants on 2008-05-27
> **LinuxIsInnovation said:**
> Why are you even creating an archive? Just copy your /home/yourname folder to some other storage media..


mainly i want it as a compressed archive so that it is
a) smaller
b) one file
c) easy to add in sequence (ie backup1.tar backup2.tar etc)
d) its on a laptop so i want to send the archive file to my usb drive when its connected once a week, and not have to copy everything over file by file in copy mode when i connect.


i am guessing by the answers that 2hours back up time is not uncommon, for 3.4 gigs.. by useing xarchive or nautilus

nutz

---

### Post by Paqman on 2008-05-27
> **nutpants said:**
> 
i am guessing by the answers that 2hours back up time is not uncommon, for 3.4 gigs.

On really old hardware maybe.

---

### Post by nutpants on 2008-05-27
> **Paqman said:**
> On really old hardware maybe.

its a dell xps m1210 laptop

Intel Core Duo Processor T2500 (2GHz/667MHz FSB/2MB Cache)
2GB (667MHz DDR2 SDRAM)
120GB @ 5400 RPM  hard drive


so i would not say it is either old or slow,, but no its not spanking new.

nutz

---

