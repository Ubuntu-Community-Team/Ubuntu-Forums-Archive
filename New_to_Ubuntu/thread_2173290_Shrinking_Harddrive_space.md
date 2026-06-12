---
title: "Shrinking Harddrive space"
date: 2013-09-08
forum: New to Ubuntu
---

### Post by jdedeaux on 2013-09-08
So, I'm running 12.04 on my HP dv6. After some obvious web searching and tweaking. This thing runs amazing! Only issue I am having is a threw my 60gig SSD in it because all I do is browse the web. After installing Ubuntu when i right click in my home folder and go to properties , yesterday it said I had 30 gigs avail (30 out 55ish) i think nothing of it as im sure there are partitions made for something some where but 15ish gigs? hmm....all ive done the past two days is browsed the web, installed a theme or two and now im down to only 20 gigs avail... strange!

i've installed and ran bleachbit and that hasn't done much so im at a loss here as to of where my hdd space is going.


im a windows user so im used to emptying temp or looking up in windirstat - but im new to ubuntu!

any help would be appreciated!

---

### Post by Bucky Ball on 2013-09-08
Be VERY careful with Bleachbit, in fact, for a newcomer I'd advise against and say 'get rid of it'. It is generally unecessary for most users and more 'Windows think'.

Open Gparted (partition manager) and take a look in there. Perhaps post a screenshot of it here so we can all see.

---

### Post by Bucky Ball on 2013-09-08
Be VERY careful with Bleachbit, in fact, for a newcomer I'd advise against and say 'get rid of it'. It is generally unecessary for most users and more 'Windows think'.

Open Gparted (partition manager) and take a look in there. Perhaps post a screenshot of it here so we can all see.

Please advise which release of Ubuntu you are using and how you installed: did you let Ubuntu partition things or do it manually?

---

### Post by jdedeaux on 2013-09-08
got rid of bleachbit! im on 12.04 and I just selected my SSD and let the installer do its thing. I installed via booting from USB - downloading gparted now will post screenshot in a sec

---

### Post by jdedeaux on 2013-09-08
[IMG]http://i41.tinypic.com/wkhdf4.png[/IMG]having an SSd is nice but it is only 60  gb.... i thought i could get away with it. I may have to throw my 640gb that came with the laptop back in it and re install if it eats up space like that... none the less here is my gparted ss!

---

### Post by Bucky Ball on 2013-09-08
All good. No need for the extended partition, really. Unsure why Ubuntu 12.04 is taking up that much room, though. I don't use it (minimal install with xfce4 desktop environment) but can't imagine it has grown that much. See this:

> 5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach) 

From here:

[https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition](https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition)

What is taking up all the space with this install is indeed an anomoly. Is this a fresh install with no Apps added?

PS: Despite the debate, you really don't need more than 2Gb /swap unless you are hibernating regularly with your full complement of RAM packed full o' data.

PPS: I have NEVER installed Ubuntu on anything more than 15Gb and a fresh install has never come close to filling that (I always use a separate /home partition, not directory, for personal data). 

I have an Xubuntu 12.04 install on another partition which is jammed with apps and stuff (my experimental plaything, or one of them) and that is around 13.5Gb. Have you by any chance dumped any personal data into the /home directory on your fresh / install?

---

### Post by Bashing-om on 2013-09-09
jdedeaux; Hi !
Another consideration is the log files running amuck, reporting an error - a million times over.
The following command is useful for finding out which directories are using all your space...
```
 du -h --max-depth=1 | sort -hr
```
As I see nothing alarming from the GParted screenshot.

And Welcome to ubuntu ! in general and the forum in particular.

[INDENT][INDENT]open source, we are all in this together 
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-09-09
> **Bashing-om said:**
> 
Another consideration is the log files running amuck, reporting an error - a million times over.

This. Good point, bashing-om.

---

### Post by jdedeaux on 2013-09-09
I could slap myself! I found it and why it was shrinking over days. DROP FREAKING BOX! I forgot I installed dropbox and drop box actually downloads the files locally rather than just accessing them when you install the dropbox desktop manager. So in other words, roughly 20gigs of data has installed over the past two days, slowly LOL!


WOW...

running that script you mentioned is how i figured it out!

---

### Post by Bucky Ball on 2013-09-09
Nice one! If solved to your satisfaction, to help others, please mark solved from Thread Tools at top right. Only when you're ready, o' course. ;)

---

