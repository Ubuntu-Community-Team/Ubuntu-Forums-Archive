---
title: "Ubuntu LTS 18.04 does not resume from suspend"
date: 2019-08-23
forum: New to Ubuntu
---

### Post by mas192 on 2019-08-23
Hi All,

I am having a issue where when I suspend my machine, all the current work get lost when I resume. Also while I try to resume, the system asks my password first then the screen black out and then asks password again. 
Once it login in, all my previous work (files, browser) do not restore.

Please help me fix this. 

Thanks,
mas192

---

### Post by CatKiller on 2019-08-23
You haven't described a resume from suspend problem, you've described a crashing display server problem.

---

### Post by mas192 on 2019-08-26
Oh I see thanks CatKiller, How do I trouble shoot this problem?

---

### Post by CatKiller on 2019-08-26
You could say what hardware you're using, and whether you're using a proprietary driver or not.

If you're using X, the log file will be /var/log/Xorg.0.log; I have no idea about Wayland. You can see kernel messages with dmesg or look at /var/log/kern.log. You might see useful information there about something you could change to stop it crashing, or it might simply log the fact that it's crashed. 

Both AMD and Nvidia have had bugfixes for displays crashing on resume fairly recently. You could just not suspend for a while until those fixes trickle down into the software you're using.

---

### Post by mas192 on 2019-08-26
At Catkiller, I am using a msi with i7 8750 with nividia 1050, I am running nvidia drivers on it. 

Below is the content of the Xorg server log.  Could you help me decipher the log.

I hope the driver trickles down quickly. 

Here is my log, [https://paste.ubuntu.com/p/B8PMxpBmx6/](https://paste.ubuntu.com/p/B8PMxpBmx6/)
The forum didn't allow me to put it here or attach it.

---

### Post by CatKiller on 2019-08-27
> **mas192 said:**
> Below is the content of the Xorg server log.  Could you help me decipher the log.

Not really. I can't see anything there that's indicative of a crash.

---

### Post by mas192 on 2019-08-28
Awe, that is a bummer, any other place I can check for the trouble maker?

---

### Post by mas192 on 2019-08-30
I have more info,
 
I have attached the image of the error, I get when I awake the screen. Do this is could help us trouble shoot?

---

### Post by CatKiller on 2019-08-30
That error is about your WiFi, which has historically had some trouble resuming from suspend, but I don't think it's related to the problem you're having.

---

### Post by rbmorse on 2019-08-30
I don't know if this will help, or not, but it doesn't cost anything to try.  After the machine fails to resume from suspend enter the following keys:

```
<ctrl>+<alt>+<F3> 
``` which means hold down both the <ctrl> and <alt> keys, then press the <F3> key.  Release all three. That should bring you to another login screen.  Don't log in, rather,  enter the following keys:

```
 <ctrl>+<alt>+<F2> 
```

All this exercise does is force a reset of the display server, but it may be all you need.

---

### Post by mas192 on 2019-08-30
Oh Awesome, I will give this a shot and keep you posted. Thanks so much!!!

---

### Post by mas192 on 2019-09-03
Hi CatKiller,

Sorry that did not work. I hope there is something else we could try?

---

### Post by mas192 on 2019-09-20
Hi Catkiller, I reinstalled ubuntu, and that fixed it. Thanks so much for troubleshooting with me!!!

---

