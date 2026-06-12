---
title: "Sound Flash Firefox"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by 124C41+ on 2008-04-29
Im sure you have dealt with this tonnes of times. I have googled it and have tried the following fix. 

[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

It still does not work. Suggestions?

---

### Post by 124C41+ on 2008-04-29
bump

---

### Post by mister_pink on 2008-04-29
What exactly is the issue? Is there never any sound at all? That thread is very old so likely not relavent anymore.

I suspect the problem is the known bug in flash that exists at the moment that means it cant make sound at the same time as anything else.

The easiest fix is to install libflashsupport, but I should warn you that this brings with it stability issues - some people find firefox crashes a lot when viewing flash things.

See [https://bugs.launchpad.net/bugs/192888](https://bugs.launchpad.net/bugs/192888) for the bug report.

---

### Post by 124C41+ on 2008-04-29
I already tried it and still nothing....

---

### Post by jflarm on 2008-04-29
[http://ubuntuforums.org/showthread.php?t=763664&highlight=libflash](http://ubuntuforums.org/showthread.php?t=763664&highlight=libflash)


Found this, but i think it's the same solution as the one above

---

### Post by 124C41+ on 2008-04-29
> In my setup, this problem was fixed with this:

# Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

No other changes needed.

I hope this works for other people.

Im gonna try this.

---

### Post by jflarm on 2008-04-29
looks like he is making a soft link (shortcut) to the /usr/lib/libesd.so.0 library
And he also creates a .esd directory in temp (maybe for the link he just created). The /tmp directory is emptied everytime you reboot, so I don't think this is a definitive solution, but maybe someone else has more understanding of this.

---

### Post by 124C41+ on 2008-04-29
Yeah im still stumped.... No idea. And quite frankly surprised flash sound is so hard to setup when every other sound does. Makes no sense -_-.

---

### Post by jflarm on 2008-04-29
Here's what I'd do...
1.Remove everything about flash in the Synaptic.
2.Install gnash and see if it worked.
3.If it didn't work, then remove gnash and install the non-free-flash plugin
4.If it doesn't work, remove it.
5.Go to youtube and try to play a video, and follow the instructions to install the adobe flash plugin.

---

### Post by metol on 2008-04-29
> **124C41+ said:**
> Im sure you have dealt with this tonnes of times. I have googled it and have tried the following fix. 

[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

It still does not work. Suggestions?

The following worked for me and for a few others after I posted it in another thread:

```
sudo apt-get install libflashsupport
```

From the description: [I]Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible.
[/I]

You will need to restart Firefox after installing this utility.

Regards,
Metol

Edit: After reading the rest of this post I see that you had already tried this... sorry, I should have read more carefully.

---

