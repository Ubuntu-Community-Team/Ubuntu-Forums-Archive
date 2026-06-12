---
title: "Is Ubermix the right choice over Edubuntu"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by kazakore on 2014-08-26
I hope it's OK to ask this here, as Ubermix isn't an official Ubuntu release. I did also briefly consider the Debian based Skolelinux...

Anyway: I am volunteering in Nepal currently and the small school here has a handful of dated laptops donated by previous volunteers. I admit I don't know the range of specs covered but should image all are at least a few years old. Currently all are running various versions of Windows, half of which seem to be flagging up as being non-Genuine. I was considering to suggest standardising, as much as possible, across the whole estate, so have been reading on the various different distributions aimed at education and think I may settle with Ubermix.

The main reason Ubermix stands out to be in the claims of ease of administration, with simple install procedure and easy way to reset the system to default in very little time. There is nobody out here particularly technically minded so the easier for them to manage the better.

The children on the whole are 3-14 and English isn't their native language, nor are much computer skills likely to be learned elsewhere, so educational game and activities aimed at primary school should be perfectly suitable, plus the basics of word processing, drawing and spreadsheet. All education distros seem to cover these bases fine.

Any reason why I should go for Edubuntu over Ubermix, or any wrongs in my reasoning above?

[http://www.ubermix.org/](http://www.ubermix.org/)



PS. What is wrong with SSO at the moment? I'm only staying logged in for about 10 seconds at a time and having to use two tabs in my browser, one to log in and one to refresh and post this message. Is it just me? Never had problems before using the same setup!

---

### Post by Rob Sayer on 2014-08-26
I haven't used ubermix, but the first thing I do when looking at a Linux distro is go to their site and look at their tech support forum.  Which I just did.  And I wasn't that impressed.  I've seen worse but there still don't seem to be any real experts there and their 'expert' seem to happily give out bad advice.

Besides, their site says "a turn-key, 5 minute installation, 20 second quick recovery mechanism"?  That's ad copy, not information.  Ubuntu installation is quite good, but it's turn key until it isn't.

In other words, you will quite likely need tech support at some point since Linux needs to be configured more than windows.  No other linux distro suitable for beginners has tech support near Ubuntu's.

It's based upon Ubuntu with the Unity desktop.  This is *not* a good choice for old donated computers.  You'd need pretty powerful graphics hardware to just run the desktop itself, let alone other graphics intensive programs.  In fact, if you're talking about a computer with less than 1 Gb of memory I'd never install Unity.  If it's 500Gb or less you'd want Lubuntu or maybe another, lighter distro.

Edubuntu is based on Unity as well so I'd have trouble recommending it for old hardware.  Though it's hard to definitively say without knowing specs, anything that originally had Windows XP on it is suspect.

You could always try a lighter desktop and then find out what software Edubuntu comes with.   Then install that.

---

### Post by uRock on 2014-08-26
Install them both and try them. If one makes you happier than the other then use it. If they are very close in workmanship, then I'd lean towards Edubuntu. As mentioned by Rob Sayer, Ubuntu Forums is probably the best place for seeking help. 

I would also recommend seeing if the other guys have an IRC channel. Some times that is the fastest place to get help with smaller distros.

---

### Post by grahammechanical on 2014-08-26
From the little reading I have just done I would say that the fast install is useful and so is the simple recovery method but you will find that things get more technical when It comes to adding and removing applications 

And when it comes to upgrading the system to a version based upon an upgraded version of Ubuntu then you have to in effect re-install. The fast install works ( I guess) by installing the OS to the USB stick and then copying it on to the hard disk. To benefit from the upgrades and fixes made to Ubuntu you will have to download and install to a USB stick a newer version and then install that onto your machines.

For example, if you was running version 1 based upon Ubuntu 12.04 and you wanted to upgrade to a version of Ubermix based upon Ubuntu 14.04 you would have to download and install Ubermix version 2. So, although Ubuntu Long Term Support (LTS) versions have 5 years support and Ubermix is built upon a Ubuntu LTS version, you actually would be using a version that  is not supported for five years. It is like using Ubuntu with the update feature disabled.

Regards.

---

### Post by stalkingwolf on 2014-08-26
the edubuntu packages can be installed from synaptic in any buntu flavor.  Mint as well.  as can the edu DE

---

### Post by grahammechanical on 2014-08-26
I would like to add that Ubuntu and its flavours like Edubuntu do have a Nepali (macrolanguage) pack and a Nepali keyboard layout.

---

### Post by kazakore on 2014-08-27
> **Rob Sayer said:**
> I haven't used ubermix, but the first thing I do when looking at a Linux distro is go to their site and look at their tech support forum.  Which I just did.  And I wasn't that impressed.  I've seen worse but there still don't seem to be any real experts there and their 'expert' seem to happily give out bad advice.

As I said the principle here is probably the most technical permanent staff and despite him having spent a few years living and working in Europe I would still call him far from tech-savvy! I doubt they would ever go onto a forum to try and find a solution and spend time working through an issue. That's why the Restore To Factory Setting/Restore option of Ubermix quite appealed to me.

> Besides, their site says "a turn-key, 5 minute installation, 20 second quick recovery mechanism"?  That's ad copy, not information.  Ubuntu installation is quite good, but it's turn key until it isn't.

They actually list a fair few instances where they have found it isn't and possible fixes... Bottom of page: [http://www.ubermix.org/download.html](http://www.ubermix.org/download.html)

> In other words, you will quite likely need tech support at some point since Linux needs to be configured more than windows.  No other linux distro suitable for beginners has tech support near Ubuntu's.

It's based upon Ubuntu with the Unity desktop.  This is *not* a good choice for old donated computers.  You'd need pretty powerful graphics hardware to just run the desktop itself, let alone other graphics intensive programs.  In fact, if you're talking about a computer with less than 1 Gb of memory I'd never install Unity.  If it's 500Gb or less you'd want Lubuntu or maybe another, lighter distro.

Edubuntu is based on Unity as well so I'd have trouble recommending it for old hardware.  Though it's hard to definitively say without knowing specs, anything that originally had Windows XP on it is suspect.

You could always try a lighter desktop and then find out what software Edubuntu comes with.   Then install that.

As you say it's based on Ubuntu, so most Ubuntu support will be relevant. Both Ubermix and Edubuntu use Unity (2D rather than 3D IIRC??) so no difference there. Thought the 2D version may not be too much of a resource hog....

Couple of the computers I've checked this morning do only have 512MB RAM so that's a bit of a worry! Seem to be running Vista Home (and think one was Win7) somehow though! :o

I had originally considered trying to make a system for them, based on maybe xubuntu (I never personally like LXCE so don't like to recommend it even though it is more lightweight.) This would require a lot of learning and reading and probably more time than I have here, plus I have found XFCE on Ubuntu Studio 14.04 to be much, much slower and a bit of a weird resource hog compared to on 12.04 for some reason! I have heard that a well configured KDE, with al effects stripped out, is possibly the best for support on a wide variety of hardware and isn't bad on resources if you turn everything fancy off...


> **uRock said:**
> Install them both and try them. If one makes you happier than the other then use it. If they are very close in workmanship, then I'd lean towards Edubuntu. As mentioned by Rob Sayer, Ubuntu Forums is probably the best place for seeking help. 

You clearly haven't experienced Nepali internet!!! Download them both really isn't an option! It took over 2 days to download ~600MB of updates to a computer the other day, so to download both would take over a week, plus testing time, I'll likely be gone before that is achieved!

> I would also recommend seeing if the other guys have an IRC channel. Some times that is the fastest place to get help with smaller distros.

See my comment above. I really don't expect anybody here to seek proper technical support. Hence the Restore option being so appealing. And the appeal of it having Flash, mp3, general media and things set-up which many users would expect to just work and do not on an average Ubuntu release.

> **grahammechanical said:**
> From the little reading I have just done I would say that the fast install is useful and so is the simple recovery method but you will find that things get more technical when It comes to adding and removing applications.

Adding and removing should be exactly the same as any other Ubuntu based distribution! But I am kinda relying on the fact that this should cover their needs as is really....

> And when it comes to upgrading the system to a version based upon an upgraded version of Ubuntu then you have to in effect re-install. The fast install works ( I guess) by installing the OS to the USB stick and then copying it on to the hard disk. To benefit from the upgrades and fixes made to Ubuntu you will have to download and install to a USB stick a newer version and then install that onto your machines.

For example, if you was running version 1 based upon Ubuntu 12.04 and you wanted to upgrade to a version of Ubermix based upon Ubuntu 14.04 you would have to download and install Ubermix version 2. So, although Ubuntu Long Term Support (LTS) versions have 5 years support and Ubermix is built upon a Ubuntu LTS version, you actually would be using a version that  is not supported for five years. It is like using Ubuntu with the update feature disabled.


Sounds just like Ubuntu to me!! The dist-upgrade option has NEVER worked  in my experience and I've always had to download the latest LTS  version. (Tried from 10.04 -> 12.04 and 12.04 -> 14.04 Ubuntu  Studio following all the instructions and had to give up!) But with old, donated hardware it's not something I'm so worried about either...


> **stalkingwolf said:**
> the edubuntu packages can be installed from synaptic in any buntu flavor.  Mint as well.  as can the edu DE

As I said earlier I did vaguely consider something like this originally but I don't think I really have the time and the knowledge and want something that can be installed onto any new laptops that might be donated and has some easy administration (restore option and already having Flash, mp3 and some things Ubuntu generally does not.)

> **grahammechanical said:**
> I would like to add that Ubuntu and its flavours like Edubuntu do have a Nepali (macrolanguage) pack and a Nepali keyboard layout.

This particular school teaches in English and the computers are donated by volunteers, so there is a variety of keyboard, non Nepali. (US, French, Polish/Czech at least. I would really like to standardise the keyboard but couldn't even find any blank paper stickers in the local stationary shop.

---

### Post by kazakore on 2014-08-27
It seems they have a Lite version on their Downloads page: (second link down)
[http://www.ubermix.org/files.html](http://www.ubermix.org/files.html)

Also at least 1.05 had a selection of Desktop Environments to aide with slower computers, so hopefully they haven't dropped that with later versions...
[http://wiki.ubermix.org/page/Alternate_Environments](http://wiki.ubermix.org/page/Alternate_Environments)

---

### Post by kansasnoob on 2014-08-27
> Edubuntu is based on Unity as well so I'd have trouble recommending it for old hardware.

Edubuntu also offers the lightweight flashback w/metacity session during installation:

[https://www.edubuntu.org/sites/default/files/docimages/install-precise/030-edubuntu-options-oneiric.png](https://www.edubuntu.org/sites/default/files/docimages/install-precise/030-edubuntu-options-oneiric.png)

I made some notes about that session here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

I use 14.04.1 wherever I can but with it's implementation of Gallium via/llvmpipe I find that it performs poorly with some older hardware, so in those instances I use Precise installed using the [archived 12.04.1 images]("http://old-releases.ubuntu.com/releases/12.04.1/") to avoid [HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").

The only way to decide what you prefer is to try them yourself.

---

### Post by kazakore on 2014-08-27
> **kansasnoob said:**
> Edubuntu also offers the lightweight flashback w/metacity session during installation:

[https://www.edubuntu.org/sites/default/files/docimages/install-precise/030-edubuntu-options-oneiric.png](https://www.edubuntu.org/sites/default/files/docimages/install-precise/030-edubuntu-options-oneiric.png)

I made some notes about that session here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

I use 14.04.1 wherever I can but with it's implementation of Gallium via/llvmpipe I find that it performs poorly with some older hardware, so in those instances I use Precise installed using the [archived 12.04.1 images]("http://old-releases.ubuntu.com/releases/12.04.1/") to avoid [HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").

It's good to know edubuntu also ships with a more streamlined DE and although ease of maintenance seem possibly the most important the larger community of edubuntu does also obviously appeal.

> The only way to decide what you prefer is to try them yourself.

Not to sound rude but I'm starting to feel, that if I had time to download and try them all (or even both I just about felt I could narrow it down to) I in some ways feel I would more lean towards learning the Arch system and build myself a package with the essentials and none of the clutter. Up in the Himalayas downloading multiple distros to just briefly try really doesn't seem an option. It's not like I'm used to in Europe! ;)

---

### Post by uRock on 2014-08-27
For future gigs I recommend downloading and keeping a library of ISOs for possible deployment. This way when you travel to areas with less than desirable bandwidth you only have to download updates. When someone calls me wanting me to demonstrate Linux with the intent of installing, I take Ubuntu, Xubuntu, Lubuntu, and Linux Mint with Cinnamon in my CD case. 

If you don't expect the next admins on those systems to be savvy enough to go to forums for help, then Arch would be one of the last distros to install. At this point, I'd say go with what you think would be the best.

If you decide to go with the Ubermix and need help with it, then you can ask for help with it in this [sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=401").

---

### Post by kansasnoob on 2014-08-27
> **kazakore said:**
> It's good to know edubuntu also ships with a more streamlined DE and although ease of maintenance seem possibly the most important the larger community of edubuntu does also obviously appeal.

Not to sound rude but I'm starting to feel, that if I had time to download and try them all (or even both I just about felt I could narrow it down to) I in some ways feel I would more lean towards learning the Arch system and build myself a package with the essentials and none of the clutter. Up in the Himalayas downloading multiple distros to just briefly try really doesn't seem an option. It's not like I'm used to in Europe! ;)

I didn't mean to sound at all rude either, sorry if I came across that way :redface:

Obviously I prefer Ubuntu and it's official flavors because I'm familiar with the whole infrastructure surrounding it, so I can't give an unbiased opinion regarding the pros and cons of Ubuntu compared to distro X, Y, or Z.

I do see that there is a Nepal Ubuntu LOCO:

[https://launchpad.net/ubuntu-np](https://launchpad.net/ubuntu-np)

[https://launchpad.net/~ubuntu-np](https://launchpad.net/~ubuntu-np)

Of course I have no idea what level of help they may be able to provide.

---

### Post by kazakore on 2014-08-28
Only had power and thus internet for about an hour today, wanted to ask this morning. I know I've seen an Edubuntu member post on this thread so hopefully I can get a knowledgeable reply.

Does Edubuntu come with Flash and Java pre-configured? These are quite important things for people first exploring the web and learning and if it would be extra steps after base installation it is a fair tick against the distro for this kind of circumstance.
Will Edubuntu run on a 1.7GHz Celeron with 512MB RAM using the Metalcity/Gnone2(esq) DE?

Thanks.

---

### Post by kazakore on 2014-08-30
Slipped to page 3. Quick bump for my above questions...

---

### Post by uRock on 2014-08-30
I downloaded and installed the 64bit version of Edubuntu in a VM. After the install I ran updates, which will downloads 192MB, then I installed the LXDE desktop used in Lubuntu. Another 13MB. The command for the LXDE is```
sudo apt-get install lxde
```This is the only thing I installed.

After getting everything installed and guest additions set up for VBox, I shut it down and cut the VM specs to a single core and 512 megabytes.

I found that booting into flashback with Metacity. ran alright until I started playing with Tux Paint and it started slowing down.

I booted into the LXDE desktop and it was much faster. Tux Paint worked fine.

**Your results may vary, but I think the systems will do alright with Edubuntu running the LXDE. **

---

### Post by kazakore on 2014-08-30
Thank you very much for doing that (Virtual Machines is something I've still never played with.) It is as I expected, the quoted 512MB minimum may let you load the OS but really not do anything.  Ubermix claim their 1.x (12.04 based) version should be OK on such old machines but even their Lite version of 2.x probably wont run correctly. Might give Ubermix 1.x my attention first then, as they also claim the easy administration.  Again thanks to everybody who has replied in this thread. :)

---

### Post by uRock on 2014-08-30
Using LXDE, the apps were working just fine. Since you hadn't installed anything yet, had you started downloading them yet? You probably could've downloaded both by now and had them on hand to test.

Edit. For the fun of it, I am downloading Ubermix to see how it looks and runs.
Edit #2: The images are on Google Drive. If you lose your connection, you will have to start the download over. It just happened to me.
Edit #3: They don't offer and ISO file, so you will have to create a bootable thumb drive with the image following their instructions. I'm unable to install it in a VM at this time.

---

