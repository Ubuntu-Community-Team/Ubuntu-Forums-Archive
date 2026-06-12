---
title: "New to Linux and cannot open .rpm Archive type not supported."
date: 2012-04-18
forum: New to Ubuntu
---

### Post by manatarms on 2012-04-18
Hello, I'm new to Linux and I just installed Ubuntu 9.04 

I had trouble installing flash player missing plugins so I got "flash-plugin-10.3.183.18-release.i386.rpm", but I get an error that says the archive type is not supported.

thank you for any help.

---

### Post by Vaphell on 2012-04-18
9.04? why? it's not supported anymore, what's wrong with 11.10 or even 12.04beta?

Ubuntu as a derivative of Debian uses its packaging scheme based on .deb files, .rpm is the other package format.

---

### Post by ubuntu27 on 2012-04-18
Hi manatarms. I recommend you to install Ubuntu 12.04. [Ubuntu 9.04 is no longer supported.]("https://wiki.ubuntu.com/Releases")

To download Ubuntu 12.04:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


Adobe Flash (including the 64-bit version) is in the [repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") of Ubuntu 12.04. I don't know about Ubuntu 9.04


A way to install Adobe Flash is to use [Flash Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")
Install the Flash-Aid extension to Firefox, and it will download and install Flash automatically for you.

---

### Post by manatarms on 2012-04-18
Nothing wrong with them and I guess I could/should upgrade. It's just that 9.04 is what was on the disc I got from someone a long time ago. I'm running a Dell Optiplex 755, so I wasn't sure if a later release would be too much for my computer.

Also, I keep getting stuff like this;

user@ubuntu:~$ sudo apt-get update
[sudo] password for user: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
  404 Not Found [IP: ??.???.??.??? ??]

---

### Post by manatarms on 2012-04-18
ohh, okay thank you!! I'll update tonight!!  thank you again!!

---

### Post by anewguy on 2012-04-18
I believe it may have already been mentioned, but:

.rpm is a RedHat Package Manager file.  RedHat is another distribution of linux.  This type of file is not compatible with Ubuntu.

Ubuntu is based on the Debian distribution of linux.  The package manager files it works with are .deb

I don't know if that brief explanation helps you any or not.

Dave ;)

---

### Post by mastablasta on 2012-04-18
> **manatarms said:**
> ohh, okay thank you!! I'll update tonight!! thank you again!!
 
 
you get the messages because 9.04 is not supported enymore. to upgrade it see information here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
 
as it was mentioned flash can be installed using Ubuntu software center or simply by installing restricted extras package.
 
if the new versions are too demanding for oyur mashcine you can try Xubuntu or Lubuntu which use lighter desktop environments.

---

### Post by kurt18947 on 2012-04-18
It looks like a Dell Optiplex 755 should run any of the current *buntus if [these specs]("http://www.pcworld.com/product/30456/dell_optiplex_755.html?p=specs") are correct.  12.04 is looking pretty good.  You can download and install the current build.  If you update regularly, you'll have the same system as someone who installs after the official release.

---

### Post by jerome1232 on 2012-04-18
I wanted to add that you can use alien (installable from the repos) to convert rpms into debs but it doesn't work for all of them. If you can get your hands on a native deb that is preferred.

---

### Post by ubuntu27 on 2012-04-18
Here is [Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/"), which is a collection of [guides]("http://ubuntuforums.org/showthread.php?t=416802") created by [aysiu]("http://ubuntuforums.org/member.php?u=21941").

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

You might want to read [Which *buntu to pick?]("http://www.psychocats.net/ubuntu/whichbuntu") & [Getting Ubuntu]("http://www.psychocats.net/ubuntu/getting")


Good luck!


After you installed (X/K/Edu)Ubuntu, you might want to read [How to install software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by manatarms on 2012-04-18
Actually that explained a lot. Thank you, Anewguy.

---

### Post by jwbrase on 2012-04-18
> **kurt18947 said:**
> It looks like a Dell Optiplex 755 should run any of the current *buntus if [these specs]("http://www.pcworld.com/product/30456/dell_optiplex_755.html?p=specs") are correct.  12.04 is looking pretty good.  You can download and install the current build.  If you update regularly, you'll have the same system as someone who installs after the official release.

I've run 11.10 in VirtualBox on our Optiplex 755, so it (or 12.04) should be just fine on the bare hardware.

---

