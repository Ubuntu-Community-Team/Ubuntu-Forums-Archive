---
title: "I stupidly downloaded dash-to-dock on Ubuntu Unity"
date: 2017-03-16
forum: New to Ubuntu
---

### Post by kerupukmoe on 2017-03-16
I am new to Linux so bear with me.
A few days ago I installed Ubuntu Gnome on my laptop and got rid of Windows 10, it was great but pretty laggy for my machine, I use a Lenovo Z40 8gb RAM, 1.9ghz processor.

While I was playing around with Ubuntu Gnome I stumbled on dash-to-dock extension for gnome shell, it was very nice and I love it, but due to how laggy it was on my laptop I decided to switch to Ubuntu Unity, I tried booting it on a usb stick and it works fine, after installing Ubuntu 16.04 LTS, I downloaded the dash-to-dock extension using a terminal with a git clone,
( here is the link of a screenshot of the terminal: [http://imgur.com/wvrJHyj](http://imgur.com/wvrJHyj) )
but I didn't know if it would work on Ubuntu Unity, and I downloaded it anyways, after that I felt stupid and tried to remove it but obviously being the noob I was it didn't work.

Does dash-to-dock work on Ubuntu Unity? if not how do I remove it from my system?
If it does work how do I make it to work?

---

### Post by deadflowr on 2017-03-17
No, it will not work with unity.
To remove, simply delete the folder that the git clone command created in you Home folder.

The git clone command did nothing but download the source code for dash to dock, but it does nothing about actually installing it.
In order to install you would have needed to compile or make install the package yourself manually.

---

### Post by kerupukmoe on 2017-03-17
thank you kind sir.

---

