---
title: "Hardware Drivers -- cant install drivers, i guess?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Thespacegoat on 2008-11-29
Hello everyone.

Let me start by saying. I'm completely new to linux. In fact, I started earlier today. i've been working and tinkering around with it,but there is one thing that is consistently evading me. 

Ubuntu has let me know that i cant use advanced graphic settings without enabling this NVIDIA accelerated graphics driver (version 177) or (version 173). well thats all fine and dandy, and i'd love to comply and get on with it, but when i click the "Activate" button: error.

but what error? 

I couldn't tell you if i wanted too! theres no error number, no details, just a just the error button. All i get is the error symbol (red circle with the white bar in it)


any suggestions? I would really love to get past this problem. 

Some information:

1. I'm using a GeForce 8800 GO (or something.) the standard card, as far as i know
2. I run ubuntu off a portable hard drive. 

im not sure if thats usefull information.

 Any suggestions would be greatly appreciated!

---

### Post by ugm6hr on 2008-11-29
Not sure what version of Ubuntu you are using, but if you want the latest 3D drivers, I'd suggest using Envy:
```
sudo apt-get install envyng-gtk
```

More info: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by decoherence on 2008-11-29
If you haven't run Update Manager yet, I suggest you do that before trying anything else. I believe you'll find it under the System > Administration menu. What you describe sounds like a bug -- perhaps it's fixed in an update? Run the update, reboot if it asks you, then try again.

If Update Manager says you're up to date even after you click the "Check" button and installing the driver still doesn't work, then go ahead and install envy as in the above post.

The only problem with envy is that it's not official and has been known to cause issues for some users in the past when trying to upgrade. They may have that better sorted out these days, tho.

---

### Post by ugm6hr on 2008-11-29
> **decoherence said:**
> The only problem with envy is that it's not official and has been known to cause issues for some users in the past when trying to upgrade. They may have that better sorted out these days, tho.

It's in the universe repo now - so not Canonical "official" - but community supportedso the update issue is no longer a problem.

---

### Post by tomtom1982 on 2008-11-29
Well, I think you´re using Ubuntu 8.10 (nvidia-glx-173 is available in inteprid restricted sources), so all you have to do is:

Open a console

sudo apt-get install nvidia-glx-173

---

