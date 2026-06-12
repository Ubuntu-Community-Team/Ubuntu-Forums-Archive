---
title: "How do I install and run Jupiter properly?"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by migmeister on 2012-02-13
Hello Ubu-forum! 

My problem is I'm running Ubu 11.10  on dual boot and I noticed that the battery consumption is quite heavy when using Ubuntu. I noticed the fan is more active compared to using Windows7, but that's probably because the hardware settings is configured for it and doesn't support Linux. 

So I searched for solutions and found Jupiter app. It's suppose to allow me to configure hardware settings so I can optimize my power usage, right? 

I followed the instructions from the webupd8, and believed I've installed it properly as it appears in the startup applications.

However, I don't see the lightning bolt icon on my systray nor do I know how to open it/use it.

Did I installed it right or am I missing something here?

Please help, thanks! ;)

(ps: I'm using Alienware m11x r3;i7 8gb - if thats relevant)

---

### Post by wolfen69 on 2012-02-13
I think I had to open it first, then reboot for it to appear on my panel. Hit the window key and start typing jupiter. You will see it appear. Open it and see what happens.

---

### Post by migmeister on 2012-02-14
I did that. Nothing happens. Any ideas?

---

### Post by migmeister on 2012-02-14
bump

---

### Post by fuduntu on 2012-02-15
Sounds like it didn't get whitelisted.

Follow this: [http://www.fewt.com/2011/03/whitelist-utility-script-to-allow-apps.html](http://www.fewt.com/2011/03/whitelist-utility-script-to-allow-apps.html)

Whitelist Jupiter.

---

### Post by migmeister on 2012-02-16
Thanks I'll try it out :D

---

### Post by Paqman on 2012-02-16
> **fuduntu said:**
> 
Whitelist Jupiter.

This. Non-standard panel doodads need to be whitelisted before they'll appear. Is Jupiter supposed to whitelist itself fuduntu? Because I had to give my machine a prod to do it as well.

---

### Post by fuduntu on 2012-02-16
> **Paqman said:**
> This. Non-standard panel doodads need to be whitelisted before they'll appear. Is Jupiter supposed to whitelist itself fuduntu? Because I had to give my machine a prod to do it as well.

I thought the package whitelisted itself, but I'm not responsible for building the Jupiter package in webupd8s PPA so I can't say for certain.

---

