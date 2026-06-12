---
title: "Howto: Install latest version of Midori [Browser]"
date: 2009-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Pixel on 2009-06-29
This is my first how to guide, so bare with me a little bit.

**Table of Contents**
   -- Intro
   -- Installation
   -- Flash
   -- Benchmarks

> Midori (&#32209;?, Japanese for green) is a web browser that aims to be lightweight and fast. It uses the WebKit rendering engine and the GTK+*2 interface. Midori is part of the Xfce desktop environment's Goodies component.[2] As of February 2009, the project is still at alpha status.

**Office website:** [http://www.twotoasts.de/]("http://www.twotoasts.de/")

**Should I use Midori?**
Currently, as of version 0.1.7, Midori is still quite buggy.  If you don't mind a browser that might crash every once in awhile, and want to try out something new, then go for it.  I recommend that you still keep firefox installed, or whatever you are using as your primary browser, just incase you come across something that doesn't quite work as it should.

**Installation**

First, you must add two PPA's to your sources.list

```
sudo gedit /etc/apt/sources.list
```

Add these lines to the bottom of the file, then save and close it.

```
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main

deb http://ppa.launchpad.net/midori/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/midori/ppa/ubuntu jaunty main 
```

Now you must add the keys to access the new PPA's.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
```

Now update your repositories.

```
sudo apt-get update
```

And install Midori.

```
sudo apt-get install midori
```

All the dependencies should be installed and you will have the latest version installed, if for some reason it doesn't just let me know and I'll try my best to figure out what happened.

**Flash**
You can install flash as your normally would with any other browser, if you haven't installed it already, you can do so with this command:

```
sudo apt-get install flashplugin-nonfree
```

**Benchmarks**
For any of those interested, I ran a few benchmarks using SunSpider's JavaScript benchmarks.  Please note that you might not get the same speeds reported here, because of various hardware and software configurations.

Midori v0.1.7-7ca782e
Results: 1135.0ms +/- 3.8%
Details: [http://tinyurl.com/lsvx7a](http://tinyurl.com/lsvx7a)

Firefox v3.5
Results: 4018.0ms +/- 1.9%
Details: [http://tinyurl.com/l5h7vg](http://tinyurl.com/l5h7vg)

---

### Post by mrkennie on 2009-07-01
Nice howto, especially including how to add the keys. :)

Been watching Midori pretty closely and deserves a lot more recognition than it gets. Getting a bit fedup with the performance of Firefox in Linux and Midori looks set to become an ideal alternative! Flash already seems to run smoother using it (not that I'm a great fan a Flash). Love the new speed dial feature too!

---

### Post by weboide on 2009-07-06
Thanks for your howto, this works perfectly!;)

---

### Post by NJLash on 2009-07-24
Hi, thanks for the howto.
I guess something has broke since you put this up.  Midori has since updated to 0.1.8... What should I do?

sudo apt-get install midori
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  midori: Depends: libsoup2.4-1 (>= 2.27.2) but 2.26.0-0ubuntu3 is to be installed
          Depends: libwebkit-1.0-2 (>= 1.1.6) but it is not going to be installed
E: Broken packages

---

### Post by y6FgBn)~v on 2009-07-24
> **NJLash said:**
> Hi, thanks for the howto.
I guess something has broke since you put this up.  Midori has since updated to 0.1.8... What should I do?

sudo apt-get install midori
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  midori: Depends: libsoup2.4-1 (>= 2.27.2) but 2.26.0-0ubuntu3 is to be installed
          Depends: libwebkit-1.0-2 (>= 1.1.6) but it is not going to be installed
E: Broken packages

Also getting this error when trying to install.

---

### Post by user 123 on 2009-07-30
> **pcybill said:**
> Also getting this error when trying to install.

Ensure you have all of your repositories enabled.
I installed it through synaptic and it worked fine for me.

---

### Post by chriskin on 2009-08-02
it works fine for me but once i open a tab, it isn't shown like normal tabs do on the toolbar.
how can i change it?

---

### Post by y6FgBn)~v on 2009-08-07
> **user 123 said:**
> Ensure you have all of your repositories enabled.
I installed it through synaptic and it worked fine for me.

This had no effect.

---

### Post by cyb3rkn19ht on 2009-11-19
Great tutorial everything worked the first time. Thank you! I love Midori! The Ubuntu repository does not update it version that much.

Thanks,
      Brooks

---

### Post by tattee on 2010-02-19
I have no direct access to internet, so how can I install midori manually?? thanks in advance!

---

