---
title: "FGLRX fullscreen artefacts"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by vivek27389 on 2012-10-23
Last week I installed Ubuntu 12.04.1 LTS 64 Bit on my DELL Studio 1555 laptop. Everything seemed to work perfectly out of the box, including wifi and bluetooth. 3d acceleration, however was quite slow using the open source radeon drivers. So I installed the catalyst driver and 3d acceleration was working just fine. But when I play youtube videos in fullscreen or run any opengl application in fullscreen I get a couple of artefacts on the screen. Also it gets worse when I use the volume keys. These applications however work fine in windowed mode. Here is the link to the video that describes the problem. 
[https://www.youtube.com/watch?v=xah0wU-Yb2c&feature=plcp](https://www.youtube.com/watch?v=xah0wU-Yb2c&feature=plcp)

My system specs are:
Intel Core 2 Duo @ 2.1 Ghz
4 GB DDR2 RAM
ATI Mobility RadeonHD 4570 512MB

---

### Post by vivek27389 on 2012-10-23
It's not a compiz related issue since I have the same problem in gnome shell. The open source driver works fine, but 3d is lagging. Can anyone please help me?:cry:

---

### Post by mag1strate on 2012-10-23
The new gnome shell is known to be still unstable with proprietary AMD Drivers, especially on certain chipsets. The best option I can give you is to stay on the open source ones until fixes are created.

---

### Post by Mark Phelps on 2012-10-24
I've been told that AMD dropped Linux driver support for the HD 2x/3x/4x series cards this summer.  That explains why the latest Catalyst driver that works with my HD 4290 is v12.6 -- even though AMD is now up to v12.11.

So, if you're waiting for NEW drivers, you can quit waiting -- there aren't going to be any.

---

### Post by QIII on 2012-10-24
From QQ forward, you'll need the Catalyst 12.9 "Ubuntu preview Beta" or better because of X Server 1.13 and forward.  To use the legacy cards, you'll have to use the legacy driver and downgrade to X Server 1.12.

I used to support ATI, but this whole situation is a slap in the face of the Linux community.  The HD 4000 series is still on store shelves and in currently sold laptops, for Pete's sake!

---

### Post by NikTh on 2012-10-24
> **QIII said:**
> From QQ forward, you'll need the Catalyst 12.9 "Ubuntu preview Beta" or better because of X Server 1.13 and forward.  To use the legacy cards, you'll have to use the legacy driver and downgrade to X Server 1.12. 

There is a repository created for this . Look here: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
Of course any user should use it at his/her **own risk.**

> **QIII said:**
> I used to support ATI, but this whole situation is a slap in the face of the Linux community.  The HD 4000 series is still on store shelves and in currently sold laptops, for Pete's sake!
Agreed :)

---

### Post by QIII on 2012-10-24
I've seen a couple of PPAs with packages to do all the work, and I appreciate the hard work people have done.  But it shouldn't have been necessary for them to.

This is simply mindboggling.  The fact that their hardware is so good makes the driver situation all the more frustrating.

---

### Post by vivek27389 on 2012-10-24
Thanks for all your replies. By the way, the ppa provided by NikTh is only for quantal. I prefer using the LTS release. I would also like to mention that when I downgraded fglrx to version 11.11, flash started to work fine but I'm still having trouble with opengl applications. They all work fine in windowed mode. What's the deal with fullscreen mode?

---

### Post by NikTh on 2012-10-24
> **vivek27389 said:**
>  By the way, the ppa provided by NikTh is only for quantal. I prefer using the LTS release.

Yes that was a little OffTopic conversation for the ATI's/AMD's behavior :P  

This not affects you for now , but as you are using an LTS release (as I do) you will be affected in near future when the Xorg updates to 1.13. Then the fglrx driver (proprietary) will not work and you will need some of these repositories (I assume until then , support for precise has been added as well) to install the fglrx legacy drivers. 

Your problem seems a graphics driver problem , I will suggest (as already said) to use the open source driver (radeon) and try to pass a "high" key performance and test it. 

```
sudo -i
echo high >  /sys/class/drm/card0/device/power_profile 
exit
```Above code is valid **only** with open source driver .. (and not for sure) and also keep an eye in temperatures when you pass this key. 

Thanks

---

### Post by Mark Phelps on 2012-10-25
> **QIII said:**
> I used to support ATI, but this whole situation is a slap in the face of the Linux community.  The HD 4000 series is still on store shelves and in currently sold laptops, for Pete's sake!

Strongly agree -- now, more than ever.  I had an ATI X1650 -- which they stopped supporting when AMD bought them.  I built a new PC, this one with an onboard HD 4290 -- and now, they've stopped supporting that!

At least the open-source Radeon driver still works for 12.10 with my video chiset -- but I don't know if AMD deserves any credit for that or not!

---

### Post by vivek27389 on 2013-05-15
Hi everyone, it's been a while since I've replied to this thread. I've been trying to get the proprietary drivers to work for weeks now. Finally I decided to stick with the open source drivers and they seem to work quite well. Power management however, is still a problem. My gpu heats up to 85 degrees celsius in just 2-3 minutes. Are there any tweaks that I could use to lower the temperature?

---

### Post by Mark Phelps on 2013-05-15
All I can suggest is that you try Jupiter:  [http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html]("http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html")

---

