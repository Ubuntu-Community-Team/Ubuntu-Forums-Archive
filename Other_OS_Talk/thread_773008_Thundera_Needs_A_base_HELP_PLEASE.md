---
title: "Thundera Needs A base HELP PLEASE"
date: 2008-04-28
forum: Other OS Talk
---

### Post by Thundera on 2008-04-28
Well, Thundera 1.0 Coyote, the much awaited distro, has been halted in progress. We have currently stopped, as we are in need of a new base distro.

Please give out a VALID list of a good Base Distro, to build this from. (I.e. Linux From Scratch, Gobuntu, Debian, Fedora, Etc.)List it's pro's and con's and what makes it good.

Thanks...
Anyone who wants to be staff, temporarily to research this, post here and make sure to mention it :p

---

### Post by Barrucadu on 2008-04-28
Arch - Fast, starts off with nothing installed but the bare minimum, completely customizable, frequent updates, rolling-release (so no distribution upgrades), user-centric.

---

### Post by Thundera on 2008-04-28
Sounds good, I might use it as a base. I do not want a lot of things, infact I want it to have barely any programs, only GNOME DE and things required.

---

### Post by Barrucadu on 2008-04-28
It doesn't even have a GUI by default. It's... fairly minimal.

---

### Post by Thundera on 2008-04-28
So I have to add GNOME myself than? Sounds Ok. I was hoping for a distro that barerly had anything but GNOME, Settings, and some Resources...Maybe I will just strip down gobuntu to my likings.

---

### Post by Pogeymanz on 2008-04-28
Arch +1

It has the best package manager ever and it starts off with practically nothing, so you can customize it to exactly what you think a distro should look like. Gnome is one command away after you get X up and running.

---

### Post by Thundera on 2008-04-28
Thanks :p Probably Arch than.

I am emo by the way lol.

---

### Post by Barrucadu on 2008-04-28
I'm not sure whether being emo or not will make it easier to set up Arch... This sounds like a job for Science! :D

---

### Post by Thundera on 2008-04-28
Lol...
Does Arch have: Package Manger, and Normal System Utilites, like the control panel in windows and mac for instance?

---

### Post by Barrucadu on 2008-04-28
It doesn't have a control panel because it doesn't have a GUI by default. It has a package manager: pacman, which also functions as an update manager.
```

# To install something:
pacman -S package1 package2 ...

# To search for something
pacman -Ss keyword

# To update the repositories and installed packages
pacman -Syu

# To remove a package and all unrequired dependencies
pacman -Rs package1 package2 ...
```

You could install gnome-control-center if you wanted a control panel.

---

### Post by Thundera on 2008-04-28
So once a install GNOME and the GUI and the Gnome Control Center, will the package installer look more like synaptic, and be click-point easy for new Linux user's, or will they still have to do typing to install things?

---

### Post by Barrucadu on 2008-04-28
You'll need to install a graphical front-end to pacman yourself. There are a few, but I can't think of any off the top of my head - I've just always used the terminal (even in Ubuntu, it took me months to find Synaptic) to install things.

---

### Post by Thundera on 2008-04-28
Well, the users who this is aimed at, new linux computer newbies, and my friends would not know how to do that. I want to make this an easy idiot friendly distro, So I will probably do that right away to Pacman. Sounds good, when I start the dev and phase out of planning(The other 80 Percent of this project) that will most likely be he first thing I do than.

Thanks, I am sold on Arch.

**_[COLOR="Sienna"]CONSIDER THIS THREAD CLOSED AND DONE< DO NOT POST IN IT<POST IN THE NEW ONE![/COLOR]_**

---

### Post by LaRoza on 2008-04-28
> **Thundera said:**
> 
**_[COLOR="Sienna"]CONSIDER THIS THREAD CLOSED AND DONE< DO NOT POST IN IT<POST IN THE NEW ONE![/COLOR]_**

Consider it closed ;)

---

