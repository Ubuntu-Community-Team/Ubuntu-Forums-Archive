---
title: "What to do after installation"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by Josh_Mustillo on 2013-08-18
Hello Guys,

I am new to Ubuntu Ive watched a couple of videos "10 things to do after installing Ubuntu", I just want to hear it from you guys what you recommend.

Thanks,

Mustillo

---

### Post by DerpishCat on 2013-08-18
Play around a bit, look around in Software Center and see if there's anything interesting.
Do what you intended to do with your OS install, or just what you usually do.

Personally I start off by removing unwanted programs and install my own, and then get to configuring everything to my liking.

---

### Post by nerdtron on 2013-08-18
Install updates!
sudo apt-get update
sudo apt-get upgrade

Then, install mp3 and video codecs.
sudo apt-get install ubuntu-restricted-extras.

Next, the software center has a lot of recommended apps. I usually browse at it and click install on something I want such as VLC, chrome, filezilla and much more :)

---

### Post by Josh_Mustillo on 2013-08-18
[B]Thank You for that I have updated, but I get this while trying to install Ubuntu restricted extras: "To install Ubuntu restricted extras, these items must be removed: 

Libav code library
[/B]libavcodec53[B]

Libav utility library
[/B]libavutil51

---

### Post by deadflowr on 2013-08-18
> **Josh_Mustillo said:**
> [B]Thank You for that I have updated, but I get this while trying to install Ubuntu restricted extras: "To install Ubuntu restricted extras, these items must be removed: 

Libav code library
[/B]libavcodec53[B]

Libav utility library
[/B]libavutil51

Those packages should be replaced with newer packages.
If you need help playing DVDs look here
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

As far as what to do after installing, click on the super key(windows icon button on your keyboard) and when the dash menu screen comes up type help.

For changes you can try out, I always recommend installing synaptic package manager, it will become easier to install and uninstall those packages you either want or don't want than either through a command line or the software center.

And really, though, before you get package installation/removal crazy, just run the system as fresh as possible to get a feel of what it's like.
Then when you think you understand a little more and want to try some new stuff go for it.

---

### Post by joshrules001 on 2013-08-18
What I usually do is get a descent video player and music player.  Then just customize different parts of it.

---

### Post by eric-c-arellano on 2013-08-19
install updates
upgrade
codecs
install keepassx so i can login to everything :) 20char passwords are hard to remember ;)

---

### Post by asifnaz on 2013-08-19
Install gimp it is like Photoshop . Install frozen bubble it is online multiplayer game . 

my 2 cents

---

### Post by r_avital on 2013-08-19
Welcome Josh,

The first thing I do is install Synaptic Package Manager (not installed by default) -- it's the premier tool for installing/removing Ubuntu software on your pc, but it does not remove the Software Center if you prefer that.  It is available in the Software Center.. 

The I install Thunderbird ( also not installed by default).
Then I customize Thunderbird and Firefox with their extensions/addons.

Then I install themes, you can get them from gnome-look.org.  Bear in mind that if you've installed Ubuntu 13.04, you want the themes that depend on GTK3.

Then I visit the following links and pick-and-choose the components I need to download/install (all refer to approved repositories, so the downloads are safe).

[A set of quick, clean, unobtrusive alternatives to run an app with Alt+F2]("http://www.omgubuntu.co.uk/2010/11/omg-5-five-ways-to-add-altf2-fun-to-unity")
[A program to cycle your wallpapers]("http://linuxg.net/how-to-install-variety-0-4-15-on-ubuntu-13-10-13-04-12-10-12-04-and-linux-mint-15-14-13/")
[Another 13 things to do after installing Ubuntu (not a video)]("http://www.noobslab.com/2013/04/tweaksthings-to-do-after-install-of.html")
[A collection of useful panel indicators]("http://www.noobslab.com/2013/04/panel-indicators-collection-for-ubuntu.html")

Most of the above will require you to enter "apt-add" in a terminal, and that command is not installed by default, but will be after you install the Synaptic Package Manager.  The command adds another repository (another software source) to your system.  Those links have detailed instructions for that as well as for the installation of the packages they describe.

Have fun!

---

### Post by RadicaX on 2013-08-19
Set up UFW firewall.

```
sudo ufw enable
```

```
sudo ufw default deny
```

You have your super firewall up and running. After that get noscript for firefox. Do not really need a virus scanner, but firewalls and things like noscript are great for added protection.

If you like art programs have a look around, there are great ones, even ones for animation for free. 

[http://divajutta.com/doctormo/ubunchu/](http://divajutta.com/doctormo/ubunchu/)

Also you might enjoy reading the manga. XD

---

### Post by deadflowr on 2013-08-19
> **r_avital said:**
> Welcome Josh,

The first thing I do is install Synaptic Package Manager (not installed by default) -- it's the premier tool for installing/removing Ubuntu software on your pc, but it does not remove the Software Center if you prefer that.  It is available in the Software Center.. 

The I install Thunderbird ( also not installed by default).
Then I customize Thunderbird and Firefox with their extensions/addons.

Then I install themes, you can get them from gnome-look.org.  Bear in mind that if you've installed Ubuntu 13.04, you want the themes that depend on GTK3.

Then I visit the following links and pick-and-choose the components I need to download/install (all refer to approved repositories, so the downloads are safe).

[A set of quick, clean, unobtrusive alternatives to run an app with Alt+F2]("http://www.omgubuntu.co.uk/2010/11/omg-5-five-ways-to-add-altf2-fun-to-unity")
[A program to cycle your wallpapers]("http://linuxg.net/how-to-install-variety-0-4-15-on-ubuntu-13-10-13-04-12-10-12-04-and-linux-mint-15-14-13/")
[Another 13 things to do after installing Ubuntu (not a video)]("http://www.noobslab.com/2013/04/tweaksthings-to-do-after-install-of.html")
[A collection of useful panel indicators]("http://www.noobslab.com/2013/04/panel-indicators-collection-for-ubuntu.html")

Most of the above will require you to enter "apt-add" in a terminal, and that command is not installed by default, but will be after you install the Synaptic Package Manager.  The command adds another repository (another software source) to your system.  Those links have detailed instructions for that as well as for the installation of the packages they describe.

Have fun!

Good points in all.
But this got me
> [COLOR=#000000]The I install Thunderbird ( also not installed by default).[/COLOR]

You are discussing Ubuntu, right?

Thunderbird's been the default email client since Oneric/11.10, I think(maybe even Natty/11.04).

Otherwise, yep synaptic will help make life a whole lot easier, in the long run.
I use synaptic to install multiple packages at once(far easier and more efficient than software center)
It can also update your system.
And if your someone like me who runs systems for prolong periods without reinstalling a fresh install, it's helpful in cleaning up old unused items such as old old kernels.
But I don't put down the Software Center, the reviews are a great indicator if a package might be worth my while.
And running installation of a couple of packages, in ain't bad.

Anyhow, 
Have fun learning, playing, and getting to know your new operating system.

---

### Post by OrangeCrate on 2013-08-19
> **Josh_Mustillo said:**
> Hello Guys,

I am new to Ubuntu Ive watched a couple of videos "10 things to do after installing Ubuntu", I just want to hear it from you guys what you recommend.

Thanks,

Mustillo

Here's a good website to bookmark for use both now and in the future:

**Easy Linux Tips Project**

[https://sites.google.com/site/easylinuxtipsproject/](https://sites.google.com/site/easylinuxtipsproject/)

---

### Post by Lim_Xiang_Yann on 2013-08-19
get essential packages
> apt-get install build-essentials

---

### Post by ahmad3 on 2013-08-19
as all of them say install updates and make sure everything is working fine such as Wi-Fi and stuff then start playing around a bit in the dash home google stuff about ubuntu

---

### Post by r_avital on 2013-08-19
> **deadflowr said:**
> 
You are discussing Ubuntu, right?

Thunderbird's been the default email client since Oneric/11.10, I think(maybe even Natty/11.04).


Thanks for pointing it out.  I won't dispute that.  It's been my habit going from one version to the next, to expect that TB is not installed by default.  I skipped over everything from Lucid to Raring, so it's possible I didn't notice that change.

---

### Post by r_avital on 2013-08-19
Oh! Josh, one more!  How could I forget?

Install Stellarium.  It will blow your mind!

---

### Post by ian-weisser on 2013-08-19
> **Josh_Mustillo said:**
> I am new to Ubuntu Ive watched a couple of videos "10 things to do after installing Ubuntu", I just want to hear it from you guys what you recommend.

Videos like that are entertaining, but I find them rubbish for good advice.
It depends entirely upon how you plan to use your system. Programming? Gaming? Video?
Ubuntu has a nice, balanced set of features and applications out-of-the-box. Use them. Learn your system first.
Once you decide what you wish to add, if anything, it's very easy.

---

### Post by monkeybrain20122 on 2013-08-19
1. install synaptic, which is much much better than the Software centre for installing software,'sudo apt-get install synaptic'
 install gdebi (which is for installing downloaded debs for some occasion, again much snappier than the software centre) 

2. Install ccsm (compiz config settings manager). It allows you to customize your unity desktop (e.g adding virtual desktops), gnome-tweak-tools, dconf-tools (if not already installed), gconf-editor (sometimes come in handy) Search for them in synaptic.

3. install Ubuntu-restricted-extras. install libdvdcss2 for playing dvds.[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

4. I find it useful to install pulse-audio-volume control ('sudo apt-get install pavucontrol' or search in synaptic)  and alsamixer, they are useful when you need to troubleshoot or tweak sound settings.

For me this is the basic post install setup. Anything else you can add or subtract later to suit your needs. :)

---

### Post by Paari on 2013-08-19
Hi! I'm using this widget theme for ubuntu named techno-conky. I prefer looks and you may like it. Check it out...
[http://www.noobslab.com/2012/11/install-techno-conky-in-ubuntu.html#wget](http://www.noobslab.com/2012/11/install-techno-conky-in-ubuntu.html#wget)

Regards

Paari

---

### Post by Cyphrex on 2013-08-19
Same as DerpishCat, play around, make sure your browser of choice has required addons to load flash/shockwave, I loaded audacity for audio editing, warzone and 0 A.D. for gaming and removed the Libre office off the taskbar for more room. Also installed the firewall package, and put the network tools on taskbar for quick access at wifi cafes as well as the advanced settings. typically I use mine for youtube videos, surfing the net, logging geocaches (cant load to my magellan yet), and playing with Truecrypt for file encryption and USB flash drives live disk for quick boots to test equipment or where I don't want to leave a searchable "footprint". Course im still a noob and just playing around. If you're afraid to tear something up could use clonezilla to image your puter so if you mess it up could just reload it and play again.

---

