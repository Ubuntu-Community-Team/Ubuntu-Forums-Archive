---
title: "Firefox-isn't responding (must close existing instance)"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by Holy bible on 2011-11-12
Hi everybody. Nowadays Im annoyed with really bad pop-up message which tells that firefox is not responding. So step by step. It started maybe 2 weeks ago. And what it does is when I boot ubuntu everything is normal, I just click i up panel firefox and it starts with saved tabs. !BUT!. when i exit it...(left up red X), i dont use it approx. for 30 minutes, and i want to go on the net again, it shows something like  "another instance of your firefox is running already. Close it or wait until it close itself" i really dont know exactly what the message writes but in necessary case i will rewrite it. So i must go to system monitor: find firefox-bin and stop process. thats everything.. and what i want is to NOT do this annoying process...  If anyone knows what is the problem ill be happy to accept your help. ThankS

---

### Post by Holy bible on 2011-11-12
Oh well and the problem may be in router, because i bought router maybe in 2 weeks but i really dont know why will the router have some touch on the firefox in ubuntu. But if this helps, yea i bought router.

---

### Post by lovinglinux on 2011-11-12
Which version of Firefox you are using?

Please try Firefox in safe mode and test if the problem persists.

```
firefox -safe-mode
```

Instead of opening the System Monitor, you can easily kill firefox from a terminal:

```
killall firefox-bin
```

---

### Post by Holy bible on 2011-11-12
lol. How on earth can this works? :D im using 3.6.24 but the save mode i think solved it :D but i still cant understand how does this save mode works and how this solved it. :P problem is solved but i got question in my head now :D can you explain it please? ill be very pleased if you do that

---

### Post by lovinglinux on 2011-11-12
> **Holy bible said:**
> lol. How on earth can this works? :D im using 3.6.24 but the save mode i think solved it :D but i still cant understand how does this save mode works and how this solved it. :P problem is solved but i got question in my head now :D can you explain it please? ill be very pleased if you do that

The safe mode doesn't solve your problem. It is just a way to test if an extension, theme or plugin is causing the problem, because it disables everything temporarily. The fact that it works, confirms that. Must be an extension or a plugin. Try disabling flash plugin or the Global Menu extension to see if the problem persists. Again, this is only to find the culprit, not to solve the problem. Don't use the safe mode anymore.

BTW, I would recommend getting Firefox 7. See [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247).

---

### Post by Holy bible on 2011-11-12
omg. now it do it again. it hadn't solved the problem. i will try the firefox 7 and this maybe resolve problem.... btw. maybe in 1 week i downloaded NoScript add-on so this may be the breakpoint. ill try uninstall it or whatever and inform you

---

