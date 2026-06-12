---
title: "NO Display.... help"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by geobz on 2008-07-16
Hello, I'm very new with linux and ubuntu so i guess you'll have to bear with me.

I recently bought a UMPC, a [Redfox Wizbook 800]("http://www.redfoxtechnologies.com/wizbook800.html"), with a pre-installed linux os developed by a chinese company named neoshine. It was working fine but I didn't like the windows copycat interface; so, I decided to install Hardy on it 4 days ago.

I didn't encounter problems installing it, although i did have problems with not seeing the bottom toolbar. The first mini problem I encountered was shutting down... because well, it didn't shut down the laptop. Sure, ubuntu stopped running but it left me with a blank bright screen. I figured, I'll just need to press the power button everytime I shut down I guess.

The real problem began after I downloaded and installed the first batch of updates. I really didn't know which I should get so I decided to get 'em all. After installing, I powered down and slept. When I started it up today, I was met with a blank bright beige screen. I can hear it starting up, I saw the progress bar but after awhile it seems that the screen moves to the far left. After I blindly type my username and password I still hear the african startup music but the screen remains blank. 

I really don't want to revert to the old interface but if thats what it takes, I'll probably do that. I just hope that somebody can help me out and talk me out of it.

Thanks.

---

### Post by nothingspecial on 2008-07-16
Can you boot into safe graphics mode?

---

### Post by geobz on 2008-07-16
Update... If I allow the screen to sleep after a few minutes of inactivity and move the mousepad around, I get the desktop. Although this means all is not lost for me, doing this everytime I boot up is just unacceptable.

Hope to hear from anybody soon.

Thanks.

---

### Post by willie_wang on 2008-07-16
Because your display is moving to the far left, it sounds as though you have a problem with the correct resolution on your screen. All you display configurations reside in a file at /etc/X11/xorg.conf. The new xorg 7.3 in Ubuntu Hardy tries to autodetect your screen resolution, although sometimes it gets it wrong. 

Firstly, I'd try what this guys says in this post: [http://ubuntuforums.org/showthread.php?t=690760]("http://ubuntuforums.org/showthread.php?t=690760")

If that doesn't work, then maybe these two posts might help.

Check out: [http://bbs.archlinux.org/viewtopic.php?id=38041]("http://bbs.archlinux.org/viewtopic.php?id=38041")
Then to fix the xrandr, look at: [http://bbs.archlinux.org/viewtopic.php?pid=255048#p255048]("http://bbs.archlinux.org/viewtopic.php?pid=255048#p255048")

~ww

---

### Post by geobz on 2008-07-18
which choice is it when i hit esc?
thanks.

---

### Post by loell on 2008-07-18
if it didn't gave you problem the first time you installed it then its xorg.conf that has changed somehow probably after successive reboots or unclean shutdown? i'm not sure why the updates can change the xorg settings.

probably reinstall hardy, but this time arround back up your working xorg settings, so when its messed up you can just copy it back.

---

### Post by geobz on 2008-07-19
> **loell said:**
> if it didn't gave you problem the first time you installed it then its xorg.conf that has changed somehow probably after successive reboots or unclean shutdown? i'm not sure why the updates can change the xorg settings.

probably reinstall hardy, but this time arround back up your working xorg settings, so when its messed up you can just copy it back.

how do i do this?.... and pardon the ignorance.... what is xorg.conf?

---

### Post by RomeReactor on 2008-07-19
Hi. Have you tried willie_wang's suggestions? If you're using Hardy, it's probable that reconfiguring your display won't help, but it's worth a try.

Also, try booting into recovery mode (press ESC when Grub comes up) and choose XFIX.

EDIT: xorg.conf is a text file that contains the configuration of your display. It's located in **/etc/X11/xorg.conf**.

---

### Post by geobz on 2008-07-19
> **nothingspecial said:**
> Can you boot into safe graphics mode?

yes i can... what do i do when i get there? 
The thing i was talking about: being able to get to the desktop after a period of inactivity only seems to be possible if i login at the recovery mode.

by the way... if i login into recovery mode i get a blue screen with hints of script peeking at the left side... 

all is not lost... i hope

---

### Post by loell on 2008-07-19
> **geobz said:**
> how do i do this?.... and pardon the ignorance.... what is xorg.conf?

yeah, as already pointed out its in

> /etc/X11/xorg.conf. 

to back it up, just do 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

also, after solving your display, well eventually.

you might find [ubuntu netbook remix]("http://www.canonical.com/netbooks") interesting, its tailored for small devices like your Redfox Wizbook 800. ;)

---

### Post by geobz on 2008-07-25
Loell,

I tried your suggestion of installing netbook remix...it looks great but I think I have newer problems now as described in a [new thread]("http://ubuntuforums.org/showthread.php?p=5458413#post5458413").

---

