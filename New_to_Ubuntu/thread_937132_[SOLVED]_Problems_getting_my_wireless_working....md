---
title: "[SOLVED] Problems getting my wireless working..."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
So about a week ago, I downloaded Ubuntu Studio. About 3 or 4 days ago, I finally configured my MacBook Pro (Core 2 Duo; 2nd generation) to run Windows XP, Mac OS X Leopard, AND Ubuntu Studio (most of that time was spent correcting User Error [READ: My Error]). My purpose for a Triple Boot on a MBP is so I could store/manage my music/videos/other media using Ubuntu (although now I think I'll be using it for other things as well) while being able to access said media using Windows XP or Mac OS X (I use both equally for the most part).

So there's my history. Anyhow, despite how (surprisingly) intuitive Ubuntu Studio is, I cannot for-the-life-of-me figure out how to get my wireless to work! A lot of time has been spent jumping back and forth between Ubuntu and Windows (find the answer in Windows, try it in Ubuntu, realize I need a new answer....Repeat). I've found three possible solutions:

1. MadWifi driver - I've tried installing MadWifi. However, in trying to install this, you need Build-Essential. In trying to install Build-Essential, I've downloaded and installed a ton of different "lib"s and "dev"s (not the best solution, I know) and have been stuck on one where "libstdc++6-4.2-dev" has a "g++" dependency and "g++" has a "libstdc++6-4.2-dev" dependency.

2. NDiswrapper - while I haven't completely tried this one, it seems to require the use of Build-Essential...and, per the problem in #1, *whines* I don't wanna use Build-Essential!

3. ath9k - I have successfully installed this (I think), yet I'm not all that sure where to look for my wireless now...additionally, I hear it's unstable. From what I understand, NetworkManager is the standard for wireless connections, but I'm not entirely sure I have this installed (I have read that it's standard in Ubuntu 8.04, but I have Ubuntu **Studio** 8.04 and have not been able to find any program within that's congruent with what I understand NetworkManager to actually be). In trying to install NetworkManager, I run into a ton of dependencies which I don't want to rectify unless I know for sure that I don't have NetworkManager.

So after even **more** history (trying to give the whole story...sorry), I have no solution. I need wireless, as managing music can be a pain without automatic downloading of ID3 Tag Information and I don't have access to internet outside of a wireless connection.

I am running the 2.6.24-19-generic kernel as well as kernel 2.6.24-19-rt, if that makes any difference (I'm not sure) and have tried upgrading to 2.6.24-20 or -21...but who knows how to do that (not I).

Help? :D

P.S. As a side note, because I have no internet whatsoever in Ubuntu, please don't recommend I use any of the agents used for downloading packages (Aptitude and the like). I've gotten to know my way around packages.ubuntu.org, so just let me know what I need to download from there.

---

### Post by shifty_powers on 2008-10-03
do you not have access to a wired connection? if you could connect via an ethernet cable, your life would be sooooo much easier...

edit: do you have access to another pc with a good internet connection?

then have a look at apt on cd

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

> Get APT anywhere

Have you ever felt that there is no life without APT? Well, if you'd suddenly lost conection to the internet, how would you install new packages? What about dependencies? You've just finished installing Ubuntu and configured it to a rad look, with all your favorite applications? For some reason you now have to re-install it? Feel like you have to download all of your favorite programs again? What? You've already forgotten which packages you had dowloaded before?
What is APTonCD?

APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection.
With APTonCD you be able to...

Backup
    Backup all downloaded packages (via apt-get, aptitude and synaptic) to restore later.
Transport
    Take with you all your favorite packages, in a removable repository where you can install then all on anytime, anytime.
Download
    Get an entire repository, or a specifc section. Simply point-and-click, and in few time you'll have an CD(s) or DVD(s) with entire main, restricted, universe, multiverse, contrib, etc.
Share
    Share your packages with your friends without Internet conection. Also, send a meta-package for him to install the same set of packages that you have. 

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
> **shifty_powers said:**
> do you not have access to a wired connection? if you could connect via an ethernet cable, your life would be sooooo much easier...

edit: do you have access to another pc with a good internet connection?

then have a look at apt on cd

The only wired connection I have access to has, at present, no monitor (hence the jumping back and forth). Otherwise, this "APT On CD" you speak of could do me wonders.

---

### Post by shifty_powers on 2008-10-03
could you not take the ethernet cable and plug it into the laptop? maybe i am missing something i don't know, can't see your set up.

and i'm glad to help. give us a shout with anything else :D

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
I suppose that bit of info may be helpful. Sadly, I can't connect to my laptop with the wired. I live on a college campus, and they've set up their wired network so that only certain ports are turned on and those ports can only be used by the computer registered to it. Really stupid, but I don't have much control over that as they refuse to activate a second port in our apartment.

---

### Post by shifty_powers on 2008-10-03
pfft. would this be in usa by any chance?

heh amazes me what they get away with in america....

(heh, don't get me wrong, i like usa, but your isp's are a bit crappy tbh, although i know college is different...)

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
> **shifty_powers said:**
> pfft. would this be in usa by any chance?

heh amazes me what they get away with in america....

(heh, don't get me wrong, i like usa, but your isp's are a bit crappy tbh, although i know college is different...)

Yes, yes and yes. :p This place is particularly anal about wired connections...but whatevah.

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
Here's something I hadn't thought to ask...I might be able to look this up but I figured I'd just ask instead.

Does APT take care of all dependencies as well? In other words, if you have a "X.deb" and it has dependencies on "libY" and "libZ," will it in turn download libY and libZ for you when you APT-GET X.deb? Or are these additional apt-get commands you would have to plug in?

This would solve the Build-Essential issue I've been having (I assume). If I didn't have to trace down every dependency error I get, I would have to do a lot less jumping back and forth.

---

### Post by shifty_powers on 2008-10-03
if you want, you can use apt on cd to make an image (dvd would be a good idea for that, possibly dual layer), of the entire repository, giving you every dependence ever :D

you better have the bandwidth and time for it mind :D

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
> **shifty_powers said:**
> if you want, you can use apt on cd to make an image (dvd would be a good idea for that, possibly dual layer), of the entire repository, giving you every dependence ever :D

you better have the bandwidth and time for it mind :D

Intriguing...

I find that the most frustrating part about getting wireless working is that many tutorials assume you have some sort of internet connection already (apt-get and all that...not that it's a bad assumption to make, but it doesn't fit my current predicament). However, that would solve the problem entirely. A little time consuming, but still...

Any alternate suggestions? The wireless I have access to using Mac is pretty stellar, so the above is viable. However, if there were some way to anticipate dependencies before I pull up Ubuntu-with-no-internet, that may be more practical.

---

### Post by shifty_powers on 2008-10-03
you'll end up in dependency hell, i warn you...

[http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)

will give you the dependencies for each package, but many are recursive....

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
> **shifty_powers said:**
> you'll end up in dependency hell, i warn you...

[http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)

will give you the dependencies for each package, but many are recursive....

Believe me, I'm already there. :( 

You do make a valid point though. And without internet Ubuntu-side, this option would probably be helpful anytime I reinstall. I'll try the APT on CD suggestion you made tonight and let you know how it all went down. Thanks a ton!

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
I think I misunderstood before...I just re-read the APTonCD website. I thought this was a program which interfaced with the Ubuntu repositories while using different OS's. Isn't this an Ubuntu product? If that's the case, I can't use it because I don't have wireless access (or internet access at all) on my Ubuntu partition...only my Mac and Windows partition.

---

### Post by shifty_powers on 2008-10-03
sorry about that...

[http://ph.ubuntuforums.com/showthread.php?t=869422](http://ph.ubuntuforums.com/showthread.php?t=869422)

could the perfect solution for you though...

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
Yup! That's exactly what I'm looking for! Only the file is corrupted or password protected or something. I get the feeling that the creator posted it and then "peaced out." It won't open for me...Leopard tells me something about a Permission Error.

I was so excited too! I'm currently hunting for something similar to it, though.

---

### Post by Christmas on 2008-10-03
So you only have access to Internet from within Windows right? This should work, although I've never tried it. You can download all the needed packages, including dependencies, from [http://packages.ubuntu.com/](http://packages.ubuntu.com/hardy/) (choose your Ubuntu version), then write them on a CD or DVD and install them in Ubuntu using:
```
sudo dpkg -i full_package_name.deb
```
Make sure to in the directory where you have your packages (e.g. /media/cdrom0 or so). You start with the ones which don't depend on other packages.

I don't think you'll need build-essential though, it's a meta package that includes, among others, the C/C++ compiler, for compiling source code. I'm not very sure exactly what package you'll have to install in order to make your wireless connection work (I think it should have been detected by default), but maybe someone else with a Mac can help you there.

Have a look at these two links too:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by Tu1J4kXk8NUhMz on 2008-10-04
Just wanted to let you know that I'm pretty sure I've found a solution/workaround. I will be creating a virtual machine using Parallels on Mac, then installing Ubuntu Studio on it. From there, I will be using APTonCD (Thanks again for all the help, shifty_powers) to load everything onto a CD that I need and then dump the APTonCD Deb file into my physical Ubuntu partition. HOPEFULLY this will all work...but I'll let you know (I'm sure you anxiously wait on the edge of your seat) 8-[

---

### Post by shifty_powers on 2008-10-04
that was something i came across, but i suggested the link i posted first as i seemed simpler.

i'll keep my fingers crossed and hope it will all work for you :D

---

### Post by Tu1J4kXk8NUhMz on 2008-10-09
> **shifty_powers said:**
> that was something i came across, but i suggested the link i posted first as i seemed simpler.

i'll keep my fingers crossed and hope it will all work for you :D

SHE WORKS! It took me a while to get some time set aside to fix things, but the wireless card is now recognized! Thanks!

---

### Post by anewguy on 2008-10-09
There is something important that needs to be mentioned here concerning ndiswrapper.  While on a MAC you may need to compile it (I don't know as I don't use a MAC), there are OLD posts out there telling everyone to download the source and compile it, and yes that does require the build-essential package.  However, if you are/have installed from a Livecd, ndiswrapper is on that CD and you DO NOT need to do the download source and compile thing.  Just put the CD in, let it mount up and open the file explorer window, then navigate to the pool/main/n/ndiswrapper folder and double click each of the 2 files there to install it.  No compile needed.  Some people are making this harder than it needs to be.  It is only VERY RARE cases that one needs to find a newer version of ndiswrapper and therefore MIGHT need the source (usually binaries are still available).

---

### Post by Tu1J4kXk8NUhMz on 2008-10-10
> **anewguy said:**
> There is something important that needs to be mentioned here concerning ndiswrapper.  While on a MAC you may need to compile it (I don't know as I don't use a MAC), there are OLD posts out there telling everyone to download the source and compile it, and yes that does require the build-essential package.  However, if you are/have installed from a Livecd, ndiswrapper is on that CD and you DO NOT need to do the download source and compile thing.  Just put the CD in, let it mount up and open the file explorer window, then navigate to the pool/main/n/ndiswrapper folder and double click each of the 2 files there to install it.  No compile needed.  Some people are making this harder than it needs to be.  It is only VERY RARE cases that one needs to find a newer version of ndiswrapper and therefore MIGHT need the source (usually binaries are still available).

I may have to replace the ath9k driver, so this is helpful. One thing I should point out, though, is that I just checked the Ubuntu Studio DVD (it's too big for a CD), and ndiswrapper is not on it. From what I can gather, this distro of Ubuntu is somewhat stripped down so they could fit in more multimedia stuff. I assume, however, that if I were to download the standard Ubuntu .iso and mounted it in Ubuntu Studio, I could find it there, would that be right?

---

### Post by anewguy on 2008-10-10
Yes - those files are on the LiveCD for standard Ubuntu.

Dave :)

EDIT:  Since you need to use ndiswrapper, you may want to look into ndisgtk.  It is a graphical front end to ndiswrapper, so you don't have to use the command line.  Some people find this easier to use.  I don't know if it's on the distribution CD - I do know it's not in the area ndiswrapper is.

---

