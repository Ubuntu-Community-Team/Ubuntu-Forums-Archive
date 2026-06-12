---
title: "Xubuntu 8.04 is very slow on my old laptop"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by incen on 2008-06-25
My laptop got 256 MB ram (or 128 MB, I forgot) and 20 GB hard drive. I installed Xubuntu yesterday but it ran very slowly. It ran Windows XP ok (at this point, I think it's 256 MB ram) not as slowly as Xubuntu. For instance, the slowness can be visualized when I tried to click on the options in theme page. It didn't highlight the option right after I clicked on it. It would take like more then 10 sec or 20 sec or whatever. It was just slow...
How do I check the hardware management? (Like showing the CPU, ram, and etc. of my laptop?)

Thanks in advance!

---

### Post by powerpleb on 2008-06-25
In terminal type "top"

256mb is borderline for Xubuntu in my opinion. You could try IceWM or Fluxbox which will be a lot more snappy.

---

### Post by Warpedflash on 2008-06-25
> **powerpleb said:**
> In terminal type "top"

256mb is borderline for Xubuntu in my opinion. You could try IceWM or Fluxbox which will be a lot more snappy.


256mb is fine for xubuntu i used to run ubuntu on that much ram (go T21 thinkpads!) i have doubled it since and of course the performance improves


What kind of laptop are you using? (manufacturer)
also if windows xp works fine can you go to control panel > system and then say how much ram you have and what type/speed of processor. it might be just a slow processor.

---

### Post by sayakb on 2008-06-25
@OP
For older laptops, you may try Openbox. With Openbox (or Fluxbox), you can add selective resources on startup and hence, reduce memory usage. I managed to get everything working with just 78MB of RAM usage. (I used Openbox + Fbpanel + Thunar)
[http://ubuntuforums.org/showthread.php?t=807318](http://ubuntuforums.org/showthread.php?t=807318)

---

### Post by incen on 2008-06-25
I searched for even lighter OS and someone said Fluxbuntu is good but has steeper learning curve. Why and how?

---

### Post by sayakb on 2008-06-25
You can also try OzOs. You may install Fluxbox on Xubuntu rather than going for Fluxbuntu..

---

### Post by incen on 2008-06-25
> **LinuxIsInnovation said:**
> You can also try OzOs. You may install Fluxbox on Xubuntu rather than going for Fluxbuntu..

Thanks for advice. However, I'm not sure if I understand how to do it. So... I don't even need to re-install Fluxbuntu? Will it keep all the features in Xubuntu? Like application? I'm not quite sure if I understand the idea of different "windows manager".

Now, I type top and it shows my laptop got 240 MB ram (which should be 256 MB) and swap is almost 700 MB. 232 MB ram is used and only 6.7 MB is left. :( What's going on?

---

### Post by Trav1s on 2008-06-25
So if the machine shows 240 megs of ram, that tells me the machine has 256 megs with 16 megs for video and 240 megs for system.  The machine sounds borderline... but a faster processor might help.  What are the rest of the machine specs?  


I know ubuntu has the ability to turn off some of the graphics "flashiness" to speed up the machine and it works well.  Does Xubuntu offer this feature? Maybe the veterans can help with this...

---

### Post by powerpleb on 2008-06-25
Just do:
```
 sudo aptitude install fluxbox
```
or 
```
 sudo aptitude install icewm
```
or
```
 sudo aptitude install openbox
```

and in the logon screen click on the 'Sessions' option and select your window manager of choice. It will ask if you want it to be default from then on.

I find IceWM the most usable, although it usually needs a fair bit of tweaking to get it how i like it and Fluxbox is usually ready to go and easier to tweak although overall not as familiar (ie MS Windows like).

You can even install all of them (they are small downloads) and just see which one you like best.

> Now, I type top and it shows my laptop got 240 MB ram (which should be 256 MB) and swap is almost 700 MB. 232 MB ram is used and only 6.7 MB is left. What's going on?
Have a look at the list of processes to see what is taking it all. I'm running Xubuntu 8.04 with 1GB of RAM right now and it's using it all, I suppose it's just taking advantage of it all and optimizing for speed because the system certainly isn't slow.

---

### Post by sayakb on 2008-06-25
If you go with Openbox, follow the link I provided in post #4.  With Openbox, you can start specific processes on session startup by editting a rc file. Since I'm not on my Openbox computer, I cant provide the exact filename. Though the above mentioned thread might help you better..

---

### Post by avtolle on 2008-06-25
A partial answer; the ram is used to keep things in a cache, such as other programs, such that if you decide to use a program again, it starts more quickly. This ram is available for other programs, as it clears the cache when the new program is loaded. That's why it shows such a high proportion of RAM in use. The graphics card is using some of the system RAM, as posted above.

---

### Post by snowpine on 2008-06-25
> **incen said:**
> I searched for even lighter OS and someone said Fluxbuntu is good but has steeper learning curve. Why and how?

You can install Fluxbox in your existing installation by following Powerpleb's excellent instructions. One advantage to doing it this way is that you can choose between the Fluxbox and Xfce (default Xubuntu) windows managers each time you log in. So, if you can't figure out how to do something in Fluxbox, you can do it in Xfce (although it will be slower). 

To try Fluxbuntu, you have to install it from scratch. You can either wipe out your existing Xubuntu install and use the entire disk, or you could keep Xubuntu and create a new partition for Fluxbuntu (this is how my laptop is currently set up). 

I am a big Fluxbuntu fan (it is very fast and only occupies about 40mb of ram on my machine), but it is more of an abandoned "work in progress" than an "official" distro like Xubuntu or Ubuntu. There haven't been updates for 6 or 9 months, and there's no support to speak of. Whereas the support on these forums for Xubuntu (or Fluxbox on top of Xubuntu) is incredible. 

Good luck!

---

### Post by snowpine on 2008-06-25
Oh yes, one other tip, you can go to the System menu and there's an option, it's called either Services or Sessions (can't remember right now) where you can select which services are enabled at startup. If you turn off services you don't need, it can speed things up. I personally got good results from turning off bluetooth, printing (don't need it on this computer) and the tracker search tool.

---

### Post by Trav1s on 2008-06-25
> **snowpine said:**
> Oh yes, one other tip, you can go to the System menu and there's an option, it's called either Services or Sessions (can't remember right now) where you can select which services are enabled at startup. If you turn off services you don't need, it can speed things up. I personally got good results from turning off bluetooth, printing (don't need it on this computer) and the tracker search tool.

That's a great suggestion!

---

### Post by incen on 2008-07-08
> **powerpleb said:**
> Just do:
```
 sudo aptitude install fluxbox
```


Thanks!
I tried to do this line first to see if I could get fluxbox.
I fist did
```
sudo aptitude search fluxbox
```
There is nothing shown but I still did 'install'. Here is the message...
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "fluxbox"
Couldn't find any package whose name or description matched "fluxbox"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not regain the system lock!  (Perhaps another apt or dpkg is running?)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   
```

Then, I think something must be wrong with my source.list and I uncomment all the lines with URL's and did the 'install' again. However, it still didn't work. Same message shows.
Here is my source.list:
```

#deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main r$
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted unive$
 deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted u$

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb http://archive.canonical.com/ubuntu hardy partner
 deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

Something else do I need?

---

### Post by snowpine on 2008-07-08
It sounds like you are already running a different command as 'sudo'--do you have something like Synaptic or system preferences open in a different window?

---

### Post by incen on 2008-07-08
Sorry that I have to take back my words. After searching for several times, my apt finally found fluxbox. Don't ask me. I don't know why it's so weird... :(
Trying to reboot in fluxbox now... thx!!!! ^^

---

### Post by snowpine on 2008-07-08
Cool, good luck in fluxbox! It takes a little bit of getting used to. All configuration is done by editing text files. The most important ones are in your ~/.fluxbox directory. Poke around on the forums; there are some good tutorials for things like editing the menus, auto-mounting usb drives, setting a background, etc. Have fun!

---

### Post by incen on 2008-07-08
Thanks, everybody! Finally I got into Fluxbox!
Although it doesn't really fasten a lot and opening Firefox is still slow, it is better then in Xubuntu. Right now, I just need to use it to write some program. Hope I could get used to it soon. Thanks! :)

---

### Post by incen on 2008-07-08
Ahh... the first question will be...

How do I get Xubuntu updates in fluxbox? I saw some updates while in Xubuntu but don't know how to get them if i'm in fluxbox. Any places to go?

---

### Post by snowpine on 2008-07-08
> **incen said:**
> Ahh... the first question will be...

How do I get Xubuntu updates in fluxbox? I saw some updates while in Xubuntu but don't know how to get them if i'm in fluxbox. Any places to go?

From the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

or if you prefer to do it graphically:


```
update-manager
```

---

