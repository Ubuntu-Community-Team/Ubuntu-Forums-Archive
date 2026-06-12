---
title: "Upgrade worse than 7.10..."
date: 2008-11-19
forum: New to Ubuntu
---

### Post by kjacobs on 2008-11-19
Okay,

I figured I would start a new thread on this. I went ahead and upgraded to 8.10 to try and get my Gigafast 741 USB network adapter to work, with the hope that it would be automatically detected. It was not.

I also lost my screen resolution. Ubuntu 7.10 had no trouble giving me 1024X768 or more. Now I am limited to 800X600. How do I fix that?

Back to the usb wireless networking. Since it was not detected, I was going to again try to use ndiswrapper. Accept this time, there is no ndiswrapper option under the Synaptic Package Manager.

I tried to do a:
sudo apt-get install ndisgtk

And I get a package not found error

Where did everything go? I think the upgrade sent me backwords...

---

### Post by tuxxy on 2008-11-19
Screen resolution did you try to reconfigure the xorg and then reinstall video drivers?

ndisgtk is the correct package name, not sure why its no there was this a fresh install

---

### Post by kjacobs on 2008-11-19
I have not tried to reconfigure anything. I am totally new to ubuntu and wouldn't even know how. The 7.10 install worked great for screen resolution.

---

### Post by Maverick1712 on 2008-11-19
I'm the wrong guy to be helping with the display issues but as far as ndiswrapper goes, did you do:

```

sudo apt-get update
```

first, to update all of the repository lists?

---

### Post by kjacobs on 2008-11-20
It seems I've got even worse problems now....

While waiting for a reply, I was playing with Puppy Linux loaded off a live CD. I shut down from that and rebooted to Ubuntu and now it will not reboot. It is dropping to a shell at boot up, spitting out tons of line of text, and won't load correctly. Funny that ubuntu 7.10 did not do that when I tried the same thing.

Any clues??? What now???

---

### Post by Mikeyp926 on 2008-11-20
I too feel like upgrading to 8.10 was a step backwards, and I'm really kicking myself for not just sticking with 8.04.  But hey, at least it's a good learning experience to try and fix all these problems.

Anyway, I'm also kinda new to Ubuntu, but I also am only faced with a command line when I boot up, so I can tell you some of the things I have found online about this problem.
Do you have nvidia graphics?  if so, I believe you can use the "sudo nvidia-xconfig" command to edit your xconfig file.
What do the lines of text say?
Also, you could try "sudo startx" to restart the x-server and see what happens then.
Sorry I can't help more, but I'm pretty new to all this linux stuff.
Good luck!

---

