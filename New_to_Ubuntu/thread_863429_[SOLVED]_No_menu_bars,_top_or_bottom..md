---
title: "[SOLVED] No menu bars, top or bottom."
date: 2008-07-18
forum: New to Ubuntu
---

### Post by barney385 on 2008-07-18
I used a link after inserting a disc to get here. I have all my desktop items, but no menu bars (applications, places, system etc.).

I did an update yesterday, and there were some Medibuntu updates with warnings. I wrongly assumed that the warnings were to let me know these updates and Medibuntu are unsupported and I chose to ignore them.

Now today upon booting up, I don't have any menu bars.

Any help would be greatly appreciated.

Thanks, barney

---

### Post by tamoneya on 2008-07-18
hit alt-F2 and type: ```
gnome-panel
```If that doesnt work hit ctrl-alt-F1 to move down to tty1.  Login with username and password and then type:```
sudo dpkg-reconfigure ubuntu-desktop
```Then hit ctrl-alt-F7 to get back to your desktop.  If at any point you get errors on any of the commands please post the here.

---

### Post by barney385 on 2008-07-18
thanks for the quick reply. The alt-F2 would not work, so I tried the next (sudo dpkg-reconfigure ubuntu-desktop). It notified me that ubuntu desktop was not installed? It said I needed to derect it properly or something of the nature in order to repair.

Uh-oh

ETA: I have my 8.04 64 disc in also if that's any consolation.

---

### Post by tamoneya on 2008-07-18
> **barney385 said:**
> thanks for the quick reply. The alt-F2 would not work, so I tried the next (sudo dpkg-reconfigure ubuntu-desktop). It notified me that ubuntu desktop was not installed?

Uh-oh

Hmm thats odd.  I gave you that command though on the assumption that you were running ubuntu + medibuntu repositories.  Are you possibly running Kubuntu + medibuntu or xubuntu + medibuntu.

---

### Post by LowSky on 2008-07-18
You are using Ubuntu right? Not Kubuntu or Xubuntu, or Edubuntu or Ubuntu studio?

---

### Post by bumanie on 2008-07-18
Try > sudo apt-get  --reinstall ubuntu-desktop
followed by > sudo apt-get update

---

### Post by barney385 on 2008-07-18
Ubuntu 64, and yes, I activated the Medibuntu repos.

---

### Post by barney385 on 2008-07-18
> **bumanie said:**
> Try followed by

That isn't working either, so I went ahead and updated apt-get, and it showed an Medibuntu error, saying it didn't have the proper signature?

:confused:

---

### Post by barney385 on 2008-07-18
sudo apt-get  --reinstall ubuntu-desktop

I meant I tried this Bumanie...

Thanks for trying to help this poor noob...

:smile:

---

### Post by bumanie on 2008-07-18
Can you copy the exact error message and post it? That may help narrow things down a bit. Medibuntu was down a day or so ago, may be that has caused an issue. Not sure how it would be related to no desktop titlebars, icons etc. may be you have not got the medibuntu GPG key
put this code in terminal > sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get updateLacking this key may well be giving the error.

---

### Post by barney385 on 2008-07-18
For sudo dpkg --reinstall ubuntu-desktop:

[B]E: Invalid operation ubuntu-desktop

[/B]As far as the apt-get error, it's always said that the signature for Medibuntu wasn't valid or something of that nature before any of this happened.

I assumed that was because it's an unsupported repo?

---

### Post by bumanie on 2008-07-18
May be you have not got the medibuntu GPG key
put this code in terminal
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Lacking this key, may well be giving the medibuntu error. Not sure how this would be related to the desktop issue though.

---

### Post by Nem1976 on 2008-07-18
If you have your desktop but just not your panels then try this.

Run the following command from terminal 

"gconftool-2 --recursive-unset /apps/panel" minus the " "

This will reset your panels back to the following config

TOP (from right)
Shutdown launcher - Clock - Volume - Notification area - User switcher - Applications menu (left)

Bottom (from left)
Show desktop - Window menu - Separator - Trash

---

### Post by barney385 on 2008-07-18
I don't have terminal access. TTY1 won't let me copy & paste commmands.

Also, it seems the command line is trying to read the disc I used to open a link and get here.

i.e. E: Invalid command Ubuntu-desktop...

Something like that when I tried sudo dpkg --reinstall ubuntu-desktop

This is kind of a pain in the ol' rearend...

Thanks for your patience guys.

---

### Post by tamoneya on 2008-07-18
in tty1 to get errors and such just redirect the output to a file like this:```
sudo apt-get update >output.txt
```Then in graphical mode you can open the file and post it to the forums.

---

### Post by Nem1976 on 2008-07-18
> **barney385 said:**
> I don't have terminal access. TTY1 won't let me copy & paste commmands.

Also, it seems the command line is trying to read the disc I used to open a link and get here.

i.e. E: Invalid command Ubuntu-desktop...

Something like that when I tried sudo dpkg --reinstall ubuntu-desktop

This is kind of a pain in the ol' rearend...

Thanks for your patience guys.


What Disc are you talking about when you say you open a command line it reads the disc.?  Your not booting from the live Cd are you?

---

### Post by barney385 on 2008-07-18
> **tamoneya said:**
> in tty1 to get errors and such just redirect the output to a file like this:```
sudo apt-get update >output.txt
```Then in graphical mode you can open the file and post it to the forums.

-bash output.txt: access denied

I used: sudo apt-get update >output.txt

---

### Post by barney385 on 2008-07-18
> **Nem1976 said:**
> What Disc are you talking about when you say you open a command line it reads the disc.?  Your not booting from the live Cd are you?

No I'm using the disc, because it enables me to access my home folder. I have books and documents with live links that I have to use open firefox.

If that makes any sense. I've removed the disc already.

The reason I mentioned that is because of the: [E: Invalid operation ubuntu-desktop] output.

If that makes sense...

Sorry if I'm not explaining things properly

---

### Post by barney385 on 2008-07-18
OK, I'm running sudo aptitude install ubuntu-desktop right now.

Apparently apt-get does not have a install/reinstall command.

Go figure.

Also, yesterday I uninstalled Evolution. I just don't have no use for it. To me it seems rather bloated.

Now, since I started the installation of ubuntu-desktop, I see that all the Evolution stuff is coming back?

Is Evolution joined at the kernel hip as Explorer was to Windows?

Say it isn't so...


:smile:


ETA: Also the Tracker search tool, and Transmission and Ekiga is coming back...ugh. What does all this stuff have to do with ubuntu-desktop?

I'm not too happy about this...to say the least.

---

### Post by Nem1976 on 2008-07-18
So you are booting from the live CD then?  maybe I just havn't had enough coffee yet this morning.

---

### Post by barney385 on 2008-07-18
No, I'm just using the disc to open up firefox, and then I remove it.

---

### Post by silkstone on 2008-07-18
The problem may be that uninstalling Evolution also uninstalls gnome-desktop. i.e. they are joined somehow.

I don't use Evolution and I remember trying to get rid of it once, and getting a warning that gnome-desktop would go too. Strange, but I think that's the answer.

---

### Post by SunnyRabbiera on 2008-07-18
> **barney385 said:**
> OK, I'm running sudo aptitude install ubuntu-desktop right now.

Apparently apt-get does not have a install/reinstall command.

Go figure.

Also, yesterday I uninstalled Evolution. I just don't have no use for it. To me it seems rather bloated.

Now, since I started the installation of ubuntu-desktop, I see that all the Evolution stuff is coming back?

Is Evolution joined at the kernel hip as Explorer was to Windows?

Say it isn't so...


:smile:


ETA: Also the Tracker search tool, and Transmission and Ekiga is coming back...ugh. What does all this stuff have to do with ubuntu-desktop?

I'm not too happy about this...to say the least.

Yeh evolution is tied into your gnome desktop, but its possible to install a base evolution package or two to get your DE working...
removing evolution is the source of your issues.

---

### Post by barney385 on 2008-07-18
Yeah, thanks Silkstone and SunnyRabberia.

I'm pretty sure that is the source of my problems. I wouldn't have done that if I was remotely in a state of awareness on this issue...Evolution uninstallation.

Oh well, I'll just have to deal with it. 

It just kinda sucks for me because I have such a slow DarpaNet connection...

Thanks for the confirmation!!

:smile:

---

### Post by SunnyRabbiera on 2008-07-18
well try to install these base packages if you are still having issues, you dont need the full evolution:
evolution-data-server
evolution-data-server-common

it should give you your gui back after you install them via apt.

---

### Post by barney385 on 2008-07-18
I just switched to TTY1 and it's already 87% done.

I wish I would of knew that before I started it.

It's really not a big deal having Evolution installed I guess. I just prefer to customize my install without hindrance. You know, I just didn't want something on my disc I don't use.

This is the very first issue I've had with Hardy, so I'm not complaining.

I might try that minimal installation of Evolution later. 

Thanks for the tip friend.

:smile:

---

### Post by SunnyRabbiera on 2008-07-18
Yeh, well unfortunately evolution is a part of the package (for now) though efforts are being made to be rid of it.
Its all on gnomes head more then ubuntu, gnome pre packages a lot of crap people dont like and ubuntu can only do so much.
If you are unsure what gnome or a DE is here is some info:
[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)
[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

---

### Post by barney385 on 2008-07-18
OK, I'll check those links out. It's working again now.

It definitely was Evolution not playing nice. I'll mark this thread solved if I can figure that out.

So gnome is attaching apps to their DE?

Hmm...I thought that attitude went out with the windows...

:lol:

thanks again [SunnyRabbiera]("http://ubuntuforums.org/member.php?u=23967")

---

### Post by SunnyRabbiera on 2008-07-18
well all desktop environments have their quirks, and yes one of the strongest criticisms going against gnome is its reliance on evolution.
If you dont like gnome its possible to try other DE's out in ubuntu without it hurting your system.
KDE and XFCE are easy enough to install and try out, you can use them without loosing much.

---

### Post by barney385 on 2008-07-18
There really isn't nothing wrong with the gnome DE. I think they should realize that people don't particularly like having software forced upon them.

I'm familiar with the other desktops and I might have to look into that.

Now I have to remove transmission and tracker.

I like the Beagle and Deluge better...

Thread is marked as solved...

---

### Post by SunnyRabbiera on 2008-07-18
Yeh, well gnome is pretty close to what I hear to being rid of evolution

---

### Post by barney385 on 2008-07-18
> **SunnyRabbiera said:**
> Yeh, well gnome is pretty close to what I hear to being rid of evolution


That's really good. To me it kind of defeats the purpose and intent of open-source by embedding software in this manner.

Gives me scary flashbacks of Windoze....


:)

---

### Post by CatKiller on 2008-07-18
> **barney385 said:**
> Now, since I started the installation of ubuntu-desktop, I see that all the Evolution stuff is coming back?

The ubuntu-desktop package is a meta-package that depends on all of the things that are installed in the default Ubuntu installation, so that if you want to install the default Ubuntu, you just install this package and everything that's actually needed gets installed automatically.

If you remove one of the things that ubuntu-desktop depends on, then ubuntu-desktop has to be removed as well since its dependencies can't be met.

---

### Post by Bethra 0_0 on 2008-07-20
> **Nem1976 said:**
> 

"gconftool-2 --recursive-unset /apps/panel" minus the " "


Thank you! I'd lost my gnome panel & this got it back \\:D/

---

### Post by barney385 on 2008-07-20
> **CatKiller said:**
> The ubuntu-desktop package is a meta-package that depends on all of the things that are installed in the default Ubuntu installation, so that if you want to install the default Ubuntu, you just install this package and everything that's actually needed gets installed automatically.

If you remove one of the things that ubuntu-desktop depends on, then ubuntu-desktop has to be removed as well since its dependencies can't be met.

I got rid of Tracker Search Tool and Transmission with no problem and they both come with the meta-package. Only uninstalling evolution caused me any problems.

:lolflag:

---

