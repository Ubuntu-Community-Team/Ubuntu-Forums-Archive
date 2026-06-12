---
title: "Installing local apps via synaptic"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by dult on 2014-02-06
Hello everyone,

I've finally moved to linux, first puppy, then linux lite, and now lubuntu.

The latter one is the one I'm most satisfied (I use loads of old pcs). The number of apps installed also please me because it's less I have to uninstall.

Now, lubuntu LTS will be coming out in April, and though it will take me about 1 hour to install all the apps I use and uninstall all the one's I don't need, I was wondering if It's  possible to install all the apps I use (blender, gimp, chromium, libreoffice, php5 and apache2 for example) in my local user so I can simply backup my home folder and copy it into the new lubuntu install... I would also like to keep all  my config (visual and menu wise) in my user folder.

I've searched on how to do this, but I can't seem to find a way using synaptic to ALSO keep them updated.

Any tips?

Thanks in advance.

---

### Post by robin7 on 2014-02-06
In Synaptic there is a bit of software called **aptoncd** ("apt on CD").  It lets you copy the packages (.deb files in Lubuntu) of your installed applications onto a CD.  Then you can use the CD as a "repository" to install the software on another computer.

However:  A lot of things change from one release to another, especially from one LTS release to the next, and the older copied software may simply not be compatible with the newer OS.  In my Xubuntu, for example, the differences between 12.04 and the next LTS are huge, ginormous, gargantuan changes, like the whole desktop environment (xfce 4.8 to xfce 4.10) and a bunch of other stuff.

Aptoncd is nice for installing software on multiple computers without a connection to the internet and stuff, and great for "backing up" some installed programs, but with upgrades it may be a headache if a lot of stuff has changed.

---

### Post by ajgreeny on 2014-02-06
I used to use aptoncd but now simply copy the package cache from /var/cache/apt/archives/ to a usb drive and then copy them to the /var/cache/apt/archives/ folder in the second machine, which effectively does exactly the same thing as aptoncd.

However, I am not quite sure what you mean by locally installed applications, but I can tell you that you can not choose to install packages to your /home when using any of the apt frontends or applications, such as synaptic, aptitude, update-manager, apt-get, etc etc.

---

### Post by dult on 2014-02-06
So, if I understand correctly, it's better to simply backup that cache folder (I believe it'll hold every app installed) and then copy it back to the place and fix broken packages...right?

---

### Post by ajgreeny on 2014-02-06
By default the cache will only keep packages that are still available in the repos, so if, for example a new version of blender appeared and you updated your version, the old version would no longer be available in the repos and would automatically be removed from your apt cache.

You can change that if you wish, to keep everything permanently in cache by using the "files" tab of synaptic->settings-> preferences, but beware; if you do not have a lot of disk space your cache could grow and become very large.

---

### Post by dult on 2014-02-06
Will this keep all libs also? How about lubuntu core apps like LXDE?

---

### Post by ajgreeny on 2014-02-06
Yes, everything you have installed or updated after the original installation with any apt frontend will be in the cache.

---

