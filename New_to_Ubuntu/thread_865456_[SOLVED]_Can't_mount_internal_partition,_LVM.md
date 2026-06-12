---
title: "[SOLVED] Can't mount internal partition, LVM"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by ctoaun on 2008-07-20
I cannot mount an internal partition. 
I created a vfat partition using gparted. It's /dev/sda15. The intent was to put virtual box on it. However, /dev/sda15 can't be mounted for whatever reason. The "sudo gedit /etc...stuff never works. Neither does some similar solutions which ends with the "chown" command.

---

### Post by llama320 on 2008-07-20
have you tried

```
mkdir /media/foo
sudo mount /dev/sda15 /media/foo
```

If it doesn't work post the output (if any)

Good Luck

---

### Post by neurostu on 2008-07-20
have you tried mounting with pmount?

---

### Post by ctoaun on 2008-07-20
> **llama320 said:**
> have you tried

```
mkdir /media/foo
sudo mount /dev/sda15 /media/foo
```

If it doesn't work post the output (if any)

Good Luck

Doesn't work, no output
I just need /dev/sda15 (label=virtual) to show up at every startup just like home & tmp partitions show up. This /media/foo only mounts stuff until one reboots. I need a permanent solution.
/dev/sda15 appears to need a permanent mount point
thanks anyway

---

### Post by llama320 on 2008-07-20
> **ctoaun said:**
> Doesn't work
I just need it to show up at every startup just like home & tmp partitions show up. This mounts stuff until one reboots. I need a permanent solution.

I know it isn't permanent, but I wanted to see if it worked, otherwise you may have had another problem (i probably should have made that clear)

You said that no "/etc...stuff" works..does that include /etc/fstab..because that's the place for automounting. The settings are a bit tricky to get right..the following line worked for me (sorry if you've already tried this..)

```
/dev/sda15	/media/foo	vfat	user,fmask=0111,dmask=0000	0	0
```

again, make sure /media/foo exists (using mkdir).

So to be clear: use root privileges to edit /etc/fstab and add the above line to the end of the file.

Good Luck

---

### Post by ctoaun on 2008-07-20
> **llama320 said:**
> I know it isn't permanent, but I wanted to see if it worked, otherwise you may have had another problem (i probably should have made that clear)

You said that no "/etc...stuff" works..does that include /etc/fstab..because that's the place for automounting. The settings are a bit tricky to get right..the following line worked for me (sorry if you've already tried this..)

```
/dev/sda15	/media/foo	vfat	user,fmask=0111,dmask=0000	0	0
```

again, make sure /media/foo exists (using mkdir).

So to be clear: use root privileges to edit /etc/fstab and add the above line to the end of the file.

Good Luck

first: I cannot edit /etc/fstab. I know this because all previous attempts failed, which is what led me to post. It is either that or the directions were incomplete which kills critical thinking. Therefore, could you please write these instructions as steps such as 1, 2, 3 etc? What is our end goal because now I am feeling lost?

---

### Post by ctoaun on 2008-07-20
> **neurostu said:**
> have you tried mounting with pmount?

a quick look at the website has caused me to infer that this "pmount" will circumvent root permissions to some extent. I think this may be what I might want for my shared partition so thanks

---

### Post by llama320 on 2008-07-20
> **ctoaun said:**
> first: I cannot edit /etc/fstab. I know this because all previous attempts failed, which is what led me to post.

you may already know this, but for the sake of completeness, when you say you cannot edit it..you need "root" privileges to edit just about anything outside your home folder. root is equivalent to administrator in windows. In any event, you put sudo in front of a command at the terminal. Then it will query you for a password. Enter the password you've set up (it'll probably be the same as for your user account). You won't actually see anything being typed, but type it in good faith, press enter, and it'll go through. This isn't a bug, it's a security feature so that people watching don't know the length of your password. now you should be given root privileges. So when you say you cannot edit /etc/fstab, is sudo failing you or is it some other problem?

> **ctoaun said:**
> could you please write these instructions as steps such as 1, 2, 3 etc?

So...steps:
1) Open a terminal (Applications > Accessories > Terminal)
2) type ```
sudo gedit /etc/fstab
```
3) add ```
/dev/sda15	/media/foo	vfat	user,fmask=0111,dmask=0000	0	0
``` to the end of the file.
4) reboot

> **ctoaun said:**
> What is our end goal because now I am feeling lost?

At startup, ubuntu loads a bunch of configuration files..among these are /etc/fstab. This tells ubuntu which partitions to automount. Then, if your syntax is right, it will automount the partition you've added at startup.

If I haven't been clear please ask questions (this is half the fun of linux..the other half being when it actually works :D)

---

### Post by txcrackers on 2008-07-20
If you're actually using Kubuntu, as your subject header shows, substitute "kate" for "gedit" in the above instructions. *gedit* is the Gnome (default Ubuntu) editor, while *kate* is the editor for KDE.

---

### Post by ctoaun on 2008-07-20
[QUOTE=llama320;5426096]you may already know this, but for the sake of completeness, when you say you cannot edit it..you need "root" privileges to edit just about anything outside your home folder. root is equivalent to administrator in windows. In any event, you put sudo in front of a command at the terminal. 


"sudo gedit /etc/fstab" "sudo: gedit:" command not found," as usual, I copied and pasted so this was not my error. This command never works. Maybe Kubunt is different. appreciate the effort though. I must conclude that sudo gedit is irrelevant to Kubuntu.

---

### Post by ctoaun on 2008-07-20
[QUOTE=llama320;5426096]you may already know this, but for the sake of completeness, when you say you cannot edit it..you need "root" privileges to edit just about anything outside your home folder. root is equivalent to administrator in windows. In any event, you put 


all the sudo stuff I knew. Substituting Kate just works but now I get errors. probably the result of following this stupid post:[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Error: "/var/tmp/kdecache-addy001" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-addy001" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-addy001" is owned by uid 1000 instead of uid 0.
/dev/sda15      /media/foo      vfat    user,fmask=0111,dmask=0000      0       0

so basically, ti's probably uninstall & then reinstall, correct? It seems to be the only sure way to get partitions to automount.

---

### Post by llama320 on 2008-07-20
First off I should have realized (considering you said it on multiple occasions) that kate was the program to use instead of gedit. That was completely my fault..sorry to steer you in the wrong direction.

> **ctoaun said:**
> so basically, ti's probably uninstall & then reinstall, correct? It seems to be the only sure way to get partitions to automount.

I don't know much about chown, but there are probably ways to change the 1000's into 0's..but that could lead to more problems and frustration. Reinstalling would certainly fix the problem, and would ensure all your settings are back to default.

---

### Post by ctoaun on 2008-07-20
[QUOTE=llama320;5426327]First off I should have realized (considering you said it on multiple occasions) that kate was the program to use instead of gedit. That was completely my fault..sorry to steer you in the wrong direction.

I can certainly respect someone big enough to say I screwed up, definitely no hard feelings. I will most likely join a pay to learn site. Not because of this, but typically, Linux documentation is inferior to windows documentation. In other words, it's not atypical for one to spend 2.5 hours on Google to learn a 15 minute job,which is more than my disposition can bear. Some can think positively of such experiences;I cannot legally print what I think of such experiences. 
>
Thanks for the great step-by-step 
It almost worked!

---

### Post by ejpyle on 2008-07-20
> **ctoaun said:**
> [QUOTE=llama320;5426327]First off I should have realized (considering you said it on multiple occasions) that kate was the program to use instead of gedit. That was completely my fault..sorry to steer you in the wrong direction.

I can certainly respect someone big enough to say I screwed up, definitely no hard feelings. I will most likely join a pay to learn site. Not because of this, but typically, Linux documentation is inferior to windows documentation. In other words, it's not atypical for one to spend 2.5 hours on Google to learn a 15 minute job,which is more than my disposition can bear. Some can think positively of such experiences;I cannot legally print what I think of such experiences. 
>
Thanks for the great step-by-step 
It almost worked!


I will be totally honest with you I had the same problem and running the chown command and changing from root to my user name corrected the problem....I have also learned (the hard way) that any partition with some type of windows file system is #$*&^%!!!

---

### Post by ctoaun on 2008-07-26
Here I am a week later exactly where I started. How does one permanently mount a drive in Kubuntu? Please do not think of responding with gedit! This is Kubuntu :) By the way, I reinstalled Kubuntu, so no "oh it's the configuration responses, please:) !

---

### Post by llama320 on 2008-07-27
> **ctoaun said:**
> Here I am a week later exactly where I started. How does one permanently mount a drive in Kubuntu?

Okay, when you say you're exactly where you started..do you still get the same errors from a week ago, or is it a different problem now. Did you try my step-by-step from a week ago (replacing gedit with kate, of course :D)

Are there any error messages and such that we can work with?

also, is the partition still in the same place (/dev/sda15) that it was before the reintsall?

---

### Post by ctoaun on 2008-07-27
> **llama320 said:**
> Okay, when you say you're exactly where you started..do you still get the same errors from a week ago, or is it a different problem now. Did you try my step-by-step from a week ago (replacing gedit with kate, of course :D)

Are there any error messages and such that we can work with?

also, is the partition still in the same place (/dev/sda15) that it was before the reintsall?
1) Reinstalled Kubuntu 
1a) I've still have no ideal of how to automount /dev/sda16, /dev/sda18 /dev/sda18. They show up in "fdisk -l" but they do not show up in fstab.
2) People say edit the fstab or add a line. However, they do not specify how to backup fstab before modifying it. Currently, I believe this to be critical. 
3) I treat fstab like a registry, so instructions that say do something to fstab without specifying how, are not going to be followed. In example, instructing me to "add the following entry to fstab" will not be followed since it does not specify where to add the entry.

Part of the "sudo kate /etc/fstab" output is as follows. These are the only errors.
>
Error: "/var/tmp/kdecache-zulis001" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-zulis001" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-zulis001" is owned by uid 1000 instead of uid 0.
>
I appreciate help, and I realize that not everyone has Linux memorized

---

### Post by llama320 on 2008-07-27
based on the link below, I have an idea how to fix up these error (maybe)
[http://ubuntuforums.org/archive/index.php/t-622263.html](http://ubuntuforums.org/archive/index.php/t-622263.html)

The second to last post is the one that I'm copying from, but here's what you should type into terminal:
```
sudo chown -R *your_username* /dev/sda15
```

hopefully that will fix some of the errors

***
now to get to the fstab stuff. When I say "add" this line or that line, I mean paste it to the very bottom of fstab. So, step-by-step:

1) Open a terminal (Applications > Accessories > Terminal)
2) type
```
mkdir /media/foo
sudo kate /etc/fstab
```
3) add
```

/dev/sda15	/media/foo	vfat	user,fmask=0111,dmask=0000	0	0
```

to the end of the file.
4) reboot

*note that I added the mkdir step (which wasn't in my original steps)
*note that /media/foo is the location of your choosing. Make it something descriptive
*I've posted a copy of my fstab. the last line (beginning with /dev/sda2 is the one we're trying to emulate)[ATTACH]79200[/ATTACH]

---

### Post by ctoaun on 2008-07-28
> **llama320 said:**
> based on the link below, I have an idea how to fix up these error (maybe)
[http://ubuntuforums.org/archive/index.php/t-622263.html](http://ubuntuforums.org/archive/index.php/t-622263.html)


*note that /media/foo is the location of your choosing. Make it something descriptive
*I've posted a copy of my fstab. the last line (beginning with /dev/sda2 is the one we're trying to emulate)[ATTACH]79200[/ATTACH]

[B][SIZE="5"]Questions[[/SIZE]/B]

You said, "[COLOR="Red"]Make it something descriptive[/COLOR]"

1)To what do you refer, the mount point or the label?

2) In example, If you are referring to the mount point, do I change your/media/foo to music/foo or is it /media/music?

3) In example, If you are referring to the label, do I change your/media/foo to music/foo or is it /media/music?

4) Your help  is appreciated. **However, since this is all a question of creating mountpoints, labels & automounting, could you please limit your responses to those which use the terms mountpoint, label & automount where appropriate?** I simply lack the requisite background knowledge and intuition necessary to fill in gaps in communication. Thank you again

**Statement**

I cannot open your attached file with Kate or "Open Office."

---

### Post by llama320 on 2008-07-28
> You said, "[COLOR="Red"]Make it something descriptive[/COLOR]"

1)To what do you refer, the mount point or the label? 

I'm not sure I can distinguish between the mount point and the label. see the 2nd and 3rd answer for (i hope) clarity

> 2) In example, If you are referring to the mount point, do I change your/media/foo to music/foo or is it /media/music?

change my /media/foo to /media/music. /media is where all your partitions and any usb drives and such will go. As an aside, it's customary to put "foo" and "bar" (and "foobar") as filler for "make up whatever you want here," so that's why i chose that gibberish

> 3) In example, If you are referring to the label, do I change your/media/foo to music/foo or is it /media/music?

again, change it to /media/music. The label and the mount point should be the same location.

> 4) Your help  is appreciated. However, since this is all a question of creating mountpoints, labels & automounting, could you please limit your responses to those which use the terms mountpoint, label & automount where appropriate?

I'll do my best..i remember what it was like to try to get into linux (not the easiest thing in the world)

> I cannot open your attached file with Kate or "Open Office."

I've posted it below as plain-text, hopefully that will help :)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8b0aca70-053c-482a-b2f6-00662d11ad9b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d3b9a0ac-0d40-44b2-a11b-9b240fdf9153 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1	/media/Vista	ntfs	rw,auto,user,fmask=0111,dmask=0000	0	0
/dev/sda2	/media/Transfer	vfat	user,fmask=0111,dmask=0000	0	0
```

again note, we're interested in the line beginning /dev/sda2, because that is of type vfat

---

### Post by ctoaun on 2008-07-28
Although I now understand everything heretofore, this did not work. I copied & pasted, so I know it's not a type-o on my end. Everything is in fstab as it should be. Did not do the chown thing because the home, var, opt usr and other partions all automount regardless of who owns them.

---

### Post by llama320 on 2008-07-29
Can you go into terminal and type
```
cat /etc/fstab
```

and paste the output here so I can have a look?

---

### Post by ctoaun on 2008-07-31
> **llama320 said:**
> Can you go into terminal and type
```
cat /etc/fstab
```

and paste the output here so I can have a look?

Thanks for the response

If you want me to do the "cat...fstab" thing for the sake of you learning, satisfying your curiosity & perhaps you teaching others, to possibly include me, I can do it. However, I did three reinstalls using the "Alternative Install CD." The only conclusion that I can draw, based upon errors during the reinstalls, is that Kubuntu is really buggy about mounting anything once one has more than 14 LVMs. The ultimate goal was two fat 32 partions, one Vbox partition and one as share, followed by one ext3 as a backup. As you have probably guessed, I have a partion for everything! From boot-tmp,from user-srv, everything has its own partition.

I reduced the number of partitions, and now it mounts the first partition as media, NTFS (XP) and it mounts /dev/sda14 of partition two as media mounted on virtualbox.

While I may be incorrect, I'd say that my postulation is not an unreasonable one based on the errors during the first two reinstalls. What says thee?

---

### Post by llama320 on 2008-07-31
> **ctoaun said:**
> Thanks for the response

While I may be incorrect, I'd say that my postulation is not an unreasonable one based on the errors during the first two reinstalls. What says thee?

While I don't see a reason for the bug, it is certainly not unreasonable to think one exists, especially after your experiences. You can try reporting a bug at

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

and seeing if that amounts to anything. If nothing else, the bug will be on record for others to find.

Also, while I again don't know why this might or might not work, you could try just installing standard ubuntu. If that happens to work, then you can install kde "over" gnome. You can find out more about that below

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Good Luck and happy linux-ing

---

### Post by ctoaun on 2008-08-02
> **llama320 said:**
> While I don't see a reason for the bug, it is certainly not unreasonable to think one exists, especially after your experiences. You can try reporting a bug at

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

and seeing if that amounts to anything. If nothing else, the bug will be on record for others to find.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Good Luck and happy linux-ing

I think I shall go the "report a bug route." After all, I followed your "kate...fstab" advice to a "T." I even copied & Pasted to be sure. After restarting my system, and even looking at sample Fstabs on line, I refuse to believe that I mistyped anything or made an error.
I wish to extend a heartfelt thanks for you time, patience & efforts.

---

### Post by ctoaun on 2008-08-02
**Bug Report Submitted[B]**[/B]

M**[B]**[/B]y goal was to create a partition for every part of Kubuntu. E.g, The primary partition is boot. On a physical extension I created multiple LVMs. One LVM for swap, one for home, one for tmp, one for opt, etc. Subsequent to this, I created a shared partion, formated in "fat 32," so that I could share files between "windows XP," which is on partition 1, and Kubuntu, which is on partitions 2 & 3. I also then created a partition for "virtualbox," and a backup partition. Kubuntu 8.04 "alternative install cd" will create as many LVMs as one desires. However, it will refuse to mount them. Once installed, one cannot go back into a terminal to execute the "Kate...fstab" modificaations either. IN other words, Kubuntu 8.04 "alternative install cd" limits the number of LVMs one can create & mount. The version is Kubuntu 8.04 x386

---

### Post by ctoaun on 2008-09-16
There is a limit to the number of LVMs one can have in Kubuntu. The limit is far lower than the limit set by reason and the limits of today's technology.

If you can't mount LVM drives in Kubuntu or you see the red screen  while using the the alternative install cd's partioner, you have too many LVM drives, period.

---

