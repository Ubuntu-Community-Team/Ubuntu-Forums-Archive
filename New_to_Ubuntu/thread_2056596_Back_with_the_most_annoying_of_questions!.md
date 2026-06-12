---
title: "Back with the most annoying of questions!"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by anewguy on 2012-09-11
I REALLY hate to ask this - I can't tell you how much.  It's an age old problem, and me in my old age isn't getting very far - I should already KNOW this.

I recently was given an old Dell Inspiron 1501 and decided to put 12.04 on it in place of Windows, leaving my newer laptop for Windows 7 and my desktop with Windows 7, maybe sometime Windows 8.  Those of you who have been watching the forum will already be familiar with the problem.

The laptop has a BCM4311 wireless adapter, so of course it has the blessed "firmware missing".  This laptop also has a Broadcom chipset for the onboard hard-wire ethernet port as well, so I don't know if that's adding to my problems or not.

I tried rmmod'ing b43 and being sure ssb was gone, seeing if the STA driver might somehow work - but no it's still needs the firmware.  Several months ago I remember going through this with someone and there were 3 packages I had them grab to make it work.  Be darned if I can remember any of that now. So..........

- will it be a problem using the drivers with the onboard BCM ethernet chipset?

- with no access to the router right now, can someone tell me (again) what packages and where to download them from using Windows so I can move them to the old laptop with a USB flash stick?

I apologize deeply for what I know from the past is a "beat to death" question.  This old guy just got himself stuck!  I even went so far as to try ndiswrapper with the 64-bit driver file (I'm using 64-bit 12.04.1) but even though ndiswrapper swore the device was found and loaded, I still couldn't get it to work.

---

### Post by coffeecat on 2012-09-11
> **anewguy said:**
> - with no access to the router right now, can someone tell me (again) what packages and where to download them from using Windows so I can move them to the old laptop with a USB flash stick?

The package you need for the firmware is b43-fwcutter. Have a look here:

[http://packages.ubuntu.com/precise/b43-fwcutter](http://packages.ubuntu.com/precise/b43-fwcutter)

That's the version for Precise. If you click on either the amd64 or i386 link, depending which you want, you'll be taken to a page with links for all the mirrors. Click on one of them and you'll download the deb file.

One for your bookmarks! :wink:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Search for the package you want in whichever version of Ubuntu and you will be able to download the deb package(s).

**EDIT**: Oops - hold everything. That may not work. The b43-fwcutter package - if I remember correctly - needs to download something when you install it. That was probably the three packages you were referring to. You mention ethernet. Does it work on that laptop with 12.04?

---

### Post by Hadaka on 2012-09-11
Hi, here ya go...no internet access required to load b43 drivers

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
 
```grab the zip file first, drag it to your desktop, right click, open here

soon as i figure out how to give you the zip file.......

---

### Post by Hadaka on 2012-09-11
[attach]224034[/attach]

---

### Post by newb85 on 2012-09-11
I recall doing this for a friend a year or two ago (circa Maverick, I think), and at that time, I didn't need any internet access, because b43-fwcutter was included on the Live/Install CD.

---

### Post by anewguy on 2012-09-12
Hadaka, that was perfect!!  Thanks!!  I am on my old laptop right now.  I have also been trying to get a poster in another thread to provide some info, as I think they might be having the same problem - if so I'll point them to your instructions!

Thanks again!

Dave ;)

---

### Post by anewguy on 2012-09-12
> **coffeecat said:**
> T
One for your bookmarks! :wink:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Search for the package you want in whichever version of Ubuntu and you will be able to download the deb package(s).


Thanks for that!!!  I know I've used that before but just can't remember anything anymore (I think the 60's and 70's are catching up with me ;) ).

Have a good one, coffeecat, and thanks again!

Dave ;)

---

### Post by mips on 2012-09-12
> **anewguy said:**
> 
- with no access to the router right now, can someone tell me (again) what packages and where to download them from using Windows so I can move them to the old laptop with a USB flash stick?

If you ever need to download packages & their dependencies from the repos from a windows pc or another linux pc have a look at Keryx,

[http://keryxproject.org/](http://keryxproject.org/)
[https://launchpad.net/keryx](https://launchpad.net/keryx)

---

### Post by anewguy on 2012-09-12
> **mips said:**
> If you ever need to download packages & their dependencies from the repos from a windows pc or another linux pc have a look at Keryx,

[http://keryxproject.org/](http://keryxproject.org/)
[https://launchpad.net/keryx](https://launchpad.net/keryx)

Thanks!!

---

