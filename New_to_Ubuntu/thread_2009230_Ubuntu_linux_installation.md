---
title: "Ubuntu linux installation"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by salmanmanekia on 2012-06-24
Hi,
I am a newbie to Linux and am planning to install Ubuntu distro. I have a WinXP currently running on my HP Pavillion dv6000 laptop.
I am planning to remove windows and just have ubuntu linux on my laptop. I have two reasons. First, I want to act smart and work on Linux. Second, with WinXP my computer runs very slows. It takes ages to even open Firefox. So, i wonder and hope that with Ubuntu i will be able to get memory and performance optimization. I do not know this as a fact but somehow have this feeling that Linux will solved the performance problem, Right ?
Also, how about the drivers. The installation process as described on Ubuntu website looks pretty straightforward, bytheway i am planning to boot the .iso image through USB. Hopefully the installation goes through smoothly but after the installation should i be prepared for some sort of hardwork regarding the drivers or some software or is there any precautions which i should keep in mind before installing Ubuntu. Please share your experiences and advice. Thanks !

---

### Post by Fernhill Linux Project on 2012-06-24
The best way to make sure Ubuntu works fine and there are no driver or other problems is to test it live from the CD/USB. 

After creating & booting the Ubuntu Live CD/USB select try Ubuntu and run it live for a little while to make sure everything works. If you have any problems ask here.

If Ubuntu does not work or is very slow I would recommend trying Lubuntu or Xubuntu, they are lighter versions of Ubuntu, and may work better & faster on a laptop that came with XP

---

### Post by ronaldbrijo on 2012-06-24
I'm not sure if Ubuntu will speed up your pc responses, but would then suggest u go for Xubuntu which runs the lightest frontend "Xfce" although your pc may be able to run Kubuntu, which uses KDE as a front end.

Drivers is normally not a problem as linux supports most hardware, the only driver u may need is for the Nvidea card.

---

### Post by salmanmanekia on 2012-06-24
Thank you Fernhill. I will try it live. From your answer I have the feeling that ubuntu cannot and doesnot make any performance difference when replaced with XP. Regarding lubuntu or xubuntu can you tell that if my live test runs succesfully with ubuntu than would this also mean that it would be of succes with l/x ubuntu ? .Also, accroding to your experience which one of l/x ubuntu would you prefer. My needs are basic like browsing, documentation, media player, skype and programming with c++ and java with an IDE.

---

### Post by jfreak_ on 2012-06-24
What are your pc specs?
Anything above 750mb ram should be good enough for ubuntu.

---

### Post by Fernhill Linux Project on 2012-06-24
Lubuntu & Xubuntu are both very good and suitable for what you want, although Lubuntu is the lightest. They are all based on the same Ubuntu core with different desktop enviroments & apps.

You can also try them live to make sure they work properly and pick your favourite.

What are the specs of your computer & how much ram does it have?


[http://lubuntu.net/](http://lubuntu.net/)
[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by salmanmanekia on 2012-06-24
Specs are : 
Intel core2 CPU T7200 @ 2 GHz, 1GB RAM, NVIDIA GeForce Go 7400

---

### Post by Fernhill Linux Project on 2012-06-24
Ubuntu should work fine with those specs, just make sure to test it live first to make sure everything works. ;)

---

### Post by madjr on 2012-06-24
> **salmanmanekia said:**
> Specs are : 
Intel core2 CPU T7200 @ 2 GHz, 1GB RAM, NVIDIA GeForce Go 7400

the cpu is not so bad, but the ram is a bit low, so stick with 32bit versions, anyway here is a full tutorial for you:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

> Also, accroding to your experience which one of l/x ubuntu would you prefer. My needs are basic like browsing, documentation, media player, skype and programming with c++ and java with an IDE.

here is skype for you:

[http://www.omgubuntu.co.uk/2012/06/skype-for-linux-loses-beta-tag-bumps-to-4-0](http://www.omgubuntu.co.uk/2012/06/skype-for-linux-loses-beta-tag-bumps-to-4-0)


and as for programming, this might interest you:

[http://www.omgubuntu.co.uk/2012/06/its-not-to-late-to-enter-ubuntu-app-creation-contest-and-win-a-laptop](http://www.omgubuntu.co.uk/2012/06/its-not-to-late-to-enter-ubuntu-app-creation-contest-and-win-a-laptop)

Cheers and welcome to the ubuntu linux community!

---

### Post by xedi on 2012-06-24
> **madjr said:**
> the cpu is not so bad, but the ram is a bit low, so stick with 32bit versions

Why? Even with 1 gig 64bit has advantages over 32bit, it's not only about being able to use more memory.


> **salmanmanekia said:**
> From your answer I have the feeling that ubuntu cannot and doesnot make any performance difference when replaced with XP. Regarding lubuntu or xubuntu can you tell that if my live test runs succesfully with ubuntu than would this also mean that it would be of succes with l/x ubuntu ? .Also, accroding to your experience which one of l/x ubuntu would you prefer. My needs are basic like browsing, documentation, media player, skype and programming with c++ and java with an IDE.

Just try out Ubuntu first, it's plausible that you have already better performance with it. If not, then you can get and install the XFCE or LXDE desktop environment in the software-center in Ubuntu, which Xubuntu and Lubuntu respectively use. That way you can try out which desktop environment suits you best.

---

### Post by mastablasta on 2012-06-24
there is also Ubuntu 2D, and Gnome Fallback mode - i.e. old Gnome look (both have much lower system requirements that default Unity (which needs 3D hardware acceleration to work well)

KDE (though one of heaviest in resources) also has a low-fat-package that will drastically reduce the ram on boot (i think down to 180MB or somehting like that) without any serious impact on the system.

---

### Post by madjr on 2012-06-25
> **xedi said:**
> Why? Even with 1 gig 64bit has advantages over 32bit, it's not only about being able to use more memory.

.

hmm, i dont think so.

I have a computer with 12.04 64bit and 1gig ram (to test exactly that) and the thing gets horribly slow with just the browser open and a few tabs.

while i also have a partition with 11.10 32bit that is really smooth, which am going to upgrade to 12.04.

anyway , once we get **x32** support, all this 64bit vs 32bit will go away.

[http://www.phoronix.com/scan.php?page=news_item&px=MTA1OTY](http://www.phoronix.com/scan.php?page=news_item&px=MTA1OTY)

[http://www.phoronix.com/scan.php?page=news_item&px=MTEwMTk](http://www.phoronix.com/scan.php?page=news_item&px=MTEwMTk)

---

### Post by salmanmanekia on 2012-06-25
Thank you all. Apart from one problem related to my built-in HP webcam ( [http://ubuntuforums.org/showthread.php?t=2010280](http://ubuntuforums.org/showthread.php?t=2010280) ) which i am still facing the installation went smooth.

---

### Post by mörgæs on 2012-06-25
Good, then please mark the thread 'solved'.

---

