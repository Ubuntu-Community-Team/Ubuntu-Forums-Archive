---
title: "first install - screen blinks and can't navigate"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by exoscoriae on 2013-02-01
hello.  I followed the following thread to install ubuntu on a zotac mag hd-nd01:
[http://forum.xbmc.org/showthread.php?tid=68653](http://forum.xbmc.org/showthread.php?tid=68653)

The primaru difference is i got Ubuntu 12.10 (where-as that tutorial seems to have been written when 9.10 was out).  After formatting the usb as fat32, and running the netbootin tool, I was able to make a functional install usb drive.

I did a clean install of it to the system, wiping out the win8 install that was previously on there.

Everything seems to go well through the install process.

On the first reboot however, I get a black background, white mouse cursor and *sometimes* I get a side bar.  If I try to click on the side bar, things start to blink rapidly, and many times when a new window opens up it is a solid block of color that i can not read.

I suspect that drivers may be the issue, however I have two problems.  The first is there are no linux drivers posted on the hd-nd01 website.  The second if the method by which to install drivers listed on the tutorial I used seems to have changed since "jaunty jackalope".  I was able to get a system window to open and be readable, however I saw no "administrator" icon, nor did I see the Update manager\hardware Drivers sections listed.

I've been using windows for nearly 20 decades now and dos before that, so I'm not new to computers... just linux.   Any assistance would be greatly appreciated.

---

### Post by windscape on 2013-02-01
Hi,

According to [this]("http://www.zotacusa.com/mag-hd-nd01.html") link, that system appears to have an NVIDIA ION chipset. To get the best experience from it, you need to install the proprietary NVIDIA drivers.

Although the link [here]("http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10") are dealing with a different model NVIDIA GPU, the instructions posted there should work.

---

### Post by exoscoriae on 2013-02-01
Thank you very much, that made the desktop useable.  However... it is very slow.... one reason i wanted to switch to linux is I believed that the software i intend to run on it would be quicker on linux.  In one thread I read about installing nvidia hardware acceleration drivers, however it was for 10.9 rather than 12.10, and the repository wasn't recgonized when I tried to install it.

The tutorial suggested:
sudo apt-get install libvdpau1 nvidia-185-libvdpau

I imagine this has been updated since then?  I'm not sure it would solve my problem installing this or not, but I figured it couldn't hurt.  Is there a method by which i can find what the most recent version is for 12.10?

---

### Post by sandyd on 2013-02-01
> **exoscoriae said:**
> Thank you very much, that made the desktop useable.  However... it is very slow.... one reason i wanted to switch to linux is I believed that the software i intend to run on it would be quicker on linux.  In one thread I read about installing nvidia hardware acceleration drivers, however it was for 10.9 rather than 12.10, and the repository wasn't recgonized when I tried to install it.

The tutorial suggested:
sudo apt-get install libvdpau1 nvidia-185-libvdpau

I imagine this has been updated since then?  I'm not sure it would solve my problem installing this or not, but I figured it couldn't hurt.  Is there a method by which i can find what the most recent version is for 12.10?
nvidia-185-libvdpau seems to have vanished, though libvdpau1 still exists.

A good way to search for packages on ubuntu is through the Ubuntu Package Search ([http://packages.ubuntu.com/](http://packages.ubuntu.com/))

Just follow the instructions in [http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10](http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10), and they should work

---

### Post by DuckHook on 2013-02-01
Wasn't aware of this cool little machine and had to google the specs for it. Glad that you introduced me to it. 

BTW, welcome to the forums. It's always nice to see new users to Linux.

Re: the Zotac:

Based on its specs, this cool little mini-machine is barely powerful enough to run the modern flavours of Ubuntu, but will run very nicely on Lubuntu. It all depends on the amount of system RAM you've loaded it with, and the amount of RAM carved off to the GPU. Ubuntu has changed greatly since the rather dated info you've read, and it is much more resource hungry now, with spinning 3D desktop cubes, fading windows and all sorts of eye-candy. It's still not as resource hungry as the latest Windows OS but it is no longer the tiny little wonder that it started out as. I suppose that this is both good and bad.

I strongly suggest that you forego Ubuntu and try Lubuntu, which is still tight and tiny because it foregoes all of the eye-candy. There are other miserly OSes, but Lubuntu keeps you within the same repositories and avails you of this help forum, among other pluses. It should run very nicely and responsively on the Zotac. You should still install the proprietary drivers, though. This is done quite simply after install much along the same lines as you've already done under Ubuntu.

---

### Post by exoscoriae on 2013-02-01
I would be very interested in trying lubuntu.  Can I find an iso and install it using the same utility as in the tutorial?  I'll have to Google around and see if I can find a lubuntu tutorial for the parts that you hinted are different.

I picked this little machine up off eBay for like ninety bucks.  I don't have super high hopes for it, but I'd like to have a little media center.  Should I try lubuntu, or simply go pull an older version like jaunty jackalope?

---

### Post by sandyd on 2013-02-01
what I would probably do (if you want a media center) is to start with Ubuntu Minimal.

Install XBMC from the xbmc PPA, and use openbox as your wm. Openbox is very light, even more than LXDE.

The only issues I had with this setup was that XBMC wouldn't shut down the computer. In the openbox startup script, I ended up adding shutdown/halt right after the script that started XBMC. Once XBMC closed, the shutdown script would automatically run. I had to add the shutdown command to sudoers so everyone could run it without a sudo password though.

---

### Post by DuckHook on 2013-02-01
I think you got a pretty sweet little deal.

You can get Lubuntu [here]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu"). I recommend the 64-bit version. I always torrent my downloads, but you have the choice of downloading directly off the site. Before installing, you may wish to check your bios settings to see how much system memory has been assigned to your video card. Since you want to use the Zotac as a media centre, I would suggest at least 128 MB. If your system RAM is 1GB or more, then increase video RAM to 256 or more. I don't really know anything about the Zotac, and its video RAM may not be assignable, in which case, I suppose you will just have to live with whatever has been preassigned.

Happy Ubuntuing!

<edit>
Listen to @sandyd and not to me. Forums Staff are always more knowledgeable and XBMC is an excellent suggestion. Still look into the video RAM thing though. Actually, I'm rather envious of this new direction you will be exploring and am half-minded to look at e-bay for a machine like that of my own! Please do post back and let us know how you make out. PM me if you like.

---

### Post by DuckHook on 2013-02-01
> **sandyd said:**
> Install XBMC from the xbmc PPA

@sandyd

Is the PPA more recent than the version in the repository? Am wondering why you recommend it over repo version.

---

### Post by drawkcab on 2013-02-01
> **exoscoriae said:**
> I picked this little machine up off eBay for like ninety bucks.  I don't have super high hopes for it, but I'd like to have a little media center.  Should I try lubuntu, or simply go pull an older version like jaunty jackalope?

NO!!! 

I had the equivalent Acer Revo 3600 running as an HTPC for the last four years or so (gpu just died :( ) so let me give you some pointers.

1.  With my revo there were some settings in the BIOS that I had to switch in order to maximize the ION graphics.  I'm sure there are some equivalent settings that need to be adjusted for your box.  I suspect this is one aspect of your troubles.

2.  Upgrade the RAM.  The n330 ion platform needs some increased overhead to operate as the system taps into the ram to run the gpu and such.  I suggest 3gb minimum but you probably just want to max it at 4.  Keep in mind it runs ddr2 which is harder to find nowadays.  I suspect this is the other aspect of your troubles.  My Revo had two slots from ram.

3.  I suggest not running lubuntu or xubuntu because it is difficult to get the desktop to scale to the television.  Instead the best option is, gasp, gnome shell.  You can use the advanced settings to scale the desktop to your TV with the slider that manages the font sizes. It is sluggish under load sometimes but it's worth it and the video that is produced has none of the tearing associated with non-gtk3 desktops!!! 

4.  As per 3, you might want to just install ubuntu gnome shell remix based on 12.04 and go from there so you don't have unity window management crossed with gnome shell.  Whatever you do, I suggest 12.04 which offers long term support and is generally more stable.  12.10 is buggy in terms of its graphical support which might account for some of your problems.

5.  Once you get your 12.04 system up and running, install the latest graphics driver and set it to sync with your display and run vdpau.  Install SMplayer and set it to use vdpau and graphical acceleration to offload decoding to the gpu.  The atom processor is not strong enough to decode hd video so you have to use vdpau to offload the processing.

Once you get it set up, your zotac should be a great little htpc/home server.  Mine ran exceptionally well for years and was at its best in 12.04 running gnome shell.

Good luck and bug me if you have any questions!

---

### Post by DuckHook on 2013-02-01
Were you running XBMC or a collection of AV-centred apps? I'm awfully curious about @sandyd's recommendation of Ubuntu minimal, openbox and XBMC. That would be the minimalist/true media centre route. I have an old Dell laptop that would work very nicely as a similar media centre and am weighing which route to take. Love both suggestions so far.

---

### Post by exoscoriae on 2013-02-01
> **sandyd said:**
> what I would probably do (if you want a media center) is to start with Ubuntu Minimal.

Install XBMC from the xbmc PPA, and use openbox as your wm. Openbox is very light, even more than LXDE.

Seeing as how this is the absolute beginners section... I don't understand =)  I got the ubuntu minimal.  And I believe that installing xbmc from ppa is the same method as described in my original tutorial.  However I don't know what openbox is, or where it fits into the equation.  My guess is ubuntu minimal has no gui maybe?  and openbox acts as the shell?

Reading online it says i can not create a bootable usb disk with ubuntu minimal... which... well, unless I got an external usb cd rom and somehow made that bootabl,e I don't know how I would install it.  

[quote=DuckHook]XBMC is an excellent suggestion. [/quote]
I've been using xbmc for a while now on my windows machines.  it is an awesome program.  I specifically started looking into ubuntu as xbmc runs slow on this ion machine w/ win 8.  But it does run, and really, it runs pretty well.  You just can't fly through the menus.  This is quite a lot to go through to pick the menu speed up a little bit, but I'm always game for a challenge.

[quote=drawkcab]Instead the best option is, gasp, gnome shell. You can use the advanced settings to scale the desktop to your TV with the slider that manages the font sizes. It is sluggish under load sometimes but it's worth it and the video that is produced has none of the tearing associated with non-gtk3 desktops!!! [/quote]

Two issues here.  One, without a tutorial i would have no idea how to do anything with gnome shell.  As a long time windows user (since 2.0 actually, before 3.x), this is my first foray into an alternate OS.  In the space of a few hours I have gone from trying to get ubuntu to work, to having lubuntu, gnome shell, and minimal ubuntu all suggested.  My mind is reeling =)

Second issue is, if it is slow under load... well, that sounds like it runs about as well as xbmc running under win 8.  As I mentioned to DuckHook, I had win8 running on this machine, and I had XBMC Frodo skinned w/ Aeon Nox (a resource intensive skin).  It scanned my windows NAS, and streamed my full dvd and blu-ray iso's at 100% speed over the network.  The only issue was scrolling through the movies was a little slow compared to my other machines (which is to be expected, my other htpc's are all core i7's of various generations).  

I have this ZOTAC Ion and I also have a ZOTAC ION motherboard, 64gb SSD, 4gb RAM, and Coolermax mini-itx case that I am building.  Whatever works best on my little ion, I plan to duplicate on the larger ion based machine.  The goal is to have an htpc of some kind in every room, pack up the physical media collection that once dominated my game room, and just stream movies\tv shows\music\pictures\etc to every room from now on through xbmc.  

So far it is all working wonderfully well on my powered up windows machines.  And it works functionally well on this ION w/ windows.  The goal right now is to see if linux can make it run better.

---

### Post by sandyd on 2013-02-01
> **exoscoriae said:**
> Seeing as how this is the absolute beginners section... I don't understand =)  I got the ubuntu minimal.  And I believe that installing xbmc from ppa is the same method as described in my original tutorial.  However I don't know what openbox is, or where it fits into the equation.  My guess is ubuntu minimal has no gui maybe?  and openbox acts as the shell?

Reading online it says i can not create a bootable usb disk with ubuntu minimal... which... well, unless I got an external usb cd rom and somehow made that bootabl,e I don't know how I would install it.  


I've been using xbmc for a while now on my windows machines.  it is an awesome program.  I specifically started looking into ubuntu as xbmc runs slow on this ion machine w/ win 8.  But it does run, and really, it runs pretty well.  You just can't fly through the menus.  This is quite a lot to go through to pick the menu speed up a little bit, but I'm always game for a challenge.



Two issues here.  One, without a tutorial i would have no idea how to do anything with gnome shell.  As a long time windows user (since 2.0 actually, before 3.x), this is my first foray into an alternate OS.  In the space of a few hours I have gone from trying to get ubuntu to work, to having lubuntu, gnome shell, and minimal ubuntu all suggested.  My mind is reeling =)

Second issue is, if it is slow under load... well, that sounds like it runs about as well as xbmc running under win 8.  As I mentioned to DuckHook, I had win8 running on this machine, and I had XBMC Frodo skinned w/ Aeon Nox (a resource intensive skin).  It scanned my windows NAS, and streamed my full dvd and blu-ray iso's at 100% speed over the network.  The only issue was scrolling through the movies was a little slow compared to my other machines (which is to be expected, my other htpc's are all core i7's of various generations).  

I have this ZOTAC Ion and I also have a ZOTAC ION motherboard, 64gb SSD, 4gb RAM, and Coolermax mini-itx case that I am building.  Whatever works best on my little ion, I plan to duplicate on the larger ion based machine.  The goal is to have an htpc of some kind in every room, pack up the physical media collection that once dominated my game room, and just stream movies\tv shows\music\pictures\etc to every room from now on through xbmc.  

So far it is all working wonderfully well on my powered up windows machines.  And it works functionally well on this ION w/ windows.  The goal right now is to see if linux can make it run better.
Hmm - if you don't want to use a cd (im guessing it has no cd drive or something), you can just use the Ubuntu Alternate iso. I recommend you stick with the 12.04 LTS release, since it is supported longer than 12.10 (in fact, there is only an alternate iso for 12.04).

Ive thought about it a bit more, and this is much more refined than my original idea.

a) Use Ubuntu Alternate Installer, when asking for what software to install, choose only "ssh server". Make sure you _don't_ choose "GUI", that will cause a lot of unnecessary stuff to be installed.

b) Login after the install, and update
```

sudo apt-get update
sudo apt-get upgrade
```

c) Install Xorg and Nvidia drivers
(you can even be more minimal by adding --no-install-recommends behind xorg, but I wouldn't reccomend it)
```

sudo apt-get install xorg

```
follow the above guide after this point to install the nvidia drivers.

Install VDPAU
```
sudo apt-get install libvdpau1
```
Generate a xorg.conf that will work with the nvidia drivers
```

sudo nvidia-xconfig
```

Restart afterwords

d) Install Openbox and lightdm
```

sudo apt-get install lightdm openbox
```

e) restart again, and you should have some kind of graphical display when you boot up.
Press Control + Alt + F1 to return to the ttys

f) Install XBMC
```

sudo apt-get install python-software-properties
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install xbmc libbluray-bdj libbluray1 cec-utils libcec libnfs1 libshairport1
```
g) restart computer - in the graphical login, hit the gear, choose XBMC, and login.

Note that the above are general instructions that are not tested, though they should work in theory

---

### Post by exoscoriae on 2013-02-01
Wow, thank you so much for the play-by-play.  I'll give it a run tonight.  I have to say, it is very refreshing to seek help on a board and see so many helpful posts and so much activity.  It definitely gives the sense that ubuntu has a great culture behind it.  Thanks again.  I'll report back on my amazing success or epic failure.

---

### Post by drawkcab on 2013-02-01
> **DuckHook said:**
> Were you running XBMC or a collection of AV-centred apps? I'm awfully curious about @sandyd's recommendation of Ubuntu minimal, openbox and XBMC. That would be the minimalist/true media centre route. I have an old Dell laptop that would work very nicely as a similar media centre and am weighing which route to take. Love both suggestions so far.

I ran xbmc on my Revo and it worked exceptionally well with remote.  You can run it from the desktop and it works without a hitch.

But, with a wireless mouse and keyboard, I ended up doing all sorts of things on the desktop so I normally never fired up xbmc.  It doubled as my home server and I ran all my torrents on it during the day since it is low wattage.  Minimal + XBMC doesn't really seem advantageous to me.

e.g. I am typing this on my TV while lying on the couch and watching a video.

---

### Post by drawkcab on 2013-02-01
> **exoscoriae said:**
> Seeing as how this is the absolute beginners section... I don't understand =)  I got the ubuntu minimal.  And I believe that installing xbmc from ppa is the same method as described in my original tutorial.  However I don't know what openbox is, or where it fits into the equation.  My guess is ubuntu minimal has no gui maybe?  and openbox acts as the shell?

Reading online it says i can not create a bootable usb disk with ubuntu minimal... which... well, unless I got an external usb cd rom and somehow made that bootabl,e I don't know how I would install it.  


I've been using xbmc for a while now on my windows machines.  it is an awesome program.  I specifically started looking into ubuntu as xbmc runs slow on this ion machine w/ win 8.  But it does run, and really, it runs pretty well.  You just can't fly through the menus.  This is quite a lot to go through to pick the menu speed up a little bit, but I'm always game for a challenge.



Two issues here.  One, without a tutorial i would have no idea how to do anything with gnome shell.  As a long time windows user (since 2.0 actually, before 3.x), this is my first foray into an alternate OS.  In the space of a few hours I have gone from trying to get ubuntu to work, to having lubuntu, gnome shell, and minimal ubuntu all suggested.  My mind is reeling =)

Second issue is, if it is slow under load... well, that sounds like it runs about as well as xbmc running under win 8.  As I mentioned to DuckHook, I had win8 running on this machine, and I had XBMC Frodo skinned w/ Aeon Nox (a resource intensive skin).  It scanned my windows NAS, and streamed my full dvd and blu-ray iso's at 100% speed over the network.  The only issue was scrolling through the movies was a little slow compared to my other machines (which is to be expected, my other htpc's are all core i7's of various generations).  

I have this ZOTAC Ion and I also have a ZOTAC ION motherboard, 64gb SSD, 4gb RAM, and Coolermax mini-itx case that I am building.  Whatever works best on my little ion, I plan to duplicate on the larger ion based machine.  The goal is to have an htpc of some kind in every room, pack up the physical media collection that once dominated my game room, and just stream movies\tv shows\music\pictures\etc to every room from now on through xbmc.  

So far it is all working wonderfully well on my powered up windows machines.  And it works functionally well on this ION w/ windows.  The goal right now is to see if linux can make it run better.

By sluggish I mean a hitch or two when the desktop animates from the hot corner.  Applications and such fired up fine.  Just research Gnome extensions to add some functionality if you go that route.

Basically what you're working with is 'buntu + some desktop environment.  Ubuntu vanilla runs Unity.  Xfce will give you xubuntu.  LXDE, Lubuntu.  KDE, Kubuntu.  Gnome Shell, Gnome Shell Remix.  There's also MATE, Qt, Openbox, Icewm, Fluxbox, E17.

I know its a bit confusing at first but the fact that Linux is modular is a huge advantage, especially in a case like yours, because you can scale your install to the resources of your hardware.

Something I never tried but might be worth checking out is the Unity 2D desktop in 12.04.

The alternate install with XBMC and openbox might be an excellent option if you're going to spend most of your time in XBMC anyway.  Openbox is a trip at first but it's a surprisingly useful wm once you get used to it and configure it to your needs.

---

### Post by exoscoriae on 2013-02-02
Working through the install instructions, I got to:

sudo apt-get install nvidia-xconfig

It tells me it is unable to locate this package.

I don't know how critical this step is, so I am hesitant to proceed past it.

edit:  I went ahead and attempted the next step (running nvidia-xconfig), it it created a config file.  I take it this means the nvidia-xconfig app come in w/ the nvidia drivers, and I didn't have to install it separately.  I'm going to go ahead and keep going since it appears I have a config file now.

---

### Post by exoscoriae on 2013-02-02
On this step:

apt-get install libbluray libcec libnfs libshairport xbmc xbmc-pvr-addons

several of those came back as not found:

The following all said "unable to locate package": libbluray, libnfs, libshairport, xbmc-pvr-addons

Seems like something didn't work so well for me.

---

### Post by sandyd on 2013-02-02
> **exoscoriae said:**
> On this step:

apt-get install libbluray libcec libnfs libshairport xbmc xbmc-pvr-addons

several of those came back as not found:

The following all said "unable to locate package": libbluray, libnfs, libshairport, xbmc-pvr-addons

Seems like something didn't work so well for me.

[s]What version of Ubuntu are you using?
I assumed you were using 12.04 - there are different packages for different versions
wait - /me knows what the problem is...[/s]

Silly Celene accidentally typed the names of the source packages instead of the binary packages - all fixed now. :oops:#-o
Just run the line again ;)

A few more things before i forget -

Things you should consider/see if it is worth adding

**Plex Media Server** - Allows you to use DLNA with XBMC. XBMC will automatically show up in Windows 7 (Maybe it does in vista as well???) and higher in the 'My Computer' section. It works with other DLNA-compatible devices

**Samba** - Works the same as Windows Sharing - allows you to share files between computers. Requires a bit of configuration

**Airplay** - The XBMC version above supports Airplay. It does on my Raspberry Pi at the very least.

**FTP/PureFTPD** - Transfer files to your Zotac fast - even faster than Samba/CIFS

---

### Post by exoscoriae on 2013-02-02
Ok, si I am getting to the gui.  On the left side is a log in windows.  It has the user name XBMC, and a spot below for a password.  When I type the password in, the screen blinks, and then I'm right back to the same screen again.

If I type the wrong password in, it says invalid password.

So i know it is accepting the password.... it just doesn't seem to be able to move to the next part...

edit: Ok, so i figured out it was asking me what to launch, and I guess I was just launching this gnome thing over and over.  Changing it to xbmc allowed xbmc to launch - YAY.

How would I go about setting it to automatically launch xbmc on startup?  

Currently I'm getting the enw skins etup, but it def. runs faster that the win7 setup at this point.

My primary concern is whether or not it will see my hared drives....  Will report back shortly.

---

### Post by sandyd on 2013-02-02
Is there a user account (other) than XBMC there? (there should be).

If there isn't, run
```

sudo adduser *username*
```
where *username* is the name of the user you want to run xbmc on.

then,
```

sudo /usr/lib/lightdm/lightdm-set-defaults --autologin *username*
```
where *username* is the name of the user you just created (above), or an existing user that isn't *xbmc*

Set the default session 
```

sudo /usr/lib/lightdm/lightdm-set-defaults --session xbmc
```

**edit - will not likely be able to get to any replies until Sunday, away until then**

---

### Post by exoscoriae on 2013-02-02
Thanks for the tips on the auto-login.  I'll wait to do that until I get everything else running first.... when i hit shutdown in xbmc it shuts the machine down, so I'm not exactly sure how to exit the program and get anything done in the OS once it starts up.

Right now the primary issue is getting the box to see my SMB shared folders/drives.  Googling tells me something about samba, but I have yet to find any step-by-steps to use it... and those I have found are more about getting files on a linux box shared over to windows... not vice versa.  Plus there appears to be so many types of linux, that some of the pages I find don't resemble the commands I've been typing so far at all.

---

### Post by sandyd on 2013-02-02
> **exoscoriae said:**
> Thanks for the tips on the auto-login.  I'll wait to do that until I get everything else running first.... when i hit shutdown in xbmc it shuts the machine down, so I'm not exactly sure how to exit the program and get anything done in the OS once it starts up.

Right now the primary issue is getting the box to see my SMB shared folders/drives.  Googling tells me something about samba, but I have yet to find any step-by-steps to use it... and those I have found are more about getting files on a linux box shared over to windows... not vice versa.  Plus there appears to be so many types of linux, that some of the pages I find don't resemble the commands I've been typing so far at all.

choose openbox instead of XBMC in the gear thingy

right clicking on the desktop opens up a nice menu.

Note - I originally *assumed* you wanted a installation that would only run XBMC, so I just got you to install a minimal desktop environment. If you want something that actually works (i.e. with web browser and such) without eating all the video/ram/cpu, try LXDE

```

sudo apt-get install lxde
```
you might have to reboot to see that the gear in the login screen now has a LXDE entry that will lead you to a nice light desktop

---

### Post by exoscoriae on 2013-02-02
ok, once in openbox, I'm not sure what to do.  I have agrey background and a mouse cursor.  Right clicking brings up a basic context menu.  Am I supposed to launch xbmc from here somehow?  Does launching from open box allow it to access SMB network shares?  

*goes to google openbox*

---

### Post by sandyd on 2013-02-02
> **exoscoriae said:**
> ok, once in openbox, I'm not sure what to do.  I have agrey background and a mouse cursor.  Right clicking brings up a basic context menu.  Am I supposed to launch xbmc from here somehow?  Does launching from open box allow it to access SMB network shares?  

*goes to google openbox*

What do you actually want to do with the desktop?

Work on stuff, run XBMC whenever, and then exit, and continue using the desktop

Or, run XBMC, logout, log into a desktop environment, and do work.

Both are possible ;)

---

### Post by exoscoriae on 2013-02-02
Once I get xbmc working, I dont need to use the desktop.  But right now it can't see my share drives, and I assume to make that work I'll need access to the terminal and all that.

On a side note, i figure out how to open a terminal in openbox and launch xbmc.  But if I launch it through openbox, it can't even see the computers on the work.  If I launch it through the gnome gui, or whatever that is, then it at least sees the computers on the network, i just don't know how to get past the user name/password prompt.

Right now my main concern is finding a way to access my shared drives.  Without that, all this work is useless, because then i have no media to play on this box.

edit1: also, what I had said before is when I exit xbmc, it shuts the machine down - it doesn't drop back to the desktop.  Maybe you missed that, because above you suggest I drop back and forth as if exiting xbmc just closes the program rather than shutting down the machine.

---

### Post by sandyd on 2013-02-03
> **exoscoriae said:**
> Once I get xbmc working, I dont need to use the desktop.  But right now it can't see my share drives, and I assume to make that work I'll need access to the terminal and all that.

On a side note, i figure out how to open a terminal in openbox and launch xbmc.  But if I launch it through openbox, it can't even see the computers on the work.  If I launch it through the gnome gui, or whatever that is, then it at least sees the computers on the network, i just don't know how to get past the user name/password prompt.

Right now my main concern is finding a way to access my shared drives.  Without that, all this work is useless, because then i have no media to play on this box.

edit1: also, what I had said before is when I exit xbmc, it shuts the machine down - it doesn't drop back to the desktop.  Maybe you missed that, because above you suggest I drop back and forth as if exiting xbmc just closes the program rather than shutting down the machine.
Oh, you were talking about that shutdown bug.
Take a look at [http://askubuntu.com/questions/237249/how-to-prevent-xbmc-from-shutting-down-or-suspending-your-computer](http://askubuntu.com/questions/237249/how-to-prevent-xbmc-from-shutting-down-or-suspending-your-computer)


As for samba - easy way to configure samba is through system-config-samba.

Before doing this, you _must_ have an account other than xbmc (instructions in above posts). I will refer to that username as *username*. If you created a user during the installation, that username is fine as well

(While Logged in as root/admin/user you created during installation)
Install Samba
```

sudo apt-get install samba gksu system-config-samba
```

(If you didn't create a user during installation)
```
sudo usermod -a -G sudo *username*
```


=== To Allow Access to XBMC computer from network ===
(Login using your new *username* (that is, if you didn't create a user during installation))
Create some folders for storing media files and such
```

mkdir ~/Videos
mkdir ~/Music

```
Setup Samba
```

gksu system-config-samba
```

Go to Preferences -> Server settings after typing in your password.

Change the Workgroup to anything you like (some people had problems when computers that werent on the same workgroup tried to share files)

Open the Security tab, and change Authentication Mode to 'Share' so that everyone can transfer files without logging in

Set the guest account to *username*.

Now, click 'ok', and click on the (+) sign. Choose "Videos" or "Music". Choose a share name, and make sure there is a checkbox in writable and visible.

Click on 'Access', and change it to 'Allow Access to everyone'

Click 'ok', and close the screen.

Run
```

sudo service smbd restart
```
to restart samba


=== To Allow XBMC to see shared content on network ===

Make sure smbclient is installed
```

sudo apt-get install smbclient
```

NOTE: Samba does NOT work with Windows 7/8 homegroups. 

To share from windows, read [http://wiki.xbmc.org/index.php?title=SMB#Windows](http://wiki.xbmc.org/index.php?title=SMB#Windows)

---

### Post by exoscoriae on 2013-02-03
Wel,l I will first pat myself on the back for being told that I could not do any of this stuff as my new user has not in the sudoers file.  Some google led me to a line I could add to the sudoers file using vi... and some more goolging actually explained how to use vi.

So when I dropped back to that user account, it was refreshing to see it actually start working now.

For whatever reason though, it just sits at the part where it should start downloading.  Currently it says:
"Temporary failure resolving 'us.archive.ubuntu.com'
0% [Waiting for headers]

This computer, which is on the same network hub, is able to ping that site just fine.

edit1: I walked away, and 15 min later it had progressed a little bit.  It seems to have downloaded 27kb.....  This is slower than my old 1200 baud modem.  So there *is* a connection (technically, but not functionally.

---

### Post by exoscoriae on 2013-02-03
seems the network has broken down for the linux box now (never ending problems).

I used ifconfig to make sure the boc has an ip, which it did.  i then tried a ping google.com and host google.com, and it gets nothing either way.

In ifconfig, there are two section.  eth0 shows an IP address.  When I check that IP address on my router, it shows the name of the linux box - si i have confirmed that the router has assigned the box an IP, and that the box is showing that ip.  In the second section, titled "lo", it just shows a local host of 127.0.0.1, and a loopback  I guess "lo" means local?

I decided to reboot the machine and try the terminal from gnome (? - I'm calling this gnome because the main screen it boots to says something about gnome), rather than the terminal from openbox, and this time it pinged just fine.  So it appears my networking issue is in openbox?

Hopefully I can do all this samba install stuff from gnomes terminal, and not openboxs....

---

### Post by exoscoriae on 2013-02-03
Ok, ran your commands up until "gksu system-config-samba"

At that point it throws back the error:
Gtk-WARNING **: cannot open display:

On e site said to fix this I need to type:
export DISPLAY=:0

After typing that, the error changed to:
Gtk-WARNING **: cannot open display: :0

:/

I really appreciate all this help.  While this is a bit frustrating for me, I'm sure it gets old for those helping me as well.

---

### Post by sandyd on 2013-02-04
> **exoscoriae said:**
> Ok, ran your commands up until "gksu system-config-samba"

At that point it throws back the error:
Gtk-WARNING **: cannot open display:

On e site said to fix this I need to type:
export DISPLAY=:0

After typing that, the error changed to:
Gtk-WARNING **: cannot open display: :0

:/

I really appreciate all this help.  While this is a bit frustrating for me, I'm sure it gets old for those helping me as well.
forgot to say that you have to run it in openbox :)

---

### Post by exoscoriae on 2013-02-04
potentially, you missed the reply I posted where I mentioned I can't get a net connection in openbox?

I guess now that I got it installed in GNOME (where I do have a net connection), I can run the setup in Openbox?

---

### Post by sandyd on 2013-02-04
> **exoscoriae said:**
> potentially, you missed the reply I posted where I mentioned I can't get a net connection in openbox?

I guess now that I got it installed in GNOME (where I do have a net connection), I can run the setup in Openbox?

You can run the command on any desktop environment (including gnome)

---

### Post by exoscoriae on 2013-02-04
Ok, so launching the samba config in openbox brings up a "enter the administrative password" box.  I have tried both the password for the xbmc account, and for the account your instructions had me create.  neither one works.  I also tried just leaving it blank.  None of these work.

edit: Launching 'gksudo system-config-samba" instead brought the dialog box up....  I just hope the password issue doesn't cause problems down the line.

---

### Post by exoscoriae on 2013-02-04
SUCCESS!

I created a new user account on my win7 server, and then went and explicitly added that user to the shared folders w/ full permissions (even though they were supposed to be full permissions for everyone).

And that worked!  Suddenly XBMC can see my windows files perfectly fine.  I'm not sure that SAMBA had anything to do with it honestly.... it appears SAMBA is for sharing things from linux back to windows.... and in this case I am simply using the linux box as a receiver.

Thank you so much for all the assistance on this.  I am going to repeat the process on another machine now.

At this point I just need to go back to your posts about how to autolaunch openbox and then xbmc, and it will be perfect.  Again, thank you so much for all the help.

---

### Post by exoscoriae on 2013-02-07
It seems that since my second box has an SSD drive, I get install errors using the exact same setup that I used for my first box.  Is there a way to install this Ubuntu 12.04 Alternative Install on an SSD?

---

### Post by exoscoriae on 2013-02-09
so i have just realized that even though it appears everything was working fine... i actually have no sound.

I have done the following:

* installed alsamixer

* made sure none of my outputs were muted, and raised the volume to max on each of them

* made sure that in xbmc under "settings\settings\audio output" that HDMI was set as the output device.

Still no sound =(  Are there any other suggestions?

---

### Post by exoscoriae on 2013-02-11
This thread seems dead now, but if anyone dregs it up in the future trying to accomplish the same thing as me, forget all of this.  Just get the XBMCbuntu Live image, use unetbootin to make a bootable usb, and then choose to install (or hell, you can even just run it off the flash drive if you want).

All the drivers were auto installed, sound worked fine, and it ran just as fast as all this minimal stuff, and *much* faster than a full 12.10 install.

If your trying to get to your files on a windows machine, simply add permissions to your windows folder/drive for the user name of your xbmc machine (in my case my username/password was xbmc - so I gave full permissions to xbmc).  Then go into file mode, choose smb, and when it asks for login use your xbmc/xbmc info.  Worked immediately for me.  none of this samba stuff, or any of that necessary.

---

### Post by pradyot on 2013-03-24
Even I am facing similar problem. After booting i got this weird coloured screen in login part.

[http://ubuntuforums.org/showthread.php?t=2128715](http://ubuntuforums.org/showthread.php?t=2128715)

---

