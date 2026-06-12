---
title: "Hello everyone, little introduction."
date: 2011-11-13
forum: New to Ubuntu
---

### Post by RossDoughty on 2011-11-13
Hello everyone, I have just installed ubuntu 11.10. I am quite impressed by it as I have been installing and following Ubuntu releases from version 7. 

Anyway, just wanted to say hello. :D

P.S. I have noticed flash videos, when streaming, are quite choppy. Just wondering if there are any programs I can use to increase performance?

Thanks,

Ross.

---

### Post by deltacomp on 2011-11-13
Hello, have you installed the video drivers for your video card? If you have not, I  would suggest starting there. If you need help, do hesitate to ask.

---

### Post by RossDoughty on 2011-11-13
Well, the computer I have installed it on has onboard graphics. The 3rd-party driver program comes up with nothing. Would changing the "Niceness" of say Firefox or chromium make any difference?

---

### Post by WasMeHere on 2011-11-13
Hello Ross,

If you describe your computer, then it will be easier to suggest what to do to improve the performance.

Is it choppy only when streaming video? What about playing files from your hard drive? What about your internet connection?

Have fun finding out :-)
Olle

---

### Post by MG&amp;TL on 2011-11-13
Weird double-post, sorry.

---

### Post by MG&amp;TL on 2011-11-13
I find flash won't run at all unless I do this:

```
sudo apt-get install ubuntu-restricted-extras
```

In a terminal.

---

### Post by RossDoughty on 2011-11-13
Okay well basically it is a P4 with on-board graphics and 1Gb DDR RAM. 

It is only choppy when streaming video, from the HD it's fine. 

The internet connection is wireless however, even if I leave the video to fully load, it's still choppy.

Hope this helps.

Ross.

---

### Post by RossDoughty on 2011-11-13
> **MG&TL said:**
> I find flash won't run at all unless I do this:

```
sudo apt-get install ubuntu-restricted-extras
```

In a terminal.

Thankyou for this, I had forgotten about it.

---

### Post by WasMeHere on 2011-11-13
I would not run Unity with that hardware. Try XFCE or LXDE either by installing those desktops directly into your system or switch to Xubuntu or Lubuntu! Those desktop environments have much smaller footprints. So more power is left for the applications.

---

### Post by RossDoughty on 2011-11-13
Yeah that's what I thought about doing. I was just wondering if anything could be done to help it a bit. Oh well I know my way around XFCE so I'll use that. Thanks all :).

P.S. 

Just a quick question now. Is the command to install XFCE:

sudo apt-get install xfcedesktop4

Thanks.

---

### Post by MG&amp;TL on 2011-11-13
Probably-I'll look. There is a few problems with that approach though, mostly that you seem to get multiple default desktop apps-so gedit and mousepad, thunar and nautilus, catfish and whatever ubuntu uses for its search facility. If it's a recent install, you might be better off installing Lubuntu or Xubuntu directly. Then you don't waste disk space with duplication and Unity desktops.

EDIT: can't find the xfce-desktop in synaptic-but you could try the Xubuntu-desktop package.

---

### Post by Paddy Landau on 2011-11-13
> **MG&TL said:**
> If it's a recent install, you might be better off installing Lubuntu or Xubuntu directly.
+1. Use [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") for the smallest hardware requirements; it is fast and should solve your problem. Test with a Live CD before making up your mind.

---

### Post by WasMeHere on 2011-11-13
These two commands should do it
```
sudo apt-get update
sudo apt-get install xubuntu-desktop

```

Please browse the internet for ***install xfce on ubuntu*** to get more details!

---

### Post by WasMeHere on 2011-11-13
But please note what several of us already suggested:

You will have a much cleaner system if you start with a fresh install of Lubuntu or Xubuntu. Try live sessions before you install anything!

---

### Post by RossDoughty on 2011-11-13
> **Olle Wiklund said:**
> These two commands should do it
```
sudo apt-get update
sudo apt-get install xubuntu-desktop

```

Please browse the internet for ***install xfce on ubuntu*** to get more details!

Thanks for that, worked a treat. I have decided to go with XFCE, as I am most familiar with it. Videos no longer lag or skip.

Thankyou all for you help. :).

---

### Post by WasMeHere on 2011-11-13
Glad it works for you :-)

After some testing, that everything works, please mark the thread SOLVED

Olle

---

