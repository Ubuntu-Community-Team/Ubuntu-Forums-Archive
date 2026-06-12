---
title: "Best e17 Distro"
date: 2008-02-05
forum: Other OS Talk
---

### Post by myusername on 2008-02-05
i want a good looking fast desktop with e17 or whatever its called (perferably with a package manager)

i have looked at elive gem 1.0, opengeu, ozOS, gOS and Elbuntu and i was wondering which you would think would be best on an old pentium 3 550mhz 512 ram 8mb video

or if you know of any better e17 distros please let me know...


thanks

---

### Post by agim on 2008-02-05
Have you tried any of these? I am interested in trying openGeu. I tried the geubuntu-desktop upgrade, but it didn't work out so well. Let me know.

---

### Post by RAV TUX on 2008-02-05
> **myusername said:**
> i want a good looking fast desktop with e17 or whatever its called (perferably with a package manager)

i have looked at elive gem 1.0, opengeu, ozOS, gOS and Elbuntu and i was wondering which you would think would be best on an old pentium 3 550mhz 512 ram 8mb video

or if you know of any better e17 distros please let me know...


thanksYou'll find more e17 distros listed at the [UEOSC]("http://cafelinux.org/ueosc/") website.

---

### Post by smartboyathome on 2008-02-05
I would say Ubuntu minimal + OzOS makes a great and extensive OS. :)

---

### Post by molom on 2008-02-05
The Maryan Linux beta should be out this month. It uses the Linux Mint 4.0 base with the amazing E17 DE. The website for Maryan Linux is - [http://maryanlinux.wordpress.com/](http://maryanlinux.wordpress.com/)

Cheers,
molom

---

### Post by exploder on 2008-02-05
myusername, getting back to your original question and the hardware specs you listed, gOS would be a good distribution to try first.

gOS is very light and it is built to run on modest hardware. 

The look of gOS is getting more refined.

This is just my opinion. I have looked at gOS, and elive.ozOS looks awesome but at the moment, is only available in a 64 bit version and will not run on the hardware you have.

I would start with gOS and try customizing it for your needs.I liked the way gOS ran and I think the Ubuntu base gives it good stability.

I would also keep ozOS in mind when the 32 bit version becomes available The 64 bit version looks very good and it's Ubuntu base is a real plus..

---

### Post by smartboyathome on 2008-02-05
OzOS can be installed on top of an Ubuntu minimal install from their repos, so it is available on that hardware.

---

### Post by myusername on 2008-02-05
I have been trying to get back to you guys..but for some reason I havent been able to log in for the last hour

I like gOS but it seems like there a are only a few apps in it (is there a package manager?)

I want OzOs but it seems to complicated to install

---

### Post by exploder on 2008-02-05
There is a package manager but I can not rember which one it uses.

---

### Post by myusername on 2008-02-05
what about apps? Does it just come with what's in the dock?

---

### Post by exploder on 2008-02-05
Mpstly web based apps, it does have OpenOffice.

You could add apps that you need.

---

### Post by myusername on 2008-02-05
ok thanks ill download it now

---

### Post by smartboyathome on 2008-02-05
> **myusername said:**
> I want OzOs but it seems to complicated to install

It really isn't that complicated. Just add the repos and install the desktop package, and everything else 'just works'. :)

---

### Post by myusername on 2008-02-06
really? i thought you had to compile a bunch of crap...

---

### Post by kelvin spratt on 2008-02-06
myusername
Oz is as simple as having a XXXX, It does it all for you providing you know how to change sessions? when you log in

---

### Post by myusername on 2008-02-06
do you have to install e17 and then oz-desktop? Cuz that's what I'm doin and it said it skipped the emotion library

---

### Post by kelvin spratt on 2008-02-06
[URL="http://ubuntuforums.org/showthread.php?t=546746"]http://ubuntuforums.org/showthread.php?t=546746 
[/URL]

---

### Post by kelvin spratt on 2008-02-06
The desktop is used mainly if you use minimal CD, but it will install the additional software for e17  like Menu entries, Thunar, Abiword, etc and can be done anytime.

---

### Post by Freddy on 2008-02-06
OzOS isn't that complicated to install, If you know how to install a regular Ubuntu, you must know how to. Sorry to say though but with your hardware OzOS won't install at all, since it's build is for 64bit processors.

If I were you I would wait for Maryan Linux, gOS has a pretty weird (in my opinion) setup of applications and Elive is pretty much outdated.

---

### Post by kazuya on 2008-02-06
i liked ozOs. I was very impressed. I also liked Elive 1.0 Gem. It was wonderfully designed and seamless., almost.

I still prefer to go Mint / Ubuntu and then install e17 desktop to have more options. But for the lightweight, I would stick with Elive 1.0 gem or ozOs when it gets finalized.

---

### Post by Freddy on 2008-02-06
> **kazuya said:**
> i liked ozOs.or ozOs when it gets finalized.
Did anyone actually read the OP:s first post? He explained that he wants to install a e17 based distro onto a old Pentium III (550 Mhz), OzOS is a 64bit distro!

---

### Post by smartboyathome on 2008-02-06
OzOS is only 64 bit on the livecd. It has repos which are 32 bit, and which you can use to install e17 and its desktop metapackage on top of ubuntu minimal.

---

### Post by Freddy on 2008-02-06
Ohh didn't know that, that's good to know :).

---

### Post by Rui Pais on 2008-02-06
Hi
Just wanted to add my 2 cts too :)

First, i think that if one has an old machine either it accepts some easy way and get some "slight" better distro than other and live with that 
or get a little more work and really do the most it can and get rewarded by a better working machine.

So my opinion, goes more or less the same as smartboyathome. Go with an Ubuntu minimal CD and than the desktop.

My 2nd cent, goes to draw the differences between e17-cvs package and OzOS. 
OzOS it's not a distro for low-end machines (it have in mind the opposite, in fact). 
OzOS use some apps that have other better/lighter options on repos.
 
e17-cvs installs a basic e17 desktop, that it's what you needs.
It compiles a lot of stuff, yes, but only do that 1st time and as K.Spratt already mentioned it's plain simple, add a repo and do an apt-get. (You can also install a login manager or log directly to e17)

But the advantage of get e17 with e17-cvs it's that you can do more with it than just the apt-get command :)

You can, before install, set cflags for your machine and get a tuned e17 for pentium 3:
Edit your ~/.bashrc and add:
```
CFLAGS="-Os -march=pentium3 -fomit-frame-pointer -pipe"
export CFLAGS
export CXXFLAGS=${CFLAGS}
```
Then 
```
apt-get install e17-cvs
```
simple :)

give a look too at this apps:
browser: kazehakase
file manager: pcmanfm, rox
text editor: scite, mousepad
login manger: slim

post on any doubt.

---

### Post by tdrusk on 2008-02-08
I'm digging gOS.

I just installed it and ran the live cd on a pentium 3 with 128 mb of ram.

I was surprised it ran.

---

### Post by myusername on 2008-02-08
thanks everybody for your posts... But my grandfather just gave me an old pentium 4 2,0 ghz 512 ram 64 video ram but the hard drive was bad so I used the one from my old pc and I'm gonna run windows till a better solution to using my iPod touch comes..ugh...I hate windows.

---

