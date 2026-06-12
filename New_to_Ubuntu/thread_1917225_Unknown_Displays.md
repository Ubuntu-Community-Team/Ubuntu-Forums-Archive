---
title: "Unknown Displays"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by bear29ht on 2012-01-29
I connected a monitor to my laptop so I could use that as my screen, but whenever I try to go to display settings, it says that there is only one display, "unknown" which is my laptop.  This is weird, because when I use my live cd, it works just fine.  I don't know how to edit the sudo nvidia settings, if that has anything to do with it. I attached mp4 video so you may see what it looks like.  Thank you

---

### Post by rgreener25 on 2012-01-29
Have you tried pressing detect displays once it is plugged in

---

### Post by bear29ht on 2012-01-30
> **rgreener25 said:**
> Have you tried pressing  displays once it is plugged in
Yes I have, and it doesn't change anything.

---

### Post by bear29ht on 2012-03-08
Can  anyone help me here?

---

### Post by kevdog on 2012-03-08
Id guess xorg problme.

---

### Post by theducksfan2010 on 2012-03-08
Is there any way to successfully run dual monitors in Ubuntu with a NIVIDIA Geforce video card?

---

### Post by bear29ht on 2012-03-08
Yes, I saw the exact problem on another thread, but he fixed it himself in the xorg file.  He didn't tell what he did though.

---

### Post by bear29ht on 2012-03-08
> **theducksfan2010 said:**
> Is there any way to successfully run dual monitors in Ubuntu with a NIVIDIA Geforce video card?
I don't want to run dual monitors, I want to change the monitor from the laptop to an external one.

---

### Post by grahammechanical on 2012-03-08
First of all, because you have Nvidia then you may need to activate the Nvidia driver. If you have already done this then the Displays utility in System Settings become inactive because the Nvidia settings utility takes over. That is why it is saying Unknown. 

Try detect displays in the Nvidia X-server Settings utility. Do not forget when you installed and when you activated the Nvidia driver the OS only saw the laptop screen. It now needs to be told that there is another screen available. It needs a configuration for this new screen.

Regards.

---

### Post by bear29ht on 2012-03-10
Thanks so much, that was the most helpful reply yet.  Anyway, how exactly do I get the configuration in the settings to override the x-server.   I looked in the x-server configuration, and I can't figure out how to make the other monitor the only display.  Is there some button that I'm not seeing?  Thanks in advance.

---

