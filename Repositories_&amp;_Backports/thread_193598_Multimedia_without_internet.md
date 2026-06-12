---
title: "Multimedia without internet"
date: 2006-06-10
forum: Repositories &amp; Backports
---

### Post by capitan.harlock on 2006-06-10
Hello, I got Xubuntu installed on workplace with no internet connection available; I need to install multimedia codecs, but with no web connection I can't use apt-get usual way; I also cannot make any test at home because of notorius eagle-usb modem trouble; so please I need a full list of package needed to be installed (starting from Xubunt 6.06 cd) in order to get at least

wmv, wma, mpg, mov, mp3 

files working, so that I can download them all from here, burning on a cd, then installing on pc at work without dependencies problem; my first choice for video in totem-xine (which is yet installed) and xfmedia or beep or xmms for audio, but other solutions are welcome, of course!

---

### Post by BitTorrentBuddha on 2006-06-10
Okay, I believe this covers them all... Add these two lines to your sources.list,

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Then..
```
sudo apt-get update
sudo aptitude install w32codecs ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-flac gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-vorbis
```

---

### Post by capitan.harlock on 2006-06-11
[QUOTE=BitTorrentBuddha]Okay, I believe this covers them all... Add these two lines to your sources.list,

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Then..
```
sudo apt-get update
sudo aptitude install w32codecs ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-flac gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-vorbis
```[/QUOTE]

I'm sorry, perhaps I didn't explained well my situation :p 
I can't get an access to the net not at workplace (in any case) nor at home with any version of Ubuntu (I'm using Mandriva, now) because of that problem with eagle-usb not working anymore; that's why I need to manually download all; I had tried yet with all packages you listed but install fail because of dependencies issues, so I suppose other packages must be installed but I can't know which ones (since I can't configure any extra repository)

---

### Post by BitTorrentBuddha on 2006-06-13
Well, the simplest way I can think of would be to take a live CD to a computer with internet access, add the repositories as suggested, then instead of using the following commands, use ```
sudo apt-get update
sudo aptitude download w32codecs ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-flac gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-vorbis
```
That will download all the packages into the current directory of the terminal (live CD user's home folder by default.) Then mail (or store on a USB stick, CD-RW, etc.) all the .debs to yourself and install them when you get back home.

---

### Post by SoftGround on 2006-06-13
This Live CD Idea sounds very useful.

Will the apt-get and aptitude commands work through a passworded proxy.  

I have got out through the firewall with Firefox.

Regards

SoftGround

---

### Post by capitan.harlock on 2006-06-13
[QUOTE=SoftGround]This Live CD Idea sounds very useful.

SoftGround[/QUOTE]

I'll have to find out a third pc, since I can't use neither home (not with Ubuntu) nor work pc to connect to the net; I'll try a workaround...

---

### Post by SoftGround on 2006-06-14
Have you tried the UbuntuPlus CD, it may have the right stuff on for you
[https://ubuntuplus.bountysource.com/]("https://ubuntuplus.bountysource.com/")

See Also: [http://ubuntuforums.org/showthread.php?t=183933&highlight=ubuntuplus]("http://ubuntuforums.org/showthread.php?t=183933&highlight=ubuntuplus")
for more information.

I need more than this, but it may be enough for you.

SoftGround

---

### Post by capitan.harlock on 2006-06-14
[QUOTE=SoftGround]Have you tried the UbuntuPlus CD, it may have the right stuff on for you
[/QUOTE]

I'll take a look, thank you!

---

### Post by SoftGround on 2006-06-14
I'm posting this from Ubuntu live throught the proxy.

I have got apt-get working throught the passworded proxy, however there was a problem with the authentication that stumped me for a while.

Gnome allows you to enter the Network Proxy on the Preferences menu, and there is a Detail button that allows you to enter the username and password.  All very easy.  But nothing seemed to use it, not even firefox (needed its own proxy entries).

The problem is that gnome doesnt pass the authentication on to the shell (even when you run it after you made the change!).
It sets $http_proxy to [http://host:](http://host:) port instead of to [http://user:](http://user:) pass@host: port.

I can see why it might consider this a security risk, but it is supposed to already be fixed in Edgy (not much good for me though)

You can however set it yourself in the shell before running apt and aptitude
using
```
 export http_proxy='http://user:pass@host:port'
```

This works for me.  Although Im not too keen on the cleartext password!
Would be a lot better if gnome put up a dialog when you tried to access a network proxy with authentication and blank passwords.

Hope you have as much success.

SoftGround

---

### Post by SoftGround on 2006-06-15
More progress today using the **Live CD**.

cd to your USB thumb before doing aptitude download so the files are downloaded to your thumb.  There is not enough memory for any other folder.

However aptitude download does not seem to download the dependencies, only the packages you list.

So with the http_proxy set as before I did sudo synaptic and selected my package.  Then I selected 'create download script' and saved the script to the USB thumb.  The script uses wget.   Watch out for memory problems though when you run synaptic, as the live CD is running in memory only.  You will need to close it before doing much else.

Then run the script in the usb thumb folder.  You get the package and the dependencies downloaded to the usb thumb.

Now what I need to know is if there is an easy way to get synaptic to install all my packages from the USB thumb (or a CD) rather than having to dpgk each one (with possible config problems to be resolved).

---

### Post by BitTorrentBuddha on 2006-06-15
How many packages did you get?

---

