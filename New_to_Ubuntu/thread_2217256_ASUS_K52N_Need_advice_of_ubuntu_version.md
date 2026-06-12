---
title: "ASUS K52N: Need advice of ubuntu version"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by 21miki21 on 2014-04-16
Hi,
Iam new to this forums and totally n00b in the world of Linux.
And ready to try new world ;) but need some advice.

So, now Iam running Windows 8.1 x64 (C- system, D-data) and Ubuntu 13.10 x64 in dualboot (with grub installed on the same partition as ubuntu is and using windows loader because If something went wrong with ubuntu windows has to work all the time). Notebook [ASUS K52N]("http://www.asus.com/Notebooks_Ultrabooks/K52N/specifications/") (single core AMD® V Series V120 2.2 GHz Processor) with 4Gb of RAM (-256Mb of shared graphics memory).

Installed 13.10 version as it is newest to try. So my question is.
Which version is the best for this type of HW? Windows 8.1 x64 is running quite nice on this 3 years old machine, but Ubuntu 13.10 x64 seems to not work as good as I expected.
Iam planning to install 14.04 tomorrow (I dont want to install any unreleased jesus, bad experiences with it from windows lol).

Ubuntu 14.04, but which version for old notebook with singlecore 2.2ghz processor and 4gb ram? x86 or x64? Now running 13.10 x64 and I dont know, it is sipmle not working as holy windows 8.1, system reactions and so on are not the best in comparison to holy windows 8.1. Next problem is my crap graphics that is not supported by AMD. ATI Mobility Radeon 4200 HD series. Tried few ways to install properietary drivers here on 13.10 without success. Ubuntu tells me that there is "Gallium 0.4 on AMD RS880" graphics installed.

And finally, what about swap partition size? Tried 6Gb now with 13.10 and seems that there is no problem with this, but I dont know if it is too oversized or small. I think I will not use hibernation here, tried hibernation and notebook started to be crazy as hell unless removed battery and start again. Maybe something incompatible with windows bootloader or MBR, I dont care. I know that ubuntu will not be 100% funcional with this configuration (installed 2 NTFS partitions with windows and grub as not primary bootloader)

Thanks for your replies :cool:

---

### Post by Canterwood on 2014-04-16
What do you mean when you say performance is not as good as it is in Windows? Are you talking about responsiveness of the system, or are CPU-intensive tasks taking longer than usual?

If it's the former, I'd advise you to have a look at a few different desktop environments. Unity (the standard desktop environment) uses 3D-acceleration and since you say your graphics card is not supported I'm not surprised that it doesn't work very smoothly. XFCE or LXDE don't use 3D-acceleration and should work a lot smoother. It worked for the guy I advised [here]("http://ubuntuforums.org/showthread.php?t=2217075&p=12988602#post12988602"). Take a look at the third post.

If your ATI graphics card isn't supported by proprietary drivers I'd stick with the open source versions. Best of luck!

Oh, and about the swap partition, Linux generally will avoid using it unless your RAM chokes, but 6GB should be plenty.

---

### Post by 21miki21 on 2014-04-16
Responsiveness of system. CPU-intensive task will probably halt whole system as it is in windows, I do not expect anything from this weak processor.

Tried Kubuntu, but KDE was visibly slow. The same with Cinnamon on Mint 16.
Ok, will try XFCE and LXDE as you adviced in that link.

Thanks

---

### Post by mörgæs on 2014-04-16
> **21miki21 said:**
> 
I am planning to install 14.04 tomorrow

I recommend that you wait at least a couple of weeks. Not because there's anything wrong with 14.04 in particular, but because no operative system is mature at release date.

---

### Post by ibjsb4 on 2014-04-16
Something else you can try on your current install is a different desktop.  You could add the Flashback mode.

Open a terminal and enter:

```
sudo apt-get install gnome-session-flashback
```

Log out and when you get back to the login window click on the icon and choose flashback with metacity, no effects.

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by su:bhatta on 2014-04-16
> **21miki21 said:**
> 
Iam planning to install 14.04 tomorrow (I dont want to install any unreleased jesus, bad experiences with it from windows lol).

Ubuntu 14.04, but which version for old notebook with singlecore 2.2ghz processor and 4gb ram? x86 or x64? Now running 13.10 x64 and I dont know, it is sipmle not working as holy windows 8.1, system reactions and so on are not the best in comparison to holy windows 8.1. Next problem is my crap graphics that is not supported by AMD. ATI Mobility Radeon 4200 HD series. Tried few ways to install properietary drivers here on 13.10 without success. Ubuntu tells me that there is "Gallium 0.4 on AMD RS880" graphics installed.

And finally, what about swap partition size? Tried 6Gb now with 13.10 and seems that there is no problem with this, but I dont know if it is too oversized or small. I think I will not use hibernation here, tried hibernation and notebook started to be crazy as hell unless removed battery and start again. Maybe something incompatible with windows bootloader or MBR, I dont care. I know that ubuntu will not be 100% funcional with this configuration (installed 2 NTFS partitions with windows and grub as not primary bootloader)

Thanks for your replies :cool:

Well, that Radeon card is not supported with proprietory drivers by AMD anymore. So you are stuck with the OpenSource drivers as stated above.
You should be having a nice experience with Xubuntu.
You can get it here: [http://xubuntu.org](http://xubuntu.org)

6Gb Swap is overkill, I would say, general thumb rule from what I've read is equal to your RAM.
But if you don't hibernate, I never have done, then even 4Gb might be too much. 2 Gb should be sufficient.

---

### Post by 21miki21 on 2014-04-16
Thank you all for your replies. I installed xubuntu and lubuntu desktop enviroments and LXDE seems to work better, but need more time anyway to test it more. + windows look for linux newbies.
Can I use Ubuntu with lubuntu desktop or better option is install Lubuntu standalone?

About swap size, next time will try 2Gb.

---

### Post by su:bhatta on 2014-04-16
> **21miki21 said:**
> Can I use Ubuntu with lubuntu desktop or better option is install Lubuntu standalone?

About swap size, next time will try 2Gb.

If you plan on installing 14.04 a couple of weeks from now, why bother in installing standalone Lubuntu now?
When you install 14.04, then you decide. If you don't/can't use Ubuntu or rather Unity, then why bother?

Just install Lubuntu. 
Any software you used in Ubuntu/Unity and is by default not there you can always use software-center, or better use Synaptic to install.

---

### Post by war28 on 2014-04-16
Hi!

You can use Ubuntu with Lubuntu Desktop, the only thing different from Lubuntu standalone is that you have more files installed because you installed Ubuntu and then installed Lubuntu (hope I made myself clear).

If you think that Lubuntu is the way to go for you and you don't mind reinstalling, I advise you to do a clean install of Lubuntu.
As other have said, you could also try Xfce (which I'm running now and love it). It's all up to you, try all of them and then do a clean install with the Desktop Environment you want.

---

