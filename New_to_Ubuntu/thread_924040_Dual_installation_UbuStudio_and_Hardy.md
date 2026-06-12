---
title: "Dual installation UbuStudio and Hardy"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by kalmdave on 2008-09-19
Mates,

Is it possible to install Ubuntu studio and Hardy heron and Vista on three different partitons?

I have Dell Inspirion 1525.

---

### Post by jamesrl on 2008-09-19
Ubuntu studio can be installed in the same partition as hardy.  The main difference between studio and hardy is that studio has a rt (realtime) kernel thats better for studio applications.  If you install ubuntu studio you can switch back and forth in the grub menu (select rt kernel when you need it).  Yes you would also see all the studio packages clutter up your sound and video list (and you can't really access it) but that seems more logical to me, then having two installations of ubuntu. 

So i would just install ubuntu + vista as normal, and then just do
```
sudo apt-get install ubuntu-studio
```

---

### Post by LeAstrale on 2008-09-19
I don't quite agree with James on this one. I think the easiest for you would be to have a seperate partition for each "/" (meaning one for Hardy / and one for Studio / ) and then have another partition for /home so you could share your own files/folders and then still have 2 seperate systems :)

---

### Post by jamesrl on 2008-09-19
I don't see your point *astral-1*.  Ubuntu-studio is just a collection of extra packages that can go on top of ubuntu (including a real-time kernel).  In your grub boot menu, you choose what you which kernel you want to startup.  If you are doing studio stuff, you choose the -rt kernel, otherwise you go with your normal one.
I've run like this and had no problems (sure ubuntu-studio tried changing the default background and the like, but you can set your own anyway).  I guess I don't see the point in installing the same version of ubuntu twice on your computer, one with an extra collection of packages and one without.
If you are worried about settings conflicting, you can have separate users.

For the record, I have been using ubuntu-studio with ubuntu on my Inspiron E1505 laptop with no problems with one install of ubuntu.  [Though I do have separate partitions for / and /home, but that's just my preference.]

---

### Post by markbuntu on 2008-09-19
If you are using Ubustudio for recording, etc, it is easier for it to have its own partition. That way, you can set up your studio the way you want and leave it that way. It can be really annoying to have evolution giving you email alerts every 10 seconds when you are trying to record. Things like that. 

For some people it just works better to have a studio without any distractions or temptations or any reconfiguring between sessions.

---

### Post by kalmdave on 2008-09-20
Thanks Mates,

I am sure you all are right at your thinking, since i'd be using it for good recording purposes so have given a dedicated partition. But the trouble is, my Hardy doesn't open now, which i had installed "Inside Windows Vista" not like clean Ubuntu Studio.

Please help.

---

### Post by Ludwig9 on 2008-09-20
Like kalmdave I have a Dell Inspiron 1525 on which I have Vista. I have not yet done a partition and put Ubuntu on it because I’m thinking of returning it (it's new) because I hate Vista with its slowness and endless updates and more particularly because I cannot run Audacity well with it. Its Sigma Tel HD CODEC driver (I have the latest update of it from the Dell Site) does not provide a sound mixer, at least not one compatible with Audacity. So I can use Audacity on the 1525 to record only in mono: the Audacity sound mixer drop-down window does not work, so one cannot select line-in as the recording source. The problem is much discussed at the Audacity forum. (cf. [http://audacityteam.org/forum/viewtopic.php?f=12&t=4887&p=19156&hilit=sigma+tel+audio#p19156](http://audacityteam.org/forum/viewtopic.php?f=12&t=4887&p=19156&hilit=sigma+tel+audio#p19156)) 
I have use Audacity for recording LPs with the help of a USB ARTcessories gizmo in Windows XP and Hardy. 
I ran Hardy on the 1525 from a good but dated live CD; I could not install Audacity with it (because Audacity was not on the list of ADD/REMOVE programs and I didn’t want to try other means to get it, etc.).
My question to kalmdave is: have you ever tried to run Audacity on your 1525 in Vista or Ubuntu? And if you are familiar with both Audacity and Ubuntu Studio, why do you prefer Ubuntu Studio?  I’d appreciate comments about the differences between these programs from anyone.

---

### Post by kalmdave on 2008-09-22
@ Ludwig and everyone

Thanks for the info, brother, i've not used Audacity yet but am using Ubuntu Studio in which Pulse audio server is configured. 

I feel the same about Vista:lolflag: but if u feel like having a good and light Vista try "eXperience Tiny Vista" (google it) am using it for a very long time, no issues yet.

Like i said after fresh installing Ubuntu Studio on my Dell 1525 on one of the partitions, i have lost my Hardy Heron which i had installed "Inside" the VISTA, now how do i get it back:confused:

---

### Post by kansasnoob on 2008-09-22
Sure you can! Right now I have XP, Hardy and Intrepid:

[ATTACH]86056[/ATTACH]

Note: If I decide to keep it that way I'll delete one SWAP, but that requires a bit of fiddling with the uuid's and chances are I'll dump one or the other soon anyway.

I fiddle around a lot trying different distros.

You'll notice that I like to keep all of my Linux in one or more extended partitions. The reason is that there's a 4 partition limit on hard drives. Right now as far as the hard drive's concerned I have two partitions!

I've had as many as 3 Linux OS's in one extended partition.

---

### Post by Ludwig9 on 2008-09-24
Anyone having trouble with Audacity while using Windows Vista or XP should look at this thread at the Audacity Forum: [http://audacityteam.org/forum/viewtopic.php?f=12&t=6421&p=25707#p25707](http://audacityteam.org/forum/viewtopic.php?f=12&t=6421&p=25707#p25707) 

> there has been some heated debate about why some vendors--specifically including **Dell and Lenovo**--seem to be either dropping support for stereo recording, or actually blocking it at a firmware or registry level in Vista. Some systems no longer have line inputs, some have changed the MIC input to mono only, and some folks allege this is all an RIAA-sponsored program to discourage copying.

As someone who has a Vista laptop and uses Audacity with it, I can tell you that "for sure" what is sometimes called "Stereo mix" has been somehow locked out of the computer. I had to go to an external sound card, in a card slot, and then voila, mysteriously that hardware can work in full stereo with no problem. But, the internal sound card can't record in stereo--even though it plays it, and in theory the hardware supports it.

I would suggest looking for a USB sound adapter, or a card adapter, and handling your audio through that. Check around on the web, you'll see that "simple" stereo recording is no longer possible with a number of machines unless you use XP (instead of Vista) and/or additional sound card/device.

I probably should have used a USB sound "card" but foolishly bought a Creative X-Fi card. I say foolishly because their Vista drivers didn't work under Vista and their tech support blithely pretends to speak YnGlitch, can't recommend using them at all, even though I finally got this one to work after literallly months of trouble.

**There are sometimes some stability issues with the release version of Audacity under Vista, I'm hoping the beta will mature soon. Meanwhile, even with hiccups, I have nothing but praise for Audacity and the generousity of the authors. The "mono" problem definitely isn't from Audacity!**

---

### Post by Ludwig9 on 2008-09-25
Those who have problems using Audacity's sound mixer in Vista and/or who have a Sigma Tel sound card should see the thread at the Audacity forum cited in my previous post. The solution may be that given there: 

> In the control panel click on the Sound icon, then click on Recording. You will then see 3 items: 1) Microphone /Line In, Sigma Tel HD Audio CODEC, not plugged in, 2) Microphone Array, Sigma Tel HD Audio CODEC, Working, 3) Microphone, USB Audio CODEC, Working.

Double click on #3. Do not click on Properties or Configure. After double clicking on Microphone, USB Audio CODEC, you will see a window with General, Levels, Advanced. Click on Advanced. You will then see a drop-down window which offers a list of channels, etc. Select 2 channel, 16 bit, 44100 Hz. Click Apply & OK. You then just need to set your Preferences in Audacity to stereo. I do not know whether it is advisable in Audacity under Preferences/Quality to select 16-bit rather than the 32-bit default setting, in order to make it match the 16-bit setting for the microphone. Perhaps one of the wise men here could advise us about that. 

Note: if one does all this, the drop-down mixer window in Audacity still remains dead, and you cannot choose line-in there. But you will get 2-channel recording anyway.

---

