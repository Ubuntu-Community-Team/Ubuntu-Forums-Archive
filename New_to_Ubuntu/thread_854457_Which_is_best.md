---
title: "Which is best?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by fiddledeedee on 2008-07-09
I have a laptop with the following specs:
Pentium 4 Processor: 2.66 Ghz, 512MB RAM
Graphics card is a Radeon 7500C.
Basically, my top priority is speed, but if my system can run Kubuntu reasonably fast, then I will pick Kubuntu.  If my system is too slow for Kubuntu and Ubuntu, I will pick Xubuntu.  If I can run Ubuntu but not Kubuntu, then I will pick Ubuntu. Which OS would be best for me?  Thanks in advance for any help.

---

### Post by Cypher on 2008-07-09
Xubuntu would probably be the best option for you..you can surely try Ubuntu or Kubuntu..but XFCE has significantly less requirements than GNOME or KDE, so you'll be making the most of the hardware you have..

---

### Post by OutOfReach on 2008-07-09
If you prefer speed, Xubuntu would probably be the best choice.

---

### Post by PHATSPEED7x on 2008-07-09
Xubuntu will be the fastest, plus it has all the nice features ubuntu has. I have ubuntu on my sony vaio with a pentium 4 2.8mhz processer, 1GB of RAM, and a 80GB HD and it's fast. I also have xubuntu on a old gateway with a pentium III 900mhz processer, 128mb of ram, and a 10GB hard drive. It will run just as fast as the sony model.

---

### Post by framinglory on 2008-07-09
you can always start with xubuntu, then install gnome/kde if you want to try them, just use

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop

will install the appropriate (gnome, kde, xfce) desktop environment. If you don't like one, just use
sudo apt-get remove package_name
to remove it.

also, if you want to use kubuntu with kde4, use
sudo apt-get install kubuntu-kde4-desktop

all those listed above are meta-packages, which means they just have a huge list of packages to install. if you like one of the heavier desktop environments, you can try installing the base system and then adding packages as you need them, rather than adding all and removing ones you don't need. the base packages (i believe) are just named gnome, kde, kde4, and xfce4. These packages will have the minimal packages required to run the respective desktop environments, and as such will likely be faster than the meta-package alternatives.

---

### Post by atomkarinca on 2008-07-09
Xubuntu and (K)Ubuntu don't have much difference when it comes to speed. If you're willing to go with Xubuntu I would suggest installing Kubuntu instead, at least that seems your favourite. If you want real speed then you should install Fluxbuntu or Openbox on top of a minimal install.

---

### Post by LowSky on 2008-07-09
your processor isn't that slow, but 512 RAM will be your enemy. Its a good amount for any *buntu but Xubuntu is the best of the bigger releases. Why not install Xubuntu and the add KDE (Kubuntu's interface) later, it is very simple.
This way you can switch between interface and find which runs better

---

### Post by tjwoosta on 2008-07-09
well..

if xubuntu isn't fast enough for you, then you could always try fluxbuntu


its not quite as user friendly as the rest of the ubuntu family, but if you know your way around linux then it is definatly worth looking into

or you could go even lighter weight and go with something like puppy linux or damnsmalllinux

just remember the lighter the distro gets the less user friendly it will be

---

### Post by snowpine on 2008-07-09
If your #1 top priority is speed, definitely Fluxbuntu or a bare-bones install of Xubuntu ([http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)).

But it sounds like you prefer Kubuntu, so why not give it a try? It should work okay on those specs.

---

### Post by billgoldberg on 2008-07-09
> **fiddledeedee said:**
> I have a laptop with the following specs:
Pentium 4 Processor: 2.66 Ghz, 512MB RAM
Graphics card is a Radeon 7500C.
Basically, my top priority is speed, but if my system can run Kubuntu reasonably fast, then I will pick Kubuntu.  If my system is too slow for Kubuntu and Ubuntu, I will pick Xubuntu.  If I can run Ubuntu but not Kubuntu, then I will pick Ubuntu. Which OS would be best for me?  Thanks in advance for any help.

If you want eyecandy and speed:

[opengue]("http://opengeu.intilinux.com/Home.html")

It's Ubuntu but with Enlightenment (e17).

---

### Post by PHATSPEED7x on 2008-07-09
I'm going to try fluxubuntu on my old desktop and see how the speed is...

---

### Post by s3a on 2008-07-09
Install Ubuntu. A Pentium 3 Processor (my laptop has 850Mhz CPU) and 384 MB RAM, runs Ubuntu very well and you have better specs so you can run Ubuntu very well.

---

### Post by billgoldberg on 2008-07-09
> **PHATSPEED7x said:**
> I'm going to try fluxubuntu on my old desktop and see how the speed is...

Go ahead, but fluxbox isn't userfriendly at all.

You are going to have issues for sure.

It would be better to just use ubuntu and optimize it for speed.

---

### Post by PHATSPEED7x on 2008-07-09
What makes it not user friendly

---

### Post by tjwoosta on 2008-07-09
lol, only one way to find out

---

### Post by ism. on 2008-07-09
> **billgoldberg said:**
> Go ahead, but fluxbox isn't userfriendly at all.

You are going to have issues for sure.

It would be better to just use ubuntu and optimize it for speed.

yea i agree with both statements.  I had the same problem  but i put Ubuntu on it and took off all the apps and things i didnt need or want and it ran like a charm!

-ism.

---

### Post by snowpine on 2008-07-09
[QUOTE=billgoldberg;5353184]Go ahead, but fluxbox isn't userfriendly at all.

You are going to have issues for sure./QUOTE]

That is kind of a pessimist attitude, don't you think?
Not that I disagree with you. :)
But I think it's better to bring up specific issues, get advice on the forums, and hopefully resolve them, than to scare a new user off. Perhaps you can share what you learned from your Fluxbox adventures...
Also be clear whether you are talking about Fluxbuntu or Fluxbox, because a lot of people confuse them.

---

### Post by djbon2112 on 2008-07-09
Frankly you won't see much difference unless you start trying to enable Compiz effects. If you leave them off, you're good. Then it's ust a matter of which WM you like more.

---

### Post by atomkarinca on 2008-07-09
> **PHATSPEED7x said:**
> What makes it not user friendly

It's not "not user friendly", it's just different than Gnome, KDE and the like and it needs more configuration. With Fluxbox you don't get a start menu but a right-click menu. You don't configure your shortcuts with a GUI but configure it by editing a text file (I think I saw an application to do this but I'm not sure). You don't get to keep Compiz Fusion but you can achieve most of its effects and usibility with xcompmgr, 3ddesktop and skippy.

Just try it and if you don't like it you can install Gnome or whatever you like. And when you're doing that don't do "sudo apt-get install ubuntu-desktop" but install a vanilla Gnome, i.e. "sudo apt-get install gnome-core".

---

### Post by snowpine on 2008-07-09
> **atomkarinca said:**
> Just try it and if you don't like it you can install Gnome or whatever you like. And when you're doing that don't do "sudo apt-get install ubuntu-desktop" but install a vanilla Gnome, i.e. "sudo apt-get install gnome-core".

This is great advice. If you are coming from Fluxbuntu (as opposed to Fluxbox over (X)ubuntu), I would also recommend you 'sudo apt-get install gdm" and use GDM instead of Slim as your login manager. It will give you better control over which windows manager is your default session.

mmmm, vanilla gnome...

---

### Post by nowshining on 2008-07-10
i'm running A P4 2.66ghz with a fx5200 video card & 512mb of ram.

Ubuntu 8.04 - runs fine
Kubuntu 7.10 - ran fine - more than likely kubuntu 8.04 will run fine.

however I use a desktop tho. :)

---

