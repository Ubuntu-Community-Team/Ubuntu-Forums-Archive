---
title: "Hardware demands"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by Elect GMax on 2013-01-05
As I've stated before, this Windows computer is running the cheapest, crappiest Atom that Intel ever made. When supplemented by a discrete nVidia graphics card, it's good enough to run Minecraft at minimum settings and playable, though far from ideal, framerates. I expected it to be capable of similar or better performance when using the allegedly leaner, more efficient Linux... but actual results were much, much worse. At first, I was puzzled, but then I realized something:

This computer runs Windows XP. The only Win7 system that I've ever owned ran much more slowly on much better hardware. XP was made way back in 2001 for the hardware that existed at the time. Windows 7 and Ubuntu 12.04 were both made a decade later, for hardware that exists now. Pangolin might be faster than Windows 7, but XP? I have my doubts.

So here's my question: How does Pangolin's use of system resources compare to that of Windows XP and Windows 7?

---

### Post by 2F4U on 2013-01-05
In my experience, 12.04 uses more resources than Windows XP, but less than Windows 7. Of course there are ways to tweak 12.04 to use less resources, but these are limited.
I have very good experiences by using LXDE or XFCE on limited hardware similar to yours, so you could try Lubuntu or Xubuntu and see if it runs better.

---

### Post by Impavidus on 2013-01-05
> **2F4U said:**
> In my experience, 12.04 uses more resources than Windows XP, ...
Not if you include the resources used by the virus scanner ;).

To the OP: Have you made sure you've installed the proprietary nvidia drivers? It could help.

---

### Post by Elect GMax on 2013-01-06
What are LXDE and XFCE?

I wasn't running a virus-scanner.

Yes, I installed nVidia's drivers.

---

### Post by ibjsb4 on 2013-01-06
> **Elect GMax said:**
> What are LXDE and XFCE?

[http://xubuntu.org/](http://xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by mastablasta on 2013-01-06
they are different desktop environemnts that are less ahrdware demanding. xFEC will need about 120 MB on idle. LXDE will need a bit less RAM. if you use debian or arch linux (more demanding) you can knock this down even further.  they also do not need so much graphics power which leaves it more for the GPU and games. then again they might not look so good.

you can also go even lower in Ubuntu. i think Bodhi linux (ubuntu based) uses E17 which has even lower sytsem requirements. then you have windows manager such as openbox or icewm which will need even less power. for example icewm looks kind of like widnows 98 but with modern porgrammes.

let's not even start with various other linux options (sllitaz, DSL, tinycore, puppy) that run on 16 MB ram....

---

### Post by tlhIngan on 2013-01-06
You need to understand that newer doesn't mean better or faster.
The trend in Microsoft Windows since Vista has been to favour appearance and bling at the expense of performance. Vista, 7 and 8 need huge hardware, and I'm sorry to say Ubuntu has been following suit.
The recommendations above regarding Lubuntu and Xubuntu are very good. I myself am running Lubuntu 12.04, and you can see the technical specs of my dinosaur (hardware dates back to 2003) below, in my signature. The lighter interface does make a huge difference.

---

### Post by mysteriousdarren on 2013-01-07
I would recommend Lubuntu 12.10 or 12.04 as that is what is running on my Acer Aspire One. After a few tweaks, adding Jupiter and other enhancements runs like a charm. Upgrade your RAM to the max 2GB generally helps alot on netbooks.

---

### Post by Calinou on 2013-01-07
> **Elect GMax said:**
> As I've stated before, this Windows computer is running the cheapest, crappiest Atom that Intel ever made. When supplemented by a discrete nVidia graphics card, it's good enough to run Minecraft at minimum settings and playable, though far from ideal, framerates. I expected it to be capable of similar or better performance when using the allegedly leaner, more efficient Linux... but actual results were much, much worse. At first, I was puzzled, but then I realized something:

This computer runs Windows XP. The only Win7 system that I've ever owned ran much more slowly on much better hardware. XP was made way back in 2001 for the hardware that existed at the time. Windows 7 and Ubuntu 12.04 were both made a decade later, for hardware that exists now. Pangolin might be faster than Windows 7, but XP? I have my doubts.

So here's my question: How does Pangolin's use of system resources compare to that of Windows XP and Windows 7?

First: use Xfce then disable its desktop effects ("compositing").
Second: install proprietary drivers if any. Note that Intel's IGP drivers are open source, but the driver is still slower than the Windows driver and only supports OpenGL 3.0.

"When supplemented by a discrete nVidia graphics card"
Optimus is not officially supported on Linux (read: "next time, buy a desktop, which is cheaper and much faster"), but you can use Bumblebee instead which is an unofficial open source implementation (again, you are expected to know how to search on the forums or using search engines, before asking how to install it here).

Always remember, when you're trying a new OS: think in a different way. Ubuntu is not a clone of Windows.

edit: if you want a free and open source alternative to Minecraft which runs well on older computers, try Minetest: [http://minetest.net](http://minetest.net)

---

### Post by Elect GMax on 2013-01-07
> **ibjsb4 said:**
> [http://xubuntu.org/](http://xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

Cool.

Is there any way to just get the lighter GUIs without having to download a whole new image file?

> **tlhIngan said:**
> You need to understand that newer doesn't mean better or faster.
The trend in Microsoft Windows since Vista has been to favour appearance  and bling at the expense of performance. Vista, 7 and 8 need huge  hardware

[IMG]http://colincosell.com/wp-content/uploads/2010/01/omg.jpg[/IMG]

I'd argue that this has been the trend since they first jumped from 3.11 to 95, but whatever.

> **mysteriousdarren said:**
> Upgrade your RAM to the max 2GB generally helps alot on netbooks.

I've already upgraded my RAM to the max, which in this case is only 1 GB. You see, the Intel BOXD945GCLF motherboard has only a single DIMM slot for DDR2-533 memory, and DDR2-533 DIMMs were never made in sizes larger than 1GB as far as I can tell.

Also, I have never owned and never plan to own a netbook.

> **Calinou said:**
> Optimus is not officially supported on Linux

wat?

> **Calinou said:**
> (read: "next time, buy a desktop, which is cheaper and much faster")

Incorrect. They're cheaper and faster if you build them yourself.

Buy... lol :rolleyes:

> **Calinou said:**
> but you can use Bumblebee instead

wat?

---

### Post by Calinou on 2013-01-07
> **Elect GMax said:**
> Cool.

Is there any way to just get the lighter GUIs without having to download a whole new image file?

```
sudo apt-get install xubuntu-desktop
```

Log out, choose Xfce by clicking on Ubuntu logo then log in.


> **Elect GMax said:**
> Incorrect. They're cheaper and faster if you build them yourself.

Erm, by "buy" I meant "build", sorry. 8)

---

### Post by ibjsb4 on 2013-01-07
> **Calinou said:**
> ```
sudo apt-get install xubuntu-desktop
```Log out, choose Xfce by clicking on Ubuntu logo then log in.

For less bloat you could:

```
sudo apt-get install lxde
```or

```
sudo apt-get install xfce
```And choose at login.  But in my opinion a fresh install is best.  Or with the full L/Xubuntu desktop:

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

---

### Post by Elect GMax on 2013-01-10
Okay then. When the Darkmoon Faire is over and I have time to work on this stuff, I'll try that and let you know what the results are.

---

