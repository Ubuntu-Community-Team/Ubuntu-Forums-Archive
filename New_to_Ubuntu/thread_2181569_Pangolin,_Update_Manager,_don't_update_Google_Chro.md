---
title: "Pangolin, Update Manager, don't update Google Chrome"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by czgirb on 2013-10-18
Happened twice already, after I do an **Update** via **Update Manager**, it said that there is **Chrome**, required to be updated.
No matter what ... I unable to check mark the Box. Why?
I wish to tried to update chrome **manually** ... but I don't know how to do that.
Please guide me ....

---

### Post by Bill Dubinski on 2013-10-18
I have absolutely no advise for you, however I wondered that same thing for a bit on my box. I am still running 10.04 LTS (Lucid) and I have that same update stuck in my update center for some time now that I can not tick/highlight to install. I do not really care too much about it myself, I am in the process of upgrading to 12.04 LTS, so I don't lose sleep over it. But just thought I would share my similar story.

---

### Post by Frogs Hair on 2013-10-18
Chrome has updated via the update manager on my installations , but I don't remember if that was the case on 12.04. The latest advertised doesn't always update immediately though unless security related. Keep in mind there may differences in the Linux, Win and Mac versions. When Chrome is installed the [http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable) main should appear in Software & Updates > Other software. If you wanted to manually upgrade you would simply download the latest version from the website remove the current version from the software center and install the new package.

---

### Post by Frogs Hair on 2013-10-18
[COLOR=#000000]Bill D.[/COLOR]

There may be unsolvable  dependency issues on older unsupported  versions of Ubuntu. This is just one reason to install a newer version . There are other desktop environments available if your reason for sticking to 10.04 is Unity.

---

### Post by slickymaster on 2013-10-18
> **czgirb said:**
> Happened twice already, after I do an **Update** via **Update Manager**, it said that there is **Chrome**, required to be updated.
No matter what ... I unable to check mark the Box. Why?
I wish to tried to update chrome **manually** ... but I don't know how to do that.
Please guide me ....

There's absolutely no problem with your system. The problem lies on Google side and there's an already reported bug - [Wrong 64-bit dependencies on 32-bit version of Ubuntu]("https://code.google.com/p/chromium/issues/detail?id=304017"). Chromium developers are working on it.

There's a suggested workaround, **which I don't advise you to try because things can go the wrong way**, that goes by unpacking the Debian package, editing DEBIAN/control to remove the incorrect dependencies and repack the Debian package.

```
~$ apt-get download google-chrome-stable
~$ dpkg-deb -R google-chrome-stable_30.0.1599.101-1_i386.deb 304017

~$ sed -i 304017/DEBIAN/control \
      -e 's/30.0.1599.101-1/30.0.1599.101-2~304017/' \
      -e 's/lib32gcc1 (>= 1:4.1.1), lib32stdc++6 (>= 4.6), //' \
      -e 's/libc6-i386 (>= 2.11), //'

~$ sudo chown root:root 304017/opt/google/chrome/chrome-sandbox
~$ sudo chmod 4755 304017/opt/google/chrome/chrome-sandbox

~$ dpkg-deb -b 304017
~$ sudo dpkg -i 304017.deb
```

---

### Post by czgirb on 2013-10-18
> **slickymaster said:**
> There's absolutely no problem with your system. The problem lies on Google side and there's an already reported bug - [Wrong 64-bit dependencies on 32-bit version of Ubuntu]("https://code.google.com/p/chromium/issues/detail?id=304017"). Chromium developers are working on it.

Thank you for the information given
So, the thread is **SOLVED**.

---

### Post by Bill Dubinski on 2013-10-18
Yes Sir. That is what I figured. I am in the "workings" of doing that upgrade now. I test drove 12.04 off Live Disk yesterday, really liked it as much as I could test off Live Disk running Ubuntu fallback. (Not a Unity fan), never have been since 11.04 that I had back then and went back to 10.04 back in 2011. Since I am only a 3 year user of Ubuntu products and only used to fresh installs, I am not used to "upgrades" or fresh re-installs when you don't want to touch your /home partition. I have to run out and pick up a bigger 2nd HDD for my "data" is larger than my installed backup HDD. I have 89 GB of mostly images because I am into graphic arts and I keep all my files. So I have to back this up before re/installing. 
I have two threads out there with "my concerns" prior to re/installing. Feel free to leand your advise. All is appreciated if you feel you know about those departments. 
All will be appreciated. 

(First post) [http://ubuntuforums.org/showthread.php?t=2181183](http://ubuntuforums.org/showthread.php?t=2181183)
(Second Post) [http://ubuntuforums.org/showthread.php?t=2181579](http://ubuntuforums.org/showthread.php?t=2181579)

Thank you,
Bill 
Bill

---

### Post by Bill Dubinski on 2013-10-18
Yes, sir. when I test drove 12.04 off Live CD, I installed Gnome Flashback from the terminal and used it with that. I liked it alot, not as much as GNOME 2, but it was atleast doable. I like having the bottom task bar versus that annoying "home row" in Unity that takes up your screen space, pops up when you don't want it, than you mouse argue when you want it back. Atleast that is how it is on my wife's laptop running 11.04 (Natty). Out of date, I know. 
The only thing I missed from Gnome flashback was the "system" dropdown from the left hand side of the upper task bar. Don't know where to find the things that were under that tab. 
But all in all, it seemed good from what I am able to do running off live CD. 
If you have any suggestions for [COLOR=#000000]desktop environments like "Gnome Flashback", please feel free to suggest. 

Like I said above, I am in the stages of upgrading. I mainly just need to get that new HDD, and 10.04 is gone. 
And no, that is not the only reason I did not upgrade yet. I use my PC for 95% work purposes. And it works te way it is for that purpose. I know if I upgrade or "get a new toy", there will be days of "play" and not working. ;-) Since there is always new things to explore with a new version of Ubuntu. There will also be days of tweaking and getting things like custom fonts for the GIMP and GIMP plug ins back installed because GIMP is my bread and butter. I need that working and confident it is in the same state it was in. Plus, I am sure there is new things I can install that I don't know about yet. That falls into "play", lol. [/COLOR]

---

