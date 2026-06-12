---
title: "lots of fun questions...."
date: 2016-02-10
forum: New to Ubuntu
---

### Post by jesse_bruffett on 2016-02-10
Im planning on switching from OS X to Ubuntu within the next few weeks. Right now I'm getting together a list of apps I will need and want. I have some experience with linux an I’m very picky about what apps I use and their GUI’s. I spend a lot of time in terminal too but I have questions about options for apps and how to install some apps from other DE’s. How do I install specific apps from KDE without installing all of them? I will probably install just the KDE DE at some point but I still wont want all the apps from it. KRDA is an example of an app I want from KDE. Geary from Gnome is another app I want that’s not part of Unity. How simple or difficult is it to install them? Ive done some searching and haven’t found a lot. Ice Weasel is another app id like. 
 
Here is a big one that I don’t know what I want yet. I need a terminal emulator like iterm2. It need to have tabs, be hot key hide and showable and have adjustable translucency. Is there such an app for linux? I haven’t found anything as of yet. 
 
Thanks for the help guys and sorry that these may seem like noob questions but in this world im not too experienced.

---

### Post by coldraven on 2016-02-11
> Here is a big one that I don&#8217;t know what I want yet. I need a terminal  emulator like iterm2. It need to have tabs, be hot key hide and showable  and have adjustable translucency. Is there such an app for linux? I  haven&#8217;t found anything as of yet.
guake is good and meets all your requirements. It's in the Software Centre
[https://en.wikipedia.org/wiki/Guake](https://en.wikipedia.org/wiki/Guake)

---

### Post by haplorrhine on 2016-02-11
The default "Terminal", which opens with Ctrl+Alt+T, has adjustable transparency in Edit > Profile Preferences > Background.

---

### Post by sandyd on 2016-02-11
> **jesse_bruffett said:**
> Im planning on switching from OS X to Ubuntu within the next few weeks. Right now I'm getting together a list of apps I will need and want. I have some experience with linux an I&#8217;m very picky about what apps I use and their GUI&#8217;s. I spend a lot of time in terminal too but I have questions about options for apps and how to install some apps from other DE&#8217;s. How do I install specific apps from KDE without installing all of them? I will probably install just the KDE DE at some point but I still wont want all the apps from it. KRDA is an example of an app I want from KDE. Geary from Gnome is another app I want that&#8217;s not part of Unity. How simple or difficult is it to install them? Ive done some searching and haven&#8217;t found a lot. Ice Weasel is another app id like. 
 
Here is a big one that I don&#8217;t know what I want yet. I need a terminal emulator like iterm2. It need to have tabs, be hot key hide and showable and have adjustable translucency. Is there such an app for linux? I haven&#8217;t found anything as of yet. 
 
Thanks for the help guys and sorry that these may seem like noob questions but in this world im not too experienced.

For minimal KDE with default Kubuntu settings + GTK Integration:
```

sudo apt-get install kde-plasma-desktop kubuntu-default-settings kde-config-gtk-style gtk3-engines-oxygen
```

Note that the above is for releases that do not have KDE Plasma - the only release that is still supported with the old KDE is Ubuntu 14.04 LTS. 

For KDE Plasma (Ubuntu 15.10 and up), try
```

sudo apt-get install plasma-desktop kde-config-gtk-style gtk3-engines-oxygen
```

Note that the above does not come with a login screen. You can install sddm or lightdm if you do not have one.

---

### Post by mj0g on 2016-07-04
Geary should work well on Ubuntu with Unity. You can make sure you always have the most up-to-date version by adding this PPA to your software sources: [https://launchpad.net/~geary-team/+archive/ubuntu/releases](https://launchpad.net/~geary-team/+archive/ubuntu/releases)

---

### Post by &amp;KyT$0P# on 2016-07-04
> **jesse_bruffett said:**
>  I have questions about options for apps and how to install some apps from other DE’s. How do I install specific apps from KDE without installing all of them? I will probably install just the KDE DE at some point but I still wont want all the apps from it. KRDA is an example of an app I want from KDE. Geary from Gnome is another app I want that’s not part of Unity. How simple or difficult is it to install them? Ive done some searching and haven’t found a lot. 
For the apps that are available through Ubuntu package manager, such as these, you can just install the packages that contain them the same way you would install any other package.  Keep in mind that they probably will need to pull in a lot of backend dependencies from their "native" desktop environment. (KDE apps especially will.)

> Ice Weasel is another app id like.
Iceweasel is Debian-specific, so you would probably have to build it from source on an Ubuntu machine in order to get an Ubuntu-compatible version of it.

It's basically just a re-branded Firefox anyway.. so why do you want Iceweasel as opposed to Firefox?

---

### Post by vasa1 on 2016-07-04
> **halogen2 said:**
> ...

Iceweasel is ... basically just a re-branded Firefox anyway.. so why do you want Iceweasel as opposed to Firefox?
+1.

Plus even [Debian is moving back to Firefox]("https://en.wikipedia.org/wiki/Mozilla_software_rebranded_by_Debian"):> In 2016, a number of Mozilla employees and Debian maintainers argued that the branding was no longer needed, and on 10 March 2016, Debian's unstable branch switched back to the Mozilla branding, with the stable branch planning to switch after Iceweasel's end of life.

---

