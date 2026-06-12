---
title: "Just installed 8.04, no sound"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Crono139 on 2008-05-22
I just installed Ubuntu 8.04 onto my laptop, and there's zero sound. I installed all of the recommended updates after the initial boot, but that didn't do the trick.

As first, I thought it was Firefox that was the problem, but when I try to preview the sounds under System->Preference->Sound, nothing is to be heard there as well.


The command **aplay -l** in the terminal provides this output:

[i]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/i]


Any help would be greatly appreciated. Thanks in advance.

---

### Post by mbeccaria on 2008-05-22
I have seen another post related to DELL Precision M4300 on a very similar issue.
The proposed solution was to install an additional package (something named backport...)

---

### Post by Crono139 on 2008-05-22
The only command that I tried was *sudo apt-get install linux-386* because I read about it in another thread, and it seemed to be the fan favorite.

No luck, though.

---

### Post by sayakb on 2008-05-22
Install:
```
sudo apt-get install linux-backport-modules
```

---

### Post by Crono139 on 2008-05-22
> **LinuxIsInnovation said:**
> Install:
```
sudo apt-get install linux-backport-modules
```

[i]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backport-modules[/i]

---

### Post by Crono139 on 2008-05-22
Bump.

---

### Post by crossedout on 2008-05-22
I believe its "linux-backports-modules".  According to synaptic, the package is listed as linux-backports-modules-2.6.2.  You might want to have a look at that, perhaps its what you are after.
Good Luck.

-Xout

---

### Post by Crono139 on 2008-05-22
Still having problems finding the listed package(s).

---

### Post by crossedout on 2008-05-22
Make sure you have all repositories enabled.
System->Administration->Software Sources
Check all from Ubuntu Software and Third-party Software.

-Xout

---

### Post by Crono139 on 2008-05-22
Alright. I enabled the 3rd party software. Everything else was already checked off.


[i]justin@justin-laptop:~$ sudo apt-get install linux-backport-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backport-modules
justin@justin-laptop:~$ sudo apt-get install linux-backports-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules
justin@justin-laptop:~$ sudo apt-get install linux-backport-modules-2.6.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-b.ackport-modules-2.6.2
justin@justin-laptop:~$ sudo apt-get install linux-backports-modules-2.6.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-2.6.2[/i]


Doh.

---

### Post by cpetercarter on 2008-05-22
Synaptic lists a package named linux-backports-modules-hardy, described as "generic linux backported drivers". The latest version is shown as 2.6.24.16.18. This may be what you are looking for.

---

### Post by crossedout on 2008-05-22
I'm at a loss.  I am staring right at the package in Synaptic.  Perhaps someone else can give a more experienced view on this problem.

-Xout

---

### Post by Crono139 on 2008-05-22
> **cpetercarter said:**
> Synaptic lists a package named linux-backports-modules-hardy, described as "generic linux backported drivers". The latest version is shown as 2.6.24.16.18. This may be what you are looking for.

That package was found, and it installed just fine.

However, it didn't manage to fix my problem, even after a nice reboot.


I may just try a quick reinstall later tonight, and see if that somehow works.

---

### Post by Eisenwinter on 2008-05-22
Try in terminal asoundconf list, see if your card is shown there.

Go into alsamixer, see if all the settings are properly configured, it may be muted.

---

### Post by Crono139 on 2008-05-22
> **Eisenwinter said:**
> Try in terminal asoundconf list, see if your card is shown there.

Yes, my Intel sound car is there.

> **Eisenwinter said:**
> Go into alsamixer, see if all the settings are properly configured, it may be muted.

Looks fine to me.

---

### Post by erginemr on 2008-05-22
Please post the outcome of the following commands from the terminal:
[http://ubuntuforums.org/showpost.php?p=4576277&postcount=5](http://ubuntuforums.org/showpost.php?p=4576277&postcount=5)

---

### Post by Inxsible on 2008-05-22
Have you tried typing in ```
alsamixer
``` in a terminal and upping all the volume levels there?

---

### Post by guildofghostwriters on 2008-05-22
My sound didn't work after install. After much fishing around, I solved it by going to alsamixer (launch a terminal and type alsamixer) and making sure that the control called 'digital/analogue output jack' was muted. It's not a volume slider, just an on/off mute/unmute switch, and that did the trick. Probably worth trying if you haven't already.

---

### Post by Crono139 on 2008-05-22
> **erginemr said:**
> Please post the outcome of the following commands from the terminal:
[http://ubuntuforums.org/showpost.php?p=4576277&postcount=5](http://ubuntuforums.org/showpost.php?p=4576277&postcount=5)

```
justin@justin-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
justin@justin-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd6400000 irq 23
```

```
justin@justin-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```


> **Inxsible said:**
> Have you tried typing in ```
alsamixer
``` in a terminal and upping all the volume levels there?

Yes. They are all at 100.

---

### Post by 00arthuryu on 2008-05-22
```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```
Hope this helps
Regards
Arthy

---

### Post by Crono139 on 2008-05-22
> **00arthuryu said:**
> ```

sudo m-a a-i alsa

```


The build of the package alsa-source apparently failed.

---

### Post by 00arthuryu on 2008-05-22
hmm..
I don't have many suggestions other than to uninstall all pulseaudio things through synaptic and do it again
Regards
Arthy

---

### Post by almabeck on 2008-05-22
[QUOTE=00arthuryu;5020608]```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```


I've got the same problem and have eagerly tried everything suggested on this forum, including this latest advice. Still no sound!

Just out of curiosity, if I get tired of no sound, is there a way to revert to the Gutsy Gibbon without losing downoaded programs on my laptop?

---

### Post by ugm6hr on 2008-05-22
This might be of interest: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229522](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229522)

---

### Post by 00arthuryu on 2008-05-22
heya almabeck
where did you get up to before it didn't work?
It should have compiled alsa-source.
My suggestion is to remove all alsa related stuff especially pulseaudio then try it again.
No I do not think you can downgrade back to gutsy without losing anything.
If you go back to gutsy, I believe a fresh install is necessary
Regards
Arthy

Edit: ah ha, ubuntu staff! you're saved :D

---

### Post by almabeck on 2008-05-22
> **ugm6hr said:**
> This might be of interest: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229522](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229522)

I don't have any sound, not even using Windows OS in VBox. Worked fine before I upgraded, though.

---

### Post by almabeck on 2008-05-22
> **00arthuryu said:**
> heya almabeck
where did you get up to before it didn't work?
It should have compiled alsa-source.
My suggestion is to remove all alsa related stuff especially pulseaudio then try it again.
No I do not think you can downgrade back to gutsy without losing anything.
If you go back to gutsy, I believe a fresh install is necessary
Regards
Arthy

Edit: ah ha, ubuntu staff! you're saved :D

Everything appeared to work all the way to the end. I just didn't have any sound, even after restarting.

---

### Post by 00arthuryu on 2008-05-22
If everything worked after doing 
```

sudo m-a a-i alsa

```
It should be working, open system-preferences-sound
And on the 'default Mixer tracks'
there should be a new one there after compiling alsa
remember to choose PCM on the selection box below.
Also try 
```

alsamixer

```
again
Regards
Arthy

---

### Post by almabeck on 2008-05-22
In sound-preferences, the device selected is HDA Intel (Alsa mixer) and PCM is highlighted. I still don't get sound when I try the "test" buttons (or anytime else).

---

### Post by 00arthuryu on 2008-05-22
Does
```

alsamixer

```
work? As it comes muted by default after compiling.
But if its not then i'm afraid its beyond my knowledge lol
Regards
Arthy

---

### Post by almabeck on 2008-05-22
I've attached a list of eveything I've tried so far. Could it be that something I did awhile back is causing problems now? (as you can probably tell, I know nothing about what I am doing. i just type in whatever someone tells me to type!)

---

### Post by almabeck on 2008-05-22
Yep. It comes up with everything at 100%

---

### Post by almabeck on 2008-05-23
For those of you with a Dell Inspiron 1420 and no sound, I fixed my problem (finally!) with a clean install. Don't know why that worked, but hey, I'm not complaining! (Unfortunately I forgot to backup my document file, but I suppose that's one way to spring clean.)

---

### Post by Crono139 on 2008-05-23
I thought this was my thread. ](*,)


I guess I'll try a clean install later today.

---

### Post by SteveNorman on 2008-05-23
I had the same issue when I loaded feisty,,I used this thread to solve it,,dated but it may work

[http://ubuntuforums.org/showthread.php?t=536036&highlight=Audio+device%3A+Silicon+Integrated+Systems+%5BSiS%5D+Azalia+Controller](http://ubuntuforums.org/showthread.php?t=536036&highlight=Audio+device%3A+Silicon+Integrated+Systems+%5BSiS%5D+Azalia+Controller)

also when you click on the speaker icon by the date in the top right corner what does it show?

---

### Post by erginemr on 2008-05-23
> **Crono139 said:**
> I thought this was my thread. ](*,)


I guess I'll try a clean install later today.

Ha ha! :popcorn:

I suggest you to follow this, gving priority to the second link therein first:
[http://ubuntuforums.org/showpost.php?p=4450631&postcount=5](http://ubuntuforums.org/showpost.php?p=4450631&postcount=5)

Hope you will solve your problem.

---

### Post by xenocide13 on 2008-05-25
Hey i have been having the same problems with sound.
i go to the alsamixer and my headphone volume is turned all the way down i dont have speakers and cant turn the headphone volume up
anyone have a clue why? and i cant find the unmute button either.

---

