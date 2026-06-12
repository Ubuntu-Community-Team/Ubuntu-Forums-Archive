---
title: "What is the state of LTS mini-iso support?"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by verymadpip on 2013-09-20
Hi everybody.
I'd like some clarification regarding the length of time an install from a mini-iso is supported for.
Here's the story:

In order to revive an ancient Compaq TC1000 tablet I did an install from the non-PAE 12.04 mini-iso, added a window manager, panel & a few other bits & pieces.
I'd like to know if this installation will receive 5 years' support, 3 years, or just 18 months.  (Some of the chaps on IRC tell me I'd get 5 years, which is awesome if correct).

An interesting (IMO) additional question then is:
If I had installed a *buntu DE, Lubuntu or Xubuntu, for example, using the lubuntu/xubuntu-desktop meta packages from the repos what effect does that have on the support time period?
Would the L/Xubuntu specific packages become obsolete & cause a problem?  
What happens if one installs the vanilla LXDE or XFE DE rather than a *buntu DE?
What happens if one just installs a WM as opposed to a full *buntu DE?

Would the answers to these questions also apply to the regular (PAE) mini-iso?

Sorry if this seems trivial to some, but I feel it to be a source of confusion & clarification would be much appreciated.

---

### Post by mastablasta on 2013-09-20
> **verymadpip said:**
> Hi everybody.
I'd like some clarification regarding the length of time an install from a mini-iso is supported for.
Here's the story:

In order to revive an ancient Compaq TC1000 tablet I did an install from the non-PAE 12.04 mini-iso, added a window manager, panel & a few other bits & pieces.
I'd like to know if this installation will receive 5 years' support, 3 years, or just 18 months. (Some of the chaps on IRC tell me I'd get 5 years, which is awesome if correct).


5 years. desktop packages (e.g Lubuntu-desktop) are a different matter.
> 
An interesting (IMO) additional question then is:
If I had installed a *buntu DE, Lubuntu or Xubuntu, for example, using the lubuntu/xubuntu-desktop meta packages from the repos what effect does that have on the support time period?


it is supported as long as the installed desktop is supported.
> 
Would the L/Xubuntu specific packages become obsolete & cause a problem? 

yes computer will emplode and take the whole universe with it. make sure you upgrade when the time comes. :-)

nothing specific actually happens. you just don't get updates anymore. for the desktop and desktop applicaitons. you would sitll get updates for kernel and such. basically all components that are shared between variosu desktops and server.
> 
What happens if one installs the vanilla LXDE or XFE DE rather than a *buntu DE?


lubuntu is customized LXDE. if you install only lxde you get only lxde packages without the Lubuntu customisation.

> 
What happens if one just installs a WM as opposed to a full *buntu DE?

you mean if you install it in virtual box and the OS reaches end of life ? same as above only the virtual computer impodes... :-)


> 
Would the answers to these questions also apply to the regular (PAE) mini-iso?

mini-iso is just the basics upon which you can install your own things. it includes basic OS. kid of like MS-DOS was for windows 95, 98 if you know that OS. only better.

debian calls it netinstall i belive.

you said you installed a wm - well after certian time the wm won't be patched anymore (not sure how many security patches they actually receive anyway). 
i eblieve this can be solved by using a PPA and keeping those up to date (if it's really necessary). same goes for applications.

if you are looking for something very light that has long support. - have a look at LXLE - it's lubuntu based but will be maintained for the whole 5 years.
another option is AntiX - debian/mepis based with IceWM. quite long support.

aside from these you have Red Hat based Scientific Linux and CentOS and a few others.

there are also a few other distributions made for older mashcines with long term support of packages. Puppy based on Ubuntu 12.04/using it's repositories for example.

---

### Post by verymadpip on 2013-09-20
Hi there & thanks for the reply.

Let's see if I have understood this correctly.
If I do a base install from a mini-iso & then add things from the 12.04 repos, whatever I've added is supported as long as it's in the those repos?

My confusion really lies in what happens if one uses *buntu-desktop meta packages to install a GUI.
If I've installed from 12.04 mini-iso (I guess the same will hold true for 14.04) & added lubuntu-desktop via, say, synaptic or apt-get I'm not really running Lubuntu 12.04 am I?
Consequently, IF all the packages pulled in by lubuntu-desktop are supported for 5 years I can happily continue computing by doing my regular updates? I don't want the universe to implode!!!

My thinking is that it is probably less risky to install vanilla lxde, or a window manager or whatever, from the repos.  Granted I lose the customized DE, but may avoid some pain, & universe implosion, further down the line.
Am I along the right lines here?

As an aside, with the TC1000 I found full Lubuntu a bit too heavy for it, which is why I went mini-iso plus window manager & panel etc.
I heard of LXLE recently & was thinking of taking it for a test drive on a machine with a bit more oomph!!

I happen to think that the mini-iso is a really great way of trying to bring older, low spec hardware back to life, it's a fantastic learning experience, & with 5 years of support for non-PAE, using 12.04, there's the chance to keep ancient kit like mine useful to a large extent.

---

### Post by buzzingrobot on 2013-09-20
Updates are provided via patched packages in the repos.  When support ends, no patches are done, so no new packages are added. 

Use of the mini.iso has no impact on support.  It's just a different installation method.  Support for a package ends when it ends, regardless of how you installed it.

So, if you do a mini install of the current LTS, 12.04.03, support for it runs as long as 12.04.03 installed any other way.  That includes all the software Canonical considers part of the 12.04.03 release (the packages on the repos).

Kubuntu, Xubuntu, Lubuntu, etc., offer the same period of support as the Ubuntu version they are based on, more or less by default because they use the same repos. (I.e., they don't maintain Ubuntu packages.) However, in the case of independent components that these distributions supply that are *not* maintained in the Ubuntu repos by Canonical, then support for those components is whatever that distribution says it is. E.g., on its wiki, Lubuntu says the Lubuntu components on its releases based on Ubuntu LTS are not LTS, i.e., they won't be supported for the full lifetime of Ubuntu 12.04.03.

Don't overthink this.  Software is supported for as long as its maintainers say it's supported, regardless of how it ends up on your machine.

---

### Post by Bucky Ball on 2013-09-20
If you're running the mini.iso, why install a *buntu-desktop anything??? That totally defeats the purpose. You may as well just install the *buntu version as same same. 

Just install a desktop environment; xfce4, lxde, openbox, whatever, and the apps you use/want/need only. Cut the bloat, that is the whole idea of the mini. I have xfce4 and only the apps I use. That is it. My own personal rocket box!

Repeat, if you're going to go to the bother of a mini.iso install only to then install a *buntu-desktop on it, don't waste your time. A bit off-topic, I know, but just thought I'd mention.

Incidentally,

> **buzzingrobot said:**
> 
Kubuntu, Xubuntu, Lubuntu, etc., offer the same period of support as the Ubuntu version they are based on. 

Not exactly. The LTS version of Xubuntu is three years, Lubuntu is not an LTS at all (18 months) and don't know about Kubuntu. ;)

---

### Post by amjjawad on 2013-09-20
> **Bucky Ball said:**
> Not exactly. Lubuntu is not an LTS at all (18 months)

Hi,

Lubuntu 12.04 is supported for 18 months
Lubuntu 13.04 is supported for 9 months, just like Ubuntu.

Lubuntu 14.04 is going to be the first LTS version of Lubuntu.

Releases: 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by amjjawad on 2013-09-20
> **verymadpip said:**
> Hi everybody.
I'd like some clarification regarding the length of time an install from a mini-iso is supported for.
Here's the story:

In order to revive an ancient Compaq TC1000 tablet I did an install from the non-PAE 12.04 mini-iso, added a window manager, panel & a few other bits & pieces.
I'd like to know if this installation will receive 5 years' support, 3 years, or just 18 months.  (Some of the chaps on IRC tell me I'd get 5 years, which is awesome if correct).

Hi,

To make your life easier, I will answer this only Q and hope it would be clear for you :)

Ubuntu and any of its official Flavour (Xubuntu, Lubuntu, Kubuntu, etc) if we want to break the system down to parts then:

1- Core System
2- Desktop Environment
3- Installed Packages/Applications

Example:
Ubuntu (in general) consists of:
1- Core System
2- Unity
3- The default installed Applicaitons

Specifically:
Ubuntu 12.04 (LTS) consist of:

1- Core System (Ubuntu Mini 12.04 LTS)
2- Unity Packages (LTS)
3- The default installed applications (LTS)

Now, please pay attention to: Lubuntu

Lubuntu until now, has NO official LTS release. Having that said, Lubuntu 12.04 consists of:

1- Core System (Ubuntu Mini 12.04 LTS)
2- Lubuntu Desktop Package and LXDE
3- The default installed applications of Lubuntu

While the Core System is indeed an LTS release, the other parts ARE NOT. Having that said, while you are indeed will receive security updates for your core system for 5 years, you will NOT have any updates for the other part (Lubuntu Desktop Package and/or LXDE). Lubuntu has not enough manpower to go LTS but the team has finally decided to go for an LTS version the next release, that is 14.04 :)

LTS: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Mini ISO: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Lubuntu 12.04 is not LTS: [https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu](https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu)

As for Xubuntu 12.04, it is an LTS version and that means: each and every package is supported for 3 years (instead of 5).

So, in your case, if you will install the Mini ISO ALONE, that core/base system is an LTS if you are going to use Ubuntu 12.04 Mini ISO.

Whatever you are going to install on the top of that? that depends on what DE you will use and what packages.

Hope that helps!

Edit:
Does 12.04 LXDE have LTS?
[http://askubuntu.com/questions/23707...-lxde-have-lts]("http://askubuntu.com/questions/237077/does-12-04-lxde-have-lts")

---

### Post by buzzingrobot on 2013-09-20
@Bucky:  The Ubuntu packages the spins rely on and take from Ubuntu repos are supported for as long as Canonical decides. A spin can only end support for packages it actually supports. That was the gist of my point. I'm not aware of any 13.04 spin, for example, official or unofficial, that will, or could, provide support after 13.04's support ends.  They can't because they'd need to take on maintenance of the defunct 13.04.

---

### Post by mörgæs on 2013-09-20
If you want something light, supporting non-PAE computers and with long term support you should try Bodhi. There's a link in my signature.

Regardless of the length of support Lubuntu 12.04 is buggy, and it's very unlikely that fixes will be provided.

---

### Post by amjjawad on 2013-09-20
> **mörgæs said:**
> If you want something light, supporting non-PAE computers and with long term support you should try Bodhi. There's a link in my signature.
Bodhi Linux is NOT the only system that offers support for NON-PAE Machines: [http://crunchbang.org/download/](http://crunchbang.org/download/)

Just FYI :)


> Regardless of the length of support Lubuntu 12.04 is buggy, and it's very unlikely that fixes will be provided.

For you, it might be buggy but for me, it was fine!

And, overall, it is really depends on the user and what he/she is planning or going to use that machine for :)

---

### Post by verymadpip on 2013-09-20
Hi again guys, & thanks for the responses.
This has been extremely helpful, (hopefully not just for me :)) & I'd like to thank everyone for their input.

@bucky; I couldn't agree more that mini-iso + *buntu-desktop is a bit pointless, especially with something like the TC1000.
I did try Bodhi on it & ran into some issues (can't recall exactly what as it was in December or January) & eventually opted for Openbox plus lxpanel, which kind of gave me a Lubuntuish feel.  Something familiar for me, as I am a big Lubuntu fan.
I'm sure if the TC1000 had a little more grunt Bodhi would've been cool.  I even had some problems with Slitaz!!!

@amjjawad, thanks for that breakdown, that really clarifies how things are put together for me.

I plan to install Lubuntu 14.04 on my MSI Wind U180 netbook, as long as the graphics drivers for the PowerVR chip keep working as well as they do in 13.04.

It's great to know that there's a way to eke out every bit of life from that hardware I thought was dead.

I'm going to go ahead & mark this as solved.
I don't know if maybe this info should be included in a wiki in some form?  I guess it's all out there somewhere, but it'd be neat to have it all in one place - the old hardware thread even?

Once again, thanks everyone...gotta love this community :D

---

### Post by amjjawad on 2013-09-20
> **verymadpip said:**
> @amjjawad, thanks for that breakdown, that really clarifies how things are put together for me.

At your service. Glad that helped :)

> I don't know if maybe this info should be included in a wiki in some form?  I guess it's all out there somewhere, but it'd be neat to have it all in one place - the old hardware thread even?


Maybe this?
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

OneStopPlace for Lubuntu: [https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
OneStopPlace for Ubuntu GNOME: [https://wiki.ubuntu.com/UbuntuGNOME/OneStopPage](https://wiki.ubuntu.com/UbuntuGNOME/OneStopPage)
Search Engine for Ubuntu and its flavours: [www.googlubuntu.com](www.googlubuntu.com)

AskUbuntu is a nice place too ;)

In general, if you are typing the correct question, you should get what you are looking for so easily with a quick google search :)

---

### Post by Bucky Ball on 2013-09-20
It's all in one place right here. ;)

Good luck with it.

---

