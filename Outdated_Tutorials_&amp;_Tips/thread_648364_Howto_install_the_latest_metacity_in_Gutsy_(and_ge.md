---
title: "Howto: install the latest metacity in Gutsy (and get a built-in composite manager)"
date: 2007-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by picpak on 2007-12-23
What's new in Metacity 2.21.5 is a built-in compositing manager, meaning that you don't have to run xcompmgr or similar programs alongside it. If you use Hardy, you've already got it and can skip to step 7 to turn it on. For Gutsy, however, you can either

a) go to the bottom of this post and install my .debs or
b) compile it yourself.

[size=4]Method 1: Compiling[/size]

The longer method. Use method 2 if you prefer.

1) Open up a terminal (Applications>Accessories>Terminal) and edit the file /etc/apt/sources.list:

```
gksudo gedit /etc/apt/sources.list
```

place the following on a new line at the bottom:

```
deb-src http://ca.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
```

Save it and exit.

2) Update so that it notices the new line:

```
sudo aptitude update
```

3) Install the needed programs for compiling metacity:

```
sudo aptitude install build-essential cdbs devscripts dh-make fakeroot
sudo apt-get build-dep metacity
```

4) Get the source package:

```
mkdir -p ~/packages/metacity
cd ~/packages/metacity
apt-get source metacity
cd metacity-*
```

5) Add a new entry to the changelog indicating that this is being built on Gutsy:

```
dch -iDgutsy
```

The first section should look something like this:

```
metacity (**1:2.22.0-0ubuntu1~gutsy1**) gutsy; urgency=low

  * Adopted for Gutsy

 -- Firstname Lastname <youremail@yourhost.com> Sun, 23 Dec 2007 11:52:10 -0600
```

Press Ctrl-X to save and exit the file.

6) Build and install the new metacity:

```
dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../metacity*.deb ../libmetacity0*.deb
```

7) You're still not done! Run the following to turn on the compositor:

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

You may need to log out and in for the changes to take effect.

8) Now re-open the file /etc/apt/sources.list:

```
gksudo gedit /etc/apt/sources.list
```

and remove the following line:

```
deb-src http://ca.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
```

Save it and exit.

9) Update again:

```
sudo aptitude update
```

Enjoy your new metacity!

[size=4]Method 2: Installing debs[/size]

The much faster method. Download and install 3 files, enable compositing and you're done.

1) Download the following files:

[metacity_2.21.5-0ubuntu1~gutsy1_i386.deb](http://www.sendspace.com/file/m604e5)
[libmetacity0_2.21.5-0ubuntu1~gutsy1_i386.deb](http://www.sendspace.com/file/e7iee6)
[metacity-common_2.21.5-0ubuntu1~gutsy1_all.deb](http://www.sendspace.com/file/y0wbm9)

2) Install them:

```
sudo dpkg -i metacity*.deb libmetacity0*.deb
```

libmetacity-dev is optional, but I've uploaded it just in case:

[libmetacity-dev_2.21.5-0ubuntu1~gutsy1_i386.deb](http://www.sendspace.com/file/ytnqvs)

3) Remember to run the following to enable the compositor!

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

You may need to log out and in for the changes to take effect. Enjoy!

---

### Post by Ttech on 2007-12-26
> **picpak said:**
> What's new in Metacity 2.21.5 is a built-in compositing manager, meaning that you don't have to run xcompmgr or similar programs alongside it. If you use Hardy, you've already got it and can skip to step 7 to turn it on. For Gutsy, however, you can either

a) go to the bottom of this post and install my .debs or
b) compile it yourself.

[size=4]Method 1: Compiling[/size]

The longer method. Use method 2 if you prefer.

1) Open up a terminal (Applications>Accessories>Terminal) and edit the file /etc/apt/sources.list:

```
gksudo gedit /etc/apt/sources.list
```

place the following on a new line at the bottom:

```
deb-src http://ca.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
```

Save it and exit.

2) Update so that it notices the new line:

```
sudo aptitude update
```

3) Install the needed programs for compiling metacity:

```
sudo aptitude install build-essential cdbs devscripts dh-make fakeroot
sudo apt-get build-dep metacity
```

4) Get the source package:

```
mkdir -p ~/packages/metacity
cd ~/packages/metacity
apt-get source metacity
cd metacity-2.21.5
```

5) Add a new entry to the changelog indicating that this is being built on Gutsy:

```
dch -iDgutsy
```

The first section should look something like this:

```
metacity (**1:2.21.5-0ubuntu1~gutsy1**) gutsy; urgency=low

  * Adopted for Gutsy

 -- Firstname Lastname <youremail@yourhost.com> Sun, 23 Dec 2007 11:52:10 -0600
```

Press Ctrl-X to save and exit the file.

6) Build and install the new metacity:

```
dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../metacity_2.21.5-0ubuntu1~gutsy1_i386.deb ../metacity-common_2.21.5-0ubuntu1~gutsy1_all.deb ../libmetacity0_2.21.5-0ubuntu1~gutsy1_i386.deb
```

7) You're still not done! Run the following to turn on the compositor:

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

You may need to log out and in for the changes to take effect.

8) Now re-open the file /etc/apt/sources.list:

```
gksudo gedit /etc/apt/sources.list
```

and remove the following line:

```
deb-src http://ca.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
```

Save it and exit.

9) Update again:

```
sudo aptitude update
```

Enjoy your new metacity!

[size=4]Method 2: Installing debs[/size]

The much faster method. Download and install 3 files, enable composting and you're done.

1) Download the following files:

[metacity_2.21.5-0ubuntu1~gutsy1_i386.deb](http://www.sendspace.com/file/m604e5)
[libmetacity0_2.21.5-0ubuntu1~gutsy1_i386.deb](http://www.sendspace.com/file/e7iee6)
[metacity-common_2.21.5-0ubuntu1~gutsy1_all.deb](http://www.sendspace.com/file/y0wbm9)

2) Install them:

```
sudo dpkg -i metacity_2.21.5-0ubuntu1~gutsy1_i386.deb metacity-common_2.21.5-0ubuntu1~gutsy1_all.deb libmetacity0_2.21.5-0ubuntu1~gutsy1_i386.deb
```

libmetacity-dev is optional, but I've uploaded it just in case:

[libmetacity-dev_2.21.5-0ubuntu1~gutsy1_i386.deb](http://www.sendspace.com/file/ytnqvs)

3) Remember to run the following to enable the compositor!

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

You may need to log out and in for the changes to take effect. Enjoy!


Is there a way I can switch between the Ubuntu default and MetaCity?

---

### Post by picpak on 2007-12-27
> **Ttech said:**
> Is there a way I can switch between the Ubuntu default and MetaCity?

Well, if you turn off compositing you have a near-Ubuntu default, but I don't think you can switch between this version and the Ubuntu default without reinstalling the packages. Sorry.

---

### Post by ShodanjoDM on 2008-03-08
Thank you very much. It's working just fine :)

Followed the instruction and now I have drop shadows without having to use Compiz :D

Oh btw, the latest metacity version when I compiled this evening is 2.21.21

---

### Post by yizuman on 2008-03-08
Getting this error now from number 6...

> cannot access archive: No such file or directory
Errors were encountered while processing:
 ../metacity_2.21.21-0ubuntu2~gutsy1_i386.deb
 ../metacity-common_2.21.21-0ubuntu2~gutsy1_all.deb
 ../libmetacity0_2.21.21-0ubuntu2~gutsy1_i386.deb
anonymous@anonymous:~/packages/metacity/metacity-2.21.21$ 


Now what?

---

### Post by yizuman on 2008-03-09
bump! sorry! Anyone help?

---

### Post by yizuman on 2008-03-09
None of the deb files exists. They're gone. The newest version is 2.23.2 and there isn't any deb file installer for that version available.

[http://ftp.gnome.org/pub/gnome/sources/metacity/2.23/](http://ftp.gnome.org/pub/gnome/sources/metacity/2.23/)

help?

I was on number 6 and nowhere to go now...

---

### Post by picpak on 2008-03-09
> **yizuman said:**
> Getting this error now from number 6...



Now what?

Sorry, I edited the guide yesterday to work with metacity 2.21.21 and I may have made a typo. Try running:

```
sudo dpkg -i ../libmetacity0*.deb ../metacity*.deb
```

instead.

---

### Post by ShodanjoDM on 2008-03-09
Hmm, I wonder what's changed in the 2.23.2 version...

So far I can only find this:

[http://www.linuxcompatible.org/metacity_2.23.2_released_s107699.html](http://www.linuxcompatible.org/metacity_2.23.2_released_s107699.html)

> metacity 2.23.2 has been released

    "Metacity is a simple window manager that integrates nicely with GNOME 2.

    * What's changed ?
    =================

    Almost nothing, except that a few debug statements were removed. 

EDIT: 
Now this is what i call funny: [http://blogs.gnome.org/metacity/2008/03/07/2232-the-rather-embarrassing-release/](http://blogs.gnome.org/metacity/2008/03/07/2232-the-rather-embarrassing-release/)

I guess there's no need to download and recompile then :lolflag:

---

### Post by yizuman on 2008-03-10
Thanks it worked, but I noticed a change in the version when I typed in the command,,,

> apt-get source metacity

The version it gave me was 2.22.2 (I think, I know it isn't .21 anymore.

---

### Post by yizuman on 2008-03-10
Ok, I got a stupid question, after installing all this, (I'm a newb btw) and I don't see "Metacity" anywhere in "system", so my question is, is Metacity the same as "appearance" in "system" "preferences"?

Color me a confused newb.

(I feel like an idiot, so sorry for asking)

---

### Post by ShodanjoDM on 2008-03-12
It's in the System>>Appearance>>Customize>>Window Border

---

### Post by picpak on 2008-03-12
I've edited the guide to work with any current and upcoming metacity versions.

Compiling metacity 2.22 right now... :)

---

### Post by captive on 2008-03-13
Hi!
I read today about metacity compositing capabilities; I was just wondering how it compares to compiz. Which kind of effects can it handle? How do you configure it? Is it as smooth as compiz, on the same hardware?
Thanks in advance!

---

### Post by ShodanjoDM on 2008-03-13
> **captive said:**
> Hi!
I read today about metacity compositing capabilities; I was just wondering how it compares to compiz. Which kind of effects can it handle? How do you configure it? Is it as smooth as compiz, on the same hardware?
Thanks in advance!

It just gives a basic (unconfigurable) drop shadows under menus and open windows. But since it means using metacity as your composite manager, you can also run screenlets without rendering problem.

Personally I prefer this basic capabilities over compiz. And it takes less hardware resources too.

---

### Post by frodon on 2008-03-13
According to gnome release notes it has also transparency capabilities and live preview in Alt+Tab swicher.

BTW, anyone can post a screenshot  showing the shadow and live preview just for the pleasure ?

I myself also prefer metacity over compiz as it is rock solid and lighter.

---

### Post by captive on 2008-03-13
> **frodon said:**
> 
I myself also prefer metacity over compiz as it is rock solid and lighter.

And maybe it won't take 2 weeks to login to your desktop as compiz does...:(

---

### Post by ShodanjoDM on 2008-03-13
> **frodon said:**
> According to gnome release notes it has also transparency capabilities and live preview in Alt+Tab swicher.

BTW, anyone can post a screenshot  showing the shadow and live preview just for the pleasure ?

I myself also prefer metacity over compiz as it is rock solid and lighter.

Ah, how can no one remember to put a screenshot? It's a must! :D
See the attachments below :guitar:

Gimp'd, resized from 1280x960 to 1024x768 & sharpened a little.

Anyway, if you want to enable compiz, you must turn off the metacity drop shadow in the gconf-editor first. Otherwise, the compiz won't run.

---

### Post by skrribble on 2008-03-27
i can't get screenlets to run just using the new metacity with the compositing enabled... i know the compositing is working because AWN works, but screenlets wont show up... any suggestions??

---

### Post by xfile087 on 2008-03-29
> **ShodanjoDM said:**
> Ah, how can no one remember to put a screenshot? It's a must! :D
See the attachments below :guitar:

Gimp'd, resized from 1280x960 to 1024x768 & sharpened a little.

Anyway, if you want to enable compiz, you must turn off the metacity drop shadow in the gconf-editor first. Otherwise, the compiz won't run.

May I ask what theme your running? I know I've seen it before but I can't quite remember the name - it looks pretty slick!

---

### Post by Nythain on 2008-03-29
> **frodon said:**
> According to gnome release notes it has also transparency capabilities and live preview in Alt+Tab swicher.
that is exactly what i was hoping for... only reason i even consider running compiz is the true transparency on things like gnome-terminal... and the live previews it provides... definately gonna have to look into the new metacity

---

### Post by ShodanjoDM on 2008-04-01
> **xfile087 said:**
> May I ask what theme your running? I know I've seen it before but I can't quite remember the name - it looks pretty slick!

Because it *is* [Slickness]("http://gnome-look.org/content/show.php/SlicknesS?content=71993"). :D

---

### Post by ShodanjoDM on 2008-04-01
> **skrribble said:**
> i can't get screenlets to run just using the new metacity with the compositing enabled... i know the compositing is working because AWN works, but screenlets wont show up... any suggestions??

Hmm... try to restart all running screenlets perhaps? Do you have the newest version?

---

### Post by skrribble on 2008-04-01
> Hmm... try to restart all running screenlets perhaps? Do you have the newest version?I have the newest version, and I've restarted, reinstalled (both numerous times), and done everything else I can think of.  I've basically given up for now and just decided to try it again when I get Hardy installed.  It'll only be a couple of weeks anyway.

---

### Post by JorgeMIlla08 on 2009-02-19
> **picpak said:**
> What's new in Metacity 2.21.5 is a built-in compositing manager, meaning that you don't have to run xcompmgr or similar programs alongside it. If you use Hardy, you've already got it and can skip to step 7 to turn it on. For Gutsy, however, you can either

a) go to the bottom of this post and install my .debs or
b) compile it yourself.

You may need to log out and in for the changes to take effect. Enjoy!

The deb files are gone is there an easier way to install? throug synaptic maybe?...

---

