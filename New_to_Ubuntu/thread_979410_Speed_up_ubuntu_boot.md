---
title: "Speed up ubuntu boot"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-11
no problem here

So I just upgraded my pc to AMD Phenom 9850 x4 processor and 4gb ram
I was expecting my boot time to jump from what it was down really really low
So ended up installing intrepid over agin, as the upgraded 8.04 to 8.10 got mad and now every thing works well...

So useing a tool called bootchart (in the repos) i saw my new boot time was 21 seconds not to bad hey not bad at all on my amd 3500+ it took a min

But now i wanna try to speed it up more ;)
So in reading i found a "hack" in Debian in the the /etc/init.d/rc script
i changed CONCURRENCY=none to CONCURRENCY=shell
and i shave 2 seconds off my boot time :)

going to read more and Try to cheep track of the changes i make here

all comments are welcome 
except for the ones on my spelling
sorry if the thread is in the wrong spot

---

### Post by Tatty on 2008-11-12
Keep an eye on the concurrency setting.  I remember a while ago reading about a possible problem it can sometimes cause where differing speeds of the separate boot threads can cause some things to not load sequentially and the boot can fail.

I know nothing more about this though, Its just something i remember so I thought I would mention it incase you happen to stumble into this problem.

19 second boot is scary fast btw... well done!

---

### Post by simtaalo on 2008-11-12
these two links *may* help

[http://ubuntuforums.org/showthread.php?t=938771](http://ubuntuforums.org/showthread.php?t=938771)
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/)

---

### Post by eternalnewbee on 2008-11-12
Also, you can disable some Applications which are selected to start by default. You can check this under **Main Menu > System > Administration > Services**

---

### Post by igknighted on 2008-11-12
I'd be careful discussing this in beginner talk, many of the tweaks you are talking about (such as disabling services from starting) are the types of things that only those who understand what they are doing should be messing with.  The last thing we want is for someone who has slow boot times (likely because of the normal driver issues), but no idea what they are doing on Ubuntu to start turning stuff off.

That said, there was an article the other day about some guys (i believe intel devs?) who got Fedora to boot to an idle desktop (not login screen) in 5 seconds.  And there was room for some more if you really wanted to push.  If you really invest the time, linux can very comfortably be made to boot in a fraction of the time Ubuntu now boots, with little to no loss of functionality.

link: [http://lwn.net/Articles/299483/](http://lwn.net/Articles/299483/)

---

### Post by cariboo on 2008-11-12
There is a pretty cool tool called sysv-rc-conf that allows you to start and stop services, but before using it you really better know what all the services do. I tried it a couple of weeks ago and maanged to speed up my boot by another couple of seconds.

Have a look here for more info:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Until I searched for something on sysv-rc-conf I didn't realize this thread was here. I was reading Apress's Beging Ubuntu Server Administration From Novice To Professional when I came upon this tool.

Jim

---

### Post by eternalnewbee on 2008-11-12
> I'd be careful discussing this in beginner talk, many of the tweaks you are talking about (such as **disabling services from starting**) are the types of things that only those who understand what they are doing should be messing with. The last thing we want is for someone who has slow boot times (likely because of the normal driver issues), but no idea what they are doing on Ubuntu to start turning stuff off.
Agreed. I was thinking about for example bluetooth, if you don't use it, you don't need to waste resources (however little that is of course).

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-12
thanks for all the input guys
i have had bluetooth disabled for some time
my 19 second boot is not really my doing its just the hardware

---

