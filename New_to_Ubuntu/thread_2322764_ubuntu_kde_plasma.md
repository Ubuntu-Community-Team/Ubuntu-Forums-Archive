---
title: "ubuntu kde plasma"
date: 2016-04-30
forum: New to Ubuntu
---

### Post by pasan_mendis on 2016-04-30
Hi, I'm a new ubuntu user.I installed KDE PLASMA to my computer. Now it's boiring to me. Now I try to switch to ubuntu unity. But I can't switch to it, I try to do switch to ubuntu unity by the switch in start home but I can not do that. please help me :D:D:D

---

### Post by T.J. on 2016-04-30
You need to install it first.  When you install from a Kubuntu disc, Unity is not available.  You need to run an install in the terminal:

[I]sudo apt-get install ubuntu-desktop ubuntu-restricted-extras

[/I]Once that is done, log out and change your session type, then login again.

---

### Post by pasan_mendis on 2016-05-01
Thank you for reply.But I cannot switch to unity.I click the session type but the machine will not respond.:?::?:

---

### Post by grahammechanical on 2016-05-01
Have you installed Ubuntu or Kubuntu? Which version? 14.04, 15.10 or 16.04? How did you install KDE Plasma? What version of Plasma? Version 5?

I do not use Kubuntu. I would not install an alternative desktop environment on to Ubuntu because they are not easy to remove when we are finished playing with them. I avoid experimenting with my working install of Ubuntu. I dual boot and experiment with an installation that I do not mind re-installing over. Sometimes a re-installation is the less troubling way of fixing things.

Some people install an alternatice desktop and then remove Unity. Have you done that?

Regards.

---

### Post by T.J. on 2016-05-01
I need more information please.  I am assuming you ran the install commands, logged out, switched the desktop session type and  tried to log in?  Then it froze or did it simply not login?  If it did not login, then the install was incomplete for some reason and we will need to investigate.

In theory, that should never happen, unless the package chain was released with a bug.

---

### Post by T.J. on 2016-05-01
Just installed 16.04 as you did, except that I switched from Unity to Mate - but the process to switch should be identical, with only slight changes.

Try *sudo apt install ubuntu-desktop ubuntu-restricted-extras ubuntu-restricted-extras*.  It should get the job done. The last two restricted are optional.  They may not be legal in your jurisdiction, and should be used at your own risk.  You will need to restart for it to behave.

If you want to have the bootup spash and so on, that is an extra step.

[I]sudo apt-get install ubuntu-artwork
sudo apt-get purge kubuntu-artwork
sudo update-initramfs -k all -u[/I]

Then reboot.

---

### Post by pasan_mendis on 2016-05-02
> **grahammechanical said:**
> Have you installed Ubuntu or Kubuntu? Which version? 14.04, 15.10 or 16.04? How did you install KDE Plasma? What version of Plasma? Version 5?

I do not use Kubuntu. I would not install an alternative desktop environment on to Ubuntu because they are not easy to remove when we are finished playing with them. I avoid experimenting with my working install of Ubuntu. I dual boot and experiment with an installation that I do not mind re-installing over. Sometimes a re-installation is the less troubling way of fixing things.

Some people install an alternatice desktop and then remove Unity. Have you done that?

Regards.
I used ubuntu 14.04, my plasma version is 5

---

### Post by neu5eeCh on 2016-05-04
> **pasan_mendis said:**
> I used ubuntu 14.04, my plasma version is 5

Wait... what?

Plasma 5 wasn't released with 14.04. If you installed the Kubuntu desktop, KDE 4.x should have been installed. Plasma 5 could only be installed via the Kubuntu Backports PPA?

Somethin' don't add up here....

---

