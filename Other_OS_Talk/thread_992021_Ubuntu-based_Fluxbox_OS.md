---
title: "Ubuntu-based Fluxbox OS?"
date: 2008-11-24
forum: Other OS Talk
---

### Post by tcoffeep on 2008-11-24
Hello.

I understand Fluxbuntu is around (although, they're Intrepid release is still in testing), and Fluxbox is easily installed over GNOME in Ubuntu, but, other than Fluxbuntu, is there an OS that uses the Ubuntu base? I'm not sure if I'm making sense here, honestly, but, I love Ubuntu, and I love Fluxbox (especially since it's one of the only Desktop Environments that don't overheat my laptop), and I can't find any Fluxbox distros worth using. (not including USB distros).

---

### Post by Elfy on 2008-11-24
Linux Mint Fluxbox perhaps - [http://www.linuxmint.com/blog/?p=404](http://www.linuxmint.com/blog/?p=404)

---

### Post by tcoffeep on 2008-11-24
Is this based off of Intrepid?

---

### Post by kk0sse54 on 2008-11-24
Use the alternative Intrepid CD installer for Ubuntu which will give you a minimal install with no DE from which you can add fluxbox and whatever else you would like. [https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)

---

### Post by Sorivenul on 2008-11-24
And not Ubuntu based, but Debian based: MEPIS antiX.

---

### Post by Elfy on 2008-11-24
> **tcoffeep said:**
> Is this based off of Intrepid?

I think the next version is.

You could use the minimal install - [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Get the small iso [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and build it up with only the things you really want.

---

### Post by tcoffeep on 2008-11-24
Hey, thanks.

I'll try the minimal install. I was going to use Slackware, and install Fluxbox, but, I really like the dpkg management. :)

---

### Post by Elfy on 2008-11-24
When I did it I had a list of stuff I wanted to install before I started - it wasn't a very long list, but it did make it easier than trying to remember what I wanted :D

Good luck.

---

### Post by tcoffeep on 2008-11-24
> **forestpixie said:**
> When I did it I had a list of stuff I wanted to install before I started - it wasn't a very long list, but it did make it easier than trying to remember what I wanted :D

Good luck.

There are a few concerns I have about installing via minimal cd. I use a nvidia card, will this cause problems? I know with the main Ubuntu CD it had the whole "Restricted Drivers", will I have to find the name for this?

Also, will I still be able to run GNOME/KDE programs? Or will I need to download specific libraries that are depended on?

---

### Post by Elfy on 2008-11-24
It'd make life easier I expect - but then I didn't worry too much myself - wasn't interested in 3d or any of that and the nv driver worked fine.

Which card do you have?

You should certainly be able to get it going with the normal nv driver or vesa to get in if it causes problems.

---

### Post by tcoffeep on 2008-11-24
Off the top of my head, I can't remember my laptop specs. It is, however, an Inspiron 5150.

---

### Post by aysiu on 2008-11-24
Can you elaborate a bit about what you don't like in Fluxbuntu?

---

### Post by tcoffeep on 2008-11-24
I never said I held an opinion of Fluxbuntu. But, the intrepid version is still in testing, and the last time I ran a distro in testing I damaged my last laptop. I'm not savvy enough to handle bugs yet. (And I'm looking for an Intrepid-based distro).
Although, I try and figure things out, which usually leads to more damage. O.o

---

### Post by snowpine on 2008-11-24
> **tcoffeep said:**
> I never said I held an opinion of Fluxbuntu. But, the intrepid version is still in testing, and the last time I ran a distro in testing I damaged my last laptop. I'm not savvy enough to handle bugs yet. (And I'm looking for an Intrepid-based distro).
Although, I try and figure things out, which usually leads to more damage. O.o

Just to clarify, the *Gutsy* version of Fluxbuntu (7.10) is still "in testing," although testing seems to have stopped over a year ago. There are no Hardy or Intrepid versions of Fluxbuntu, and probably never will be. :)

(edit) Well I stand corrected--there does seem to be some recent activity on the Fluxbuntu site! I have some fond memories of Fluxbuntu (I particularly like the artwork), so I hope they are able to revive the project. Best of luck, Team Fluxbuntu!

The reason there aren't a lot of Fluxbox based distros is that Fluxbox users tend to prefer very minimalistic setups. Most prefer a minimal Ubuntu install and then adding your pick of applications. (One of the problems with Fluxbuntu was the questionable choice of applications, such as the terrible Kazehakase browser instead of Firefox, or including both Abiword and OpenOffice writer in a "lightweight" distro.) Or, if you want something full featured, you can install a full distro, like Ubuntu, and then install Fluxbox on top of that. You will already have all of the great Ubuntu applications (which will work fine in Fluxbox) and you can switch to Fluxbox from your login screen (by choosing sessions).

Openbox seems to be more popular than Fluxbox these days. There are lots of great Openbox based distros; my favorite in the Ubuntu category is Crunchbang. SliTaz is another great Openbox distro that blows away other "lightweight" distros, in my opinion.

Good luck!

---

### Post by mikjp on 2008-11-26
> **snowpine said:**
> Just to clarify, the *Gutsy* 
The reason there aren't a lot of Fluxbox based distros is that Fluxbox users tend to prefer very minimalistic setups. Most prefer a minimal Ubuntu install and then adding your pick of applications. 

Or install a minimal Debian testing and comand as root:

apt-get install openbox

Greetings,

mikko

---

### Post by jay576 on 2008-11-26
I tried fluxbuntu on this computer before I upgraded and did not enjoy it.  I wasn't found of fluxbox and it took forever to load granted it was an older setup with only a 128 mb ram chip in it, I still believed it should run faster than that.  I am currently working on building my minimal install of 8.10 it always seems almost done and then it is barely started but I have yet to install the nvidia drivers on my desktop and it doesn't really bother me.

---

### Post by L815 on 2008-11-26
I tried Crunchbang linux this weekend which is Ubuntu with Openbox but with a few default configurations. It's not fluxbox, but it's close enough.

I enjoyed it a lot and would use it, although I find it just a tad too minimalistic for me :P.

---

### Post by Naiki Muliaina on 2008-11-26
Theres always nUbuntu. Its intended for security testing but it is an Ubuntu based fluxbox distro. Tiny ISO ^^

---

### Post by walkerk on 2008-11-26
Minimal install + fluxbox. As for the nvidia drivers i suggest installing  "envyng"

```
sudo apt-get install envyng
```
Run it to install your nvidia driver...
```
envyng -t
```

I always do a minimal install and load openbox & pekwm.

:)

---

### Post by Twitch6000 on 2008-11-28
Well I know of a Fluxbox Distro.. but not ubuntu based...

That would be PCFluxboxOS(based on PClinuxOS).

You could try it out and see what you think about it.

---

