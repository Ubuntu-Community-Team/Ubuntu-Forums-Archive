---
title: "Setting up a chroot for 11.10 partition from 10.10"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by repkam09 on 2011-09-21
Hey Folks,

I recently installed Ubuntu 11.10 as a dual-boot with my normal Ubuntu 10.10 so I could play with it and try it out. I already have a basic chroot setup so that I can run programs and update the 11.10 partition. (Such as fixing the networking bug that appeared recently.)

How would I go about setting up Xnest (or similar) so that I could get the full unity-2d from 11.10 running alongside my normal 10.10? Additionally, how do I go about starting up a unity-2d session from the command line in the first place...

Is there a way I can have 10.10 running on one screen ("Ctrl-Alt-F7") while 11.10 is running in a chroot, with the x server pointing to another screen? ("Ctrl-Alt-F8")

I'm not quite sure what the "Ctrl-Alt-F7/F9" are called exactly.

Of course I could just re-boot the system and use the other OS, but this just seems like a really useful thing to be able to do if it is not too difficult.

Thanks!

---

### Post by lucazade on 2011-09-21
> **repkam09 said:**
> Hey Folks,

I recently installed Ubuntu 11.10 as a dual-boot with my normal Ubuntu 10.10 so I could play with it and try it out. I already have a basic chroot setup so that I can run programs and update the 11.10 partition. (Such as fixing the networking bug that appeared recently.)

How would I go about setting up Xnest (or similar) so that I could get the full unity-2d from 11.10 running alongside my normal 10.10? Additionally, how do I go about starting up a unity-2d session from the command line in the first place...

Is there a way I can have 10.10 running on one screen ("Ctrl-Alt-F7") while 11.10 is running in a chroot, with the x server pointing to another screen? ("Ctrl-Alt-F8")

I'm not quite sure what the "Ctrl-Alt-F7/F9" are called exactly.

Of course I could just re-boot the system and use the other OS, but this just seems like a really useful thing to be able to do if it is not too difficult.

Thanks!

to start ubuntu 2d session use this:
gnome-session --session=ubuntu-2d

for the rest I can't help, never tried myself

---

### Post by xebian on 2011-09-21
> **repkam09 said:**
> Hey Folks,

I recently installed Ubuntu 11.10 as a dual-boot with my normal Ubuntu 10.10 so I could play with it and try it out. I already have a basic chroot setup so that I can run programs and update the 11.10 partition. (Such as fixing the networking bug that appeared recently.)

How would I go about setting up Xnest (or similar) so that I could get the full unity-2d from 11.10 running alongside my normal 10.10? Additionally, how do I go about starting up a unity-2d session from the command line in the first place...

Is there a way I can have 10.10 running on one screen ("Ctrl-Alt-F7") while 11.10 is running in a chroot, with the x server pointing to another screen? ("Ctrl-Alt-F8")

I'm not quite sure what the "Ctrl-Alt-F7/F9" are called exactly.

Of course I could just re-boot the system and use the other OS, but this just seems like a really useful thing to be able to do if it is not too difficult.

Thanks!

A virtualbox setup is what you need

---

### Post by ranch hand on 2011-09-21
I have never even heard of xnest before reading this post.  How interesting it is.

I agree with Torvalds that virtualization is evil.  You are not running on real hardware.  This would do that.

Not at all sure, after very brief study, that what you propose is possible however.

You would, at least, need xnest installed on both OS'.  Probably need the same package on both to make them as similar as possible.  The difference in xserver versions may be a deal breaker.

I am going to look into this further but it will have to wait for a while.

I did find these interesting links;
general info
[http://en.wikipedia.org/wiki/Xnest](http://en.wikipedia.org/wiki/Xnest)

man page (if you do not have it)
[http://www.xfree86.org/4.2.0/Xnest.1.html](http://www.xfree86.org/4.2.0/Xnest.1.html)

howto for the intended usage
[http://box.matto.nl/xnest.html](http://box.matto.nl/xnest.html)

I will be watching this thread to see how you get on with this.  Perhaps that last link will give some hints on how to get it to work in a chroot.

The first link may too, at least if it has external links (I have not looked at it at all really).

Refining my search to include chroot gives, with no study of the sites at all;
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
which deals with a display in chroot

[http://www.gelato.unsw.edu.au/IA64wiki/XinChroot](http://www.gelato.unsw.edu.au/IA64wiki/XinChroot)
which supposed to deal with remote sessions
"One fairly nice way to get a remote gnome session with a minimum of fuss is to use **Xnest**."

Good luck, report back.  Have FUN.

---

### Post by ranch hand on 2011-09-21
Reading the man page link indicates that this will work in some manner.

Says it works best if client and server are on the same network, or better yet on the same box.

I have a project running on Boinc from World Community Grid that is about to end.  I have run this from the first time I fired up Boinc.  I really intend to get 2 years crunching time in on it.  Can't afford to fool around more than a few minutes a day doing anything that will demand cpu cycles.

Will reach that goal before the end of the month though and will be playing with this as a priority item.

Thanks for the boost.

---

### Post by repkam09 on 2011-09-22
Well, this has been an interesting experiment so far. When trying to view 11.10 from 10.10 I get piles of d-bus errors when I try to start up unity-2d (using: gnome-session --session=ubuntu-2d)

However, just because, I decided to try going the other way. I booted into 11.10 and tried going into 10.10 instead.

Using [Xephyr]("http://www.freedesktop.org/wiki/Software/Xephyr") (similar to Xnest) and the following script it actually worked surprisingly well!

```

#!/bin/bash
sudo mount -o bind /proc /mnt/other/proc
sudo cp /etc/resolv.conf /mnt/other/etc/resolv.conf
Xephyr -ac -screen 800x600 :1 &
sudo chroot --userspec=mark /mnt/other

```

The above script simply mounts the proper locations, adds network access in the chroot ([link]("https://help.ubuntu.com/community/BasicChroot#Setting-up_the_chroot")) and starts up a Xephyr session to view the UI of the chroot system. I was originally logging in as root (not using the --userspec) but decided to try logging in as myself. Partly to see if I could, and partly to minimize potential damage...

Now that I was in a terminal chroot for my 10.10 system, I could simply use:
```
export DISPLAY=localhost:1
gnome-session &

```

Which tells the display for the chroot to the Xephyr window I was running on the host and then to start the normal gnome session.

Most things seemed to work okay. I did notice that the 10.10 chroot appears to be using the 3.0.0-11 kernel of the host. Which is not surprising, but I would have thought it would cause more issues.

Some images: (Not shown inline due to size)
Desktop - [(Link)]("http://i.imgur.com/Tmk8n.jpg")

Running applications - [(Link)]("http://i.imgur.com/4a82i.jpg")

I am not that experienced of a Linux user so I am quite pleased that I got this far. And I learned a lot about using chroot! Now to get it to working going from 10.10 to 11.10 like I originally wanted...

---

### Post by lucazade on 2011-09-22
really cool! compliments.
going to bookmark this post :)

---

### Post by repkam09 on 2011-09-22
I'm glad someone else finds it interesting! Going to take a bit more research and learning on my part to see exactly what the limits of this are.

If any more experienced people see any obvious dangers of doing this, let me know.

---

### Post by ranch hand on 2011-09-22
I do not see any real danger inherent in doing this at all.

I do have a question.  Are you installed on just one partition?  I am on two and can see how there could be some problems if working through a chroot, at least as I set it up.

There are only about 6 cpu days left for my goal on my boinc unit.  This will probably take about 2.5 real days.

I will be looking at this Xepher as soon as I post this.  I have heard about it at sometime but know nothing about it.

This thread is really interesting.  Keep it coming.

If you are linked to the X stack on another installation you are going to be running that installation in the window that shows it.  Therefore you will be using that installs OS.  Any other way to do it would be a problem.  You are basically just running a remote session on the other OS.

Thanks again.

---

