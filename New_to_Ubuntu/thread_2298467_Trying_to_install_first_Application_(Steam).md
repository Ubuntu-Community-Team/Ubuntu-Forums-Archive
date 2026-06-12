---
title: "Trying to install first Application (Steam)"
date: 2015-10-11
forum: New to Ubuntu
---

### Post by lcharvey1 on 2015-10-11
Hi,

Decided to bite the bullet and try Ubuntu but i have no Linux experience so have a severe learning curve ahead lol. Trying to install my first app steam and get the message that these packages need to be installed  but keeps failing. Any idea what i am doing wrong? Thnx Lee.

I will try to attach a picture of the screen.

[[IMG]http://s29.postimg.org/5k1zqbmnn/Screenshot_from_2015_10_11_16_49_20.jpg[/IMG]]("http://postimg.org/image/5k1zqbmnn/")
[[IMG]http://s29.postimg.org/amjbl3vxv/Screenshot_from_2015_10_11_16_49_41.jpg[/IMG]]("http://postimg.org/image/amjbl3vxv/")

---

### Post by Ubunterrific on 2015-10-11
Hope the bullet-biting is going well, (lee) :D

Open up a terminal (holding** Ctrl+Alt+T** is probably fastest) and run:
```
sudo apt-get install libglapi-mesa:i386 libcheese-gtk23 libcheese7 unity-control-center libgl1-mesa-glx:i386 libc6:i386 libgl1-mesa-dri:i386
```

Input your password, give it a **y** for yes and then try again. Really, the steam application should have pulled in the dependencies itself though - these packages it needs are 32bit variants of what you probably already have because steam is unfortunately not a 64bit application in 2015 lol

Btw, do you mind if i ask - are you trying to install steam via 
```
sudo apt-get install steam:i386
``` as this should have probably pulled in the right dependencies with it?

---

### Post by lcharvey1 on 2015-10-12
Hi Terrific,

I had installed Steam using the Ubuntu Software Centre but after   your post i uninstalled through the centre and then used the that second shorter command you gave to install steam and it worked fine. I then typed Steam and now it is installing Steam updates. Just wondering is there a way to copy and paste from the code window on here to the terminal? Also wondering a good place to get info on basic commands etc.

Thnx for the help Lee.

---

### Post by Ubunterrific on 2015-10-12
Excellent :popcorn:  Yeah, sure, just highlight what's in the code box on here, and copy it with **Ctrl+C** or **right-click** **and select copy**, then it can be pasted into a terminal (**right-click** **and paste**).

There are lots of sites with basic commands, something like a cheatsheet is probably quicker [http://files.fosswire.com/2008/04/ubunturef.pdf](http://files.fosswire.com/2008/04/ubunturef.pdf)  but you'll pick stuff up over time, if you stick with it. For simplicity, most things have become easy to do with a GUI nowadays, but it's usually faster or more satisfying to do things the old fashioned way!

The most important commands are:
**sudo apt-get update** to grab a fresh list of available software + their new version names
**sudo apt-get upgrade** to download and install new package updates without doing any big cosmetic work (like removing older versions e.t.c.)
**sudo apt-get dist-upgrade** to download and install new package updates that require old cruft out first
**sudo apt-get install the-name-of-a-packag**e  to install something
**sudo apt-get remove the-name-of-a-package** to take something out without removing any configuration files you might have made for it
**sudo apt-get purge the-name-of-a-package** to completely rip out something


I recommend installing **synaptic** which is a great package manager that lets you see everything that's installed, see what is 'autoremovable' i.e. not in use, update by pressing 'reload' and upgrade by marking them and applying changes. It also has a handy link to see which repositories you have activated up in its menu bar, allowing you to tick and untick whichever package lists (ppas) you might want to add (e.g. the ubuntu mozilla daily ppa [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa) when added, allows you to install packages listed there which include the latest version of Firefox's alpha, Nightly.)

---

### Post by lcharvey1 on 2015-10-12
Brilliant thanks for the tips, I did copy the text but for some reason I didn&#8217;t think I could right click in the Terminal window #Facepalm lol. I will install synaptic now. To be honest so far everything seems to be working great. Installed Chrome also as Netflix works off the bat with that but read there is some playing around involved getting it working in Firefox. Also installed VLC as a media player and got my first game (Kerbal Space Program) working so it is all coming together lol.

Thanks again for getting me started   :)

---

### Post by Bucky Ball on 2015-10-12
Control+c will not work in a terminal. You need control+shift+c (and control+shift+v to paste).

---

### Post by Ubunterrific on 2015-10-12
No worries, i have been known to be useful sometimes lol :popcorn:

---

### Post by lcharvey1 on 2015-10-12
Ahh that is why then. Thnx Guys.

---

### Post by yetimon_64 on 2015-10-12
> **Ubunterrific said:**
> Excellent :popcorn:  Yeah, sure, just highlight what's in the code box on here, and copy it with **Ctrl+C** or **right-click** **and select copy**, then it can be pasted into a terminal (**right-click** **and paste**)....

That is perfectly fine for use with this site, however a general warning if using that on other internet sites is to paste to a text editor first and check the code carefully. Then copy and paste from the text editor to the terminal. 

It is possible on web sites to hide some of the code from the users view but pasting directly to terminal can pass on the hidden code to be run. Not a safe situation, especially if root commands are involved and the website has any nasty intent. 

Though as I noted above this site should be pretty safe to copy/paste from OP; I don't use the text editor technique with this site and have never had a problem in about 7 years of using the site.

---

