---
title: "I broke my last installation can I transfer stuff from the old one"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-07-25
I just re-installed because I broke my last installation. 

Can I transfer the stuff I installed on the broken one on to the new one?

Stuff like installed programs.

I can access the partition.

Thanks in advanced!

---

### Post by LowSky on 2008-07-25
you should really just reinstall them, but if you have your old /home folder you can reload your settings easily.

---

### Post by pluckypigeon on 2008-07-25
> **LowSky said:**
> you should really just reinstall them, but if you have your old /home folder you can reload your settings easily.

I have my /home directory on a different hard drive anyway so that is ok

I just want to copy and paste the programs i have installed, im just not sure what i should copy and what i shouldnt.

Does anyone know a way that i can?

---

### Post by Thelasko on 2008-07-25
> Can I transfer the stuff I installed on the broken one on to the new one?

Stuff like installed programs.
1.  If you broke your last install, it might not be a good idea to transfer programs and configuration files.  it might break your current install.  Transferring regular files, like music, video, and documents is fine.

2.  Always use APT (apt get), synaptic, or "Applications>Add & Remove Software" to install and remove software.  Using other methods will break Ubuntu if you don't know what you are doing.

---

### Post by pluckypigeon on 2008-07-25
> **Thelasko said:**
> 1.  If you broke your last install, it might not be a good idea to transfer programs and configuration files.  it might break your current install.  Transferring regular files, like music, video, and documents is fine.

2.  Always use APT (apt get), synaptic, or "Applications>Add & Remove Software" to install and remove software.  Using other methods will break Ubuntu if you don't know what you are doing.

i broke my install messing around with wrong repos, i know it was wrong

so im guess doing this is impossible then

---

### Post by Thelasko on 2008-07-25
> so im guess doing this is impossible then 
Nothing is impossible in Linux

Trying to move programs from your old install to the new install will be very difficult, and you will likely break something.  It's much easier to reinstall them and get it right.

If you are concerned about losing your settings, I will give you some pointers for moving those, but I usually tell new users to avoid doing so.

Most program settings are hidden in your home folder with a "." in the beginning of the file name.  You can view them by pressing ctrl+h

You can try copying some of them over to your new install.  This works for some programs better than others (Firefox works very well, Gnome not so much).  If your program stops working properly after you move the configuration files, close the program, delete the files, and restart the program (when the program restarts it will recreate the files with default settings)

Good luck

---

### Post by pluckypigeon on 2008-07-25
is there a way to see what was in my application menu??

I know some stuff isnt stored in the default place.

any ideas??:confused:

---

### Post by LowSky on 2008-07-25
not that I am aware of.

but what you can do is create your own version of ubuntu with all your aps and prefeences preinstalled, so you have a decent start, if you need to start fresh again.

look at this
[http://maketecheasier.com/reconstructor-creating-your-own-ubuntu-distribution/2008/07/05](http://maketecheasier.com/reconstructor-creating-your-own-ubuntu-distribution/2008/07/05)

---

### Post by Thelasko on 2008-07-25
The contents of your application menu are stored in one of the /home/username/.gnome folders (there are several and I can't remember all of their names) last time I checked.  This is part of the reason I don't recommend moving those folders over, by doing so you could add things to the menu that aren't installed.  Try digging through there and see what you find.  If you find the applications list, only use it as a reference to set up your fresh install.  Treat it like a term paper that got accidentally thrown in the trash, use it for it's information only.  Don't try to use it as is.

---

### Post by arpanaut on 2008-07-25
You could tale a look in "/var/cache/apt/archives" on your old install to see what is there and use as a guide to install in NEW.
I'm not sure I would do a wholesale installation of all these packages, some may be dated etc.
I personnaly enjoy configuring a fresh install taking into account my good/bad experiences and going from there.  Sure it's a lot of work but it sure feels good having a nice clean set-up and going from there. Plus knowing my previous screw-ups aren't hanging over me.

Whatever?

There is an app. called "aptoncd", but I don't know if you need a working system to get that to go.

[http://packages.ubuntu.com/hardy/aptoncd](http://packages.ubuntu.com/hardy/aptoncd)

---

