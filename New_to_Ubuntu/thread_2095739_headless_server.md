---
title: "headless server"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by lucifur on 2012-12-17
I know there is a lot of threads and such about this topic, however I did a search and found some instructions on how to get Ubuntu to boot without a monitor.
   I copied and pasted this thing into the terminal "you don’t want to know how long it took me to find that thing" and then I copy and pasted what looked like a bunch of code into the thing and hit several key combos that were supposed to save it.
    Well now I get err message from time to time saying something about err being detected and such, this I feel is not good.
    So I decided that in order to get non outdated instructions ect. that it would be prudent to get answers strait from the horses mouth, and no I have no Idea how to discern what version of Ubuntu this is so I will need instruction for that also.
     I did get team-viewer installed and found the proper instructions to get it to boot at start-up, but this is before I screwed up the OS with bad code and got scared to touch terminal instruction type things.

    So if some one would please be kind enough to assist me in setting up this computer so as it will boot without a monitor and then if you guys are feeling generous I am sure to need help setting it up as an online file server. My plan is to start a collection of Unreal Tournament GOTY "UT99" files for download as I see lots of UT99 web sites have stopped hosting files, I know it might be slow but I don’t expect a big rush of downloading any way, probably not more than one or two at a time any way.

---

### Post by Cheesemill on 2012-12-17
If you want our help we're going to need more info.

What code did you type into the terminal? What errors are you getting? You say this is a server but then you say you've installed TeamViewer. What desktop environment did you install (Ubuntu Server is usually command line only without a graphical interface). What exactly are you trying to achieve? What are the specs of your machine and what version of Ubuntu have you installed?

You can find out the Ubuntu version by opening a terminal and typing:
```
lsb_release -a
```

---

### Post by lucifur on 2012-12-17
Ok it says:

Distributor ID:  Ubuntu
Description:       Ubuntu 12.10
Release:              12.10
Codename:         Quantal

  As far as a special server Linux I am sure that would be way above my head I just want to be able to set some files a side that can be accessed from the web like the FTP server interface I use for my game server, this as far as I know is just a run of the mill Ubuntu thing, if I should be using something els let me know.

  If it would be easer you are welcome to use team veiw and connect strait to it.

  ok here is the link to the instructions that I followed to try and get it to boot without the monitor attached:

  [http://olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/](http://olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/)

  As far as the err message I have been unable to get it to come up again on demand, one time it came up after it booted and another time it came up when I clicked the display icon.

  Hopefully this is the info you asked for, if not I will try to find more per your requesting, thanks for helping me.

intell Atom  CPU 330 @ 1.60GHz x 4
32-bit
2 gig mem

---

### Post by lucifur on 2012-12-18
I have done some more research and if I am not mistaken it seems this computer wont let you boot without a monitor, so thanks for your help.

---

### Post by tgalati4 on 2012-12-18
Is there a switch in BIOS--"Ignore All Errors"?  I have a headless server with a BIOS switch that I had to set so I could remove the video card, keyboard, and mouse and still have it boot.  It's running freenas.

---

### Post by lucifur on 2012-12-20
I did not see a switch in the bios, guess dad has an old little monitor in the garage I can use for it, I don't under stand why any mother board company would make such a board that requires a monitor with the popularity of home servers these days, oh well I guess I will be fine. 

I found the forum topic on making a little fake monitor plug with four resisters, to bad somebody doesn't sell those things.

Well I will probably be back after I get things going as it is likely I will still need help setting up the file server part of it, thanks for the help so far.

---

