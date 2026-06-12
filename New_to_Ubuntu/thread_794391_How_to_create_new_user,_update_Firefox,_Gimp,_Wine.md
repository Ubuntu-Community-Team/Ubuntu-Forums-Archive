---
title: "How to create new user, update Firefox, Gimp, Wine,..."
date: 2008-05-14
forum: New to Ubuntu
---

### Post by oopsy on 2008-05-14
Being a spring green newbie, I'd very much appreciate baby-steps directions. Thank you very much.

I've just installed Ubuntu from a cd, but I'm having trouble getting my head around it.

1. I've read somewhere not to log in as administrator unless required, but I can't figure out how to create another user name. I searched the help files, but I can't find it. How do I create a new user name?

2. It came with Firefox 2.0.0.6, but there is no way to update it. I can't even change the font. I can change the font size, but not the typeface. How do I update to the latest Firefox?

3. I would like to resize a picture from 300x350 to 350x350 pixels but I can't figure out how to do it. I tried Gimp, but when I resize the width to 350 it brings the height to 400. How do I modify the size of a picture?

4. I would like to get Irfanview (great free photo editing), but it works on Linux only through Wine. How do I get it, and what do I do with it to make Irfanview work?

Sorry for asking so many questions (although I'm afraid it will very likely not be the last ones).
Any help is very much appreciated. Thank you.

---

### Post by penguinbreath on 2008-05-14
I believe to resize your image to 350x350, you need to first crop your original image with a fixed 1:1 aspect ratio.

[[IMG]http://img88.imageshack.us/img88/8237/screenshotgimpek7.th.png[/IMG]](http://img88.imageshack.us/my.php?image=screenshotgimpek7.png)

---

### Post by billgoldberg on 2008-05-14
> **oopsy said:**
> Being a spring green newbie, I'd very much appreciate baby-steps directions. Thank you very much.

I've just installed Ubuntu from a cd, but I'm having trouble getting my head around it.

1. I've read somewhere not to log in as administrator unless required, but I can't figure out how to create another user name. I searched the help files, but I can't find it. How do I create a new user name?

2. It came with Firefox 2.0.0.6, but there is no way to update it. I can't even change the font. I can change the font size, but not the typeface. How do I update to the latest Firefox?

3. I would like to resize a picture from 300x350 to 350x350 pixels but I can't figure out how to do it. I tried Gimp, but when I resize the width to 350 it brings the height to 400. How do I modify the size of a picture?

4. I would like to get Irfanview (great free photo editing), but it works on Linux only through Wine. How do I get it, and what do I do with it to make Irfanview work?

Sorry for asking so many questions (although I'm afraid it will very likely not be the last ones).
Any help is very much appreciated. Thank you.

1. you can't login as admin in ubuntu (well, not easily anyway) If you still want to make a new user: 

system -> administration -> users and groups (users and groups is called something else in older ubuntu version, it think it's just called "users")

2. I presume you are running an old ubuntu version. It will have the latest firefox 2 version if you update your system (the update manager updates the OS as well as all applications you installed from the ubuntu repo).

If you want to run firefox 3 beta:
[http://linuxowns.wordpress.com/2008/04/03/firefox-3-beta-5/](http://linuxowns.wordpress.com/2008/04/03/firefox-3-beta-5/)

3. in the gimp you should go to scale image and then choose "none" for interpolation. (this might be different in older gimp versions).

4. It would be better if you learned how to use the gimp, it's much more powerfull and pretty easy to use once you grasp the basics.

If you want to use that application, download the windows xp version and install it using wine. Check the winehq database to see if the program can run under wine and if you need to do something special to get it to work.

Don't be sorry to ask questions, that's why this forum is here, and we all love to help.

Note:

I might be wise to use the latest ubuntu version instead of an older one. The new ubuntu version (8.04 hardy heron) is a LTS release.

---

### Post by penguinbreath on 2008-05-14
> 2. It came with Firefox 2.0.0.6, but there is no way to update it. I can't even change the font. I can change the font size, but not the typeface. How do I update to the latest Firefox?



To update to the latest version of Firefox 2.x, try going to *System-Administration-Update Manager* and do an update.  I believe the update manager will update Firefox to its latest version.

---

### Post by N.N. on 2008-05-14
1. At the community wiki you can find an illustrated guide on how to add users, see [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto). The screenshots are a bit dated but the outlined procedure should also apply to the version of Ubuntu that you're running.

2. The update manager should prompt you with an update for firefox at some point. Try navigating to "System" > "Administration" > "Update Manager" and check for updates.

3. Resizing a picture can easily be done with The GIMP. Open the picture and go to "Image" > "Scale Image". Click on the chain icon so that it "snaps apart": this will allow you to specify the dimensions of the picture as you please. If the chain icon is intact, the program will force a certain aspect ratio, allowing you only to specify either width or height.

4. See the following entry in the community wiki: [https://help.ubuntu.com/community/Wine/IrfanView](https://help.ubuntu.com/community/Wine/IrfanView). You must issue the commands in a terminal. You can open a terminal by navigating to "Applications" > "Accessories" > "Terminal". You will probably end up using the terminal frequently, so if you ever need to kill some time, check out the following community documentation to familiarise yourself with it: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal).

Please note that some of the "command names" I have mentioned (such as "Image" > "Scale Image") might not match the ones that you will find in your programs exactly. My menu items are all in Danish, so I translated them freely. :)

---

### Post by t0p on 2008-05-14
> **oopsy said:**
> 

4. I would like to get Irfanview (great free photo editing), but it works on Linux only through Wine. How do I get it, and what do I do with it to make Irfanview work?


I don't know Irfanview, so I've no idea how "great" it is... but I do know that there are some great photo management and image manipulation apps that run natively in Linux.  **The Gimp** is the obvious one - it's a brilliant app, and there are photography plugins available.  There are others too - heck, in Synaptic do a Search for "photo" and look at the list... an embarrassment of riches!!  And I believe it's better to use a native app than a Windows app in Wine.

---

### Post by oopsy on 2008-05-14
Thank you so much for the quick replies.

Good to know that I'm not logged in as administrator. I'm not sure what it means, though, but I'm sure I'll eventually learn what "adminstrator" is.

I don't want to crop the picture, just change its size and shape.
I tried to apply every interpolation (what does that mean?) option, but none works. It still stretches all sides, while I only want to stretch the width.

I'll try the wine thing, although I'm not really sure how to use it.

I bought the disk quite recently, so it shouldn't be that old. Isn't 7.10 gutsy the version just before 8.04?
I almost updated to 8.04, but then I read in another thread that it comes with Firefox beta and that there is some problem with it.
I don't want any beta of anything. I'm having enough trouble learning a new system without adding beta to the mix.

How can I replace the Firefox I have with the latest stable version (2.0.0.14)? I have downloaded it, but I don't know what to do with it since the update function is disabled and update manager only gives me the option to update ubuntu. 
I don't have any other browser so I need to make sure that I won't find myself without a way to get online.

Thank you much.

---

### Post by oopsy on 2008-05-14
Oops! didn't see the latest replies before posting mine. Thank you.:)

Your Danish/English translation is perfect for Gimp. I just resized my image the way I wanted. Nice trick that chain thing. Thank you so much. :)

I'm going to check the other links and suggestions to learn this whole new system.

One more thing. Can I simply run the 2.0.0.14 Firefox and ignore the old one for the time being? And if so, how do I open it?
Thank you much.

---

### Post by sneeks on 2008-05-14
you can add another browser from the add/remove add under applications.
opera is not too bad and has a lot of the stuff that firefox does,and if you get into it,you can use voice commands too!!

---

### Post by N.N. on 2008-05-14
> **oopsy said:**
> Oops! didn't see the latest replies before posting mine. Thank you.:)

Your Danish/English translation is perfect for Gimp. I just resized my image the way I wanted. Nice trick that chain thing. Thank you so much. :)

I'm going to check the other links and suggestions to learn this whole new system.

One more thing. Can I simply run the 2.0.0.14 Firefox and ignore the old one for the time being? And if so, how do I open it?
Thank you much.

You're welcome. :)

I think I found a solution to your firefox problem in the community wiki. It involves running firefox with elevated permissions temporarily. According to the entry, you go about doing this by following these steps:

[LIST=1]
[*]Press ALT+F2 to bring up a quick-launch dialogue. Type the following in the dialogue to start firefox with elevated permissions: [FONT="Courier New"]gksudo firefox[/FONT]. (You need to enter your password at the prompt that shows up). Do NOT browse other sites while firefox is run with these permissions. Doing so is unsafe practice!
[*]Once firefox has launched, go to "Help" -> "Check for updates". If updates are available, apply them. When it asks to restart, use the Restart option. Following the restart you should see a Mozilla page confirming that you're using the latest version of firefox.
[*]Close firefox and start it as a normal user (i.e. the way you normally start it). Once closed, firefox will no longer run with elevated permissions.
[/LIST]

This procedure is based on the instructions in the following entry in the community wiki: [https://help.ubuntu.com/community/FirefoxNewVersion#head-63727d73c1ddc18dd45d4c74609fff93c3919abc](https://help.ubuntu.com/community/FirefoxNewVersion#head-63727d73c1ddc18dd45d4c74609fff93c3919abc).

---

### Post by ZabiGG on 2008-05-14
And if you want more info about your system, follow the link in my signature.

You'll find links to all kinds of starter info ;)

---

### Post by oopsy on 2008-05-16
Thank you so much for the help.
I apologize for not responding sooner. When I tried to print your instructions to make sure I wouldn't mess up, I realized my printer was not working. It took me a long time to figure out what the problem was (it only needed to be "enabled". Duh!). I really got sidetracked...

N.N. your directions are perfect. I really appreciate it. Thank you very much.
Unfortunately, it didn't work. It actually showed more links disabled. In normal mode, only *Check for updates* is disabled. In gksudo, *Report broken web site* and *Report web forgery* are also disabled.

Maybe I should try a different Linux system, alongside Ubuntu 7.10? I'm moving up from WindowsMe, so I might not need many bells and whistles. At least not at the beginning. I'd like something very clean that gives me as much working space on the desktop as possible. Any recommendation?

I know there is a learning curve, but to tell the truth, I'm not that crazy about Ubuntu. It feels sluggish, cramped and quite jumpy. At times, I can't get the side scrolling bar from jumping up and down, making it very difficult to read anything. It not only does that in Firefox, but also in other applications, like Text editor or photo viewer. Is it normal behavior?

Sorry, my thoughts seem to be jumping all over the place. It's way past my bedtime. I'll check back in the morning. Thank you all.

---

### Post by oopsy on 2008-05-16
Sorry for the negative sounding post last night. I was really down and discouraged. I feel sooo overwhelmed by the amount of learning I need to do.
I am very much lacking time, I need to have things working (so I can work), and I feel like I'm running in circle trying to catch up after a train that's going way too fast for me. I'm out of breath and I really should have gone on that diet and exercise regimen before starting running after that darn train. :lolflag:

OK. Time to get some new perspective. Why don't I start with something that should be simple. Right now the font is some type of monotype and it takes a lot of desktop space, so I went into *System>Preference>Appearance>Font* but I have no idea what to do.
How do I change the font to make the characters take a lot less space, something like Arial for example?

Also, looking into *System>Preference>Appearance>Visual Effects*, when I tried to set it on *Normal* it told me that it is impossible. It even made the browser freeze (while I was typing this post!). I had to restart it. The browser also froze twice yesterday while searching the forum for a solution to my printer problem (I can't remember if I was also using an application at the time).
I have nothing but Ubuntu installed on this new 80GB HDD with 512MB RAM. It's an old laptop, but still... Is there something wrong?

I'm probably asking too much for that one thread, but thank you very much for all your help.

---

### Post by N.N. on 2008-05-18
Pardon the late reply. Didn't seem like you were going to reply to this thread any more.

 Sorry to hear that the fix didn't work and that Ubuntu isn't meeting your requirements. I don't understand why your Ubuntu doesn't suggest to update Firefox. I've never experienced that problem myself. :(

I'll try to address the issue once again, though, by suggesting a manual install of Firefox this time:[LIST=1][*]Open the Firefox download page on Mozilla.com: [http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)
[*]Download Firefox to your home directory (i.e. to /home/<your_username>). The program will be in a gzipped tar format (.tar.gz).
[*]Open a terminal and type the following command to navigate to [FONT="Courier New"]/usr/lib[/FONT] where we will install Firefox: ```
cd /usr/lib
```
[*]Then type the following command to extract Firefox to this directory: ```
sudo tar -zxvf /home/<your_username>/firefox-2.0.0.14.tar.gz
``` Firefox will now be located in [FONT="Courier New"]/usr/lib/firefox/[/FONT].
[*]Finally, update your symbolic link in [FONT="Courier New"]/usr/bin/[/FONT] to point existing shortcuts to the new, manual install: ```
sudo ln -sf /usr/lib/firefox/firefox /usr/bin/firefox
```
[/LIST]
By following these steps you should finally be able to run Firefox 2.0.0.14.

Now to address your other problems:

1. The scrolling issue you have described is not normal behaviour. Are you using a mouse in combination with the touchpad on your laptop? I have experienced a similar issue on my laptop when I used that combination of hardware. Unfortunately, though, I never found a solution to the problem.

2. Adjusting font families and font sizes can easily be done from the "font" tab in "System" > "Preference" > "Appearance". Simply click the names of the listed fonts, and a dialogue will appear that will allow you to choose font families and font sizes. (See attached image if my explanation doesn't suffice). You can install Microsoft TrueType core fonts from the Synaptic package manager. The package name is "[FONT="Courier New"]msttcorefonts[/FONT]".

3. I think Visual Effects can be enabled only if you are using a video card driver that supports direct rendering. To determine whether your installed drivers support this feature, open a terminal and type the following command: ```
glxinfo | grep direct
``` If it says "direct rendering: No" then either your video card doesn't provide hardware-accelerated 3D, or the video card drivers in use don't support this feature. Try navigating to "System" > "Administration" > "Hardware Drivers" and see if you can install or enable the proprietary drivers for your video card as these drivers often provide support for hardware-accelerated 3D.

Ubuntu doesn't meet the requirements of everybody. On certain hardware the performance might be so poor that trying to make it usable won't be worth the bother, or perhaps you'll eventually find yourself disagreeing with the roadmap of the distribution. Either way you shouldn't be afraid of trying out other linux distributions. Perhaps another one will be more to your liking. This probably isn't very helpful to someone who wants to get a lot of work done on his system instead of dealing with what can seem like technical trifles, but that's the way it is.

Remember, though, that with enough effort you will often be able to customize any distribution to suit your liking. To address some of the concerns you have described you could start by upgrading to the newest version of Ubuntu (8.04), since that version is supposed to be faster than the one you're using. Then you could install a lightweight window manager such as Openbox or IceWM to achieve even snappier performance. Forum member aysiu hosts an illustrated guide on how to install and use IceWM in Ubuntu (see [http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)), while another member, urukrama, has written a detailed guide on installing and configuring Openbox (see [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)). I know that you don't like that the beta of Firefox 3 is included in version 8.04 of Ubuntu, but that can easily be taken care of (see [http://www.psychocats.net/ubuntu/firefox2hardy](http://www.psychocats.net/ubuntu/firefox2hardy)).

---

### Post by oopsy on 2008-05-18
Oh, N.N. you are so wonderful. Thank you so much for writing back. I figured I had offended everyone with my previous negative mood. After all, you guys had been very helpful and I rewarded you by whining!

I think I found why the Firefox update function is disabled:
"Only the Official Firefox builds from Mozilla can use the software updater as one cannot expect Mozilla to support unofficial/third-party builds not built by them with patches as every build may be different in configuration. Even with the builds from Mozilla, one needs to have write permissions where the Firefox folder is."
and "The check for updates button is always disabled unless you're root. This is a security feature (no user write access to the Firefox binary). However, it would be nice to be able to just check for existance of updates, here's the related bug. (won't affect you unless you go the manual way, outside the repos, that is)".
This is a small excerpt from a conversation I've been having with some great people on this Firefox support forum [http://forums.mozillazine.org/viewtopic.php?t=656310&postdays=0&postorder=asc&postsperpage=15&start=0](http://forums.mozillazine.org/viewtopic.php?t=656310&postdays=0&postorder=asc&postsperpage=15&start=0)

I have updated to 8.0.4 thinking it would solve my problem, but it hasn't so far.
I have very little time right now, but here are my thoughts so far, in no particular order:

1. Since I was using a virgin HDD, I needed a live CD to be able to connect, but it would probably be smart to use a distro with little bells and whistles, just for the purpose of having a minimal OS to be able to get online, then install the distro of choice by downloading it from the official site. (ironically, I started with Xubuntu CD, then decided to install Ubuntu CD. Duh!)

2. I'm going to follow your instructions to check the video card. Since I'm using an old laptop it's very likely the culprit. It might also be why things are so jumpy at times, since I don't have a mouse attached.

3. I'll also install the fonts. So far, FF beta doesn't pose any particular problem, but if it does I can always install 2.0.0.14 manually, thanks to you.

4. It would probably be smart to scrap everything and start with option #1. I must be careful not to loose my ability to connect to the internet, though, because I had a hard time getting my ISP hooked up. Verizon doesn't support Linux and I had to go through some hoops to get it installed (I was previously on dial-up and there was no way to get it to work in Linux).
By the way, for anyone having trouble installing Verizon dsl in linux here is the link that saved me [http://healthysystem.blogspot.com/2007/06/verizon-dsl-doesnt-support-linux.html](http://healthysystem.blogspot.com/2007/06/verizon-dsl-doesnt-support-linux.html) I've been meaning to create a post to let people know about it, but I got sidetracked.

Well, these are my thoughts. I've go to run, but I'll be back to tell you what happened.
Thank you so, so very much.

---

### Post by oopsy on 2008-05-19
Hi,
I can hardly keep my eyes open, so I'll be brief.
1. I've done "glxinfo | grep direct" and it returned "direct rendering: Yes", so I assume my video card is OK.
2. I've searched for "msttcorefonts", but it returned Openoffice which is already installed. Maybe I should mark it for "reinstallation"?
3. I've installed icewm but I haven't had time to play with it.
I'll do some more tomorrow and let you know.
Thank you much.

---

### Post by N.N. on 2008-05-19
Hi again,

1. According to that output the video card drivers you use should provide support for hardware-accelerated 3D and thus Visual Effects. I can't figure out why, then, that Ubuntu won't allow you to enable those effects. Can you post the exact error message you get when you try to enable them? I'm not very knowledgeable about this subject, but I suspect the problem lies with the video card drivers. If your video card is old, then it might be using the default, open source graphics driver which might not support Visual Effects. Try running the following command in a terminal to determine what card you have: ```
lspci | grep VGA
``` Anyway, if you're already experiencing sluggishness with your Ubuntu install, I wouldn't recommend enabling Visual Effects as these require more system resources. (See [https://help.ubuntu.com/8.04/desktop-effects/C/compiz-problems.html](https://help.ubuntu.com/8.04/desktop-effects/C/compiz-problems.html)).

2. The [FONT="Courier New"]msttcorefonts[/FONT] package is in the multiverse repository. Make sure you have it enabled by going to "System" > "Administration" > "Software Sources" and checking the multiverse box. Then open Synaptic, click "Reload" to update the package manager's list of packages (it should prompt you to do that), and then search for [FONT="Courier New"]msttcorefonts[/FONT] again. If you still can't find it, try issuing the following command in a terminal: ```
sudo aptitude update && sudo aptitude install msttcorefonts
```

3. I hope that you'll experience a noticeable performance increase with IceWM. It should take up much less system resources than the default window manager (metacity). :)

---

### Post by oopsy on 2008-05-20
Hi,
Thank you very much. Sorry for taking so long to respond. I'm so far behind in my work that I'm treading dangerous waters.

1. Here is the video card driver. Is it the true thing, or a generic one? At any rate, I'll follow your advice and not install visual effects.
01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)

I've also noticed that in system>software sources I now have Main, Universe and Multiverse but not Restricted which is proprietary drivers for devices. Should I add it?

2. Got the fonts! Thank you very much.

3. I've decided not to run iceWM for now. Not to have the ability to see any file at the start just scared me too much. I really don't have time to learn yet one more new system. My brain (assuming I still have one LOL) just can't process it. I'll try it when I'm a bit less under pressure. I haven't even looked at openbox yet. I appreciate your mentioning them, though.

4. When starting the computer, it hangs for quite a long time. The orange scrolling bar goes to the far right, comes back to the middle, and hangs there for about 10 minutes. Before upgrading to 8.0.4, it only took a minute or two. (I should probably create a thread just for this, it might also help someone with the same problem).

I'm wondering if it's not all related, the jumping, hanging, visual effects incompatibility, and entries like this "Stumbleupon extension for Firefox cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."
My old laptop may not be powerful enough for all these bells and whistles.

5. Which brings me to my last point, would it be possible to download and install a lightweight distro like Xubuntu or whatever you would recommend, alongside Ubuntu? I had first installed Xubuntu, but when I added Ubuntu it wiped it out. At least I think it did. How do I find out exactly what's on my PC? Would I also be able to uninstall Ubuntu if I needed to?

It wouldn't wipe out my internet connection settings, would it? What would happen to the partition? Right now, when I look into "Computer" I see a 40GB media, CD drive, travel drive and file system.
The 40GB media puzzles me a bit, because I know I have a 80GB HDD. I've also seen somewhere that I have 30GB free. The math doesn't seem to compute, and how big of a footprint does 8.0.4 have? I've got a few files, but I'm pretty sure it's less than 1GB.

6. If there was a light distro with a look closer to Windows (I know, I'm a heretic good for nothing but the stake's fire LOL) that'd be nice. I especially miss Explorer (not IE!) and having all folders and programs in the left column and being able to display the content of each folder in the right column just by clicking on it. I found it easier to drag and drop files rather than copy/paste. Does something similar exist in Linux? Maybe it's there and I haven't found it, or maybe that's one of iceWM features?

Thank you so very much.

---

### Post by N.N. on 2008-05-20
Sorry to hear that you're behind with your work. Hope you'll pull through it.

I'm afraid that answering your questions satisfactorily exceeds my competence, but I'll try anyhow:

1. From that output I can't tell which driver is in use, only what model your graphics card is. I requested the output to see how old your graphics card is, because that allows me to guess what driver is in use, and I'm guessing that an open source one is. However, it probably would've been wiser of me to request the output of the following command, as it outputs which video card driver is specified in the configuration file for xorg: ```
cat /etc/X11/xorg.conf | grep Driver
```

You can safely enable the restricted repository for proprietary drivers. Doing so will allow you to look for proprietary drivers for your graphics card by navigating to "System" > "Administration" > "Hardware Drivers". Proprietary drivers often provide better support for hardware-accelerated 3D, but they aren't supported by the Ubuntu developers.

3. Sorry to hear that. You might want to try installing Openbox and using it in combination with Gnome by selecting the "Gnome/Openbox" session form the login manager. Such a session is less intensive on system resources than a default one, and it allows you to see icons on the desktop and so on.

4. Unfortunately I can't help you with that problem. It would be a good idea to create a new thread about it here on the forums once you have more time on your hands.

5. I would recommend just installing Xubuntu from Ubuntu. There is a xubunu-desktop package in the repositories that allows you to easily transition to Xubuntu by means of a package manager. This way you won't have to touch partitions or internet connection settings; these will just be carried over to Xubuntu as is.

Making such a transition is straightforward:
[LIST=1]
[*]Open a terminal.
[*]Paste the following command: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```
[*]Once the install has finished, log out.
[*]Under "Session", select "Xfce"
[*]Log in again.
[/LIST]

As for the mismatch between your hard disk's actual size and the one that Ubuntu is registering, I'm guessing that it's a matter of partitioning, which I'm not particularly knowledgeable about. I think that there could be unpartitioned space on your hard disk which isn't being registered by Ubuntu. The footprint of 8.04 is less than 5 GB, so it's not Ubuntu that is taking up the missing space. My guess is that you unintentionally set up the partitions so that only 40 GB was available to Ubuntu when you installed it. If that's the case, the missing space should be easy to reclaim with a program such as gparted. I've never tried that myself, however, so you should probably consult someone more experienced for details on how to do that.

6. Actually, there is a tree view feature in nautilus (the default file manager in Gnome) similar to that in Explorer. In the sidebar there is a drop-down menu where it says &#8220;Places&#8221;. Simply click that and select &#8220;Tree&#8221;. If you want to try a distro that is more &#8220;Windows-friendly&#8221;, you could try Xandros ([http://www.xandros.com](http://www.xandros.com)). It's supposed to be easy for Windows users to switch to, but it's commercial. Alternately, you could simply try a distribution that uses the KDE desktop environment (such as Kubuntu) instead of Gnome, as that supposedly looks more like Windows than Gnome.

---

### Post by oopsy on 2008-05-20
Thank you so much.
This is just a very quick reply that only touches the drivers. I haven't yet had time to play with anything else.

I've got
cat /etc/X11/xorg.conf | grep Driver
	Driver		"kbd"
	Driver		"mouse"
	Driver		"synaptics"
	Driver		"wacom"
	Driver		"wacom"
	Driver		"wacom"
	Driver		"savage"

I've enabled the proprietary drivers in software source, but when I checked it told me I don't have any proprietary driver installed. That been said, I didn't restart Ubuntu, so it may change after I do. I'll check again.

On a side note, I think you'll be happy to know that I'm beginning to feel more comfortable with the "Linux feel". Nothing happened, I think my brain is simply slowly adapting. Who said you can't teach old dogs new tricks? ;)

I really owe it to you. Thanks. :)

---

### Post by oopsy on 2008-05-22
Hi again,
I have installed Xubuntu from Ubuntu 8.0.4, but it is still slow and jumpy, and now takes 15 minutes to load. And I'm still with FireFox beta which is begining to drive me nuts. I can't stand having the tabs scrolling and the way the command line displays history.
And neither Ubtu nor Xubtu recognizes my camera, which I desperately need.
I seem to be piling up the problems, don't I? On the bright side, when all is set and done, I should be fluent in Linux. ;)

I've open a separate thread, just for the camera, but all I got is one reply telling me to get a card reader!
I've read several posts saying that since they installed 8.0.4 they can't get their camera to be recognized, so given all the trouble I'm having, I don't want to use 8.0.4 of any kind anymore. The hardy heron, although a beautiful bird, just doesn't seem to like me.

I don't know what the problem is, maybe I had a bad disk to start with, but I can't afford to waste any more time on it.
I've taken a look at Kubuntu (thanks for the suggestion) and it seems OK, so...

Would you mind helping me install Kubuntu 7.10 (Gutsy Gibbon) alongside Ubuntu and Xubuntu? Since I have the space, I'm going to keep them as a backup for now and delete them later if I need to.
I'm going to download it while I try to get a few hours of sleep, so I will have it right on my desktop, ready to install.

I've also posted a separate thread about it here [http://ubuntuforums.org/showthread.php?p=5016465#post5016465](http://ubuntuforums.org/showthread.php?p=5016465#post5016465) so anyone having a similar problem will easily find an answer.

I am so sorry to be constantly asking for your help. I really, really appreciate it.
Thank you much, N.N.

---

