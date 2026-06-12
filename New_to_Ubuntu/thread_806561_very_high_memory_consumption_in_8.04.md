---
title: "very high memory consumption in 8.04"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by ans5685 on 2008-05-25
Hi although I am new to Linux, 8.04 is the third Ubuntu release I am using
but what puts me off is the insane level of memory it is using.
Just gnome panel uses 80+ MB !!!!!!!
And running Firefox with just 4 tabs open takes up 150+ MB even with DOWNTHEMALL (my only add on) disabled!!!!!
I know that running Compiz-Fusion has a severe memory penalty and so does AWN but I ran those two in the previous release too without many issues.

The performance hit is so much that running Azureus results in 400 MB+ swap space being used and just changing themes make Rythmbox skip (am trying to change over to mp3blaster ).

Please don't tell me to turn CF off 'coz I really use Scale  a lot and I like the Cube desktop as is the case with AWN.

Is there anything else that I can do ????????
Please help.
And thanks in advance.

---

### Post by sayakb on 2008-05-25
Wow, even in my case, Gnome panel uses 44MB memory! And some python processes (either panel applets or screenlets) consume about 20MB each (ie. 20x8 =160 MB by just python processes!) So my 2GB memory is more than 50% utilized. God, this is even higher than the resource hog Vista!!

---

### Post by Inxsible on 2008-05-25
try```
killall gnome-panel
```Gnome Panel should never take 80 MB. Try killing all instances. it should auto start again.

---

### Post by Inxsible on 2008-05-25
> **LinuxIsInnovation said:**
> Wow, even in my case, Gnome panel uses 44MB memory! And some python processes (either panel applets or screenlets) consume about 20MB each (ie. 20x8 =160 MB by just python processes!) So my 2GB memory is more than 50% utilized. God, this is even higher than the resource hog Vista!!That is really strange. I used Ubuntu and the max it took was 300 MB without starting any apps except Compiz and AWN

---

### Post by ans5685 on 2008-05-25
> **Inxsible said:**
> try```
killall gnome-panel
```Gnome Panel should never take 80 MB. Try killing all instances. it should auto start again.
Thank you Inxsible
Kill all did bring it down from 84 to 22 MB
but in the meantime my swap consumption wint up from 0 to 156 MB :(
Is there any more permanent solution to this problem?

---

### Post by skymera on 2008-05-25
Wow that is strange, all my times i check out my memory statistics, not as radical as that.

Personally they need to sort out Gnome.

Im intriuged by this, so treat this as a nice bump i guess.

---

### Post by misfitpierce on 2008-05-25
Yeah Gnome-Panel can go into the 40 range of MB's especially if you logged on for really long time and have applets all along it. I have never hit over 50 even logged on for a week straight on Ubuntu 8.04. So i'm not sure why you hit 80 something lol :)

---

### Post by hyper_ch on 2008-05-25
don't run azuerus

---

### Post by housam on 2008-05-25
If you are running a 64 bit distro , read [[COLOR="Red"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=794854")

---

### Post by philinux on 2008-05-25
Linux uses memory very differently to windows. The top few paragraphs explain.

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by ans5685 on 2008-05-25
> **philinux said:**
> Linux uses memory very differently to windows. The top few paragraphs explain.

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)
I am using a 64 bit Hardy
But the other thread still doesn't explain the astronomical amount in gnome panel
yes guys it's back at 84.1 MB!!!!!!!
Thats 8 more than Xorg at 76
and 3 times that of compiz.real at 28
only kazehakase with 104 takes more but it is running 8 tabs now.

I heed help.

---

### Post by hyper_ch on 2008-05-25
post:

```

free -m

```

---

### Post by misfitpierce on 2008-05-25
Honestly mine has never gone over 500MB that I have seen running like 8+ diff apps at once including Opera and more. Though it's not to say that I care very much because with 2.9GB swap and a gig of ram I doubt i'll ever fill it so I dont really watch my ram count anymore because I trust that on Ubuntu i'll be fine as I always have :)

---

### Post by philinux on 2008-05-25
[http://ubuntuforums.org/showthread.php?t=472305](http://ubuntuforums.org/showthread.php?t=472305)

However my system monitor shows gnome panel like this for me.

Resident  Shared
27.2      14.9

---

### Post by ans5685 on 2008-05-25
> **hyper_ch said:**
> post:

```

free -m

```
ans@ans-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           752        741         10          0         16        196
-/+ buffers/cache:        528        223
Swap:         1027        300        726


The applications that I am running are Kazehakase,mp3blaster.

---

### Post by cb951303 on 2008-05-25
my gnome-panel uses 20.3 mb

---

### Post by hyper_ch on 2008-05-25
using [noparse]```

```[/noparse] makes text more readable ;)
but for just kazehahkase and mp3blaster it seems much....

---

### Post by brunolabs on 2008-05-25
Mine is always in the 400MB - 600MB zone.

---

### Post by skymera on 2008-05-25
Im very rarely above 300MB.
I have 
-Ubuntu itself
-Compiz Fusion
-Firefox - 4Tabs - lots of addons
-Pidgin
-2 terminals
- and Rhythmbox

Im at 274MB RAM with 0MB Swap.

---

### Post by sayakb on 2008-05-25
Yeah.. my uptime goes above 2-3 weeks usually. Killing the gnome panel reduces it to 20s. The worst part is that even the smallest of the clock or calendar screenlets eat 15-20 MB of memory :( Plus, restarting them using the screenlets daemon does no wonders. Anyway, looks like rebooting reduced the memory usage to 800MB (for my laptop having a 2gb RAM) and 650MB for another one having a 1GB RAM :)

---

### Post by markbuntu on 2008-05-25
firefox is the big pig here, followed distantly by rythmbox and python.
The more tabs open in firefox, the more ram it uses. even with one tab it is up to 178mb and climbing... when the toal ram use hits about 1.1gb firefox causes kernel panic and I have to push the panic button. This is with 3gb ram. Swap is never used.

---

