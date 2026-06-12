---
title: "new to ubuntu (12:04) and many things dont seem to work"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by gnowair on 2014-06-09
install sort of went well. although was'nt great.
many errors but then eventual restart sorted it out.
many letters (fonts) dont always appear correctly, almost nothing installs well (and most installs are too difficult for me anyhow), constant error code 1 (something to do with packaging?)
firefox constantly freezing up (i thought that was only windows?)
none of my media players can show videos. the inbuilt media player shows a frozen first frame, and vlc only shows in task bar but dopsnt actually appear to load at all.

cant get fullscreen in firefox, and perhaps not in vlc either.
there are many instructions online with some of my issues, but it makes no sense to a bigginer, like i need to be in a secret society to understand the lingo.
i get the basic ideas of using terminal, however most instructions dont lead you into it very well as if your already meant to know it all already.

so far am really dissapointed, and its becoming a little soul-destroying right now.

please do feel free to ask me for more relevant info.
OH! i just tried installing furious iso, and again,mgetting notice stating install fialed due to something about a failed package or something

---

### Post by Bucky Ball on 2014-06-09
What exactly went wrong with the install? Can you remember any error messages?

How are you trying to install things? Best to use the Software Centre. That is not difficult at all. Just search and install. Have you got the correct video card drivers installed? 

Please do an update and then install ubuntu-restricted-extras and restart after running these three commands in a terminal, one at a time, hitting 'enter' after each. Post any errors it returns.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

After the update, check 'Additional Drivers' (or could be 'Hardware Drivers' in your release) and see if you are offered anything.

No secret society, but yes, can take a bit of time and an attitude shift to get the hang if coming from Windows ... ;)

---

### Post by gnowair on 2014-06-09
firefox goes dark and freezes up within as little as ten seconds.j
ust tried google chrome (which i doint particularly like,but...) it wont install, and isnt showing in recent list either. 
in fact i havnt a clue where the installer will be (firefox folder).

even the software centre froze up!!!!

i havnt gotten ONE single device running properly. and EVERYTHING gives me an error when i try to install.
i really want to like ubuntu (my son was a disigner for it a few years ago) but if this is my first day on it,it has been soul destroying. i just wanna give up. ruined a whole day and made everything worthless and un-done.

---

### Post by Bucky Ball on 2014-06-09
Chromium Browser is what you want and it is in Software Centre, but with things going this badly, I wouldn't bother; sounds like something went wrong during the install, perhaps, but you provide no details of any error messages and do not identify why the 'install went sort of well' or the 'many errors', as requested. 

Open a terminal and issue the commands I gave in my previous post. Report back any errors, please. I understand your frustration ...

---

### Post by stalkingwolf on 2014-06-09
how did you install? DVD or usb?  i have had the experience of a cd/dvd not liking a particular media but not so much in the last couple years.  Is this a new or older computer?
Could the dvd rom be dirty or getting old and flaky?

With so many questions and no information.......

---

### Post by gnowair on 2014-06-09
software centre not helpoful at all. fails everytime.
google chrome wontn install, and software centre stuck in a loop between installing it, and trying to repair "package" missing, or something.
absolutely nothing has installed all day. soulseek wont connect, media player has played once succesfully,vlc just wont work, dj mixxx cant run audto dj, firefox wont run.
only thing i can do is try to somehow install the fesh copy of recent ubuntu i did manage to get.
however, the way this is going, i reaslly dont think that might be a good idea. who knows.
so much conflicting advise everywhere, use ppa, use re[ositories, do,dont,dont,do.....
my brains turning into ozze now.
i just wanted away from the bull... of windows,and at the moment its just worse.
incidsently,been using that command today already.... i still fail to see what it did then. honest mate.
will try it once more,even though i havnt a clue exactly what its meant todo.ok,will try......,.

thank you though. i really do appreciate. just been a little distressed here mate.


right,let me see..... dam font still a bit weird.....
eh, terminalhas gotten to "...reading package lists... done" and thats it. that right?

---

### Post by 3rdalbum on 2014-06-09
Ubuntu 12.04 is rather old now. Although it is still supported, I would recommend you download Ubuntu 14.04 instead and try using that.

14.04 is the latest version. If your computer or any of the hardware you are trying to use was made after April 2012 it might not work or might not work well with Ubuntu 12.04, but probably will with 14.04.

Also, if you have problems with 14.04 please describe one problem at a time, in as much detail as possible (for instance, instead of "It said there was a package error or something" you would say "As I tried to install VLC from Ubuntu Software Center, an error message told me there was a held package").

Try not to get discouraged; Ubuntu actually isn't difficult to use, it's just very different to anything you've used before. It does sound like you have had extraordinary problems; possibly your CD was scratched and caused Ubuntu to not install properly. Most people don't have these kinds of problems. I also understand you when you say there is a lot of conflicting advice out there - you're correct, there is, but try to focus on advice given by people who have been here for several years. And only take recent advice - for Ubuntu 14.04, anything said before 2014 could be irrelevant or completely wrong. A bit like trying to follow Windows 95 instructions on Windows 7.

---

### Post by gnowair on 2014-06-09
i installed from a dvd.
and now,also have a very up to date ubuntu iso, 
to attempt fresh install. 
but yes, very frtustrating, i havnt done  a useful peice of work all day.

---

### Post by Bucky Ball on 2014-06-09
Yep, but run all three commands in my first post and follow the other stuff there. Report any errors. 

What are the specs of the machine, model and make? RAM and CPU?

---

### Post by Navneet_Kumar on 2014-06-09
i think you should freshly install the os once more.......formatting the drive..........and then hope for the best.......:D

---

### Post by Bucky Ball on 2014-06-09
> **Navneet_Kumar said:**
> i think you should freshly install the os once more.......formatting the drive..........and then hope for the best.......:D

Possibly best as sounds like something was well screwed up during install. Without knowing exactly how you went about installing or what errors it threw, hard to tell what, but looking at what's happening now, something appears to be drastically wrong. 

I understand it's nightmarish, but neither was Windows conquered in a day! You are trying to get your head around an alien OS. Deep breath. ;)

Please let us know how you intend to install or how you tried to install last time ... or both. If you can let us know how you went about it to start we might be able to spot what went wrong, if anything.

---

### Post by gnowair on 2014-06-09
i think thats my best bet there, to install but with 14.04,
so,i'll have to jump out to shops and get a dvd to put the iso onto? or is there a getround for that? probably not.

to recap on contantly failed installations, every attempt gave me a notice regarding failed, or missing, or corrupt pakcages, and an error code (1).
and none of the attempted fixes run by ubuntu mananged to help at all. incidently many of the attempts made by ubuntu also failed sadly to download various update/upgrades.

and its not difficult to imagine that 12.04 may well be too old to handle current state of the game.
thanx so far!

---

### Post by buzzingrobot on 2014-06-09
> **gnowair said:**
> install sort of went well. although was'nt great.
many errors but then eventual restart sorted it out.


That's a clue, because the install should be, and typically is, error free. Do you recall the errors?

Also, what happens when you select the "Try Ubuntu" option?

---

### Post by Bucky Ball on 2014-06-09
12.04 LTS is supported until April 2015, is well current and rock solid. From what you've said, sounds like a dodgy burn to DVD. It happens. If you can boot from that DVD and choose the option 'Check the disk for defects' you'll soon find out. My guess is it's that simple. :-k

You can create a LiveUSB rather than use a DVD. That is another option for installing.

---

### Post by ajgreeny on 2014-06-09
> **Bucky Ball said:**
> 12.04 LTS is supported until April 2015, is well current and rock solid. From what you've said, sounds like a dodgy burn to DVD. It happens. If you can boot from that DVD and choose the option 'Check the disk for defects' you'll soon find out. My guess is it's that simple. :-k

You can create a Live USB rather than use a DVD. That is another option for installing.
This would be my choice.

It definitely sounds as if your burned DVD may have been bad, and that is certainly is more likely than a bad transfer to USB using either startup-disk-creator or unetbootin, and you can also then simply reuse the USB for any data you want.

You have still not said what your hardware is, ie the CPU, RAM, and graphic card, as they can make life a lot more easy, or difficult depending on the makes and sizes.

---

### Post by gnowair on 2014-06-09
> **Bucky Ball said:**
> Yep, but run all three commands in my first post and follow the other stuff there. Report any errors. 

What are the specs of the machine, model and make? RAM and CPU?



ubuntu 12.04 LTS
memory: 3.8 GiB
graphics: "unkown"
OS type 64-bit (which i wasnt aware of! ah ha! maybe the issue? i installed 32-bit)
disk: 241.8 GB

oh,and processor: Pentium(R) Dual-Core CPU T4200 @ 2.00GHz × 2

---

### Post by Bucky Ball on 2014-06-09
Shouldn't be a problem with the hardware, then. Try another burn or USB. You could try this to make a bootable install USB using Windows:

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Also, 32bit should be fine, although 64bit is advisable to get the most from your hardware.

I'd get the ISO via a torrent, if you are familiar with using them:

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Most reliable way as checked on way through.

---

### Post by gnowair on 2014-06-09
ok, let me see. i only have a 500gb iomega memory drive. would it be possible to do from it?

oh,and cant use torrents as i cant get anything to install useably

no,for now,on this set up, there's no chance of setting up a usb boot. ubuntu software centre etc cant find it 
"Archive:  /tmp/Universal-USB-Installer-1.9.5.3.exe
[/tmp/Universal-USB-Installer-1.9.5.3.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /tmp/Universal-USB-Installer-1.9.5.3.exe or
          /tmp/Universal-USB-Installer-1.9.5.3.exe.zip, and cannot find /tmp/Universal-USB-Installer-1.9.5.3.exe.ZIP, period."

and cant get the usb creator by getting it directly thru the software centre, it gives a totally different failnotice from trying to grab iot from the link you gave me. to do with packages again....

---

### Post by Vladlenin5000 on 2014-06-09
How many times more should we tell you that you have a completely broken installation? How many times times more should we say to download _using another computer_ because that one as it is now is BROKEN?

---

### Post by buzzingrobot on 2014-06-09
> **gnowair said:**
> .../Universal-USB-Installer-1.9.5.3.exe


That's a Windows program.

(500 gb is easily more than enough.)

---

### Post by gnowair on 2014-06-09
it needs to reformat my iomega meory drive, so i cant do it at all just now. it would mean wiping out all of my work before i can get it on this laptop.
the above terminal commands, am not sure if anything changed after trying that.
 if only there was a way, as i can with windows,create or mount a virtual disc! but then,how can i install it!

---

### Post by buzzingrobot on 2014-06-09
Well, again, it's unclear exactly what steps you've taken.

In any case, as mentioned, it certainly seems like the install was broken.  In such cases, the only real alternative is to do a fresh installation.

When you boot a working ISO image, the initial display will offer an option to install Ubuntu or to try Ubuntu. The 'Try Ubuntu' option runs Ubuntu in so-called Live Mode, meaning it runs it off the ISO image on the DVD or USB stick and does not touch the hard drive. (It runs easonably fast off a USB, pretty slow off a DVD.)  I recommend you choose that option because it's a good way to check for hardware problems.  If everything seems to work, go on and do the install.

---

### Post by Vladlenin5000 on 2014-06-09
Is you "iomega memory drive" an external USB HDD? With 500GB it probably is... If so it won't work, don't bother. What you need is a common USB flash memory with at least 2GB (higher is OK too but some 32 or 64GB ones might not work) if you intend to (re)install your system using the USB method. Of course, you can use a DVD if the farmer method is too much for you (it probably is...), just make sure the downloaded ISO file isn't corrupt before burning - you need the same care for the USB method, obviously. THAT'S WHY several people recommended TORRENT. Again, obviously, you should do it from another computer. 

The commands were for checking only. No changes.

> if only there was a way, as i can with windows,create or mount a virtual disc! but then,how can i install it!

There is, it's even easier than in Windows but that's not what you want to do. What you "want" to do is reinstall and for that you need proper installation media. The sooner you understand this the better. You'll be wasting your time (and ours) doing otherwise.

---

### Post by gnowair on 2014-06-09
> **Vladlenin5000 said:**
> How many times more should we tell you that you have a completely broken installation? How many times times more should we say to download _using another computer_ because that one as it is now is BROKEN?

HOW many times did I have to say to YOU that i couldnt do any of the above? HOW many?
if i could physically go get a dvd, dont you think i would have?
your hiding behind being a tehcy here mate, but your playing a really nasty head-game that implies that the person having a problem IS the problem. thats rather abusive mate.

am just trying to fix something that shudnt have been broken in the first place, namely my laptop by ububtus inability to copy to disc (it is meant to be free after all,so shouyld be able to take that), and my having to deal with all the rubbish i've been dealing with all day with no work done,no chance to be with family, 
is this what i came here for? for that above message?

i deliberately said in a recently previous message, to all that took any bother to read, that i will not reformat my memory box as yet due to NEEDING the files apon it for working, 

i have no way to get the rather large distance to any form of shop or workshop (we dont all drive cars, or want to)
i cant run from my memory drive because A) ubuntu has to reformat it first (not mentioned in ANY of the info promoting it) which is a bit naff since it can read it and write in it (windows 7, iomega 500gb memory drive),
and ubuntu fails each time i try to install ANYTHING!
hence all of the above help, sadly, has had no possible way to be of any effect whatsoever, and that guy in above message is hitting it with the big-billydaddy-balls?

i came here to learn something so i could enjoy getting away from windows, and found i had a really stinkingly bad day, and ended up being as good as shouted as as if i were a jouvenile fool.

thanx ubuntu, really made my day!
will be taking a copy of these pages before you delete and block me, as i imagine such an angry nasty forum moderator would.

---

### Post by ajgreeny on 2014-06-09
You are obviously managing to post to this forum on a computer at present.

Is that computer a Ubuntu machine (never mind for the moment whether or not the OS is broken)?

If it is, then you already have a torrent client (transmission) and a disk burner (brasero) which you could try to use to download and then burn a new .iso file. It must be worth trying that as you will not need to download anything else to do the job, and with luck you may get a new good image file (the .iso image) and a good burn of that image to DVD or USB.  For a DVD make sure you burn the image at as slow a speed as is possible on your hardware.

 If you don't have an available USB that is big enough, but perhaps have a digital camera with a large enough memory card, and you also have a card reader, you could also use that; it will work just like a normal memory stick.

If you don't have any possible way to carry out any of these or other posters suggestions, and do not want to, or can not get a new blank DVD or USB flash drive, I regret that there is no way I or anybody else can help you.  We try to do our best, but we can not come up with ways to do things that need hardware that you either don't have, or can not get hold of in any way.

---

### Post by Vladlenin5000 on 2014-06-09
Look mate, we're volunteers here. Nobody here gets even a dime for the time we're wasting were with such trivialities so, first and foremost, **please tone down your comments**. It's NOT OUR FAULT your installation went wrong in the first place. Whether the problem was you, your computer's peculiarities, the climate change, north-American butterflies migration, whatever... is a moot point. What matters is you currently have an unusable OS and any attempt to fix it is probably a (huge) waste of time. You need to install again, PERIOD. How you're going to do is UP TO YOU but you need to. 

This are the requirements for the installation:
1. A correctly downloaded ISO, preferably of the latest version 14.04;
2. A blank DVD -or- a USB pen (NOT a USB hard drive -> It won't work and then you'll be back here with another rant)

If you don't have any of the #2 options - honestly - that's NOT my problem. However, you already have one DVD with 12.04, don't you? I mean the one you already used to that (botched) installation... Now, if you don't want/can't do as suggested many times before - download using torrent instead of direct download in order to avoid issues - please at least TEST the one you already have:

Boot with it and press any key when you see this image
[IMG]http://img829.imageshack.us/img829/3509/dgfdgrunningoraclevmvir.png[/IMG]

Then, select the option to verify the disk from the menu. There are two possible results, OK or fail.
OK -> Proceed to reinstall with the same media*.
Fail -> Trow that DVD to the trash, get another, a USB, whatever...

* Open another thread with the errors you experienced with the new installation, if any. Then - and only then - someone can help you.

---

### Post by buzzingrobot on 2014-06-09
> **gnowair said:**
> 

am just trying to fix something that shudnt have been broken in the first place, namely my laptop by ububtus inability to copy to disc...

That's confusing, so let me ask:

Are you working on a Windows machine trying to add Ubuntu so you can dual boot both operating systems?

Are you having problems burning the Ubuntu ISO to a DVD or USB stick?  If so, have you read and followed the advice here:  [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop).  That page offers download links and instructions for correctly burning an ISO in Windows, Ubuntu or OS X. (The ISO image cannot be *copied* as if it were an ordinary file.)

> i deliberately said in a recently previous message, to all that took any bother to read, that i will not reformat my memory box as yet due to NEEDING the files apon it for working...

"memory box" is the 500 GB Iomage drive?  An external USB drive? Is that the target for the Ubuntu install?  If so, you will need to adjust your BIOS to boot off of it, after you have installed Ubuntu.

By the way, the Ubuntu installer formats the partitions on which it will be installed. 

Not to belabor the point, but if, as you say, you saw many errors during the install attempt, the install is broken and cannot be repaired in place. (Nor could we help you repair it, even if it could be repaired, because you have not told us anything specific about what is or is not working correctly.)  Typically, if the installer encounters an error, it stops altogether.  As mentioned, if you could tell us the nature or, ideally, the wording of the error messages, we might be able to deduce what went wrong. (You have not identified the video card; unsupported or unusual video cards can be problems.)

At this point, your only course of action is to correctly burn a new ISO install image and do another installation.

---

### Post by oldos2er on 2014-06-09
Please keep replies on topic. If you come across an objectionable post, use the Report Post button to notify staff.

---

### Post by Bucky Ball on 2014-06-11
> **gnowair said:**
> 
 if only there was a way, as i can with windows,create or mount a virtual disc! but then,how can i install it!

Yes, you can do that on a working Win install. You can also do it on a working Ubuntu install, but you don't have a working Ubuntu install.

I suggest procuring a blank DVD or a 4Gb USB stick. Cheap and readily available. Borrow a USB or scrounge a blank DVD from a friend/relative/neighbour? Maybe then we can actually get somewhere with helping you get a working install. At the moment we seem to be going in circles. You don't want to/can't format your iomega because it has data on in so dead end. Forget that. Move on.

PS: And please, can we take a deep breath, calm down and keep it civil as this thread is now starting to teeter on the brink of hostility. As oldoser2 has suggested, please keep it on topic (rather than turning the thread into a slanging session - not acceptable here). Then we might start getting some way towards a resolution. Twenty nine posts in and not much has been achieved ... bar a heap of frustration. Thanks.

---

### Post by kansasnoob on 2014-06-11
> **Bucky Ball said:**
> 12.04 LTS is supported until April 2015, is well current and rock solid. From what you've said, sounds like a dodgy burn to DVD. It happens. If you can boot from that DVD and choose the option 'Check the disk for defects' you'll soon find out. My guess is it's that simple. :-k

You can create a LiveUSB rather than use a DVD. That is another option for installing.

Precise (12.04) is supported until April 2017:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I prefer using the [archived 12.04.1 images]("http://old-releases.ubuntu.com/releases/precise/") for my Precise installs/reinstalls due to the [LTS hardware enablement]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") policy.

---

### Post by kansasnoob on 2014-06-11
> **gnowair said:**
> ubuntu 12.04 LTS
memory: 3.8 GiB
**[COLOR="#FF0000"]graphics: "unkown"[/COLOR]**
OS type 64-bit (which i wasnt aware of! ah ha! maybe the issue? i installed 32-bit)
disk: 241.8 GB

oh,and processor: Pentium(R) Dual-Core CPU T4200 @ 2.00GHz × 2

That graphics info concerns me. What is the output of:

```
lspci | grep VGA
```

If that provides no info then maybe post the exact make and model info of the laptop.

---

### Post by Bucky Ball on 2014-06-11
> **kansasnoob said:**
> Precise (12.04) is supported until April 2017:



Correct. My mistake. Thanks. ;)

---

### Post by kansasnoob on 2014-06-11
> **Bucky Ball said:**
> Correct. My mistake. Thanks. ;)

No thanks needed, I make worse mistakes than that every hour :)

---

### Post by jimmyh1972 on 2014-06-11
Hi gnowair - first off all in order to install the proper OS open your terminal type:
lshw -short
copy it & post is here so we can see your hardware specifications.
after that we can advice you what flavor of Ubuntu to install.
p.s - if I were you I would install the 1404 version

---

### Post by craig10x on 2014-06-11
I agree...install the 14.04 version and 64 bit if that is what your system runs...sounds like your system should be able to handle the main edition (unity) of ubuntu without any problems...the most mine ever uses is about 1 gb (and starts off at about 600 mb on idle)...

---

