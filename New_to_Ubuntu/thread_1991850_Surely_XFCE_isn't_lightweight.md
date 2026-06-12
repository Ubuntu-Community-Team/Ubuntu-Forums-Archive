---
title: "Surely XFCE isn't lightweight?"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by flurospar on 2012-05-31
To begin with, I downloaded Xubuntu 12.04 yesterday, hoping that Xfce would be lighter on my elderly computer (Intel Pentium 4 1.8 GHZ, 1150 MB RAM, 48 MB Intel graphics controller).

But, I am not seeing any signs of Xfce being "lightweight": when run in Live mode, I can see the windows and desktop elements being rendered in slow motion. Programs are taking several seconds to open, it is taking several seconds to type in Abiword.

The Live mode shouldn't be a problem, since Ubuntu >= 10.10 have all run perfectly well on this elderly thing without a problem, and I haven't burned to disc this time, but have rather used Unetbootin, which should be faster than booting from a disc.

Are there ways to speed up Xubuntu? Is it a problem with my hardware, or can it be resolved by changing the configuration of xfwm?  Or do I have to live with this "lightweight" distro?

Please help.

---

### Post by na5h on 2012-05-31
XFCE is lighter than Unity, but opening applications in the Live version is always slower since everything has to be loaded from the CD/DVD/USB-stick. An even lighter alternative would be Lubuntu (LXDE).

Perhaps you also need to install some additional drivers for the video card? 

For the record: Ubuntu 12.04 with Unity runs just fine (although multi-tasking is slow) on my own Pentium 4 (~ 3GHz, 1GB RAM, 256MB ATI)...

---

### Post by mörgæs on 2012-05-31
Xubuntu is medium-weight. For this computer (from around 2002, I guess) I recommend Lubuntu.

---

### Post by Paqman on 2012-05-31
> **na5h said:**
> 
Perhaps you also need to install some additional drivers for the video card? 


If it's Intel graphics there should be no need, their drivers are shipped in the kernel.

---

### Post by Lyfang on 2012-05-31
> **mörgæs said:**
> Xubuntu is medium-weight. For this computer (from around 2002, I guess) I recommend Lubuntu.

1+
You can try to install LXDE beside XFCE:
```
sudo apt-get install lxde
```
After installation is complete log out & log in with your login manager to LXDE.

---

### Post by 3rdalbum on 2012-05-31
That sounds unusually slow. Have you checked the 'top' command to see if there might be a process that's using 100% of your CPU?

---

### Post by jmore9 on 2012-05-31
I was running ubuntu 12.04lts on a sempron 3000+ ( 1.8gig) and it worked just fine.  Only problem was that i was using a geforce 4 mx4000.  Not supported in 12.04 for graphics.  

So i ran it in classic mode , i think it was.  Only did that because of the graphic card.

---

### Post by steeldriver on 2012-05-31
I'd agree with posters above, it's likely going to be quite a bit faster from an installed system

I'm typing this from Xubuntu 11.10 on a 1.2GHz PIII-M laptop with Intel 82830 graphics and 1GB RAM and I find it acceptable for everyday browsing / email etc. The graphics chipset is the weak point (don't expect to watch HD media content on it) but otherwise it's quite usable.

---

### Post by Lars Noodén on 2012-05-31
If you want light weight you can go with the suggestions above to install LXDE.  

Or if you want still leaner, you can skip the Desktop Environment completely and work with a raw Window Manager.  Openbox seems to the favorite these days but FVWM (fvwm-crystal), Fluxbox, Oroborus or Enlightenment are some of the options there.  There will be less customization possible, and some of it may need to be done by editing files, but there will also be a lot less overhead.  Oroborus, for example, is said to use 63KB.

---

### Post by vasa1 on 2012-05-31
> **Lars Noodén said:**
> If you want light weight you can go with the suggestions above to install LXDE.  

Or if you want still leaner, you can skip the Desktop Environment completely and work with a raw Window Manager.  Openbox seems to the favorite these days but FVWM (fvwm-crystal), Fluxbox, Oroborus or Enlightenment are some of the options there.  There will be less customization possible, and some of it may need to be done by editing files, but there will also be a lot less overhead.  Oroborus, for example, is said to use 63KB.

Do you have any links on the subject? I know that Bodhi Linux uses Enlightenment and that looks pretty despite being lightweight.

---

### Post by Lars Noodén on 2012-05-31
Here's a longer list: [http://xwinman.org/others.php](http://xwinman.org/others.php)

But you can go through the Ubuntu repository and pick some out to try.  I added fvwm-crystal above because it shows how much you can customize even a simple window manager.  If you compare it to plain fvwm, the difference is profound.

---

### Post by uRock on 2012-05-31
I have a machine with P4 and 1GB RAM. It ran well with ubuntu and xubuntu. Sounds like most of the issue is from running it via LiveCD. Those things have always been slow for me.

---

### Post by vasa1 on 2012-05-31
> **Lars Noodén said:**
> Here's a longer list: [http://xwinman.org/others.php](http://xwinman.org/others.php)

But you can go through the Ubuntu repository and pick some out to try.  I added fvwm-crystal above because it shows how much you can customize even a simple window manager.  If you compare it to plain fvwm, the difference is profound.
Can I ask about two necessities: one is psensor ([http://wpitchoune.net/psensor](http://wpitchoune.net/psensor)), the other is system load indicator ([https://launchpad.net/indicator-multiload](https://launchpad.net/indicator-multiload)). Both need to be always visible even though apps such as a browser or LibreOffice are running maximized.

---

### Post by Peripheral Visionary on 2012-05-31
When you run *ANY* Linux distro *from the LiveCD*, _it will be SLOW!_ It's performance hugely, immensely, vastly improves *when installed*. Even the ultralight Crunchbang Linux is slow when experienced from a LiveCD. Lubuntu will behave the same way. You simply have to *install* it (either to your hard drive or a virtual environment) to experience and rightly judge it's performance.

**I have found** **[COLOR=DarkOrange]no discernible difference[/COLOR] in speed or performance on my computer - which has HALF the RAM of yours - [COLOR=DarkOrange]between Lubuntu and Xubuntu[/COLOR].** None. Lubuntu is sweet and fast and pretty, but a bit buggy yet on my hardware, and lacks some features (panel applets, etc) that Xfce offers. So for me it has been an easy choice. I have my cake and eat it too! Xubuntu is screamin' fast on my aging, hand-me-down hardware, yet still offers the little extras I like.

---

### Post by mastablasta on 2012-05-31
increase the speed by loging out and selecting xfce desktop instead of xubuntu dekstop. should trim down some special effects... since you graphics card is not really anything special...
 
otherwise XFCE takes about 80 MB to run. Xubuntu version will use abotu 120-130 MB ram and is really fast on older mashcines.
 
using 32MB S3 card , 256MB ram and 1.2Ghz old CPU it runs much much faster than windows XP.
 
you experience could be because of livemode or because of graphics card. i know that i had an old ATI rage card 16MB and Ubuntu worked very good as long as special effects were off. oh and the only problem at the time were some flash videos. but that maschine had 800Mhz CPU so it's not that surprising.
 
Some other light alternatives:
 
Bodhi linux (uses E17 desktop environment but based on Ubuntu, needs 800MHz CPU and 128 MB ram)
Chrunchbang (uses Openbox DE, based on debian stable, but with newer versions of programmes)
---
Slitaz
Puppy Linux
These two are designed for old maschines and can run on as low as 64MB ram some ven lower.

---

### Post by kurt18947 on 2012-05-31
I also notice a difference between USB drives.  I have an 8 GB. Relay (Staples house brand) which seems pretty .... stately.... compared to 2 8 GB. Centons from CompuUSA.  All were installed using Ubuntu's Startup Disk Creator.  And yes, live sessions on USB drives seem faster than live sessions on CD/DVD but not as fast as installed on a hard drive.

---

