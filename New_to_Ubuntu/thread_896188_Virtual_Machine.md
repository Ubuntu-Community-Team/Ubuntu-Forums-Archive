---
title: "Virtual Machine"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by bgast1 on 2008-08-20
I finally am ready to start trying a virtual machine in Ubuntu Hardy Heron. I've never done this before so I really don't know where to start. I have a couple of goals in mind. 

1.) I want to use a virtual machine to try other distros. (I have 3 hard drives, but don't know how Grub would act, and still have a lot to learn about GRUB) It was suggested to me to try to run them in a virtual machine.

2.) I want to install Windows XP so that I can try to play Civilization III or IV, and an older Golf game.

I tried a google but became a bit overwhelmed and didn't know what direction to take. There are several virtual machine applications out there and I don't know what to pick. I tried last night with virtualbox ose, but became stuck and didn't know if it was installed correctly so I uninstalled it and decided to come here for help. 

I know that you could move this over to the virtualization threads but I was there too and was a bit overwhelmed.

---

### Post by Rolcol on 2008-08-20
There's an open source Virtual machine software called [VirtualBox](http://virtualbox.org).  It's open source and there's a version of [VirtualBox](apt://virtualbox-ose) (click this link to download it) in the repositories.

---

### Post by tuxxy on 2008-08-20
Search for virtualbox in synaptic or type in terminal

```
sudo apt-get install virtualbox
```

heres a guide to get you started with creating a virtual drive

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by sdennie on 2008-08-20
If your motivation for using VM technology is to play modern games that require 3D graphics, you are going to be disappointed.  The 3D parts of your graphics card aren't presented to the virtual machine and so it's not really possible to run 3D games.  However, there is hope for many games (especially older or very popular games): Use wine and run the game natively.  Google it or check [www.winehq.com](www.winehq.com).

---

### Post by friendofpugs on 2008-08-20
I use Virtual Box too. Easy to install and enterprise strength. :)
This tutorial worked better for me: [http://ubuntuforums.org/showthread.php?t=770745]("http://ubuntuforums.org/showthread.php?t=770745")

---

### Post by bgast1 on 2008-08-20
> **vor said:**
> If your motivation for using VM technology is to play modern games that require 3D graphics, you are going to be disappointed.  The 3D parts of your graphics card aren't presented to the virtual machine and so it's not really possible to run 3D games.  However, there is hope for many games (especially older or very popular games): Use wine and run the game natively.  Google it or check [www.winehq.com](www.winehq.com).

I can accept the game problem, no real big deal there. When I decided to run Linux exclusively on my computer, I went out and bought a Playstation 3.
I'll just go out and buy Civilization Revolutions (I think that's what it is called).

What I really want to do more than anything is fool around with different Linux distros without screwing up my Ubuntu system. Is that possible? I know that there is the live disk option as well but I am unsure of just how much you can do with a live disk.

Wine is also installed on my machine. I found a thread the other night on customizing Ubuntu and followed the instructions, it installed Wine and the Virtual Box which I uninstalled tonight because of the problems I experienced last night.

---

### Post by bgast1 on 2008-08-20
> **tuxxy said:**
> Search for virtualbox in synaptic or type in terminal

```
sudo apt-get install virtualbox
```

heres a guide to get you started with creating a virtual drive

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Would this also work with ```
sudo aptitude install virtualbox
```

I'm not really sure about the differences between the two. Someone told me that it had to do with the way dependencies were handled. People have told me in the past that aptitude is a better way to go. I honestly don't know. Guess I should research it.

---

### Post by sdennie on 2008-08-20
For VirtualBox, I *highly* recommend using the version from [www.virtualbox.org](www.virtualbox.org).  It's more up to date, has more features and it's easier to keep it running in different kernels.

As for apt-get vs. aptitude, I would just stick with apt-get.  As far as I'm aware, every gui utility ends up using apt-get and so mixing aptitude into it can cause annoying problems.

---

### Post by Vivaldi Gloria on 2008-08-20
> **vor said:**
> For VirtualBox, I *highly* recommend using the version from [www.virtualbox.org](www.virtualbox.org).  It's more up to date, has more features and it's easier to keep it running in different kernels.


+1

Here's the download page:

[[COLOR="Green"]virtualbox[/COLOR]]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

Double click the deb file when you download.

---

### Post by bgast1 on 2008-08-21
> **Vivaldi Gloria said:**
> +1

Here's the download page:

[[COLOR="Green"]virtualbox[/COLOR]]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

Double click the deb file when you download.

Done.... Now all I have to do is learn how to use it.

---

### Post by Gregmond on 2008-08-21
Everyone seems to have dealt with the vbox thing so just to finish off your other option...

Wine. To improve it and add some extra functionality:
Google wine-doors and install it.

---

### Post by Vivaldi Gloria on 2008-08-21
Gregmond makes a good point. If there is a choice between running a program in a wine and running it in XP in vbox then choose wine over vbox. wine is close to native - so it'll run faster & better than in vbox. For example, I run foobar2000 (sound player/converter) in wine. It can use all cpus when converting. To find which apps run in wine seach here:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

But of course to try out an OS you use vbox.

---

### Post by bgast1 on 2008-08-21
One more question on Virtual Box. I got it installed and I installed Gutsy just to try it out. To uninstall Gutsy, do I just hit the 'delete' button in the upper left hand corner of Sun xVM VirtualBox? Will that completely get rid of all the programs and files that I may have running in that virtual machine?

If that isn't how you do it, then how do you do it? Do I have to be concerned about it affecting anything not in the virtual box?

---

### Post by ooobuntooo on 2008-08-21
> **bgast1 said:**
> One more question on Virtual Box. I got it installed and I installed Gutsy just to try it out. To uninstall Gutsy, do I just hit the 'delete' button in the upper left hand corner of Sun xVM VirtualBox? Will that completely get rid of all the programs and files that I may have running in that virtual machine?

If that isn't how you do it, then how do you do it? Do I have to be concerned about it affecting anything not in the virtual box?

The virtual hard drive still exists with gutsy still installed, you can re-use this HDD or delete it.

---

### Post by bgast1 on 2008-08-21
I have Windows XP now running in my virtual machine because I want to try a couple of things. I have 3 issues that I don't understand.

1.) Windows XP is asking me to authenticate. I have typed in the correct key, but they won't accept it as a valid key. What will happen at the end of 30 days, provided I even keep it that long?

2.) Windows XP only takes up a small portion of my screen and no matter what I do I cannot get it bigger.

3.) How do I uninstall it when I have finished with Windows XP. I will want it entirely off my hard drive when I give it the boot if it won't do what I want it to do.

---

### Post by Vivaldi Gloria on 2008-08-21
> **bgast1 said:**
> 2.) Windows XP only takes up a small portion of my screen and no matter what I do I cannot get it bigger.

Start XP in vbox. You need to install VBoxGuestAdditions in XP. Look for it in the vbox menu.

---

