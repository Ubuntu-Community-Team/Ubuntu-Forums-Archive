---
title: "Which release is will use my hardware to best advantage?"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by megenk11 on 2013-05-06
I have 1GB sdram + 82.3GB hdd + 250GB hdd, as well as NvidiaGeForce2 graphics card + IDE CD/DVD-RW, Intel Pentium 4, USB 2.0, webcam in a PC Dell Optiplex GX240.

I cling to the latest version (12.10 at the time), then found the mini.iso installation method that let me try multiple distros, window and display managers, shells, docks and I have finally realized that I need to find the version of Ubuntu that is meant to run on this older hardware. Eye candy will never replace the ability to do stuff fast or do lots of stuff. I have a 10 GB song collection in need of a refiling method and it must wait on flash stick for a flexible, strong , integrated system. 

I am hoping to hear from experience before going ahead. I have 12.04 mini.iso burned, md5sumed and ready; 13.04 offers upgrades on my tty´s. I am running xubuntu with Cairo-dock now but must turn off most toys as it feels like processing in a vat of molasses.

I like xfce if I get no docks, lxde with any dock and I usually prefer the Muon software centers applications so I am hoping a mini.iso is available of the version that you recommend.

Please offer your advice, I am using my computer for pleasure whilst cancer does whatever and Linux/Ubuntu has been a valuable and attention riveting asset.

Thanks, Megenk

---

### Post by ajgreeny on 2013-05-06
I suggest xubuntu would be the best compromise of speed with configurability.  Lubuntu will also work very well, but will need more manual text file editing for some of its configuration, whereas xubuntu has GUIs for almost everything.

I have moved from Ubuntu 10.04 to Xubuntu 12.04, as I can not get on with unity, and I find XFCE 4.10, which is available from a ppa, extremely good, fast and the ideal alternative to gnome 2.

---

### Post by DuckHook on 2013-05-06
You have a very old machine that will only run very lean OSes, but your experimentation has already told you this. I recommend that you try a full version of Lubuntu on LiveDVD before making the plunge to install. In your case, it is not so much to see what Lubuntu is all about as to see what speed it runs at. The problem with mini.iso is that we cannot tell how many dependencies your experimentations dragged in such that it deviates from a clean Lubuntu install. If you tried running an Ubuntu desktop prior to Lubuntu, then it is possible that your system is running resource sapping services like compiz and thus tainting the leanness of Lubuntu. Docks can be added to any install, but it should be noted that they take up system resources that could be better used by actual apps. It is usually better to use hotkeys than docks on resource-limited systems.

Hope that you surmount all of your health challenges.

---

### Post by sudodus on 2013-05-06
I think you should try also Lubuntu (because it has an ultra-light foot-print, while xubuntu has a light foot-print).

- from a live desktop iso file (the clean way) or

- installing LXDE ```
sudo apt-get install lxde
``` or

- installing the whole lubuntu-desktop ```
sudo apt-get install lubuntu-desktop
```

After trying, you can select your sweet point in the trade-off between speed and eye-candy. And of course, you can run a mixture of the two flavours. I run such a mixture in one computer (Lubuntu with xubuntu-desktop).

If you need extra speed and efficient use of RAM, there is plain Openbox window manager as a log in option in Lubuntu (or lubuntu-desktop). Right-click on the grey background to get a terminal window or browser.

---

### Post by Yellow Pasque on 2013-05-06
> I am running xubuntu with Cairo-dock now but must turn off most toys as it feels like processing in a vat of molasses. I like xfce if I get no docks
I'm guessing the graphics are really holding you back there. Have you tried turning compositing off? (Settings -> Window Manager Tweaks -> Compositor).

> I usually prefer the Muon
Have you tried Synaptic? I've found it to be faster and it's pretty similar.

---

### Post by slickymaster on 2013-05-06
There are actually two lightweight distros based on Ubuntu, namely Lubuntu and Xubuntu, but personally I prefer Xubuntu not only for its aesthetics but also because of its simplicity and customizability. XFCE is infinitely customizable and because of its focus on simplicity, it is incredibly responsive and fast as well.

One thing that goes against Lubuntu, in my mind, is its bland looks, but of course that's always a matter of personal taste.

---

### Post by matt_symes on 2013-05-06
Hi

> Please offer your advice, I am using my computer for pleasure whilst  cancer does whatever and Linux/Ubuntu has been a valuable and attention  riveting asset.

I hope you get better soon.

Enlightenment is another lightweight window manager you may like.

```
sudo apt-get install "e17*"
```

Kind regards

---

### Post by DuckHook on 2013-05-06
> **slickymaster said:**
> There are actually two lightweight distros based on Ubuntu, namely Lubuntu and Xubuntu,

@OP

Very true if one prefers to stay within the official family (lot to be said for that). However, if one is prepared to step outside, then there is [Bodhi Linux]("http://bodhilinux.com/") and [CrunchBang]("http://crunchbang.org/"), both of which are based on and therefore use the Ubuntu repos (you will be able to install anything from official Ubuntu repos). These are even leaner than Xubuntu or Lubuntu. CrunchBang has the added advantage/disadvantage of using the older 2.6.x kernel so it is often more compatible with older HW, but less compatible with bleeding edge stuff.

> One thing that goes against Lubuntu, in my mind, is its bland looks...

It is bland. You can spiffy it up with wallpapers and add-ons but that sort of defeats the purpose of running it in the first place.

> **matt_symes said:**
> Enlightenment is another lightweight window manager you may like.

@OP

Enlightenment is the default Bodhi desktop. If going the Enlightenment route, I would encourage you to give Bodhi a spin.

CrunchBang has the most minimalist interface of all. Users tend to either love it or hate it. No way to tell how you will like it except to try it.

---

### Post by Cheesemill on 2013-05-06
> **DuckHook said:**
> However, if one is prepared to step outside, then there is [Bodhi Linux]("http://bodhilinux.com/") and [CrunchBang]("http://crunchbang.org/"), both of which are based on and therefore use the Ubuntu repos (you will be able to install anything from official Ubuntu repos).

This hasn't been the case for a while now. Crunchbang *used* to be based on Ubuntu but switched to Debian about 3 years ago.

It's still a great recommendation, it's my go-to distro for low spec machines.

---

### Post by DuckHook on 2013-05-06
> **Cheesemill said:**
> This hasn't been the case for a while now. Crunchbang *used* to be based on Ubuntu but switched to Debian about 3 years ago.

Thanks for clarification, Cheesemill. I was misled by (in my case) the fact that I can use the same mirror site for both, and apt downloads the same apps.

@OP

Since Ubuntu is also based on Debian, CrunchBang won't feel too foreign to you. Many similarities from sudo to apt to location of configuration files--I rather think that you will still feel right at home.

---

### Post by megenk11 on 2013-05-17
> Duck hook, my gratitude, I had shyly wanted to try crunchbang, I have run Bohdi and E17 and they are just a toe over the line between beautiful and fast (They are too pretty and slow)
> Temujin, I researched the Compiz settings greediness and know it's "Animations, Window fades, Decorations off and Textures set to FAST" for me. But even though I much prefer command line to Gui, Synaptic has been WAY over my  head, so I'll read the info before I give it another go.
Thank you, > Sudodus, for your advice, there seems to be XFdesktop too, but the mini.iso seemed to clean out my box as it repartitioned. Please explain whether the live CD/DVD clears the way for itself. I like the cli minimalism of the mini.iso, in fact I haven't even tried a regular full install!
> Cheesemill, thanks to you I have actually found a blank DVD and so I'll put off precise 12.04 'till after I download, burn, md5sum and roll around in crunchbang for a good feel. I will let you know how the Dell performs.
> slickymaster, I agree with you and now have Xubuntu and xfce 12.04. They are great as my base system and now I have to remove the login choices of unity and unity 2D
Does anyone know how to pare down the log in menu?
Thank you all for helping a newbie, and the day after you answered, my liver was found to be riddled with tumors so maybe a long project to work on whilst recovering from the chop shop. Ideas? Thanks again, Megenk11

---

### Post by sudodus on 2013-05-17
> **megenk11 said:**
> ...
Thank you, , for your advice, there seems to be XFdesktop too, but the mini.iso seemed to clean out my box as it repartitioned. Please explain whether the live CD/DVD clears the way for itself. I like the cli minimalism of the mini.iso, in fact I haven't even tried a regular full install!

When you use a full install (this is the case for the standard desktop iso and the alternate iso) you can control the installation selecting '***Something else***' or '***Manual partitioning***', when you arrive at the partioning page during the installation.

It will be particularly clear if you prepare for it before the installation. So I suggest that you use ***Gparted*** (when booted from the Xubuntu install CD).

But editing partitions and installing operating systems are risky operations, so please make a ***backup*** before you start. Backup at least your personal files (documents, pictures etc)!
> 
Thank you all for helping a newbie, and the day after you answered, my liver was found to be riddled with tumors so maybe a long project to work on whilst recovering from the chop shop. Ideas? Thanks again, Megenk11
I wish you good luck at the 'chop shop' :-)

---

### Post by slickymaster on 2013-05-17
> **sudodus said:**
> When you use a full install (this is the case for the standard desktop iso and the alternate iso) you can control the installation selecting '***Something else***' or '***Manual partitioning***', when you arrive at the partioning page during the installation.

It will be particularly clear if you prepare for it before the installation. So I suggest that you use ***Gparted*** (when booted from the Xubuntu install CD).

But editing partitions and installing operating systems are risky operations, so please make a ***backup*** before you start. Backup at least your personal files (documents, pictures etc)!

I wish you good luck at the 'chop shop' :-)

That's pretty much it, with a big emphasis on the backups before you start doing it.

All the luck in the world for the next phase coming in to your life. My thoughts and positive thinking are with you.

---

### Post by richierich1986 on 2013-05-17
I would definitely recommend ChrunchBang Linux for hardware that old. 
I have an old laptop with 1gb ram and a single core 1,6Ghz CPU and it
runs perfectly on it. Quick, base system uses only about 260MB of ram,
so enough room to run some programs.

---

