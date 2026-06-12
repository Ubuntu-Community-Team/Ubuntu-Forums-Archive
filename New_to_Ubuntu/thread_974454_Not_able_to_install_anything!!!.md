---
title: "Not able to install anything!!!"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by gneo on 2008-11-07
Hello there,

I thought I'd give ubuntu a go but it's been a disaster. I tried every possible combination for the installation (inside windows, run it from live cd, full install...you name it) and it just doesn't work.

I have a philips freevents X52, 1GB RAM, Centrino Duo, that is running windows xp at the moment.

Any ideas?

---

### Post by Peter09 on 2008-11-07
What was the problem with the LiveCD

---

### Post by nhasian on 2008-11-07
i did a little googling and the results didnt look promising:

[http://www.google.com/url?sa=t&source=web&ct=res&cd=13&url=https%3A%2F%2Fanswers.launchpad.net%2Fbugs%2F140477&ei=1qUUSfq1IqCw8QTVvIH9Cg&usg=AFQjCNFQ3c77yL7_7YGyQDMGu75o1Qg6HA&sig2=B9mix3aL_FPU2zn0zsD2CQ](http://www.google.com/url?sa=t&source=web&ct=res&cd=13&url=https%3A%2F%2Fanswers.launchpad.net%2Fbugs%2F140477&ei=1qUUSfq1IqCw8QTVvIH9Cg&usg=AFQjCNFQ3c77yL7_7YGyQDMGu75o1Qg6HA&sig2=B9mix3aL_FPU2zn0zsD2CQ)

[http://www.google.com/url?sa=t&source=web&ct=res&cd=10&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D797398&ei=1qUUSfq1IqCw8QTVvIH9Cg&usg=AFQjCNEIViSXo2j6JSM-v8ovLofy91M2dA&sig2=_EyxQ3CG0Ubnl27OrSkw-Q](http://www.google.com/url?sa=t&source=web&ct=res&cd=10&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D797398&ei=1qUUSfq1IqCw8QTVvIH9Cg&usg=AFQjCNEIViSXo2j6JSM-v8ovLofy91M2dA&sig2=_EyxQ3CG0Ubnl27OrSkw-Q)

[http://ubuntuforums.org/showthread.php?t=974121](http://ubuntuforums.org/showthread.php?t=974121)

---

### Post by gneo on 2008-11-07
it just doesn't load. i get on the initial screen and then when i pick anything it freezes after about 30 secons and the whole thing needs to be switched off or even remove the battery to switch off

---

### Post by gneo on 2008-11-07
Again...sorry to bust your b***s...when I try "intall inside windows" it starts installation and halfway through it gives me something along the lines: "Can't access CD make sure no other application is using it"

---

### Post by Peter09 on 2008-11-07
LiveCD:
make sure you burn it at a low speed when you create it and check it at he menu when you boot it.

---

### Post by mkvnmtr on 2008-11-07
I think the first thing you need to do is boot the live cd. If you try an install before you know the live cd will run your chance are not very good. I am having the same problem booting the live cd on my powerpc system. I intend to wait until I have a day or so when I don't have to work on  the computer to try with the help of the forum.
When you start up and the welcome comes up hit the tab key. This should bring up several options to try to get to boot. All I can say is try them one at a time to see if one will boot for you. Something like live- nosplash is the place to start. Type in the option and press enter. If it doesn't work restart and try another. If you get to the desktop check out the system and you can try an install. I would recomend that you use only the live disk for several days until you are sure you are ready to install.
If you can'tget the live disk to boot return to the forums to ask for help. You will need to remember and post what you did and the errors you got for someone to help you.l

---

### Post by Karilex on 2008-11-07
I think your disk may not be valid try reinstalling on another disk and burning it at the lowest speed

---

### Post by gneo on 2008-11-07
Guys,

nothing works! the live cd does not boot at all...nothing...not a sausage. I've tried the lower speed burn...checked it...got the ok...startted installing...crashed.

You get what you pay for after all? I was so looking forward to use ubuntu :(

---

### Post by Karilex on 2008-11-07
Weird try ordering a cd from the ubuntu website it's free but it takes a bit of time to arrive try the live cd on another computer if it doesn't try downloading it again but from the torrent if it does it may be something to do with your computer not sure if all else fails why not try another linux distro: open suse, debian? well hope this helps.

---

### Post by gneo on 2008-11-07
I've tried an official cd (a friend passed it on) for 8.04 This also failed in exactly the same way. So far I've burned about 10 different cds from different sources.

---

### Post by jerrylamos on 2008-11-07
I'm way out of my element here, but does the machine's bios show some sort of prefetch or high speed or other option for the CD drive?  One of my systems is a bit touchy on getting the CD drive to work, so I try different combinations.

Jerry

---

### Post by gneo on 2008-11-07
Hi Jerry,

Already tried installation from an official cd...the cd is not the problem because i know it worked for my friend.

---

### Post by alzie on 2008-11-07
I did a search using "philips freevents X52" and ran into this: [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/philips-freevents-x52-hardware-dection-hang-475612/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/philips-freevents-x52-hardware-dection-hang-475612/)

Reading through the posts there it seems that this computer may be (almost) incapable of running any linux distribution unless you are a skilled user or very adventurous and willing to go through a lot of hoops with no guarantees.

Further searching I found this possible solution: [http://ubuntuforums.org/showthread.php?t=704260](http://ubuntuforums.org/showthread.php?t=704260) where **eldragon** explains how he got his computer through what seems to be the same problem.

Your computer is mentioned here: [https://bugs.launchpad.net/linux/+bug/187671](https://bugs.launchpad.net/linux/+bug/187671)  There seems to be a driver conflict in the bios that is causing the problems.

I hope this is some help to you.

---

### Post by mkvnmtr on 2008-11-07
I don't understand. If the live disk does not boot how could you start installing? Am I missing something, I thought you had to have the live disk running before you could even see the install icon?

---

### Post by Peter09 on 2008-11-07
The alternate CD will install using a text based installer, you can get the iso from the same place as the LiveCD

---

### Post by gneo on 2008-11-07
Yea thanks all,

looks like you do get what you pay for, which in this case is nothing. 

My crappy old laptop doesn't like linux (which is strange because I read and was told that Linux is perfect for old crappy laptops. So I'm sticking with Windows.

Thanks to all for your help.

---

### Post by Karilex on 2008-11-08
Oh well hope hope this doesn't disgust you from this and that you would still be willing to give it a try in a few years

---

