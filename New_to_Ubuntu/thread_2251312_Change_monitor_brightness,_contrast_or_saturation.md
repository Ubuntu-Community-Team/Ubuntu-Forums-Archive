---
title: "Change monitor brightness, contrast or saturation"
date: 2014-11-03
forum: New to Ubuntu
---

### Post by mcflay on 2014-11-03
Hello everyone, as the title suggests I would like to find a way to change the video settings (brightness, contrast, saturation, etc) of my vaio vpcca with ubuntu 12.04. Now my laptop has two video cards: an Intel HD Graphics 3000 (integrated) and AMD (discrete and disabled).  
That said, reading on internet I realized that Ubuntu by default has integrated Intel driver, so much so that if I go to Settings -> Display I can change resolution etc.. 
The problem is that if I go to Settings -> Color -> Add new account -> I do not have a chance to do anything (for example, change the saturation) because each option is disabled. 
And so the question: if it is true that the drivers are enabled, because I have not something similar to the control panel 'Multimedia and Graphics Intel' that  I have instead on Windows? 
Or at least is there a way to change the parameters related to the color of the screen? 
If I go to proprietary drivers panel I have not anything..
Some advices?
Thanks ;)

---

### Post by Lukas_Carls on 2014-11-03
Before I begin...I'm assuming you're using Ubuntu 14.04?

First, for the color settings, there are some extra packages you need to install before you can can work with those. Just click on a device listed in the device list and then click "View Details". Then it'll prompt you to install those needed packages. Why they don't come pre-installed...I don't know.

Second, in the main settings screen, there should be options for Brightness and Lock.

Hope this helps you out! Cheers and happy computing!

---

### Post by mcflay on 2014-11-04
> Before I begin...I'm assuming you're using Ubuntu 14.04?
No as said, I have Ubuntu 12.04


> First, for the color settings, there are some extra packages you need to install before you can can work with those
Yeah I had already installed


> Second, in the main settings screen, there should be options for Brightness and Lock.
Yes I know but I'm writing here to find a way to change saturation levels, grey levels etc..


So about the color settings panel, I see only these options:
1) set for all users
2) add profile -> to import a ICC file
3) calibrate -> it's greyed so I cannot do anything
4) remove profile
5) see details

Here a screenshot of the color panel:
[IMG]http://s23.postimg.org/n47k5nvvv/Schermata_del_2014_11_04_19_34_56.png[/IMG]


I tried to remove the profile and relaunch the wizard to create a new profile. 
But in the box where I can choose the available profiles for the monitor, I have only the default VPCCA3C5E..

So any other ideas?

---

### Post by Lukas_Carls on 2014-11-04
> **mcflay said:**
> No as said, I have Ubuntu 12.04



Yeah I had already installed



Yes I know but I'm writing here to find a way to change saturation levels, grey levels etc..


So about the color settings panel, I see only these options:
1) set for all users
2) add profile -> to import a ICC file
3) calibrate -> it's greyed so I cannot do anything
4) remove profile
5) see details

Here a screenshot of the color panel:
[IMG]http://s23.postimg.org/n47k5nvvv/Schermata_del_2014_11_04_19_34_56.png[/IMG]


I tried to remove the profile and relaunch the wizard to create a new profile. 
But in the box where I can choose the available profiles for the monitor, I have only the default VPCCA3C5E..

So any other ideas?

Oops, I did miss that you used 12.04. Sorry about that :)

Try creating another profile for the monitor. Also, does the monitor itself have any hardware adjustments you can make?

I don't think I have any more advice to offer, mcflay. :)

---

### Post by mcflay on 2014-11-05
> Try creating another profile for the monitor.
No as I said when I try to add another profile I have only a choice: the default VPCCA3C5E monitor (that is the monitor of my laptop so no physical button to adjust some params..) 

> I don't think I have any more advice to offer, mcflay. :smile:
thanks anyway. I surrender! 

But imho are these things that cause the failure of Linux in pc world..
I asked here and in the ubuntu italian forum and nobody knows how to do a so simply (in other OS) change.
It's really absurd :(

---

### Post by Lukas_Carls on 2014-11-05
> **mcflay said:**
> But imho are these things that cause the failure of Linux in pc world..
I asked here and in the ubuntu italian forum and nobody knows how to do a so simply (in other OS) change.
It's really absurd :(

Agreed.

---

