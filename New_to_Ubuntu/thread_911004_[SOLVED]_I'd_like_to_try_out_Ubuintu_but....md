---
title: "[SOLVED] I'd like to try out Ubuintu but..."
date: 2008-09-05
forum: New to Ubuntu
---

### Post by john60wales on 2008-09-05
....I have an old Dell Latitude laptop [1 gig & 256MB RAM] but everytime I try to install Ubuntu it just dies halfway through the installation. I have quite a bit of IT experience... unfortunately all with Windows. I'm trying to get to grips with Ubuntu but am finding it pretty heavy going!
Now I know this is going to sound stupid but...
1. where is the equvalent of Control Panel in Ubuntu?
2. Where would all the Hardware Devices be listed?
Any help gratefully received..
Cheers
John

---

### Post by Elfy on 2008-09-05
1Gb hard drive and 256Mb? - minimum reqs - > At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space

Try a low memory option, xubuntu is looking for 1.5Gb though.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by iaculallad on 2008-09-05
> **john60wales said:**
> ....I have an old Dell Latitude laptop [1 gig & 256MB RAM] but everytime I try to install Ubuntu it just dies halfway through the installation. I have quite a bit of IT experience... unfortunately all with Windows. I'm trying to get to grips with Ubuntu but am finding it pretty heavy going!
Now I know this is going to sound stupid but...
1. where is the equvalent of Control Panel in Ubuntu?
2. Where would all the Hardware Devices be listed?
Any help gratefully received..
Cheers
John

With that amount of RAM you have, I'd suggest you install (x)Ubuntu (Or if you want, you could try Zenwalk). For the control panel part: System->Administation, and to list all your hardware devices, drop to your terminal and issue the command below:

```
sudo lshw
```

---

### Post by john60wales on 2008-09-05
Thanks [both] for the reply - I'm guessing Xbuntu is a 'sawed-off' version of Ubuntu? If this is the case where would I download it?

Cheers
John

---

### Post by Elfy on 2008-09-05
[www.xubuntu.org/get](www.xubuntu.org/get)

If your hardrive is small I would look at the link I previously gave and just install a minimal system - then add to it as you see fit. Which is so much easier here than fiddling about on the internet looking for things - one command gets and installs whatever you want (as long as it's in the repositories)

Personally I use fluxbox as my window manager even though I have enough memory for all the eye candy stuff, nice and simple :)

---

### Post by sv1cdn on 2008-09-05
John FYI, I installed 8.04 Ubuntu in an old P3@500MHz with 386MB RAM. It is working fine, a bit slow but nice.
Used to be a Window guy but know that I discovered Ubuntu and the best support ever I am migrating all my Windows programs to virtual machine in Ubuntu! Try it out...

---

### Post by iaculallad on 2008-09-05
> **john60wales said:**
> Thanks [both] for the reply - I'm guessing Xbuntu is a 'sawed-off' version of Ubuntu? If this is the case where would I download it?

Cheers
John

It's not a sawed-off version of Ubuntu, it's just that it uses a light-weight desktop environment, the XFCE (Counterpart of GNOME/KDE). Go get it [here]("http://www.xubuntu.org/get").

---

### Post by waspbr on 2008-09-05
I was tinkering with an old computer as well, toshiba s207-something. Anyway, I tried xubuntu, but it didn't seem to like it, it seemed to heavy, then I tried wolvix and that worked well, but I want to restore the computer for  my parents so I have to keep it simple. I wanted a deb based system, so I did some looking around and saw that most people with old computers tended to use fluxbox systems, I wanted to give fluxbuntu a spin but I found that gOS was the most complete choice (it comes with that funky dock) and also it is tweaked for low end systems (netbooks) and it is build on good ol'GNOME.

So i would recommend u give gOS a spin.

---

### Post by ad_267 on 2008-09-05
Xubuntu still requires 1.5GB of free space to install, so if you only have 1GB it's not going to fit.

You might be able to do a base installation and then install a window manager like openbox or fluxbox. You could also try something like Damn Small Linux.

---

### Post by prshah on 2008-09-05
> **john60wales said:**
> [1 gig & 256MB RAM]

Perhaps you mean 10 Gb?

> **waspbr said:**
> 
So i would recommend u give gOS a spin.

> **ad_267 said:**
> Xubuntu still requires 1.5GB of free space to install, so if you only have 1GB it's not going to fit.

install a window manager like openbox or fluxbox. You could also try something like Damn Small Linux.

Also Puppy Linux, Slitaz, Arch, etc etc. My choice on this would be puppy.

---

### Post by Crafty Kisses on 2008-09-05
You might wanna go with Xubuntu due to your specs.

---

### Post by ronnielsen1 on 2008-09-05
> Also Puppy Linux, Slitaz, Arch, etc etc. My choice on this would be puppy. 	
I agree on the puppy. Seems the quickest and easiest but lxde is showing alot of promise

---

### Post by snowpine on 2008-09-05
> **john60wales said:**
> ....I have an old Dell Latitude laptop [1 gig & 256MB RAM] but everytime I try to install Ubuntu it just dies halfway through the installation. I have quite a bit of IT experience... unfortunately all with Windows. I'm trying to get to grips with Ubuntu but am finding it pretty heavy going!
Now I know this is going to sound stupid but...
1. where is the equvalent of Control Panel in Ubuntu?
2. Where would all the Hardware Devices be listed?
Any help gratefully received..
Cheers
John

Hi John, welcome to the forums. I have quite a bit of experience trying different distros on my Dell Latitude Cpx (650mhz, 6gb hard drive, 256mb ram since upgraded to 384mb). So, I'll subscribe to this thread and try to give advice as I can. Do you really only have a 1gb hard drive, or is that a typo? That is really going to limit you; the only thing in the Ubuntu family that requires less than a GB is a minimal install, as others have mentioned. Even "light" Ubuntu derivatives like Fluxbuntu and Xubuntu require more than 1 gb hard drive. 

I am currently using Crunchbang on my laptop. It is a good balance of speed and functionality for my tastes. I've also tried Ubuntu using the Alternate CD (Live CD requires 384mb of ram; Alternate worked but was a little too slow for my tastes), Xubuntu (not a huge improvement over Ubuntu), Fluxbuntu (loved it but unfortunately it is outdated), SliTaz (very fast but not Ubuntu), and Puppy (wanted to like it, but it simply wouldn't boot).

One tip to running Ubuntu 8.04 (and its derivatives) on an old Dell Latitude. On my model (and maybe yours), boot was ridiculously slow (over 5 minutes) until I added the command 'all_generic_ide' to my boot prompt in Grub. I'm told this problem is caused by the swappable CD/Floppy drive. On the Live CD, you can do this by pressing F6 on the first screen; once the system is installed, you can edit the /boot/grub/menu.lst file and add 'all_generic_ide' in the appropriate place.

---

### Post by ad_267 on 2008-09-05
This looks like it might fit on 1GB: [http://crunchbang.org/projects/linux/](http://crunchbang.org/projects/linux/)

It uses a minimal ubuntu intall with openbox.

---

### Post by snowpine on 2008-09-05
> **ad_267 said:**
> This looks like it might fit on 1GB: [http://crunchbang.org/projects/linux/](http://crunchbang.org/projects/linux/)

It uses a minimal ubuntu intall with openbox.

No, Crunchbang definitely does not fit in 1gb. The "lite" version is about 1.4gb and the regular is just under 2gb. I know this because I recently installed it on a 2gb flash drive. :)

The thing is, the base Ubuntu system is a certain size, so anything based on Ubuntu is not going to be tiny.

---

### Post by clinto on 2008-09-05
> **snowpine said:**
> No, Crunchbang definitely does not fit in 1gb. The "lite" version is about 1.4gb and the regular is just under 2gb. I know this because I recently installed it on a 2gb flash drive. :)

The thing is, the base Ubuntu system is a certain size, so anything based on Ubuntu is not going to be tiny.
I find anything Debian-related to be a little bloated.

I really doubt this person only has 1gb hdd, it's probably a typo.  Though I guess it's possible.  If it is true and it has usb support(I'm guessing it doesn't though), I'd think about booting from a thumb drive.  It would be slower than ata, but you can get a 4gb thumb for $15 now.  And you could use your internal 1gb for swap I think.  There are quite a few distros that can install to a thumb drive.

And either way, I wouldn't use anything like kde or gnome.  xfce is okay, but it would probably be better to use a window manager like fluxbox or openbox, etc.

---

### Post by ronnielsen1 on 2008-09-06
> 
I really doubt this person only has 1gb hdd, it's probably a typo.
I was wondering that myself. The way it's worded it could be a 1 gig and a 256 M memory stick
>  have an old Dell Latitude laptop [1 gig & 256MB RAM]
I'm not sure he's here anymore. He might have gone to xubuntu or puppyland

---

### Post by snowpine on 2008-09-06
[QUOTE=ronnielsen1;5737662
I'm not sure he's here anymore. He might have gone to xubuntu or puppyland[/QUOTE]

My parents told me Spot went to puppyland...

---

### Post by crispy_420 on 2008-09-06
Depending on your comfort level with the command line, maybe the server install (no gui) and customize to your liking by adding/removing packages.

You can always add the gui later after some trimming of the base install but 1GB is still really small to work with. And as a bonus you will get a good understanding of ubuntu along the way.

---

### Post by john60wales on 2008-09-06
Ummm.... yes... I meant 20 GB HDD - don't know why I said 1 Gig?
Maybe it was that Friday feeling:)
Cheers
John

---

### Post by Elfy on 2008-09-06
Ha ha - makes a big difference as I'm sure you have read :) but I assume the memory was right.

I'd go for xubuntu then - you could always, once you have it installed get a different window manager - just not gnome.

---

### Post by snowpine on 2008-09-06
> **john60wales said:**
> Ummm.... yes... I meant 20 GB HDD - don't know why I said 1 Gig?
Maybe it was that Friday feeling:)
Cheers
John

In that case, you will be fine. You can even install Ubuntu, if you use the Alternate CD instead of the Live CD. The lightweight, fast options we've mentioned are really fun too. :)

---

### Post by john60wales on 2008-09-06
Thanks everyone!
I must admit I've got a bit to think about! There seems to be a multitude of different versions of Unbuntu.... & being used to 1 OS at a time [as with Windows] ... I'm more than a little confused:)
So I'm going to have another beer... & a bit of a think!
I'll get to the bottom of this Open Source stuff eventually... at least I hope so:)
Thanks again..
John

---

### Post by ronnielsen1 on 2008-09-07
> hat case, you will be fine. You can even install Ubuntu, if you use the Alternate CD instead of the Live CD. The lightweight, fast options we've mentioned are really fun too. :smile:
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=5739935") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=5739935")

Add more memory if possible. More memory = faster

---

### Post by AutomaticJack on 2008-09-07
I'm having sound issues with MY laptop installation (as in NO sound). Has anyone else had that problem? If so... how did it get fixed?

---

### Post by Elfy on 2008-09-07
The best thing you could do AutomaticJack is make thread for it.

Include as much detailas you can, at least what laptop it is, threads you might have tried etc.

---

### Post by john60wales on 2008-09-09
Again I'd like to thank everyone who responded to my query... the X-ubuntu seems to have done the trick [its installing as I write this].
I now consider this thread as solved [if I can only find out how to do it]..
Cheers
John

---

### Post by clinto on 2008-09-18
A couple thOH GOD I JUST GOT HABENERO IN MY EYEOHGODOHGOD

Okay, so let us know what you think of it. :D  I for one love xfce4.  I've been using gnome the last couple months, tinkering with desktop apps and such.

By the way, most apps will work despite what de you're using, though some may seem buggy if it's made for kde or gnome.  I've never really had problems though.

Some cli apps to check out:

htop <- shows resources stats and such, like top, only a little more pretty and options.

urxvt <- Ubuntu uses gnome-teminal by default, and Xubuntu probably uses Xterm.  URXVT is pretty nice, you can set a transparent background, etc.(though you probably won't want to do that in your case)

irssi <- irc chat client

rTorrent <- I'm still learning how to use this.
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)
[http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest)

There are some interesting cli file managers too.  Thunar, which is what xfce uses, is pretty nice though.  Other gui apps:

k3b <- burning

deluge <- torrent app, much like uTorrent, but not quite as nice :D

audacious <- most people I talk to swear by this music player\

Lots of apps out there.  Have fun. :D

---

