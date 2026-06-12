---
title: "KDE, GNOME, Unity and compatibility between all those"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by buddy123 on 2015-08-17
Hi,
I recently installed ubuntu on my pc, not my first experience with linux yet never used it on my main laptop.
I see all those great desktops like kde or gnome, seems very sleek and eye candy. I like it much more than the currently running unity (Sorry!)
Is there anything I should take into consideration when installing any of those UI shells?
In terms of compatibility of my currently installed apps, or ...I dont know actually.
Should I do some sort of backup before? Is it easy to remove and switch back to unity if I regret?

Also, where can I read about the differences of all ubuntu versions? currently I installed desktop.

---

### Post by Dragonbite on 2015-08-17
Not much to worry about here. :)

Applications are mostly fully functioning regardless of the desktop environment (Unity, KDE, Gnome, etc.); 

Firefox, LibreOffice, Chromium and the like are not desktop-environment focused so they work without any problems whatsoever.  If you look in the package manager you may find some applications offer a"kde" or "gnome" variant. The advantage of these is usually that their styling is tweaked to match that listed desktop environment but it doesn't mean it won't work in another environment (just maybe not as well or look as much a part of the environment).

Apps that look like they are for one environment or another will work in any environment because when installed the required libraries are also pulled in.  The most confusing it does is sometimes pull in other applications that contain something necessary.

For example in Gnome and in Unity I have installed kPat (KPatience, the card game).  When I install it, it works fine but does bring in a few other applications such as Dolphin (the KDE file manager).  Now Dolphin does also work, though I prefer to use Nautilus in those environments.

Your settings for the desktop environment is stored in your /home directory. That being said, if you tweak one desktop environment (say, KDE), then chagne the desktop environment (to say, Gnome), those KDE settings are still there. They are just unused (except with KDE applications).  If you change back to the previous desktop environment and your settings were never deleted, it will have all the same settings you set up before!  Even if you change the distribution.

For example, I installed openSUSE Gnome on my laptop, then switched to Ubuntu with Unity.  Where the two environments cross-over, my changed settings were used in the second environment.  Now that I moved to openSUSE with KDE Plasma 5, my Unity/Gnome settings are still present if and when they are needed.

Does that help?

---

### Post by Dragonbite on 2015-08-17
In my example, things that were the same (Firefox) maintained those settings even when I installed a new desktop environment or distribution.

THE KEY is ... I have my / (root) directory in 1 partition and my /home partition in a separate partition. So when I install a new distribution I make sure it instals in the / (root) partition (reformat to get rid of the old stuff) and my /home directory will be attached, but not formatted so my files and settings are maintained.

If you have everything all together, then you will want to backup your files & settings first.

---

### Post by buddy123 on 2015-08-17
It does, but, of course, bring other questions to mind :-)

OK, as I understand from your words, and other I read over the web, Its also mainly because eventually it all draws to the same x11 graphical interface. so as long as I have gnome/kde libs, Im good to go?

Forgive me for judging by the looks, Thats all I know right now :-), I saw different desktops and I like the looks of KDE Plasma, so in order to do so I just use the apt-get command to install kubuntu-desktop? Its a different variant of ubuntu, Why dont I install just some kde-plasma packages? 

regarding your example, What do you mean by "switched to ubuntu with unity", without erasing everything and starting fresh? How can it be done and how does it make sense?
Any by saying settings, do you mean just some settings related only to the desktop environment? Or something that reflects on my running apps as well?

Edit: OK, you kind of answered that, I just posted right after your second post. how do I have my home folder in a different partition? sounds like something good for me, when Im still exploring :-)
I have 1 physical drive, what is the appropriate partitioning? Is it possible when switching distro's to seemlessly install new OS and maintain my old user, with its settings & installed apps?

---

### Post by Dragonbite on 2015-08-17
I love looking at other people's screenshots and desktops too.  Some of them are blow-you-out-of-the-water cool!



Installing 'kubuntu-desktop' is going to bring in all of the (KDE) applications with it, meaning you could have duplication of some programs (Thunderbird & Kmail, KPatience and Aisle Riot, etc.).  Although you can set up the menus to only show the desktop-orientated version (hide the non-KDE applications from the KDE main menu for example).

Keep in mind, if you have multiple desktop environments you can choose which one to use when you log in.

In my 1 physical drive on my laptop I have something like this:
[LIST=1]
[*]Windows partition (Windows wants/needs to be the first partition... it doesn't play nice with other OSs ;) )
[*]Extended partition (which is a partition that can have any number of partitions, but you can only have 4 primary partitions)
[LIST=a]
[*]/boot
[*]/(root)  =  where the operating system is installed
[*]/home  =  when installing, never check the box to have this partition formatted. Also it makes it easier to clone a single partition for backups
[*]swap   =  I keep it for suspending the laptop, usually the system doesn't need it (4GB of RAM) though that may change with development or video rendering
[/LIST]
[/LIST]

It makes me have to go in and "manually" choose my partition scheme when installing anything to make sure everything goes into the right place and only those partitions I want are formatted (which cleans them out).

Disclaimer: BACKUP ALL DATA BEFORE MESSING AROUND WITH PARTITIONS OR INSTALLATIONS!  EVEN EXPERIENCED PEOPLE CAN HAVE "OOPS!" AND LOSE THEIR DATA .... (not that I am speaking from experience :-\")

---

### Post by dino99 on 2015-08-17
i think that the most important are:
- choose what you feel better
- if you want something 'stable' and not too 'scary', then pick up what the biggest community choose, aka: gnome, kde, unity in that order if i'm not mistaking
- with old hardware, weak system, then choose Lubuntu, xubuntu

and finally the best news: you can change your mind now & then. Is not life good ?  ):P

---

### Post by buddy123 on 2015-08-17
Well, that is very interesting.
so I need to manually decide the partitioning with the advanced menus when I first install my pc?
I think I like that way of thinking, and I would like to do it do.
obviously it keeps only my files & user profile settings, nothing like OS modded files (sudoers i.e) and of course all my installed apps has to be reinstalled. and all their data/settings will also be removed upon installation. correct?

Since my computer is very fresh, I havent done so much since I installed it, and since it seems kde-plasma is the sleekest around 8-)  should I just install Kubuntu?
Do you mind instructing me how to separate my installation /root and /home partitions?

Regarding backups, of course. I have my externally installed NAS which backups everything backup-able - pcs, macs, phones.. :-)

---

### Post by buddy123 on 2015-08-17
> **dino99 said:**
> i think that the most important are:
- choose what you feel better
- if you want something 'stable' and not too 'scary', then pick up what the biggest community choose, aka: gnome, kde, unity in that order if i'm not mistaking
- with old hardware, weak system, then choose Lubuntu, xubuntu

and finally the best news: you can change your mind now & then. Is not life good ?  ):P

Thanks. Im re-starting with kubuntu. 

Regarding partitioning, Do I just create two partitions, / for root, and /home as my home partition?
What is the proper sizing, for a 0.5TB hard drive?
Can It be resized later, without formating the drive? Same as Partition magic can, if you remember this app for windows env.

---

### Post by Dragonbite on 2015-08-17
For applications that need to be re-installed, you could make a script that will install those. Like for me I would do something like ```
sudo apt-get install kpat pithos openjkd-jre 
``` (not sure if  I have the right names since I don't have the system in front of me.

If you save everything off and can blow away your installation, there are a couple of ways to re-partition your drive:

[LIST=1]
[*]During installation when you are allowed to change the partition scheme you should have the option to add or edit the partitions.  This is probably the same area where you would specify where to install and to attach your /home partition as /home
[*]Can run a live cd/usb session and use "Gparted" to delete the partitions and make the scheme you would like.
[/LIST]

You may be able to resize (shrink) the existing partition, then add a second partition without losing anything but it is risky and I would make sure you are ready to do a clean install just in case.

At least you will want 2-3 partitions ( /home, /(root) and possibly swap )  Sometimes it doesn't hurt to run a /boot partition if you are going to run multiple systems (dual-boot with win&lin or lin&lin).

If you have the space, then set up the partitions generously (50GB /(root)? 10-20GB /boot? ).  I got caught one time with running out of space on my /boot partition and it became a pain.

---

### Post by CantankRus on 2015-08-17
In response to your original question of removing all installed packages when 
installing a metapackage like kubuntu-desktop, you just have to keep a record of what's installed.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2289043&p=13332591#post13332591").

---

### Post by Topsiho on 2015-08-17
I think that a 15 GiB root ( / )partition, and no separate /boot partition, is quite enough :)
Then you might need a swap partition, of at least the size of the Ram memory, and use the rest of the hard disk for /home, in which all the personal files go.

You can keep the / partition from filling up on the (very) long run of time by wiping the not necessary anymore update files and image files using

sudo apt-get clean
sudo apt-get remove

(see man apt-get)  (man is the onboard manual for all commands, see also man man, to be used in the terminal.)

after updates, in the terminal. In some (x)ubuntu's autoremove doesn't work (e.g. Lubuntu). Then you have to remove image files by hand, except for the latest 2 or 3.
My / partition is 20 GiB, and only used for 36%, and not filling up, after some months use now, so 20 GiB is much too much :)

You can, as some have told you, install other (x)ubuntu) desktops too, such as kubuntu-desktop, mate-desktop, and others, just search for these, and while logging in choose which one you want to use.
You can use all applications in all desktops, so you are as free as a bird ...

Topsiho

---

### Post by buddy123 on 2015-08-17
Thanks.
I think I got it. I'll just explore and play with it.

I do like the tip about separate /home partition. Sounds very useful, especially when in my stage :-)
Perhaps I made a mistake giving 50GB to my root. I thought, well, after installing some apps, and IDE's for this and that..
Im used to my Windows computer being filled up with apps taking too much space.
I have 15GB /boot, 50GB / (root), 32GB Swap & 400~GB /home

---

