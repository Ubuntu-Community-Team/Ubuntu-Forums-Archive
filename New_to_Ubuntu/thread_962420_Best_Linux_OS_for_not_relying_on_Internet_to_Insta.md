---
title: "Best Linux OS for not relying on Internet to Install Everything"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-10-29
I was attacted to Ubuntu as a noob user as it was "easy to use" I find the installer's reliance on internet updates extreamly annoying as i am not on the internet.

I can download files on another pc and use them but i find Ubuntu "Not fit for purpose" for non-internet noob linux users.

Is Mandriva One likely to be a better choice of system or do all linux systems suffer from no reliable alternative to the windows setup.exe system of off-line installation?

---

### Post by Cypher on 2008-10-29
Being connected to the Internet to get the updates is NOT a necessity to use Ubuntu. You could just as easily install Ubuntu from the install CD and just leave it at that. You will find that a lot of Distro's are switching to the Internet (APT/YUM) scheme of delivery because it greatly eases the User experience and brings Linux more into the mainstream.

And in today's day and age the number of people who are not connected to the Internet at all times is significantly less than those with 24-hour connections. Now if you REALLY wanted to, you could definitely download the individual DEB files and get them to your Ubuntu installation and manually install it, but then you also have to worry about package dependencies and other things that programs like APT/YUM take care of for you..

---

### Post by dracayr on 2008-10-29
I don't know if you maybe downloaded the wrong files. But the .deb files are in principle the same as the .exe installer files in windows: a doubleclick and it installs. You can get them from [http://www.getdeb.net/](http://www.getdeb.net/)

dracayr

---

### Post by igknighted on 2008-10-29
Guys, it's the nvidia drivers that are the sticking point.  See his/her other threads to see what has gone on, but I suggested Mandriva because it comes with those drivers pre-installed.

@OP: Mandriva has always been known as one of, if not the easiest distro out there.  The ONLY reason I suggest it over Ubuntu in this case is that you won't have to worry about installing the nvidia driver.  Anything else you want to install will be just as touchy, but at least your drivers will be installed off the bat.

---

### Post by sharkster2007 on 2008-10-29
I have been trying the .deb method which i assume is similar to the windows .exe file system.

I refer to problems installing the Nvidia driver for a 6600GT and by the sounds of it any other hardware drivers required too. 

This is a total nightmare for a noob user its making me want to give up and buy 2gb RAM and a copy of Vista. 

This open-source vs restricted sistuation is not good for any new user, we just want easier set-ups, reliance (DRM and WPA) on the internet is one reason some of us are trying to leave windows in the first place.

I want to stop running Windows but I dont think, I have an alternative so looks like I am stuck with it. This is not the experience of Linux I expected and think I may well give up on it.

I thank all users for their help but as with a lot of other new noob linux users its time to run back to the windows hills, having fingers burned many times (spending days/weeks/months) just trying to get a 3D graphics card to work that works from the start on the other system (Maybe never to return again).

Thank you all for your help and support but at this time I feel no other option but return to windows the system I so wanted to rid myself of.

A crying shame really maybe I'll try again once this issue has been resolved. 

Thanks for trying to help me, But at this point in time I think its time for me to give up & call it a day I sick of wasting time on what should be their from first boot-up :-(

---

### Post by jerome1232 on 2008-10-29
Really the only difference is Ubuntu maintains  on online repository of it's software in an easy to install format, that won't stop you from installing .deb's or binary installers offline, same principle as .exe's.

---

### Post by igknighted on 2008-10-29
@OP... it's not hard, it's just different.  At some level, you have to come to grips with the fact that you are learning a completely new operating system, and there will be a steep learning curve.  It is in no way a drop-in replacement, nor should it be.  If you don't want to invest some serious time to learn, there is nothing wrong with that, but you should probably stick with windows.  It is a fine OS, I am using it right now myself.  But if you really want to learn linux, be ready to learn to do a lot of things different than you used to.

---

### Post by sharkster2007 on 2008-10-29
Thanks dracayr

If i regain the effort required to try again this will no doubt help me, I found other installations just as much hassle (Fedora, Suse, Debian) the only other one I found helpful was Linux Mint as it removed most of the installation problems for various programs, and made them "just work". 

The mint team seem to have set aside the "Open source" vs "restricted" issue and made things easier to use (Though the Nvidia driver is an issue with that too)

I may return I have given up on Linux many times before but I am always drawn back to Linux for some reason i think its the benevolence of its creators and helpfulness of its users I just wish the hardware side wasn't such a pain. 

(Not just the GFX, I could save to get a wireless router but no doubt this would become yet another problem to set-up and another major pain in the butt) . :-(

---

### Post by Duck2006 on 2008-10-29
Not sure if this will have the files that your looking for. You can get CD's or DVD's that have all the repo's on them for updatting of-line.

[http://ubuntuforums.org/showthread.php?t=352460&highlight=updating+off+line](http://ubuntuforums.org/showthread.php?t=352460&highlight=updating+off+line)

---

### Post by The Cog on 2008-10-29
The package you need is called nvidia-glx-new. Perhaps you can get a friend with internet access to download it for you.
[http://packages.ubuntu.com/hardy/i386/nvidia-glx-new/download](http://packages.ubuntu.com/hardy/i386/nvidia-glx-new/download)

---

### Post by sharkster2007 on 2008-10-29
Thanks duck2006

I thank you for your help on this matter but I am ready to give up now, maybe I'll return to the Linux scene once opensource and easier to install versions of NVidia/ATi on Ubuntu are made available.

I won't give up on linux, I was one of the "Amiga Surviors" who modded our machines rather than give in to windows, a fate we eventually had to accept to continue using computers.

We may well have fought hard to stand by our systems but we lost in the end. I have gained great respect for Linux and its founders, users and comunity and will eventually return. 

Until then I will have to settle for running open-source windows versions of linux programs and advocating them, I will continue to advocate the use of open-source programs in windows.

"Some of the Windows users, are on your side probably more than you realise, we just are unable to adapt our skills to your systems as yet"

Sharkster2007 "Ex-Amiga Survivor"

---

### Post by sharkster2007 on 2008-10-29
Thanks cog

I have access to two PC's one is on the internet (Not mine, doesn't want to install Linux) and the second one is mine (not on the internet) a custom built 2.4ghz Pentium 4, 1gb Ram, 3 HHD's 160gb,80gb,160gb and can dual boot between Windows XP & Ubuntu Linux. 

I can ferry files from one to the other via usb stick and have tried various methods all have failed (prob due to my lack of knowledge of terminal commands).

Thanks for your help and the link though

---

### Post by snowpine on 2008-10-29
You need Apt On CD:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Sef on 2008-10-29
> You need Apt On CD:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)It is available in the Universe repository.   Applications > Add/Remove > SHOW: 'All Available Applications' > SEARCH: aptoncd > click on box next to aptoncd > click apply changes > click apply > close

---

### Post by sharkster2007 on 2008-10-29
Thanks Sef

I have no internet on my PC though, this seems to be another problem adding to a previous one, I think i'll try Mandriva Linux one 2009 out, as I like Linux Mint a lot of the setting stuff up was done already "Open-source" Or not it "just worked".

Which is what I belive most linux noobs are looking for, we want to be able to learn and use a system without having to patch it dozens of times, It would be nice to get to know it before having to tinker with command lines straight off.

---

### Post by Titan8990 on 2008-10-29
> I have no internet on my PC though


How do you live?

---

### Post by sharkster2007 on 2008-10-29
> **Titan8990 said:**
> How do you live?

I have access to two PC's one is on the internet (Not mine, doesn't want to install Linux) and the second one is mine (not on the internet) a custom built 2.4ghz Pentium 4, 1gb Ram, 3 HHD's 160gb,80gb,160gb and can dual boot between Windows XP & Ubuntu Linux.

---

### Post by sharkster2007 on 2008-10-29
This has been stated many times clearly on all posts by myself, both PC's are in the same building LMAO

---

### Post by knix on 2008-10-29
I also highly recommend Mandriva 0ne. It is an excellent distro if you want all your hardware to work out of the box. Make sure you do not get Mandriva Free, as it is GNU only, and does not have codecs, drives,etc. bundled with.
One disadvantage to Mandriva is that it is very difficult to download rpms (the Mandriva package format) through a browser.
If you want to install packages without a local connection, everything in the repos is on packages.ubuntu.com.
If you want to have everything on disc,availabel, try debian (Lenny would be better than Etch). That said, you would still have to download restricted drivers from packages.debian.org.
Once you install nvidia drivers from a packages, you would need to config X to use them. The simplest way of doing so is to run "sudo nvida-xconfig" in the terminal.

Edit: here's omething cool for Ubuntu: Kerix.
It's designed for downloading packages on another computer (even Windows). It's basically like the old nonetdebs.
Homepage here:[http://keryx.betaserver.org/]("http://keryx.betaserver.org/")
howto here:[http://keryx.betaserver.org/forum/index.php/topic,5.0.html]("http://keryx.betaserver.org/forum/index.php/topic,5.0.html")

---

### Post by sharkster2007 on 2008-10-29
Thank you igknighted , Knix and the others

I have now migrated to Mandriva Linux One 2009, I find it's hardware support excellent, just what I wanted. 

Now I can explore linux without that blasted 3D effects prob (It even worked from the livecd before I installed it).

I now dual boot Windows Xp SP3 and Linux Mandriva Linux One 2009 and I am very pleased with my new Linux distro.  I did think of abandoning Linux full stop, but as I said before something keeps bringing me back to it. 

Thanks for the command line help and the Mandriva Linux One suggestion I am over the moon and still using Linux too.

Thanks to all who helped (& tried to help me) happy Linux computing to you all

Best wishes Sharkster2007

---

### Post by sharkster2007 on 2008-10-31
Hello everyone

Well at least that migration showed me it can work on my PC, I have returned with Ubuntu 8.10 the drivers are in place and installed, all dependancies are satisfied.

But the System>Administration>Hardware Drivers will not activate my Nvidia 173 drivers.

Anybody know a way to manually activate them (maybe a command line)?

---

### Post by sharkster2007 on 2008-11-01
Greyarea2 has the internet connected solution [http://ubuntuforums.org/showthread.php?t=965741]("http://ubuntuforums.org/showthread.php?t=965741")
and now I've added my sharkster2007 manual one for none internet connected users.

New Sharkster2007 (Manual Solution)
06/11/08 UPDATE: [http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038)

New thread contains better manual details of 173 & 177 Nvidia driver set-up, Activation, Compiz & Nvidia GUI set ups.

Hope it helps with the Nvidia driver problems ;-)

---

### Post by RealG187 on 2008-11-01
[http://ubuntuforums.org/showthread.php?t=946764](http://ubuntuforums.org/showthread.php?t=946764)

See my guide there.

The whole software internet install thing annoys me too. So I looked around and asked on forums (here and Kubuntu forums, I really have to thank Rog131 from Kubuntu forums, his thread is what makes up 90% of mine, I just had to add how to get the packages. Also i will upload any packages you need if you ask!) and made a guide based on this info!

---

### Post by steveneddy on 2008-11-01
There are links in my sig to make and/or buy a repository DVD for those without a good or fast internet connection.

---

### Post by RealG187 on 2008-11-01
Well depends if you find it worth it to download lots of data at once and be done, or download only what you need (at the time)

Your method is handy if you have good internet, just not on the computer you need to install on (or only want to download things once). Mine is good if you want to transfer a few programs or archive

---

