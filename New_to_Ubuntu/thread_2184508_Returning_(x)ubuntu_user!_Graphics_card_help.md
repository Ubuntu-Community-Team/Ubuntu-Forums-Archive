---
title: "Returning (x)ubuntu user! Graphics card help"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by mightyeldude on 2013-10-29
Hey all! 

Just a brief background on me (I just joined the site):
I am returning back to the Ubuntu world after using it quite a lot back in the days of 7.10 Gutsy. I have been meaning to get back into it but ever since Ubuntu switched to Unity and seemed to get more bloated (in my opinion, maybe its changed) I could never get used to it. I loved the clean look of Xubuntu so here I am, fresh install of Xubuntu 13.10 and am loving it :D Forgot how much I loved Linux! 

But anyway, I have it installed on my Alienware m11x laptop which I am also dual booting with Windows 7. The laptop has switchable graphics (NVIDIA GeForce GT 335M discrete as well as on board Intel) and on Windows I was able to press f6 and switch between the two. I can't seem get the NVIDIA graphics working even after trying to install the nvidia-current drivers. I tried selecting discrete graphics in the bios on bootup to enable the NVIDIA graphics card but I just get a blank screen after I log in. What am I missing? I know it's probably been covered before but I couldn't find any recent info. Is there a way to switch graphics on the fly or do I have to choose in the bios on bootup? I don't mind either way as long as it works but it would be nice to get on the fly switching to work like in Windows. And help is appreciated! :D Sorry noob question :D

(mods feel free to move this thread if need be)

Oh and off topic but, is there a way to change my user name? I registered for Ubuntu One in order to sign up here but it never gave me an option to choose a user name?

---

### Post by Bashing-om on 2013-10-29
mightyeldude; Hi ! Pleasing that you are back !

Historically Nvidia has not been kind to linux in respect to drivers for switchable graphics. There has been some progress made with the advent of the BumbleBee project to address this issue, and most recent is the open source developments:
see:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

These I expect to be the better solutions with version 13.10. However, others do exist, we do not want to go there yet. Those alternates, from what I have observed, are "complicated" and difficult to maintain.

[INDENT][INDENT]just my little bit
[/INDENT][/INDENT]

---

### Post by Elfy on 2013-10-29
> **mightyeldude said:**
> ...

Oh and off topic but, is there a way to change my user name? I registered for Ubuntu One in order to sign up here but it never gave me an option to choose a user name?
[Post in Resolution Centre. ]("http://ubuntuforums.org/forumdisplay.php?f=123")

---

### Post by mightyeldude on 2013-10-29
Thank you for those links, I will check them out! Much appreciated!

---

### Post by cariboo on 2013-10-29
Alberto Milone, the graphics driver dev for Ubuntu has come up with another way to get hybrid graphics to work in 12.04 and 13.10. Check out his blog [here]("http://albertomilone.com/wordpress/?p=591")

---

