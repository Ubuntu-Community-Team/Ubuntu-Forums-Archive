---
title: "Pre 8.04 questions"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by bill1971 on 2008-07-19
Great info for newbies on this site. It's a lot to take in. After a couple of evenings reading about Hardy Heron, I'm still a little confused about hardware compatibility, that I can't seem to find guidance on. (This is my very first Ubuntu/Linux excursion). I've built and/or repaired 50-60 Windows boxes over the past 10 years or so. In recent years I've done quite a bit of virus/malware removal for folks. Each day I hate Microsoft a little bit more.

What is the more compatible platform? An nVidia-based MB/chipset w/ either on-board graphics or add-on nVidia graphics card? Or Intel chipset based boards? Which chipsets are supported in 8.04?

I have enough hardware around to build anything from a Biostar   T6100 (754-pin), or a 6150 or 7050 AMD dedicated box, or I can go Intel P4. Will Ubuntu automatically have support for chipset, sound/video, LAN, or other on-board devices?

Will Linux drivers on vendors' websites work with Ubuntu 8.04?
I've read some of the dual-boot info as well. Right this moment I'm on a Dell Vostro 1500 laptop which I had Dell partition into 2 x 55+ GB drives with WinXP Home as the OS. Given some of the Dell issues, should I even consider installing Ubuntu on the D:\ partition of this laptop, since it does have a modem, LAN and wireless connections, (i.e. a little more complicated?

Many thanks in advance for any assistance. It is much appreciated.

- Bill

---

### Post by nimbis on 2008-07-19
Hey there. 

I looked around for any lists of supported hardware for Hardy, but i didn't find anything useful either. Generally, hardware support is very good on Ubuntu, and Hardy extends this. Any piece of hardware I've ever plugged into my computer has worked without a hitch instantly (I use Gutsy), but perhaps I'm just lucky.

Drivers from vendor's sites... Considering that Ubuntu is the most popular (widely used) of the linux distributions, it would be a safe bet that if drivers are available from hardware vendors, they will probably work in Hardy. I've never needed to do this though.

I know I haven't been very specific, I don't have a high level of technical know-how when it comes to hardware, but good luck :)

---

### Post by bill1971 on 2008-07-19
Thanks, nimbus - 

You really answered my question(s) pretty well - that HH has pretty good device support built into the OS, (similar to WinXP built-in driver support).

One more question - If I'm using a 64-bit processor, I might as well use the 64-bit version of Ubuntu? (Unless I plan on installing an app sometime down the road that does not support 64-bit processing).

If I'm going to install the 32-bit version, I would use which version?

Thanks again. The dwnld page is not all that clear to me. I'll need to look at it again.

- Bill

---

### Post by nimbis on 2008-07-20
The download page is [here]("http://www.ubuntu.com/getubuntu/download"), and seems to be pretty straightforward.

I can't really tell you much about the 64-bit version of Ubuntu, as I've never tried it.

Also, before you download and install Hardy you should look [here]("http://ubuntuforums.org/showthread.php?t=361240"). Installing the drivers for your graphics card is sometimes needed, and when I tried Hardy I had all sorts of troubles with fuzzy screens and incorrect resolutions. It can be a complete nightmare. I simply reverted to Gutsy which did and continues to work fine with me without any need for tweaking configuration files. Every hardware setup is different though, I think I was just unlucky.

---

### Post by a0u on 2008-07-20
[This site]("http://www.ubuntuhcl.org/") has comprehensive reviews for Ubuntu hardware compatibility.

I suggest you try the 64-bit version if your processor is capable.  Unlike Windows, for which 64-bit applications are more difficult to obtain, virtually every software package in the official Ubuntu repositories have both 32-bit and 64-bit versions (this is also generally true for most open-source projects).

By the way, I'm using 64-bit Hardy right now, and it runs just as finely as the 32-bit version.

---

### Post by Portable_Jim on 2008-07-20
> **a0u said:**
> I suggest you try the 64-bit version if your processor is capable.  Unlike Windows, for which 64-bit applications are more difficult to obtain, virtually every software package in the official Ubuntu repositories have both 32-bit and 64-bit versions (this is also generally true for most open-source projects).

By the way, I'm using 64-bit Hardy right now, and it runs just as finely as the 32-bit version.
I agree.

Also, even if there is not a 64-bit package, you can still install 32bit apps in 64-bit Ubuntu (e.g [Installing Skype into Ubuntu]("http://ubuntuforums.org/showthread.php?t=432295") - there is no 64 bit version of Skype for Linux)

---

### Post by bill1971 on 2008-07-20
Many thanks, nimbis and aOu - this is good info. There's so much info available, I've been reading until I get a little confused. Maybe I'm thinking about it too much. I just need to make the plunge as I have my CD image burned and ready to go.

Thanks again for the input.

- Bill

Thanks to you as well, Jim. Much appreciated!

---

### Post by stmiller on 2008-07-20
Any computer that is Intel based (intel chipset, etc) works great in Linux as Intel releases specs for Linux drivers to be made. But all other chipsets and motherboards work fine as well.

In general Linux has incredible hardware support.

ATI and Nvidia have Linux drivers for video, too.

---

### Post by bill1971 on 2008-07-20
> **Portable_Jim said:**
> I agree.

Also, even if there is not a 64-bit package, you can still install 32bit apps in 64-bit Ubuntu (e.g [Installing Skype into Ubuntu]("http://ubuntuforums.org/showthread.php?t=432295") - there is no 64 bit version of Skype for Linux)

Jim - did you have any trouble installing the GeForce video or the 650i chipset drivers? Just curious. Thanks.

- Bill

---

### Post by Sef on 2008-07-20
> I just need to make the plunge as I have my CD image burned and ready to go.


Before installing, run the Live CD for a while, and see if any problems occur.  If they occur with the Live CD, then they almost certainly will occur upon install.

---

### Post by Frak on 2008-07-20
I would say use 32 bit Ubuntu for a bit before you dive into a 64 bit system. Unlike the happy faces shown here, 64-bit systems do tend to have their random spastic problems compared to 32-bit systems.

Also, Nvidia on-board and Nvidia add-on's are both par with each other. Even though ATi provides drivers, they are very shotty, and I would not recommend them.

---

### Post by Oldsoldier2003 on 2008-07-20
> **Sef said:**
> Before installing, run the Live CD for a while, and see if any problems occur.  If they occur with the Live CD, then they almost certainly will occur upon install.

I agree whole-heartedly with that. I usually run a live cd for hardware testing, and use the alternate installer or the minimal iso when it comes time to install.

---

### Post by bill1971 on 2008-07-20
Many thanks for everyone's input. It is much appreciated. This is very good advice, and gives me a good bit more confidence.

- Bill

---

### Post by a0u on 2008-07-20
I hope you will enjoy your experience with Ubuntu :).

Trying out the LiveCD firsthand is best way to start, but if you're in need of more info, the [Community Docs]("https://help.ubuntu.com/community/") would also be a useful place to look.

[LIST]
[*][32bit vs 64bit]("https://help.ubuntu.com/community/32bit_and_64bit") (which reiterates most of what's been said in this thread)
[*][BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto") (for the installation of  proprietary binary/restricted drivers provided by video card manufacturers)
[/LIST]
Also, it helps to remember that the LiveCD's performance probably won't be as good as a normal hard disk installation, since loading data from an optical drive is inevitably slower.

---

### Post by bill1971 on 2008-07-20
Thanks for all of the support. Based on everyone's suggestion, since I don't have any data that needs to be backed up on the Vostro laptop, I believe I'll run the Live CD from within XP.

Now, just so I'm straight, since the WinXP OS is 32-bit, does it matter if I use the 32 or 64-bit Ubuntu version, (as long as my CPU supports 64-bit, which it does)? Thanks, and please forgive my ignorance.:confused: So, unlike Windoze, which has 32-bit and 64-bit versions, Ubuntu is actually *processor* dependent, i.e.,x86 (32-bit) vs. AMD64/Intel 64EMT (64-bit) architecture? (Sorry if I'm drifting here).

---

### Post by damis648 on 2008-07-21
> **bill1971 said:**
> Thanks for all of the support. Based on everyone's suggestion, since I don't have any data that needs to be backed up on the Vostro laptop, I believe I'll run the Live CD from within XP.

Now, just so I'm straight, since the WinXP OS is 32-bit, does it matter if I use the 32 or 64-bit Ubuntu version, (as long as my CPU supports 64-bit, which it does)? Thanks, and please forgive my ignorance.:confused:

If you run the liveCD, you must boot with it, unless you are Planning a WUBI install (which installs Ubuntu on your current NTFS partition in a way you can just use the Remove Programs dialog to remove it, only good for testing really). Set your BIOS to boot with the CD drive and fire it up. On the debate of 64 or 32-bit, use 32-bit. You really will not see too much of a difference, and 64-bit is just much more of a hassle.

---

### Post by sydbat on 2008-07-21
I haven't had a major problem with either the 64 bit or 32 bit installs (two separate machines). I think it is simply preference.

Oh, and you can run a 64 bit wubi install in XP 32 bit...

---

### Post by suprfish on 2008-07-21
> **bill1971 said:**
> Thanks for all of the support. Based on everyone's suggestion, since I don't have any data that needs to be backed up on the Vostro laptop, I believe I'll run the Live CD from within XP.

What do you mean "from within XP"? Just to clarify, if you want to try out the LiveCD, simply boot to them and they'll run Ubuntu off the CD (won't touch your hard drive). 32-bit or 64-bit Ubuntu should work just fine for you. 

> **bill1871 said:**
> Now, just so I'm straight, since the WinXP OS is 32-bit, does it matter if I use the 32 or 64-bit Ubuntu version, (as long as my CPU supports 64-bit, which it does)? Thanks, and please forgive my ignorance.:confused: So, unlike Windoze, which has 32-bit and 64-bit versions, Ubuntu is actually *processor* dependent, i.e.,x86 (32-bit) vs. AMD64/Intel 64EMT (64-bit) architecture? (Sorry if I'm drifting here).

I am not sure what you mean by "processor dependent"; the different versions simply take full advantage of whatever architecture they were designed for (same thing with Windows).
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by Sef on 2008-07-21
> Now, just so I'm straight, since the WinXP OS is 32-bit, does it matter if I use the 32 or 64-bit Ubuntu version, (as long as my CPU supports 64-bit, which it does)? Thanks, and please forgive my ignorance.

As has been mentioned, no it doesn't.  Besides, 64-bit being better with gaming, and video editing, I have found that downloading a lot of digital photos goes a lot faster.  I downloaded a friend's almost 600 photos to his usb key in less than an hour.

---

### Post by Sef on 2008-07-21
> What do you mean "from within XP"? Just to clarify, if you want to try out the LiveCD, simply boot to them and they'll run Ubuntu off the CD (won't touch your hard drive).

The OP confused Wubi and the Live CD.

---

### Post by bill1971 on 2008-07-22
> **Sef said:**
> The OP confused Wubi and the Live CD.

Thanks, Sef - 

I think I get it now. The Live CD contains a wubi folder. If I insert the CD while in XP, the autorun will give me a dialogue box with the option to "Install inside Windows" and as such, will install Ubuntu within Windows as an app, which can be removed just like any other app. Someone said this was good for "testing" purposes. As stated, you take a bit of a system performance hit by doing this. Otherwise, you would just boot from the CD and do an actual install.

At the risk of opening up a new can of worms: If I build a dedicated Ubuntu PC, what are the current limitations of Ubuntu for someone wanting to perform "normal" PC functions? Would the main limitation be in gaming? Are you limited due to the fact that most game vendors write the games to the Windows DX9 or DX10 API? 

Have most of you folks "divorced" yourselves completely from Microsoft, or do most of you dual-boot along with Windows to have all of your bases covered? I'm just curious about this, knowing fully that this is an absolutely "loaded" question, varying greatly depending on the individual.

Many thanks again, for all of the great input. This truly is a wonderful community, and everyone's input is very much appreciated.

- Bill

---

### Post by BGFG on 2008-07-22
For my 15 cents, I'd generally prefer the Amd 64 Nvidia combo. i have a dell inspiron 531 running and amd X2 and i've had no hardware issues whatsoever. The AMD64 version of Hardy is VERY fast and my machine is just average. From browsing these forums i get the sense that intel can be a bit troublesome, the motherboards i mean. 

As for gaming, I don't really do it, but WINE seems to be able to handle quite a few popular games, and the list is growing. For everything else, everyday computing , office , graphics... There's an open source monster waiting for you....

These are MY top pics;
Torrent - Deluge
Music - audacious, alsaplayer (my music needs are simple)
Graphics - Inkscape, Xara ,The GIMP
Office - Open Office
Media - VLC
Fileshare - Frostwire, Limewire

the list goes way on....

---

### Post by a0u on 2008-07-22
> **bill1971 said:**
> At the risk of opening up a new can of worms: If I build a dedicated Ubuntu PC, what are the current limitations of Ubuntu for someone wanting to perform "normal" PC functions? Would the main limitation be in gaming? Are you limited due to the fact that most game vendors write the games to the Windows DX9 or DX10 API? 
 
Have most of you folks "divorced" yourselves completely from Microsoft, or do most of you dual-boot along with Windows to have all of your bases covered? I'm just curious about this, knowing fully that this is an absolutely "loaded" question, varying greatly depending on the individual.
- Bill
 
The majority of activities that people do in Windows (e.g., office, multimedia, Internet browsing, etc.) can be done in Ubuntu. Check out Applications -> Add/Remove - there's a plethora of choices, probably more than you will ever try in your lifetime. That's the beauty of open-source freedom.
 
On the other hand, gaming and highly specialized software are Linux's present shortcomings, mostly because commercial software companies are unwilling to make the commitment of supporting Linux (considering ~90% of the desktop OS market is currently dominated by Windows). This doesn't mean there [aren't any good games]("http://www.google.com/search?hl=en&q=Linux+games") - just not the big-name titles that the mainstream gamer is accustomed to. But I'm optimistic that, in time, the gap will be bridged as Linux and other open-source projects progress. :)
 
Personally, I have a dual-boot between Ubuntu and Vista. As a high-school student, I can't really speak for the adult user (who maybe has a different set of computer priorities), but since the beginning of summer vacation I have only booted Vista twice - once to make sure GRUB was configured correctly and another to open a file with an application-specific proprietary format (*.fla, for Adobe Flash).
 
On a side note, my Vista installation has been "divorced" from M$ as much as possible, too; anything that can be replaced with a functional open-source alternative already has been...so about the only component that remains "Microsoft" is the OS itself. If [ReactOS]("http://www.reactos.org") becomes successful, "Windows" can also be finally free of M$. (OK, I finished my rant.)

---

### Post by bill1971 on 2008-07-23
> **BGFG said:**
> For my 15 cents, I'd generally prefer the Amd 64 Nvidia combo. i have a dell inspiron 531 running and amd X2 and i've had no hardware issues whatsoever. The AMD64 version of Hardy is VERY fast and my machine is just average. From browsing these forums i get the sense that intel can be a bit troublesome, the motherboards i mean. 

As for gaming, I don't really do it, but WINE seems to be able to handle quite a few popular games, and the list is growing. For everything else, everyday computing , office , graphics... There's an open source monster waiting for you....

These are MY top pics;
Torrent - Deluge
Music - audacious, alsaplayer (my music needs are simple)
Graphics - Inkscape, Xara ,The GIMP
Office - Open Office
Media - VLC
Fileshare - Frostwire, Limewire

the list goes way on....

Many thanks, B -


Good info. PC Mag had a recent article referencing some of the best free software, both for Windows and Linux, so I made a list. Thanks for taking the time for including your top picks. Very much appreciated.

My new board and CPU just came today: ASRock P45 board and Intel E8500 Core 2 Duo processor. This will most probably be a gaming rig, (my son games, I don't, but I do love good graphics). I'll (reluctantly) put Vista on it, creating a separate partition for Ubuntu, and run the Live CD to check for hardware compatibility.

I have a warehouse full of hardware, so I will also most likely build a low cost Ubuntu dedicated AMD64/nVidia box as well.

---

### Post by bill1971 on 2008-07-23
> **a0u said:**
> The majority of activities that people do in Windows (e.g., office, multimedia, Internet browsing, etc.) can be done in Ubuntu. Check out Applications -> Add/Remove - there's a plethora of choices, probably more than you will ever try in your lifetime. That's the beauty of open-source freedom.
 
On the other hand, gaming and highly specialized software are Linux's present shortcomings, mostly because commercial software companies are unwilling to make the commitment of supporting Linux (considering ~90% of the desktop OS market is currently dominated by Windows). This doesn't mean there [aren't any good games]("http://www.google.com/search?hl=en&q=Linux+games") - just not the big-name titles that the mainstream gamer is accustomed to. But I'm optimistic that, in time, the gap will be bridged as Linux and other open-source projects progress. :)
 
Personally, I have a dual-boot between Ubuntu and Vista. As a high-school student, I can't really speak for the adult user (who maybe has a different set of computer priorities), but since the beginning of summer vacation I have only booted Vista twice - once to make sure GRUB was configured correctly and another to open a file with an application-specific proprietary format (*.fla, for Adobe Flash).
 
On a side note, my Vista installation has been "divorced" from M$ as much as possible, too; anything that can be replaced with a functional open-source alternative already has been...so about the only component that remains "Microsoft" is the OS itself. If [ReactOS]("http://www.reactos.org") becomes successful, "Windows" can also be finally free of M$. (OK, I finished my rant.)

Thanks for the input, a - 

You seem like a fine young man with a bright future ahead of you. This is all very good info. Thanks for the links.

- Bill

---

