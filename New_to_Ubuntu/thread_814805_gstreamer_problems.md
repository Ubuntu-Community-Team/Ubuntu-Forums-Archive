---
title: "gstreamer problems"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ratdude747 on 2008-06-01
Hi. I was trying to play mp3 files off my flash drive, but totem said I needed new plugins. That computer has no internet access and all of my other stuff runs on windows. Can I download the package elsewhere and then install it?

---

### Post by sayakb on 2008-06-01
On a remote PC having internet, do:
```
code sudo apt-get install ubuntu-restricted-extras
```

Now goto /var/cache/apt/archives folder and copy all gstreamer deb packages on a flash disk and install them onto your computer.

---

### Post by ratdude747 on 2008-06-01
uh... The computer with internet runs windows, not linux (ubuntu, etc.)

---

### Post by wolfen69 on 2008-06-01
i believe you could use a live cd on the windows machine to accomplish this.

---

### Post by Maestro23 on 2008-06-01
Goto Ubuntu Packages and d/l them from you XP machine. Search "Restricted Extras".

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by ratdude747 on 2008-06-01
I installed the plugins. Unfortunately, totem did not load the codec and It prompts for the gstreamer extra plugins page. with no internet connection, I am bact to where I started. :mad:

---

### Post by wolfen69 on 2008-06-01
take out the hard drive from the ubuntu machine, take it to the net connected pc and temporarily swap drives and install ubuntu and configure it. bring it back and pop it in the ubuntu machine.(with cd in drive) i bet it works.

---

### Post by ratdude747 on 2008-06-01
I dont mean to complain, but That trick may not work. the other computer has a dial-up modem that is unsupported by linux, and that is the only method I have of connecting

---

