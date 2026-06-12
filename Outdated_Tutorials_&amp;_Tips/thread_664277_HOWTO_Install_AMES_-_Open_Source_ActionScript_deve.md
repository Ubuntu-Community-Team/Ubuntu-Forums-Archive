---
title: "HOWTO: Install AMES - Open Source ActionScript development for everyone!"
date: 2008-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by JT673 on 2008-01-11
Hello, this is my first time making a deb package and writing a tutorial, but it's quite stable.

[SIZE="4"]What is AMES?[/SIZE]

AMES (ASDT, MTASC, Eclipse, Swfmill) is a fully open-source ActionScript editing-and-compiling-and-viewing suite.  You might have heard about sister suites FAMES and FAME, but neither of those are fully open source .I'll make FAMES deb later.

The deb package I made is an automatically configured Eclipse instance, and a workspace in your home directory that already includes an example.  Skip down to "What if I want to use my current Eclipse install?" if you...want to keep your current Eclipse install.
[SIZE="4"]
Why do I want to install it?[/SIZE]

1) Because Adobe's Flash isn't compatible with Wine anymore, and you can't register other versions anymore :(.  And you can't keep copying that wine drive forever. 
2) You love open source.

[SIZE="4"]How do I install it?[/SIZE]

On Gutsy and before, you need to install the swfmill package, which is only available for Hardy and up:

[http://packages.ubuntu.com/hardy/utils/swfmill]("http://packages.ubuntu.com/hardy/utils/swfmill")

On Hardy and later:
```
sudo apt-get install swfmill
```

Now down this 80+ MB Deb package and be off on your way! :guitar:

[http://rapidshare.com/files/82881277/ames_0.0.8.3.3.1.1_all.deb.html]("http://rapidshare.com/files/82881277/ames_0.0.8.3.3.1.1_all.deb.html")

[SIZE="4"]What if I want to use my current Eclipse install?[/SIZE]

It's easy, too:

ASDT: Install this remote site: [http://aseclipseplugin.sourceforge.net/updates/](http://aseclipseplugin.sourceforge.net/updates/)
MTASC:
```
sudo apt-get install mtasc
```
Swfmill: See "How do I install it?"

Open Windows/Customize Perspective and check the ActionScript box under New.
[SIZE="4"]
Some FAMES/AMES tutorials[/SIZE]: [http://osflash.org/fames_tutorials]("http://osflash.org/fames_tutorials")

_____________________________________________________________

Hope you love your new IDE!  Post your suggestions, comments, bugs, etc. here.

---

