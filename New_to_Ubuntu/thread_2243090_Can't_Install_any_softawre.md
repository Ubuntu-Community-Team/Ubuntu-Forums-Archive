---
title: "Can't Install any softawre"
date: 2014-09-06
forum: New to Ubuntu
---

### Post by connor10 on 2014-09-06
Hi I am new to Ubuntu and thus have no idea why this is happening but everytime I try to install any software (for examlpe I wanted to install the package "pill" so I could try out google's tesseract software) this is what I get

  sudo apt-get install pill
  Reading package lists....Done
  Building dependency tree
  Reading state information....Done
  E: Unable to locate package pill

yet if I search for it like this:   sudo apt-cache search pill
it searches and successfully finds a bunch of matches
I should also mention I did: sudo apt-get update 
and updated everything successfully. Also I was able to install "pip" using sudo apt-get install pip  so I don't understand what the issue is. 
Thanks for the help

---

### Post by sammiev on 2014-09-06
Have you tried there site? 

They do have deb packages [here]("http://www.getdeb.net/software/Penguin%20Pills").

---

### Post by EuclideanCoffee on 2014-09-06
Have you tried the Software Center?

You can also try installing Synaptic Package Manager and then looking for the package.

---

### Post by grahammechanical on 2014-09-06
You may be using the wrong command. The command apt-get install is correct but you may be spelling the package wrongly or it may be a more specific package name. It may simply be that the package that you are trying to install is not in the Ubuntu repositories. Or that you have not enabled all the repositories. Do you have universe and multiverse repositories enabled?

Regards.

---

### Post by coffeecat on 2014-09-06
Welcome to the forum.

> **connor10 said:**
> Hi I am new to Ubuntu and thus have no idea why this is happening

I can tell you why that is happening. There is no package called "pill" in any of the four standard Ubuntu repositories.
 
> **connor10 said:**
> 
yet if I search for it like this:   sudo apt-cache search pill
it searches and successfully finds a bunch of matches

Yes, but look at the matches.

```
$ sudo apt-cache search pill
libplasma3 - Plasma Library for the KDE Platform
python-pil - Python Imaging Library (Pillow fork)
python-pil.imagetk - Python Imaging Library - ImageTk Module (Pillow fork)
python-sane - Python Imaging Library - SANE interface (Pillow fork)
python3-pil - Python Imaging Library (Python3)
hannah - pacman-like game, child oriented
hannah-data - pacman-like game, child oriented - data files
kapman - Pac-Man clone
metacity-themes - Themes for the Gtk2 metacity window manager
python-reclass - hierarchical inventory backend for configuration management systems
reclass - hierarchical inventory backend for configuration management systems
ttf-aenigma - 465 free TrueType fonts by Brian Kent

```

The string pill will be somewhere in the listed package metadata. For example: *hannah - pacman-like game, child oriented* - if you run:

```
sudo apt-cache search --full pill
```

You get this for hannah:

```
Package: hannah
Description-md5: bcc88734f78b965d8a248d3ccad34674
Description-en: pacman-like game, child oriented
 Help Hannah's Horse is like a cross between Pacman and the Dizzy game
 "Fastfood". The objective is to move Hannah to collect the **pills** around
 the maze while avoiding the ghosts. Moving around the maze there are also
 carrots which Hannah must also collect in order to complete the level.
```

(My bold).

What exactly is "pill" and what does it have to do with tesseract? I have never heard of it. If you give more details, perhaps people will be able to help you with this.

---

### Post by JeQhdMD on 2014-09-06
What grahammechanical say's is right.   The program you actually want is in the Ubuntu Software Center and is called "YAGF" . . . .

---

