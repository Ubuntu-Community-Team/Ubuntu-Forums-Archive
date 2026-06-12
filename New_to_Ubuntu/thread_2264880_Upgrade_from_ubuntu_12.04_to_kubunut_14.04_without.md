---
title: "Upgrade from ubuntu 12.04 to kubunut 14.04 without reintsalling all programs"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by mohsenof on 2015-02-10
Hello
I have been working on Ubuntu 12.04 for some years and I've installed some programs on it. Now I want to upgrade to Kubuntu 14.04 but I don't want to reintsall all programs. I've downloaded kubuntu installer but don't know how to install it to save my programs.
Thank you

---

### Post by Bucky Ball on 2015-02-10
If you were sticking with Ubuntu, then you could do an upgrade via the Software Updater to 14.04 LTS and all programs would remain. As you are changing to Kubuntu, that would mean a complete reinstall, so your programs and settings would be wiped. 

What you could do is install kubuntu-desktop, which is pretty much the same as installing Kubuntu, and then upgrade via the Software Updater to 14.04 LTS.

The problem with this method is that you will have all the Ubuntu default programs, dependencies AND the Kubuntu programs and dependencies. This can get bloated and menus cluttered and you will find you have redundant apps (Kubuntu apps will do the same things as some you already have installed).

If you are wanting to move to Kubuntu, these are your two options: reinstall and lose your installed apps. Upgrade as explained, but you will have a bit of bloat and redundant programs. Personally, I'd install Kubuntu, perhaps on another partition leaving 12.04 where it is for the moment, and start again. But that's me. Good luck. ;)

---

### Post by monkeybrain20122 on 2015-02-10
Why don't you just back up your data and do a clean install? A lot faster and safer. If you have a separate /home that is even easier (so make one this time if you haven't one already) If you 'upgrade' with the update-manager it would take a long time (maybe hours) and there is a good chance that you will end up with a broken system if you have modified your system in ways that made it different from 'factory condition' (installing proprietary drivers, ppas and third party applications, tweaked configuration files etc) A clean install takes about 20 minutes and maybe another 10 to reinstall the software. It would take longer if you have some customisation, but as noted, 'upgrade' will likely fail if you have a lot of non trivial customisations.

---

### Post by fantab on 2015-02-10
> **mohsenof said:**
> Hello
I have been working on Ubuntu 12.04 for some years and I've installed some programs on it. Now I want to upgrade to Kubuntu 14.04 but I don't want to reintsall all programs. I've downloaded kubuntu installer but don't know how to install it to save my programs.
Thank you

Its not possible to upgrade from Ubuntu to Kubuntu, as suggested previously. You need a clean fresh install.
Ubuntu runs on Gtk+ and Kubuntu on Qt+. They use very different libraries and dependencies.  
So if you remove ubuntu-desktop and install kubuntu-desktop you'll end up with gtk and qt mess. 
If the programs you installed need gtk then on Kubuntu these will pull in loads of gtk libs and deps. Not advisable.


If I were you, I would install Kubuntu on a separate partition, update ubuntu 12.04 to 14.04 and dual boot Ubuntu and Kubuntu.
I would also have my personal data on a separate linux partition shared between Ubu and Kubu. No need of a /home partition.

---

### Post by newb85 on 2015-02-11
What is it you like about Kubuntu?  Is it the default apps, or the Plasma desktop environment.  If it's just the environment, you can install it with
```
sudo apt-get install plasma-desktop
```

It won't be configured exactly as in Kubuntu, though.  That would be achieved by also
```
sudo apt-get install kubuntu-default-settings
```

If you decide there's an app you also want, it can also be manually installed.

---

