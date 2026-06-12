---
title: "Netbook Version"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by daouddajani on 2013-01-01
hi,
What is the latest version that can be installed on a netbook. i have installed version 10.10 Remix but it doesnot see my wireless adapter.
also i tried 12.10 but after the installtion completed the system hangs and stopp working
 
please advice
 
thank you

---

### Post by 3rdalbum on 2013-01-01
> **daouddajani said:**
> hi,
What is the latest version that can be installed on a netbook. i have installed version 10.10 Remix but it doesnot see my wireless adapter.
also i tried 12.10 but after the installtion completed the system hangs and stopp working
 
please advice
 
thank you

The latest version of Ubuntu works on netbooks. There might be a bug that's stopped 12.10 from working on your specific computer, or maybe you have bad RAM in your netbook.

Otherwise you could try 12.04.

Definitely don't try anything older than 12.04.

---

### Post by Paqman on 2013-01-01
Don't use 12.10, it no longer supports the 2D version of the Unity interface, so you'll be forced to use 3D. That's probably why you couldn't get it to work properly.

Install 12.04 and pick the 2D interface from the icon next to your user name on the log on screen.

---

### Post by desktorp on 2013-01-01
In situations where your wireless device isn't being detected by the installer, I find that it is often helpful to start a LiveCD / graphical environment, prior to installation, to manually configure the connection.

As for 12.10 hanging (as already stated) it's hard to say why, but it might be helpful to know what kind of netbook you're using.  A first or second generation netbook might not have enough storage capacity or memory to handle 12.10 + the graphical requirements might just be too much.

Personally, I would probably just build something from Debian stable or testing, but you might be fine rolling back to Ubuntu 12.04 and using a lightweight environment.  Maybe a Ubuntu variant, such as Xubuntu/Lubuntu.

Semi-related, Chdslv was trying to rediscover a modern form of EasyPeasy, in the Other OS forum and mentioned contacting the original developer.  I know people who still have EasyPeasy (which I believe is based on 9.04..?) on their netbooks.

---

### Post by Paqman on 2013-01-01
> **desktorp said:**
> 
Personally, I would probably just build something from Debian stable or testing, but you might be fine rolling back to Ubuntu 12.04 and using a lightweight environment.  Maybe a Ubuntu variant, such as Xubuntu/Lubuntu.


I use vanilla Ubuntu 12.04 on my Eee PC 1000 and it works fine as long as you're in Unity 2D. Some people choose to use a lighter DE, but it's not strictly necessary (same as on more powerful machines).

---

### Post by 3rdalbum on 2013-01-01
> **Paqman said:**
> Don't use 12.10, it no longer supports the 2D version of the Unity interface, so you'll be forced to use 3D. That's probably why you couldn't get it to work properly.

Eh? I use Unity 3D on my netbook. It runs just fine. Netbooks have supported 3D hardware.

---

### Post by Paqman on 2013-01-01
> **3rdalbum said:**
> Eh? I use Unity 3D on my netbook. It runs just fine. Netbooks have supported 3D hardware.

Depends how good a graphics chipset you have. I find 2D much more usable on my machine with Intel 945 graphics, it's not inconceivable that the OP has some oddball chipset that is refusing to play ball. Most netbooks were wall-to-wall Intel, but not all of them.

I'm quite happy to be wrong though, there could have been some other problem with 12.10 on that machine. Either way trying 12.04 is a good bet, especially with it being LTS.

---

### Post by grahammechanical on 2013-01-01
We need to clear out some FUD. It is true the 12.10 does not support Unity 2D unlike 12.04 but another method of providing a 3D user experience on lower specification machines is being used.

> Those lacking sufficient graphic grunt will get a hardware accelerated interface powered by the OpenGL rasterizer LLVMpipe, whilst anyone with a capable graphics card will see that utilised.

[http://www.omgubuntu.co.uk/2012/08/unity-2d-removed-from-ubuntu-12-10]("http://www.omgubuntu.co.uk/2012/08/unity-2d-removed-from-ubuntu-12-10")

> *As long as Ubuntu&#8217;s minimum system requirements are met.

The OP needs to give more information about he/she means when he says "the system hangs and stops working." Otherwise we are all just guessing.

Regards.

---

### Post by verymadpip on 2013-01-01
> **Paqman said:**
> Depends how good a graphics chipset you have. I find 2D much more usable on my machine with Intel 945 graphics, it's not inconceivable that the OP has some oddball chipset that is refusing to play ball. Most netbooks were wall-to-wall Intel, but not all of them.

I'm quite happy to be wrong though, there could have been some other problem with 12.10 on that machine. Either way trying 12.04 is a good bet, especially with it being LTS.

+1

I have a graphics issue with my MSI Wind U180.  Fortunately there appears to be a solution available in the Precise (12.04) repos, which does NOT seem to be available in the Quantal (12.10) repos.

---

### Post by mysteriousdarren on 2013-01-11
After struggling with 12.10 Ubuntu I changed to 12.04 after some research. Googling around helped me figure out all the problems I was having and absolutely what I have now. Soon I will upgrade to 2GBs but even on the one right now it absolutely flies. Cheers!

---

