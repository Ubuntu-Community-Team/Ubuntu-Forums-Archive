---
title: "Mouse won't move"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by philmacdonald2 on 2012-02-24
Hi, for no apparent reason to me my mouse won't move at all. I'm running Ubuntu 11.10 on a desktop and the mouse is connected on one of the old PS/2 green port mice. I've tried disconnecting and reconnecting the mouse, starting up withoput the mouse plugged in and then adding it, and just booting with the mouse in the port, all to no avail.

I can get to terminal, so I should be able to fix this, I just don't know how.

---

### Post by HeroOfCanton on 2012-02-24
Just in case, have you tried another mouse?

---

### Post by philmacdonald2 on 2012-02-24
> **HeroOfCanton said:**
> Just in case, have you tried another mouse?
No, but I have tried the mouse in a different computer and it worked. It also works fine on the Win Vista OS (it's a dual boot machine).

Mouse does work, its something wrong inside Ubuntu.

---

### Post by roelforg on 2012-02-24
> **philmacdonald2 said:**
> No, but I have tried the mouse in a different computer and it worked. It also works fine on the Win Vista OS (it's a dual boot machine).

Mouse does work, its something wrong inside Ubuntu.
I'm gonna advise temp. hanging an USB-mouse to the pc so it'll be usable.

---

### Post by philmacdonald2 on 2012-02-24
> **roelforg said:**
> I'm gonna advise temp. hanging an USB-mouse to the pc so it'll be usable.
Yes, that is a temporary solution. But I was wondering how I can get Ubuntu to see the PS/2 port to make the other mouse work. It did work on Ubuntu before, it just doesn't seem to work after I ran sudo apt-get update.

---

### Post by roelforg on 2012-02-24
> **philmacdonald2 said:**
> Yes, that is a temporary solution. But I was wondering how I can get Ubuntu to see the PS/2 port to make the other mouse work. It did work on Ubuntu before, it just doesn't seem to work after I ran sudo apt-get update.
What version are you using?
(Mine seems fine with my PS/2 mouse)

---

### Post by philmacdonald2 on 2012-02-24
> **roelforg said:**
> What version are you using?
(Mine seems fine with my PS/2 mouse)
Running Ubuntu 11.10. 
It did work for a while. It's just stopped after that update and hasn't worked since... 
It seems like ubuntu can't detect that it is there. The little trackball thing (red light where the mouse detects movement - can't think of the name) doesn't light up anymore. Not sure exactly why, or how to fix it.

---

### Post by MG&amp;TL on 2012-02-24
> **philmacdonald2 said:**
> The little trackball thing (red light where the mouse detects movement - can't think of the name) doesn't light up anymore. Not sure exactly why, or how to fix it.

Interesting...if you mean an infrared mouse, one of these : **[mouse]("http://www.google.com/imgres?q=infrared+mouse&um=1&hl=en&sa=N&biw=1280&bih=891&tbm=isch&tbnid=A7nzLlTRFfmwvM:&imgrefurl=http://hacknmod.com/hack/convert-an-optical-mouse-to-hand-held-scanner/&docid=lXVSqGi7OxKVdM&imgurl=http://farm3.static.flickr.com/2053/2455729846_d5f70f0d2c.jpg&w=495&h=372&ei=8s9HT52YMdPb8gPq6qirDg&zoom=1")**

the light going off means there's no power. If you and I didn't know better, I would definitely say the mouse has had it.

---

### Post by philmacdonald2 on 2012-02-24
> **MG&TL said:**
> Interesting...if you mean an infrared mouse, one of these : **[mouse]("http://www.google.com/imgres?q=infrared+mouse&um=1&hl=en&sa=N&biw=1280&bih=891&tbm=isch&tbnid=A7nzLlTRFfmwvM:&imgrefurl=http://hacknmod.com/hack/convert-an-optical-mouse-to-hand-held-scanner/&docid=lXVSqGi7OxKVdM&imgurl=http://farm3.static.flickr.com/2053/2455729846_d5f70f0d2c.jpg&w=495&h=372&ei=8s9HT52YMdPb8gPq6qirDg&zoom=1")**

the light going off means there's no power. If you and I didn't know better, I would definitely say the mouse has had it.
Yeah, thats the mouse I mean. 
However if I boot Vista, the red bit lights up. And it works. So I don't think it's the mouse.

---

### Post by HeroOfCanton on 2012-02-24
If it's working elsewhere it's not a bad mouse. No matter how much it sounds like one.

If someone would just invent a teleporter already I would send you a PS/2 to USB converter to test. :grin:

I read on another forum post that was really out of date (so no link) that someone managed to get it working by disabling the USB mouse and keyboard in BIOS. Worth a shot maybe?

---

### Post by HeroOfCanton on 2012-02-24
One more older tip I stumbled on was to unload and reload the mouse module. Hopefully it's still relevant. Try dropping to terminal and typing the following:

```
rmmod psmouse ; modprobe psmouse
```

---

### Post by philmacdonald2 on 2012-02-25
> disabling the USB mouse and keyboard in BIOS.  Any suggestions  which one to disable? None of them seem relevant. [http://flic.kr/p/bkikQ3](http://flic.kr/p/bkikQ3)

Also, when I type the command ```
rmmod psmouse ; modprobe psmouse
``` I get the error ```
ERROR: Module psmouse does not exist in /proc/modules
FATAL: Could not load /lib/modules/3.0.0.16-generic/modules.dep: No such file or directory
```Does that maybe mean that the config file for the mouse is completely missing?

---

### Post by philmacdonald2 on 2012-02-25
Bump

---

### Post by MG&amp;TL on 2012-02-26
That is weird. What kernel are you using (I guess it could be using the wrong kernel)

```
uname -a
```

---

### Post by philmacdonald2 on 2012-02-26
> **MG&TL said:**
> That is weird. What kernel are you using (I guess it could be using the wrong kernel)

```
uname -a
```
it says:
```
linux phillip-Aspire-M3641 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i386 GNU/Linux
```

Seems like a fairly recent kernel. Maybe I need to update again? It might sort itself out then.

---

### Post by MG&amp;TL on 2012-02-26
> **philmacdonald2 said:**
> it says:
```
linux phillip-Aspire-M3641 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i386 GNU/Linux
```

Seems like a fairly recent kernel. Maybe I need to update again? It might sort itself out then.

No, the kernel is the right version, I was thinking it was trying to read a config file for a kernel that didn't exist, or wasn't the right one...but it seems not.

output of:

```
ls /lib/modules/3.0.0.16-generic/
```

I know you probably did this anyway-but it should be:

```
sudo modprobe psmouse
```

What happens with this?

---

### Post by philmacdonald2 on 2012-02-26
Yeah, I typed the modprobe psmouse command like that. Just to check, I typed it again, but the same error was returned.

The output of ls /lib/modules/3.0.0.16-generic/ is very odd:
```
ls: cannot access /lib/modules/3.0.0.16-generic/: No such file or directory
```

This seems to be hinting there are no modules there at all. Which is probably rather bad, and could explain a few things... :shock:

---

### Post by MG&amp;TL on 2012-02-26
No idea if it would work or not, but you could try reinstalling the kernel and rebooting. Somehow something must have deleted that file, it's there on my machine.

---

### Post by philmacdonald2 on 2012-02-27
Oh, okay then. My question is how do I reinstall the kernel without networking? (no modules, no network card detection or function...)

---

### Post by MG&amp;TL on 2012-02-27
> **philmacdonald2 said:**
> Oh, okay then. My question is how do I reinstall the kernel without networking? (no modules, no network card detection or function...)

...you can't, really. You *can* download the package from the ubuntu repos on a connected machine, but you might have problems with dependencies. (I don't know which package supplies /lib/kernelversion/modules.dep...) and that assumes you have a connected machine.

You can also download a tarball from kernel.org, then build your own, but not recommended, and you can't report bugs. My suggestion would be to backup and reinstall. No idea how that file got deleted...

---

### Post by philmacdonald2 on 2012-02-27
> **MG&TL said:**
> ...you can't, really. You *can* download the package from the ubuntu repos on a connected machine, but you might have problems with dependencies. (I don't know which package supplies /lib/kernelversion/modules.dep...) and that assumes you have a connected machine.

You can also download a tarball from kernel.org, then build your own, but not recommended, and you can't report bugs. My suggestion would be to backup and reinstall. No idea how that file got deleted...
Your guess is as good as mine as to how it was deleted. Maybe the update deleted it but never added another file... I haven't got a clue. Considering I already have a problem with dependencies, downloading the modules.dep only may make the problem even worse, especially because if I'm honest, I wouldn't know what I was doing.

I don't think it's a good idea to go down a route with no support, so I'll stick to the normal kernels. However, I've noticed a "Update Ubuntu 11.10 to 11.10" option in the install. Would that reinstall the OS without losing my data? I really don't want to start again... I'll have to set up all the samba and java configs, and that took me quite a while.

I don't know, it seems like that would work, but what do you think?

---

### Post by MG&amp;TL on 2012-02-27
> **philmacdonald2 said:**
> Your guess is as good as mine as to how it was deleted. Maybe the update deleted it but never added another file... I haven't got a clue. Considering I already have a problem with dependencies, downloading the modules.dep only may make the problem even worse, especially because if I'm honest, I wouldn't know what I was doing.

I don't think it's a good idea to go down a route with no support, so I'll stick to the normal kernels. However, I've noticed a "Update Ubuntu 11.10 to 11.10" option in the install. Would that reinstall the OS without losing my data? I really don't want to start again... I'll have to set up all the samba and java configs, and that took me quite a while.

I don't know, it seems like that would work, but what do you think?

Give it a go. Is the mouse working in the live environment? My guess it that it keeps configs and user data, but reinstalls the system.

---

### Post by philmacdonald2 on 2012-02-27
> **MG&TL said:**
> Give it a go. Is the mouse working in the live environment? My guess it that it keeps configs and user data, but reinstalls the system.
Yeah, the mouse works in the live enviroment. I'll give it a go and see what happens.

**EDIT:** Installing now, will inform to see if it works afterwards.

---

### Post by philmacdonald2 on 2012-03-31
Thanks for all your help, turns out on the first install I installed with a corrupted ISO file, meaning things weren't installed correctly. I have reinstalled with a new, stable ISO, and everything seems to be running smoothly.

Thank you for all your time and relpies :)

---

### Post by adeii on 2012-08-24
> **philmacdonald2 said:**
>  ```
modprobe psmouse
``` 
Thank you, it worked in my case.
(Power loss at upgrading u11.04 to u11.10)

---

