---
title: "Linux distro för an old Dell Latitude laptop?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by davidlegge on 2008-05-18
Hi,
I'm interested in getting Linux up on an old Dell laptop I have. It's a Latitude CPi R, from about year 2000, with a Pentium II processor, 128MB ram, 6GB disk and internal CD drive. Currently running XP.

I have tried running ubuntu from CD, but after the ubuntu logo and orange bar moving to and fro, got a lot of CD/Disk access and not much else (ie nor error messages). I put this down to the RAM I have available. (Recall reading after the fact that I need 256MB min...)

I've also tried Puppy from CD, but get an error messge and a system hang...

Can anyone suggest any other distributions that I might try?

Thanks.

/david

---

### Post by shifty_powers on 2008-05-18
damn small linux?

designed to fit into 50mb iirc, but actually really quite funcional.

try and google it.

plus, why not try xubuntu, and install the fluxbox desktop? it's designed to be VERY lightweight but still look good ;)

---

### Post by jrusso2 on 2008-05-18
I doubt xubuntu is going to work well at 128 mb of ram.  I never had any luck with it at that amount.

I would maybe try something slackware based like zenwalk, or even slackware if you have some experience.  Maybe Debian even.

The antix is supposed to be good also.  I have run sam linux on a similar pc with good luck and 128 mb for ram and I used the ICEWM.

---

### Post by JoshuaRL on 2008-05-18
I would suggest running Linux Mint Fluxbox.  Kind of weird, but works fast.

---

### Post by Joeb454 on 2008-05-18
It may be worth doing a minimal install on there, so you can pick and choose what components you want, and then putting something like Fluxbox on there, or even Openbox

---

### Post by NightwishFan on 2008-05-18
Fluxbuntu, or try booting puppy with ```
puppy acpi=off
```
Also try Debian.

---

### Post by atomkarinca on 2008-05-18
Your best bet would be installing a base system with a [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD") and installing Fluxbox on it. When you boot up with minimal cd type:

```
cli
```

and answer a bunch of questions. When you restart install the necessary packages for the window manager. First uncomment the universe repository:

```
sudo nano /etc/apt/sources.list
```

save with ctrl+o and exit with ctrl+x. Then install the needed packages for a WM and WM of your choice (I suggest fluxbox):

```
sudo apt-get update
sudo apt-get install gdm xorg xserver-xorg xserver-xorg-video-vesa x-window-system-core gksu synaptic xterm fluxbox
```

after all that start gdm:

```
sudo /etc/init.d/gdm start
```

---

### Post by kwacka on 2008-05-18
I haven't tried it, but how about 'Ubuntu Lite': 

"There is a new version of ubuntulite. **It is currently in beta testing**. It will be based on open-box, with fbpanel, and the slim display manager. We want it to run lighter than the old version. As always the goal is to run on Win9x era machines with 32 to 68 mb of ram."

(My emphasis)

 see: [https://help.ubuntu.com/community/InstallingUbuntuLite](https://help.ubuntu.com/community/InstallingUbuntuLite)

---

### Post by eriqjaffe on 2008-05-18
> **atomkarinca said:**
> Your best bet would be installing a base system with a [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD") and installing Fluxbox on it. When you boot up with minimal cd type:

```
cli
```

and answer a bunch of questions. When you restart install the necessary packages for the window manager. First uncomment the universe repository:

```
sudo nano /etc/apt/sources.list
```

save with ctrl+o and exit with ctrl+x. Then install the needed packages for a WM and WM of your choice (I suggest fluxbox):

```
sudo apt-get update
sudo apt-get install gdm xorg xserver-xorg xserver-xorg-video-vesa x-window-system-core gksu synaptic xterm fluxbox
```

after all that start gdm:

```
sudo /etc/init.d/gdm start
```I second most of this, but I'd recommeng using [SLiM]("http://slim.berlios.de/") instead of GDM.  For a lighter-weight graphical login, there's XDM, or you could just login at the command-line prompt and enter "startx" to be really lightweight.  Also, I wouldn't recommend using Synaptic - I do all my package management with apt-get and dpkg, and it works just fine.

---

### Post by JoshuaRL on 2008-05-19
Yeah, and you could also use Aptitude if you wanted a GUI of sorts.  It handles things nicely if you're a little afraid of the CLI.

---

### Post by CJ56 on 2008-05-19
I would definitely go for Zenwalk -

I've got it running as sweet as a nut on an old Dell Inspiron 1200 with 128 Mb RAM, a crappy Celeron processor and a plug-in Dell wireless card

Zenwalk 5.0 has got a few nice new touches over previous versions - including easier wireless configuration - the repos seem to offer everything you might want, & it all runs very nicely & much faster than Xubuntu

Give it a try - ;)

---

### Post by Inxsible on 2008-05-19
> **davidlegge said:**
> Hi,
I'm interested in getting Linux up on an old Dell laptop I have. It's a Latitude CPi R, from about year 2000, with a Pentium II processor, 128MB ram, 6GB disk and internal CD drive. Currently running XP. OH the horror !!!  :D

Well I am in a similar, if not the same boat. I just found me a Dell Latitude C810 -- P3, 256MB RAM, 30gb HDD and was going to install Xubuntu in a dual boot with Arch on it. But I might also go for Ubuntulite. I haven't decided yet :)

But yeah, Fluxbuntu, DSL, Puppy are great choices. Puppy does run in that config, you might just have to try out some acpi options as mentioned earlier.

---

### Post by linuxlizard on 2008-05-19
Try the others suggested, but make sure you try pcfluxboxos. I've tried them all on several older computers and hands down pcfluxboxos is the best. It's fast and light like puppy but is a *real* linux with synaptic and thousands of the latest software versions (unlike puppy or dsl).

I've got an old p2 with 128 mb ram desktop that I use as a second computer when my kids are hogging my main machine for games. With pcfluxboxos, it's running the latest versions of gimp, firefox, open office, gizmo, etc, and it runs them well. It doesn't feel slow.

---

### Post by nowin4me on 2008-05-19
It really dose depends on what you want.

Do you want small OS? So you can download lots of programs? [Due to disc space].
Or do you want a fast OS? Less programs more fast? [Due to disc space].

REMEMBER: Theres no harm in trying. [If they are free]

---

### Post by JoshuaRL on 2008-05-22
You could also try the first (Google Apps based) version of gOS, that is if you like the Enlightenment Desktop Environment.  Should run fast.

---

