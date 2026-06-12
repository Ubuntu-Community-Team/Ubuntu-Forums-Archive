---
title: "[SOLVED] A few noob questions from a guy trying to get away from windows"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-09-08
I have been running windows all my life, except for my first computer, which had DOS and Windows 3.1, which of the two, i preferred running the command line in DOS.  A coworker of mine has turned me on to Ubuntu, and for the past week, I have been on here, researching and seeing if it is something that will work for me.  I have a couple key concerns.  First of all, let the records show that the computer I will be using is not my only computer, and if I get frustrated, I have no problem going back to just windows.  Just bare that in mind before answering any of these questions.  OK,  QUESTION 1!

1.  It seems as though Ubuntu is the most widely known version, but my research here has turned me on to Kubuntu, Xubuntu, etc.  It there any real difference aside from a different GUI running on top of linux??

2.  As far as files go, I have all my important docs in word, no movies, but all my music is DRM encoded WMAs.  I downloaded them all from the new napster, where you actually pay, so I am assuming that have DRM.  Is it feasible (and free) to get a converter to turn them into ogg vorbis files?

3.  I want to make this my little project, to become a power user on ubuntu, so I have taken to reading some instruction docs on this website.  Maybe its cuz i was microsoft fed since the 3rd grade, but reading about all the codes and fixing your problems is making my head spin!  I dont really want to have a dual partition HD, but is that the best way to go?

4.  I have a dell inspiron 700m with 40 gig HD, 1.6gz intel processer with centrino, and .5gig of memory.  Is this a worthy rig of Ubuntu, and if I had to, is it worthy of a dual OS system?

If this is is too long of a post, or too basic, please someone give me the heads up, I know all the resources are in front of me, but I am having a hard time understanding even the basic stuff!  I am the type of person who wants to just jump in head first (i.e. wipe out windows, jump in head first) but I am afraid this might be a little rash this time around.  Thanks in advance!!

---

### Post by echo314 on 2008-09-08
1. I would not worry too much about the different sub-versions yet, the best way IMO is to just start with one, and learn about it. After you have learned a bit about it, then just install another type from the repository, and then booting up you can select that new display manager and try it out. Simple!

2. Maybe. I don't know. VLC can play most files, but I don't know how it handles DRM...you can always put in a LiveCD and see if it plays though!

3. Dual partitioning is easy, and allows you to switch to a different Linux OS with ease. Just make one partition mounted at "/", without the quotations (about 8 gigs) and make a second one "/home", thats where all your data goes so you want to make that one nice and roomy. Plus a small partition mounted at /swap. 

4. The specs do seem a little low, but I'm not sure as to the exact recommended specs for Ubuntu. You can always try using Fluxbuntu first, its lighter-weight compared to both Gnome and KDE.

Dual booting is a great way to go. I too weaned myself off XP, and within 2 or 3 months deleted it.

If you have any further questions please ask!!! Love to help.

---

### Post by jerome1232 on 2008-09-08
Okay I'm going to take a stab at a few of your questions.

1: No real difference except the desktop enviroment and/or window manager, they all have access to the same repositories (That's what provides your software), you can even have all 3 at the same time if you so wanted. KDE (kubuntu), Gnome (ubuntu), and XFCE (xubuntu)

2: I don't know, but will hit google and look. I'm sure I've seen things about doing that. 

This looks promising [http://www.lockstockmods.net/2008/04/06/remove-drm-from-wmv/](http://www.lockstockmods.net/2008/04/06/remove-drm-from-wmv/)  unsure of legality but you aren't removing drm to share them with the world so I see no issues

3: When you first start out, it'll probably be best to keep Windows around, dual booting it.

4: Yes that should run on Ubuntu just fine, although it's a bit low on Hard Drive space for dual booting (dual booting doesn't take any more resources than booting one OS, you just get to choose which one you want into when you turn the computer on)

You might want to look at the community contributed documentation it has alot of great how-to's.

---

### Post by simtaalo on 2008-09-08
well im still quite a noob, had ubuntu running around 6 months. i took the jump in head first option, and aside from minor problems (all my own creation) its been great. ive had no hardware issues.

the system you describe is more than capable of running ubuntu. personally i think you would have more problems trying to run the dual boot than running ubuntu on its own.

converting the audio files is no problem, theres a program called oggConvert that will do the job.

---

### Post by Cl0ud9 on 2008-09-08
2. I don't think there is any need to convert file formats at all. Instructions on playing wma files can be found here: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

The VLC media player will play just about anything and oppenoffice will open word doc files.

---

### Post by Miljet on 2008-09-08
You don't have to dual-boot. Especially since you have more than one computer. I would just wipe the disk and install Ubuntu.

Your system is fine for Ubuntu. It will install on as little as 6 MB hard disk space and requires 384 meg of memory. You didn't mention a graphics card so I am assuming that you have integrated graphics. Ubuntu should find it and set it up automatically. ATI graphics cards don't play real nice with Linux.

I have converted two of my three computers so far and haven't looked back. Just waiting to get a new graphics card before converting the third.

Go for it and good luck. If you have problems just post here.

---

### Post by Samhain13 on 2008-09-08
> 1. It seems as though Ubuntu is the most widely known version, but my research here has turned me on to Kubuntu, Xubuntu, etc. It there any real difference aside from a different GUI running on top of linux??

It may only be GUI but from experience, when you get used to one like KDE, it's not easy switching to another like GNOME. It gets more difficult switching DE's if you're one to do a lot of customisations.

> 2. As far as files go, I have all my important docs in word, no movies, but all my music is DRM encoded WMAs. I downloaded them all from the new napster, where you actually pay, so I am assuming that have DRM. Is it feasible (and free) to get a converter to turn them into ogg vorbis files?

For the Word files (.doc, not .docx), you can use OpenOffice, which comes as the default office suite in Ubuntu.

Sorry, I know next to nothing about DRM. But regarding the feasibility of transcoding/converting, if you're talking about hundreds of files, then clearly it's not feasible; although, there many available apps for Ubuntu that can do the transcoding like ffmpeg, mendcoder, VLC can also do some transcoding, among others.

> 3. I want to make this my little project, to become a power user on ubuntu, so I have taken to reading some instruction docs on this website. Maybe its cuz i was microsoft fed since the 3rd grade, but reading about all the codes and fixing your problems is making my head spin! I dont really want to have a dual partition HD, but is that the best way to go?

You also say, "the computer I will be using is not my only computer". So dual booting is not necessary if you have a spare box to practise on.

> 4. I have a dell inspiron 700m with 40 gig HD, 1.6gz intel processer with centrino, and .5gig of memory. Is this a worthy rig of Ubuntu, and if I had to, is it worthy of a dual OS system?

It's worthy. I used to have almost similar specs in terms of processor speed and memory. As for the part where you ask dual OS worthiness, that depends on your available HD space.

Cheers! :D

---

### Post by panhandle on 2008-09-08
I'd recommend just using a live CD before you make any sort of installation.

I think one of the more recent issues of Linux Pro had all three Ubuntu versions available for testing.

---

### Post by jerome1232 on 2008-09-08
> **Cl0ud9 said:**
> 2. I don't think there is any need to convert file formats at all. Instructions on playing wma files can be found here: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

The VLC media player will play just about anything and oppenoffice will open word doc files.

Not DRM protected WMA files, they are basically encrypted media files, nothing can read them unless it knows how to decrypt them. No matter what the DRM needs to be removed to play them in something other than Windows Media Player. VLC is a great media player though, haven't found a format yet it can't tackle :)

edit: I would just remove the drm and leave them wma, transcoding lossy format to lossy format causes quality loss.

---

### Post by sloggerkhan on 2008-09-08
Having your music in WMA with DRM really sucks. To get them to play, you will have to put your whole music collection on audio CDs or revert to an old version of windows media with a DRM loophole. Then, if you reimport them to any format other than wma, there will be a slight loss of audio quality as the tracks will probably have to compression passes coded out of them from lossy compression.

Other than your music, you're fine, though.

---

### Post by flamingswrd on 2008-09-08
1) It depends on what you prefer. Gnome is a basic interface and is easy to maneuver. I too am a linux newb and have started with plain 'ole Ubuntu and it is a nice change of pace...not so many windows to go through to change things. These are assumptions from research: Kbuntu is a modification of the desktop to look like Windows, so it is a weening aid, IMO. Edbuntu is comes preloaded with educational software, so you probably wouldn't need it. 

2) Yes there is a program available through the add/remove feature that will convert them...I think. Otherwise like everyone else says VLC is free and works. 

3) I was going to dual boot...then I found a box to play around with. If you have the physical resources (another box) to use, I suggest wiping, partitioning, and starting from scratch to get that real learning experience. You always have a Windows Install CD to fall back on (assuming you still have one).

4) Those specs should work fine for an linux distro. Dual booting on that small of a drive is generally not recommended. 

Whatever you do, good luck, have fun, and the forums are a good place to start/get help.

---

### Post by rideburton56 on 2008-09-09
Well everyone, I decided I am going to take the dive.  No Partitioning, no more xp, just ubuntu.  Its going down now as we speak.  As for all the responses, thanks!  I am sure I will be posting on this more, but let me just say that this has been a very comforting experience with all the help i recieved!

Now to figure out how to make the post say SOLVED (ill figure it out myself dont worry :)

---

### Post by Threbus5 on 2008-09-09
> **rideburton56 said:**
> I have been running windows all my life, except for my first computer, which had DOS and Windows 3.1, which of the two, i preferred running the command line in DOS.  A coworker of mine has turned me on to Ubuntu, and for the past week, I have been on here, researching and seeing if it is something that will work for me.  I have a couple key concerns.  First of all, let the records show that the computer I will be using is not my only computer, and if I get frustrated, I have no problem going back to just windows.  Just bare that in mind before answering any of these questions.  OK,  QUESTION 1!

1.  It seems as though Ubuntu is the most widely known version, but my research here has turned me on to Kubuntu, Xubuntu, etc.  It there any real difference aside from a different GUI running on top of linux??

No real difference except for the built in educational software in Edbuntu.

2.  As far as files go, I have all my important docs in word, no movies, but all my music is DRM encoded WMAs.  I downloaded them all from the new napster, where you actually pay, so I am assuming that have DRM.  Is it feasible (and free) to get a converter to turn them into ogg vorbis files?

Be careful, depending upon the version of Word that you have the Open Office word processor may fail. For example, the Word.docx (Word 2007) files will not presently open in Open Office. As far as sound goes, research the forums. Most audio files convert.

3.  I want to make this my little project, to become a power user on ubuntu, so I have taken to reading some instruction docs on this website.  Maybe its cuz i was microsoft fed since the 3rd grade, but reading about all the codes and fixing your problems is making my head spin!  I dont really want to have a dual partition HD, but is that the best way to go?

If you decided to become a power user then attack the hill and become one. A decision to become an Ubuntu power user will require learning all those codes and making your head spin. If you want only one OS on your machine at a time, then OK. Backup whatever system resides there onto something that you can use to restore it. Then install Ubuntu. Be aware that Ubuntu is not 100% substitutable with Windows, you will find that somethings do not work, and be prepared to learn, struggle, and learn again. If you do not want to make a commitment then why bother?

If you want to succeed as an Ubuntu user then once you have landed on the foreign shore do the same thing that Coronado did to encourage his men to dedicate themselves to their quest - burn the boats. In other words, make no attepmt to reinstall Windows. Your statement concerning having no compunctions about returning to Windows suggests that you are less than committed to becoming a power user.

NOTE, if you use your computer for school or work or games determine that the Ubuntu functions flawlessly in that environment before running it from anything other than the live CD.

4.  I have a dell inspiron 700m with 40 gig HD, 1.6gz intel processer with centrino, and .5gig of memory.  Is this a worthy rig of Ubuntu, and if I had to, is it worthy of a dual OS system?

That will work ok for a single system. I have Ubuntu 8.04.1 running on an almost identical configuration. However, if you want eye candy and cuteness that also runs quickly you will need to use a faster processor with more RAM. Faster as in 3+ or more and RAM as in 1 G. In other words, do not expect miracles from an old machine. BUT, it will probably perform better than Windows under the same hardware limitations.

If this is is too long of a post, or too basic, please someone give me the heads up, I know all the resources are in front of me, but I am having a hard time understanding even the basic stuff!  I am the type of person who wants to just jump in head first (i.e. wipe out windows, jump in head first) but I am afraid this might be a little rash this time around.  Thanks in advance!!

Best wishes for a successful investigation and experience.

---

### Post by alyxx_on_phyer on 2008-09-09
A good friend tuened me on to ubuntu and I have spent most of the day looking at it and so far it seems really cool and I am thinking if switching from vista, I have a brand new conpaq laptop ( 1gig ram, dual HHD 137gig/11.7gig AMD 64 athlon x2 dual core 1.9 ghz with a nvidia graphics ) so far I have no real problem with the switch. 

However I have 2 dozen .avi movies and 1000 mp3`s running in itunes. I have tried converting my .avi to dvd for burning but vista takes up so much that it takes 5+ hours just to convert and I end up with audio video lag and its not burnable.

So my questions are since I have 2 drives is it possable to install ubuntu over vista without having to format both drives?
and is there a burning software built in? if not will I still be able to use nero 8?

---

### Post by macvr on 2008-09-09
> **rideburton56 said:**
> 
4.  I have a dell inspiron 700m with 40 gig HD, 1.6gz intel processer with centrino, and .5gig of memory.  Is this a worthy rig of Ubuntu, and if I had to, is it worthy of a dual OS system?

ur specs aren't bad, dual booting would work too
check the minimum specs required
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by sloggerkhan on 2008-09-09
> **alyxx_on_phyer said:**
> A good friend tuened me on to ubuntu and I have spent most of the day looking at it and so far it seems really cool and I am thinking if switching from vista, I have a brand new conpaq laptop ( 1gig ram, dual HHD 137gig/11.7gig AMD 64 athlon x2 dual core 1.9 ghz with a nvidia graphics ) so far I have no real problem with the switch. 

However I have 2 dozen .avi movies and 1000 mp3`s running in itunes. I have tried converting my .avi to dvd for burning but vista takes up so much that it takes 5+ hours just to convert and I end up with audio video lag and its not burnable.

So my questions are since I have 2 drives is it possable to install ubuntu over vista without having to format both drives?
and is there a burning software built in? if not will I still be able to use nero 8?

Ubuntu has burning software built in called brasero. There are other burning softwares available in the repos if it doesn't fit your exact needs.

So far as .avi movies go, you can play them on ubuntu if they don't have copy protection, just install the correct codecs or vlc or smplayer. Of course you can play mp3s, too.

---

### Post by crlcan81 on 2008-09-09
I'm also a Ubuntu Noob, been on it not even a month, or little more then that. Ran nearly every windows ever made except NT and business versions except Pro. 3.0 on up to XP and a little vista. I deleted XP within three weeks of being on Ubuntu, cause anything XP can do, ubuntu can do better. I'm running even lower then that. Gateway E3600 NEVER upgraded. Bought a 1400 dollar system for 50 bucks five years after it was made. Even then this baby runs BEAUTIFUL.

---

### Post by alyxx_on_phyer on 2008-09-09
I have never done a dual boot, its all kinda new to me and im not sure how to do it,I have more then enough disk space to do the dual boot, what do I do?

---

### Post by macvr on 2008-09-09
> **alyxx_on_phyer said:**
> I have never done a dual boot, its all kinda new to me and im not sure how to do it,I have more then enough disk space to do the dual boot, what do I do?
this is the easiest guide for a dual boot install
XP>[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")
VISTA>[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

i'm a noob too, installing UBUNTU is SOOOOOOOOOO much easier than XP/VISTA!

---

### Post by Idefix82 on 2008-09-09
If you already have Windows on your computer and you want to install Ubuntu, you just install it. Ubuntu recognizes the windows system and at the next startup it offers you the option of booting linux or windows.
However, if you don't absolutely need windows, I wouldn't keep it. Disc space is the one thing but you will also make life easier for Ubuntu, since windows is very sloppy with hardware and Ubuntu has to keep fixing things. You will find out soon enough what I mean, when you just pull out your USB stick under windows and try to put it back in under Linux.

---

### Post by misswham on 2008-09-09
I am a 3 mth user of Ubuntu.  Let me tell you once you start you wont go back to windows, hell you wont even look out of a window hahaha.  I dual boot with xp on my desktop and dualboot vista and ubuntu and i have full ubuntu on another one.  I only use windows to print something out, because my lexmark doesnt have a linux driver, and to sync my phone with microsoft outlook.  There have been weeks that I havent logged on at all to windows.  Also your wma and wmv files will play fine without conversion.

---

### Post by alyxx_on_phyer on 2008-09-09
So far doing a dualboot seems pretty easy, I think the part im having a problem with is that I dont have a vista CD and I dont want to lose everything I have on my laptop. 

I think im just worried that if something goes wrong I will be in big trouble you know,I know its easier if I get step by step instructions as I dont really understand how all of this stuff works. So im asking whats step one?

---

### Post by fballem on 2008-09-09
When I first decided on converting from windows, I decided 'no dual boot'. I experimented with Kubuntu and ubuntu (re-installing several times). Settled on ubuntu for two reasons:

[LIST=1]
[*]Kubuntu seems to be an integrated environment and I didn't like k-office - there are problems reading MS Word and MS Excel files. There is a project to incorporate Open Office into KDE, but I wasn't sure how far along it was.
[*]I found that ubuntu was actually closer to the Windows XP experience than Kubuntu.
[/LIST]

I use Windows at work (corporate supplied machine), but I have two machines at home that are running ubuntu. My kids had a really easy time. I found several links that help with the installation of codecs and other stuff, especially this one: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I've got the install process for ubuntu, including all of my custom configurations, down to less than 1 day (it usually takes me close to 2-1/2 days to do an installation of Windows and all software, including custom settings).

Before you convert, make sure that you preserve e-mails and contacts from your windows machine, as well as any document files that you will need in the new environment.

---

### Post by macvr on 2008-09-09
> **alyxx_on_phyer said:**
>  I dont have a vista CD and I dont want to lose everything I have on my laptop. 


i too never had an XP CD for yrs, n was worried of my install....

BUT I realized that u can use ANY install CD for re-installing ur XP.
all u need is ur ProductKEy[if its on the sticker] thats enough.

it worked for XP should be same for Vista too. if u want to check if ur KEY works with any CD, try first to install on a Virtual machine... thats what i did first, then re-installed on my system

---

### Post by t0p on 2008-09-09
> **Samhain13 said:**
> 

Sorry, I know next to nothing about DRM. But regarding the feasibility of transcoding/converting, if you're talking about hundreds of files, then clearly it's not feasible


This isn't true.  A key feature of Linux is its powerful command line.  Converting 5 files or 500 files can be equally easy.

---

### Post by alyxx_on_phyer on 2008-09-09
I am an avid user of Utorent and torrent downloader, will I still be able to download torrents with utorrent on ubuntu or do I have to get something else?

---

### Post by jerome1232 on 2008-09-09
By default Ubuntu uses Transmission, however there are several other torrent programs to choose from, deluge, azureus, rtorrent, etc...

Utorrent is windows only, however you can install it under WINE which is a compatibility layer for windows programs.

---

### Post by alyxx_on_phyer on 2008-09-09
ok I have azureus on my laptop already but found I liked utorrent better for some reason, so theres 1 more less thing holding me back.

I just finished making the boot CD but im not sure how to get started

---

### Post by macvr on 2008-09-10
> **alyxx_on_phyer said:**
> 
I just finished making the boot CD but im not sure how to get started

if u want to reinstall vista in future? i suggest u do it before u install ubuntu, else u have to do a bit of editing of the grub later

incase u want to  know bout reinstalling Vista _*since u r worried u dont have CD*_, PM me[since that would be out of topic in the forums]

---

### Post by alyxx_on_phyer on 2008-09-10
I dont want to get away from vista right away so I was going to dualboot

but im not 100% sure how to do it

---

### Post by macvr on 2008-09-10
> **alyxx_on_phyer said:**
> 
but im not 100% sure how to do it
u r not sure of how to dual boot? or reinstall vista

---

### Post by Idefix82 on 2008-09-10
OK, here goes (assuming that you are installing 8.04):

**Step 1:** Insert your Ubuntu boot CD, start up the computer and tell the BIOS to boot from CD. Usually after turning on the computer you have a couple of seconds to press a button (normally F10 I think) to choose, which device to boot from. Alternatively, go into the BIOS setup (usually F2 during the same few seconds) and tell the BIOS to try booting from CD first.

**Step 2:** In the menu that follows, say that you want to install Ubuntu. You have a couple of options here. The easiest one will be to tell Ubuntu to resize the existing partition and install itself in the space it creates. You can tell it, how much space to leave for Windows and how much to allocate to Ubuntu.
Well, actually, I am lying. By far the easiest option is to make a clean sweep and to tell Ubuntu to use the entire hard drive, but I am assuming that you don't want to do that.

**Step 3:** Sit back and relax. Before that, in case Ubuntu asks you how much space to allocate to the SWAP partition, go for roughly double your RAM (since you were saying that you have plenty of hard drive space).

Before you get to step 3 you will be asked some trivial questions about your preferred language and your location, but you don't need a guide on what to do with them :)

You can go make yourself a cup of tea. When you are done with the tea you should have a dual booting computer. Restart it when Bubuntu tells you to and choose whether you want to boot with Windows or with Linux.

One more thing: if you have a tool with which you can resize the Windows partition safely before starting this whole process, let me know. In Vista for example such a tool is integrated. In XP there is commercial software like partition magic and whatnot. Then you get more control over how to use the space for Linux and you get an even more robust and fail safe system (it will already be much more stable than your windows installation).

---

### Post by sloggerkhan on 2008-09-10
For a full featured torrent gui with daemon to use on ubuntu I recommend the latest deluge from [http://deluge-torrent.org](http://deluge-torrent.org).

---

### Post by Samhain13 on 2008-09-11
> **t0p said:**
> This isn't true.  A key feature of Linux is its powerful command line.  Converting 5 files or 500 files can be equally easy.

5 < 500. :D

I do a lot of transcoding myself, via ffmpeg. Transcoding as many 500 files maybe doable but finding a suitable application to play the music files, without transcoding them, is optimal.

---

### Post by alyxx_on_phyer on 2008-09-11
thanks Idefix82, that helped out alot.

But how do I know how much space to give ubuntu? and how much to give to vista? 

my OS drive has 2.03gigs free of 11.07gigs of space but im not sure how much of that is vista and how much is free space?

---

### Post by Idefix82 on 2008-09-11
Hang on, are you saying that your entire hard drive is 11 gig out of which 2 are free? If I understood you correctly then you might be struggling with a dual boot system on such a hard drive, but I am sure I misunderstood you.

If you boot vista and click on your hard drive in the windows explorer then just press Alt+Enter and it will show you how much space is free and how much is occupied. Out of the free space you can then decide how much you want to grant to Ubuntu.
The latter decision depends on which system you will primarily use for which tasks. For example if you think that you will be watching films from the hard drive on Ubuntu then obviously you want to have a lot of space for that, similarly for Vista. Personally, I would recommend granting Linux as much space as possible because if you are anything like me (I installed Linux for the first time in my life a month ago) then you will never want to go back to Windows :-)

---

### Post by alyxx_on_phyer on 2008-09-12
no I have two drives in my lap top the other drive is 137gig's its the OS drive that only has 11gig's, the problem is I dont think I will have enough space to do the dualboot.

I just dont want to lose the stuff I have on the second drive ya know, but my OS drive only has 2gigs free space

---

### Post by jerome1232 on 2008-09-12
Yeah, I would shrink the partition on the other drive a bit, create a new partition in the free space that gets created and install Ubuntu to that, 11 GB will not fit 2 OS's on it.

---

### Post by Idefix82 on 2008-09-12
In that case you are sorted. Just boot with the Ubuntu CD, tell it to resize the 137 gig drive and install itself in the free space. If I remember correctly, that's the first option in the installation menu.

Or, even better, use the Vista partitioner to resize the 137gig partition and choose the manual installation option (last one in the list) when you install Ubuntu. In the free space create one SWAP partition (roughly double the size of your RAM), one boot partition (I would say 1 gig is enough for that) and one partition which you mount as / to which you allocate all the remaining space. Choose Ext3 as file systems for the boot and the / partition. If all this doesn't make sense now, it will once you start the installer.

---

### Post by airtonix on 2008-09-12
[rideburton56]("http://ubuntuforums.org/member.php?u=660289") : i would *highly* recomend you split your ubuntu install over three partitions ( irecommend this even in windows). 
* first partition is your swap drive, make it at least twice your phyiscal ram size (more if you think you might be installing more ram later on). This is important since the "hibernation/suspend/resume" situation requires the contents of physical ram to be saved to the harddrive effectivly as a dvd image. 
* second partition will be your root or system partition, what you would normally refer to as your C drive in windows, make this at least 10gb
* third partition will be your home folder where all the users who log into your system will have their personal files stored. make this the rest of the drive space.

So for a 40gb drive (which is really 39~) you have : 1: swap-drive (1g) 2: / (10g) 3: /home (29g~)

Reasoning behind splitting home from the root is that any reinstalls you do later on will not wipe out your personal files, configs for your desktop, icons, themes etc. Just remember : a) create users in same order each time, b) to keep same username on subsequent re-installs for each user.

[alyxx_on_phyer]("http://ubuntuforums.org/member.php?u=660687") : 
> So my questions are since I have 2 drives is it possable to install ubuntu over vista without having to format both drives?
and is there a burning software built in? if not will I still be able to use nero 8?
NOt sure what you mean by your first question, but your second has been addressed a few pages back, however I will summarise some options for you : 

* by default , nautilus will allow you to navigate to "burn:///" and create a data cd/dvd from files/folders dropped there. works pretty much like windows explorer does here, except proly more effcient.
* brasero, will operate pretty much like nero
* there is nero4linux, although i havent tried it. looks fairly tacky.
* k3b a fairly extensive disc burning suite
* you can get more options by searching through the [system -> admin -> synaptic package manager ].

You can create dvds of your movie files with devede, encoding time will be limited by your processor and memory.

Personally I wouldnt run any modern operating system as a desktop with less than 1gb of ram & a dedicated graphics card. but then i have many apps running at once, your situation could less drastic.

---

### Post by alyxx_on_phyer on 2008-09-12
ugh, sorry guys im even more confused now, I think I will just call a tech friend of mine and see if I can get her to do it. 

You guys have been great but I am just worried I will end up lossing everything ya know. 

So thanks again for your help.

---

