---
title: "CrunchBang vs Damn Small Linux vs Puppy"
date: 2011-03-20
forum: Recurring Discussions
---

### Post by linuxyogi on 2011-03-20
Hi,

Besides Ubuntu 10.10 I am using CrunchBang 10 openbox on the old Celeron computer (see my sig. ).

CrunchBang is running well but even a little multitasking is making my pc slow. For example, if I run FF alone it performs well but if I try to listen to some music using vlc or smplayer it becomes very slow.

Now, has anyone here used both CrunchBang & DSL or CrunchBang & Puppy ?

I am trying to know which one of these is the lightest & can be installed to hard drive ?

Please confine your choice within these three.

Thanks in advance.

---

### Post by TeoBigusGeekus on 2011-03-20
DSL is dead; hasn't been updated since '08 (I think).
Replace it with Slitaz.

From all the above mentioned, the lightest is an Arch linux install with Openbox stand alone (or any other feather weight window manager).
My 2 drachmas.

---

### Post by mips on 2011-03-20
^^

---

### Post by Hur Dur on 2011-03-20
Crunchbang - The only thing light about it is the window manager. It has programs that are meant for newer computers.

Puppy - Not as light as DSL, but it is actively being updated, and has a lot of programs.

DSL - Not actively developed, but it runs like a champ on 10+ year old hardware. I've heard that it flies on 32mb RAM with X.

Personally, I would go with Arch + IceWM or Openbox, or go for Slackware. Or, if you prefer the complete package, SliTaz is good.

I had the same specs on my older laptop, and there really isn't a limit to what distros you can and can not use on it. I had a pretty good experience with Linux Mint Debian on it.

Kick Firefox for something lighter. I really liked Dillo, and Netsurf, but you could always go for a more feature-rich browser, like Midori.

---

### Post by mips on 2011-03-20
> **TeoBigusGeekus said:**
> 
From all the above mentioned, the lightest is an Arch linux install with Openbox stand alone (or any other feather weight window manager).
My 2 drachmas.

For that Archbang could be an option.

---

### Post by mips on 2011-03-20
> **linuxyogi said:**
> For example, if I run FF alone it performs well but if I try to listen to some music using vlc or smplayer it becomes very slow.


FF is a hog, maybe try a different browser.

---

### Post by jerenept on 2011-03-20
> **linuxyogi said:**
> Hi,

Besides Ubuntu 10.10 I am using CrunchBang 10 openbox on the old Celeron computer (see my sig. ).

CrunchBang is running well but even a little multitasking is making my pc slow. For example, if I run FF alone it performs well but if I try to listen to some music using vlc or smplayer it becomes very slow.

Now, has anyone here used both CrunchBang & DSL or CrunchBang & Puppy ?

I am trying to know which one of these is the lightest & can be installed to hard drive ?

Please confine your choice within these three.

Thanks in advance.
Your processor is not stopping you, it seems to be the RAM. I like Puppy, SliTaz, Tiny Core. (and FreeNAS, I will never stop recommending FreeNAS and a couple big HDD's.) You might want to check out XBMC Live distro, it runs fairly well on the specs you give (provided you have a decent graphics card, mine is a GeForce 6600, and it flies.)

Also try a lighter browser. Midori, Dillo, Chromium, Epiphany, even Opera.

Try using mplayer from the command line. It's really not that much more effort than using smplayer or vlc, although you will miss a lot of features.

---

### Post by tgalati4 on 2011-03-20
Celerons have a small cache and generally don't perform as well as Pentiums for desktop use.  I agree with jerenept that freenas will run fine and provide many services without taxing the processor and celerons use much less power than Pentiums.

So although it's fun to play with these light distros, as soon as you find better hardware, you will quickly switch the Celeron to server use and then you will look at freenas.

---

### Post by andras artois on 2011-03-20
CrunchBang is definitely not light.

Go with what everyone else is saying. Arch, OpenBox, and Tint2 would be a fairly simple but still nice setup. Midori is a nice lightweight browser and PCManFM or Thunar are lightweight file managers. I think it's XMMS that's a commandline music player so should be fairly lightweight. Might be worth checking the Arch forum and searching for low spec builds.

---

### Post by linuxyogi on 2011-03-20
Presently Downloading Puppy. In case  I don't like Puppy I will try Arch.


I have used both Chromium & Opera & I like them both. I am still with FF because of its security features. In FF I have added Addons like Adblock Plus, No Script, Better Privacy.
I have no other issues about replacing FF with another browser other than security. What about security ?
**Can browsers like dillo, Chromium offer the same amount of security as FF (with all these addons)?**

I will write back about my experience with Puppy.

Thanks to all you guys.

---

### Post by jerenept on 2011-03-20
> **linuxyogi said:**
> Presently Downloading Puppy. In case  I don't like Puppy I will try Arch.


I have used both Chromium & Opera & I like them both. I am still with FF because of its security features. In FF I have added Addons like Adblock Plus, No Script, Better Privacy.
I have no other issues about replacing FF with another browser other than security. What about security ?
**Can browsers like dillo, Chromium offer the same amount of security as FF (with all these addons)?**

I will write back about my experience with Puppy.

Thanks to all you guys.

Well, there is adblock plus for Chrome/Chromium, and midori supports ad blocking OOTB (you just have to select a blocklist)
I don't think Dillo even has support for Javascript, so you should be safe there.

In all browsers that I know of, you can disable/enable JS on certain sites.

---

### Post by coolbrook on 2011-03-21
Try VectorLinux and wattOS.  I find that they both run faster than Puppy.

---

### Post by Warpnow on 2011-03-21
Puppy Linux is the only lightweight linux distribution that will not require alot of setup or configuration.

That said, if you put the time into it, a command line install of ubuntu with just like openbox installed with chromium and necessary apps, will fly.

---

### Post by johntaylor1887 on 2011-03-21
I vote for Slitaz. (the new and improved dsl, imo) Extremely lightweight and easy to work with.

---

### Post by johntaylor1887 on 2011-03-21
> **coolbrook said:**
> Try VectorLinux and wattOS.  I find that they both run faster than Puppy.

Hmmm, really? I tried vector before, but don't remember it being faster than puppy. In puppy, things open instantly. How can you get faster than that? I can't speak for wattOS.

---

### Post by linuxyogi on 2011-03-22
_Puppy_

Downloaded & burned it to a RW. Boot process went without any problem. I finally decided to install. It detected even my partitions properly but whenever I selected the (ext3) partion the installer vanished. This happened multiple times. Finally I gave up & decided to download Slitaz.

_Slitaz_

Again, the boot process went fine. But there is  a problem with Slitaz's pppoe-setup. It won't register the DNS servers, no matter if you mention them or leave  it blank to use your ISP's servers. I thought lets install it I will later google about this issue using my other computer & solve it. The installation process completed without showing any error  After installation the grub menu appeared but when I selected Slitaz it said "no such hard drive" (or similar).

Beleive it or not presently I am using Xubuntu 10.04. 

These so called light weight distros are really buggy. They seem to run only in live mode.

And yes the real reason behind my pc getting slow was FF. 

As sugested, I am using Chromium & using mplayer from the comman line & everything is fine now. 

Unless it gets better FF  will soon become history.

---

### Post by |{urse on 2011-03-22
Slitaz owns all these distros. :-({|=

---

### Post by tgalati4 on 2011-03-22
These lightweight distros tend to work better in live mode because they use "safe" defaults.  As soon as you install it, you have to configure it for your specific hardware, and that is where problems arise.

So these lightweight distros appear buggy, but they really just need a lot of tweaking to get running properly on your hardware.  Some people don't have the time or patience or skill required to make these tweaks, so they end up installing Ubuntu--which works but is slow on old hardware.

---

### Post by linuxyogi on 2011-03-22
> **tgalati4 said:**
> These lightweight distros tend to work better in live mode because they use "safe" defaults.  As soon as you install it, you have to configure it for your specific hardware, and that is where problems arise.

So these lightweight distros appear buggy, but they really just need a lot of tweaking to get running properly on your hardware.  Some people don't have the time or patience or skill required to make these tweaks, so they end up installing Ubuntu--which works but is slow on old hardware.

As I have mentioned I tried to install both Slitaz & Puppy. They just won't install or boot. The installer itself crashes in Puppy & after the installation when I select Slitaz it won't boot.

How can one tweak them if they won't install  ?

---

### Post by alexan on 2011-04-05
[http://www.kolibrios.org/](http://www.kolibrios.org/)

---

### Post by Habeouscorpus on 2011-04-05
Chromium is a kick-butt browser with many of the same privacy addons. Except Torbutton. All your old favorites like WOT, adblock, flashblock...

Dillo I don't know about.

---

### Post by linuxyogi on 2011-04-10
> **Habeouscorpus said:**
> Chromium is a kick-butt browser with many of the same privacy addons. Except Torbutton. All your old favorites like WOT, adblock, flashblock...

Dillo I don't know about.

> What about adblock plus ? Is ABP available for chromium ?

Sorry about that. What really wanted to ask was about the availability of **[COLOR="Red"]noscript[/COLOR]** for chromium.

---

### Post by Spice Weasel on 2011-04-10
Even today when it is seriously outdated, no distribution beats DSL on the features/minimum requirements ratio. TinyCore is much better but if you have under 100mb RAM you have to be careful how much you install.

---

### Post by linuxyogi on 2011-04-20
> **Habeouscorpus said:**
> Chromium is a kick-butt browser with many of the same privacy addons. Except Torbutton. All your old favorites like WOT, adblock, flashblock...

Dillo I don't know about.

> What about adblock plus ? Is ABP available for chromium ?

Sorry about that. What I really wanted to ask was about the availability of **[COLOR="Red"]noscript[/COLOR]** for chromium.

---

### Post by CurseThePhobia on 2012-08-20
try using lubuntu...it is very good for crappy pc. furthermore, your battery (if laptop) can stand longer than your actual battery  life.

---

### Post by TeamRocket1233c on 2012-08-23
You could also build up a lightweight desktop configuration from a base command-line Ubuntu install.

---

### Post by linuxyogi on 2012-08-23
> **TeamRocket1233c said:**
> You could also build up a lightweight desktop configuration from a base command-line Ubuntu install.

 Thats the best option IMO.

---

### Post by linuxyogi on 2012-08-23
The PC that I was talking about is now dead. I used this PC primarily to download files via torrents.

I am planning to buy an Intel Atom Dual Core.

---

### Post by mips on 2013-06-17
Thread necro.

Beginning to feel like the linux kernel is just getting so big. I'm about to try out a few distros like slitaz, alpine, vector, manjaro-net, dragonfly bsd because my old laptop just feels so slow (using manjaro openbox edition currently). I have 3 spare hard drives so this could be interesting.

---

