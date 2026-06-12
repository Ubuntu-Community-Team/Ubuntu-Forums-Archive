---
title: "How to permanently disable slow keys?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-06-10
Its a real big problem for me now. Just one hour before I lost all my simulations running on my computer. Accidently slow keys turns itself on and I am able to see all new features of ubuntu. First realized that keys are not working, so I guessed correctly that slows keys are turned on, then it took a hell lot of pressure on keyboard to reach to disable slow keys, but then I don't know what I thought I didn't turned off the slow keys but reduced its delay to the minimum. So now what, I am getting two letters on one hit of a key and even more, when I pressed alt+F4 to close the window, I am in tty4, so I just pressed alt+F7 to go into gdm. But this is not it, when I pressed Backspace to delete some characters I AM LOGGED OUT. All my simulations are gone. I don't know what to do. Please help me so that I can get rid of this nasty creature on ubuntu called "SLOW KEYS" permanently. Thanx very much in advance.

---

### Post by lazyart on 2008-06-10
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/31720](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/31720)

> > Is there any way to have Slow Keys deactivated completely?
I had the popup constantly too.
There is a simple way: Activate it and set it to 0 milliseconds.

---

### Post by _sphinx_ on 2008-06-10
But that what I did, I started getting 2 characters on one hit. And moreover I had been constantly watching launchpad for this slow key "feature" but no help. It's still a bug. I just posted here just because, in case anyone has a better solution then it would be GREAT help for me.

---

### Post by _sphinx_ on 2008-06-10
By the way can anybody tell me why do we have the slow key feature AT ALL in an Operating System.

---

### Post by tent405 on 2012-09-14
For a more up-to-date discussion on this topic, you can look here: 
[https://bugs.freedesktop.org/show_bug.cgi?id=52611](https://bugs.freedesktop.org/show_bug.cgi?id=52611)

For a quick fix, try installing a different window manager. (I'm going to try switching from gdm3 to lightdm .. lightdm on ubuntu 12.04 definitely does not display this behavior)

_solution:_
```
sudo apt-get remove gdm*
sudo apt-get install lightdm
sudo init 6
```

---

### Post by overdrank on 2012-09-14
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

