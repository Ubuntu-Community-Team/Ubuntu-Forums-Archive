---
title: "Can I run unity on one computer,  the rest of ubuntu on another?"
date: 2016-02-22
forum: New to Ubuntu
---

### Post by david494 on 2016-02-22
I'm hoping I can run the gui on one machine, and the underlying file system, cpu, etc on another.

I just installed the desktop version (14.04) on one machine, but I think I'm going to use it headless most of the time.  I have ssh set up, so could always get in that way, but would prefer to have the gui option too.  Both would be on the same network - 192.168.1.x

Unfortunately it's physically located in an inconvenient place to hook up a monitor.

I'm new to ubuntu, have used linux in the past, and am comfortable with the cli.

---

### Post by newbie-user on 2016-02-22
Use xrdp or vnc to remotely log into a gui.

---

### Post by david494 on 2016-02-24
Thanks, I'll look into those. Looks like Google has an app too

---

### Post by gordintoronto on 2016-02-25
If you're running headless, you might as well use Xubuntu.

---

### Post by david494 on 2016-02-25
> **gordintoronto said:**
> If you're running headless, you might as well use Xubuntu.

Ok, but does that help with my question or is it just a suggestion? I'm new to this, but do understand that xubuntu uses xfce which is lighter than unity.  I've already installed ubuntu 14.04 on the machine, which has plenty of ram/storage - 4gb/64gb.

-david

---

### Post by newbie-user on 2016-02-25
You can still install xfce after. Up to you what desktop environment you want to log into. Either way, you still need to install a VNC server or RDP server on the Ubuntu box.

---

### Post by QIII on 2016-02-25
If you want a much faster protocol, I might suggest NoMachine NX.  It's no longer open source, but it is free (as in beer) for personal use.  NX is far and away more efficient than VNC or RDP protocols.  NoMachine also has inbuilt public/private key-based encryption end to end.

It has progressed to the point where you can almost (...almost...) run hi-def video over it.

---

### Post by newbie-user on 2016-02-26
> **QIII said:**
> If you want a much faster protocol, I might suggest NoMachine NX.  It's no longer open source, but it is free (as in beer) for personal use.  NX is far and away more efficient than VNC or RDP protocols.  NoMachine also has inbuilt public/private key-based encryption end to end.

It has progressed to the point where you can almost (...almost...) run hi-def video over it.

Thanks for the tip!

---

### Post by david494 on 2016-02-26
> **QIII said:**
> If you want a much faster protocol, I might suggest NoMachine NX.  It's no longer open source, but it is free (as in beer) for personal use.  NX is far and away more efficient than VNC or RDP protocols.  NoMachine also has inbuilt public/private key-based encryption end to end.

It has progressed to the point where you can almost (...almost...) run hi-def video over it.

Thanks!  I had this up and running in 5 minutes, I couldn't believe it.  I still need to put the correct security measures in place, however.

---

### Post by raman07 on 2016-02-27
> **QIII said:**
> If you want a much faster protocol, I might suggest NoMachine NX.  It's no longer open source, but it is free (as in beer) for personal use.  NX is far and away more efficient than VNC or RDP protocols.  NoMachine also has inbuilt public/private key-based encryption end to end.

It has progressed to the point where you can almost (...almost...) run hi-def video over it.

I failed to make it work in ubuntu 14.04 :( 
Please give me any website link with instruction or guide

Edited : Oh it was easy to setup NoMachine :) I did it
PS : I think x2go is better than NoMachine.

---

### Post by raman07 on 2016-02-27
@david494 How did you make it work with ubuntu 14.04? Any website you follow?

---

### Post by david494 on 2016-02-27
[https://www.nomachine.com/getting-started-with-nomachine](https://www.nomachine.com/getting-started-with-nomachine)

For the "2nd" computer I downloaded the App from the Play store

---

