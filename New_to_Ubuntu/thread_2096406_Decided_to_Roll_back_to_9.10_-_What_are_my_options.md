---
title: "Decided to Roll back to 9.10 - What are my options?"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by Captainhepp on 2012-12-19
Hello Everyone!

I've been using Ubuntu on my netbook since 9.10 had just been released. It came with Windows 7 Starter.... which took me all of a week to decide I absolutely hated. What a stupid excuse for an OS. At any rate, that's when I started to research Linux... eventually leading me to choose Ubuntu Netbook Remix (9.10). Loved it. Totally. SO easy and simple to use, and SO fast on a netbook. 

So I've been using it pretty consistently since then, upgrading to new versions as they came out. Everything was great until... 12.10(?). I can no longer control the brightness of my screen (previous solutions for my netbook no longer worked), and the interface was constantly crashing to the login screen. Every. Ten. Minutes. Not good. Especially when the machine's primary purpose is to take notes at business meetings and conferences!

So I decided I'd flush 12.10 (after wiping Ubuntu off the HDD and starting again with a clean install... which still had issues), and roll back to the old 9.10 that I loved so much. I'm typing on it right now. It just seems there's absolutely no support for it anymore! I understand that there will be no new updates and all, but The software center keeps telling me that nothing is available "for your current hardware configuration" or "In the current Data" or some other similar message. Annoying. 

What are my options? Am I totally stuck with strictly the default installation? Or is there another repository somewhere I can get things like the FFmpeg libraries? Alternatively, is there a lighter version of Ubuntu available somewhere for a slower computer? Or could I run the old interface under 12.10?

Thanks a bunch in advance!

Mark

---

### Post by bfmetcalf on 2012-12-19
lubuntu or xubuntu are probably better suited to lighter hardware.

---

### Post by VideoRoy on 2012-12-19
I went through the same thought process as you for my netbook and almost dumped 12.10 as well.  12.04 worked very well but did not support all my hardware (touchpad) properly so I was really eager to get 12.10.

Many crashes and Unity was much slower than previous.  I was about to go to Xubuntu which I tried on live USB stick and works great but I installed gnome-session-fallback and have been using that successfully for about a month now. It is still the core 12.10 so it might not solve your screen issues but it runs better than Unity.

I actually really like the Unity dash, etc. so I installed Cairo dock to replicate the Unity dock and it solved my issues.

In the future I may go to Xubuntu or Lubuntu though.

---

### Post by Paqman on 2012-12-19
9.10 is completely unsupported. You can access the old repos by switching your sources to those at [http://old-releases.ubuntu.com/]("http://old-releases.ubuntu.com/"), but I wouldn't recommend running an unsupported version, as you will be vulnerable to any new flaws found in the software.

10.04 is still supported for another few months and does have an old-style netbook interface available. Otherwise your options are running 12.04 in Unity-2D mode, or with an alternate DE such as LXDE of XFCE. I would advise against using the latest version (12.10) if you were installing standard Ubuntu, as it no longer has a DE that will run well on a netbook.

Lots of choice there really ;)

---

### Post by mastablasta on 2012-12-20
to add to the choices... Kubutnu (KDE) has a netbook plasma interface available. it's not the same as what you have but maybe worth exploring...
 
[https://wiki.ubuntu.com/Kubuntu/NetbookPlasma](https://wiki.ubuntu.com/Kubuntu/NetbookPlasma)
 
[http://www.kde.org/workspaces/plasmanetbook/](http://www.kde.org/workspaces/plasmanetbook/)

---

### Post by zikalify on 2012-12-20
If on 12.04 you could run unity 3d then there is no need to go to a light weight distro, just go back to 12.04 and wait for 13.04 and try your luck. If you couldn't run 3d in 12.04 I'd suggest moving to xubuntu or some other xfce distro (I personally have been trying Manjaro, it's a little more difficult to setup than ubuntu (although not really) but it comes with xfce by default and I really like it!)

---

### Post by Pjotr123 on 2012-12-20
Xubuntu 12.04 LTS. Definitely.
[https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

You'll like what you'll get, I have no doubt! :)

---

### Post by whatthefunk on 2012-12-20
Xubuntu or Lubuntu would be your best choice.  Your worst choice would be to stick with an unsupported older edition of Ubuntu.  There will be no more security fixes so your system would be at risk.

---

### Post by Captainhepp on 2012-12-22
First off, I want to thank everyone for their replies! I really appreciate it!
 
As a result of reading through this the other day, and my own research, the netbook is currently running Kubuntu 12.10. Everything seems to work, it's just a different interface to get used to... but it still seems to lock up randomly every 20 minutes or so, and the screen brightness levels seem to be scrambled. The keys work, but provide seemingly random brightness levels when pressed. Same thing when the system "Dims" the screen. I've disabled that feature for now. I remember there was a work-around for older versions, but is there one for 12.10? I have an Asus Eee PC 1005PE.

---

### Post by VideoRoy on 2012-12-22
> **Captainhepp said:**
> First off, I want to thank everyone for their replies! I really appreciate it!
 
As a result of reading through this the other day, and my own research, the netbook is currently running Xubuntu 12.10. Everything seems to work, it's just a different interface to get used to... but it still seems to lock up randomly every 20 minutes or so, and the screen brightness levels seem to be scrambled. The keys work, but provide seemingly random brightness levels when pressed. Same thing when the system "Dims" the screen. I've disabled that feature for now. I remember there was a work-around for older versions, but is there one for 12.10? I have an Asus Eee PC 1005PE.

That sounds like the video driver problem I had on my desktop with 12.10.  My netbook does not have any video driver options but my desktop did and when I switched to the proprietary nVidia driver things got more stable.

If this is an option for you, the location for proprietary drivers has changed.  They are located in Software Sources if they are available.  You can get there in System Settings -> Software Sources or if you happen to have Snyaptic loaded to can get to the same place there.

---

### Post by vasa1 on 2012-12-22
> **Pjotr123 said:**
> Xubuntu 12.04 LTS. Definitely.
[https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

You'll like what you'll get, I have no doubt! :)

> 
The text editor (notepad) is called **Leafpad**. In the terminal without capital, so **leafpad**. Good to know when you want to use a terminal command that contains gedit (the text editor of Ubuntu).

You may want to fix that.

---

### Post by Captainhepp on 2012-12-22
OK, after more testing, the winner seems to be Xubuntu 12.04 LTS. It's stable, simple, and fast. :p
 
Thanks to everyone for their input so far. My only bug at the moment is the screen brightness flicker issue. It's not as bad as with 12.10 for sure, but still a minor annoyence. I read the post about additional drivers. My Netbook has an Intel integrated chip. Would you find those drivers under "Additional Drivers?"
 
Am I right in thinking Xfce is actually based on Gnome? It looks awful similar. If I ever want to experiment with a different DE do I just point and click in the software center? Thanks again!

---

### Post by audiomick on 2012-12-22
> **Captainhepp said:**
> ... My Netbook has an Intel integrated chip. Would you find those drivers under "Additional Drivers?"

As far as I know, intel graphics is supposed to work with the default drivers, but I am not absolutely sure. The easiest way to find out is just find the additional drivers application and let it run (whilst the computer has an internet connection). If there are drivers available, it should find them. If not, no harm done. As I said, I don't think there are any, but it definitely wont do any damage to look.


 > 
Am I right in thinking Xfce is actually based on Gnome?

No. As far as I know, xfce is completely independant of Gnome.
[http://en.wikipedia.org/wiki/Xfce]("http://en.wikipedia.org/wiki/Xfce")

My guess is that perceived similarities have more to do with a mutual similarity to familiar ground established by Apple and Microsoft in the past.

> If I ever want to experiment with a different DE do I just point and click in the software center? 
Yes. You can install any DE available in the software centre, and choose it at log in and run it. I only ventured into this area quite recently myself, but it doesn't seem to create any problems whatsoever.

---

### Post by JHawk56 on 2012-12-23
> **Captainhepp said:**
> If I ever want to experiment with a different DE do I just point and click in the software center? Thanks again!To add to what audiomick said, I've added Lubuntu DE to Ubuntu in both 12.04 and 11.10, and it was painless even for a Linux newbie like me.

---

### Post by Peripheral Visionary on 2012-12-23
Gnome and Xfce (and LXDE also) are built on the GTK "foundation," so to speak, which is why they integrate so well and seem so alike in many ways. KDE is built on the Qt "foundation." Unity, I've read, borrows a great deal from both GTK and Qt.

Adding another desktop environment is really easy to do in Ubuntu.  Before you just add desktop meta-packages (Ubuntu-desktop, xubuntu-desktop, lubuntu desktop, etc) though, take a few minutes to read [this description of Linux desktops]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893"). It's a little out of date now but it's still the best "layman's language" description I've ever found.

---

