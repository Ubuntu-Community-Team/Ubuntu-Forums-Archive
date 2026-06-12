---
title: "Installing Ubuntu Over Corrupt Vista"
date: 2015-05-23
forum: New to Ubuntu
---

### Post by greg82 on 2015-05-23
I've got an HP laptop with a corrupt install of Vista (CQ70  p/n FS110UA). 

HP no longer supports or has any replacement CD's for this laptop, so they informed me to just buy a copy of 64 bit WIN 7.

I would like to try Ubuntu on it, but not sure if it'll install over the Vista that doesn't boot. 

The backup copy was on the HD, which I already tried repairing from, and reinstalling from to no avail.

---

### Post by oldfred on 2015-05-23
If it is Vista era, how much RAM and what video.
Older systems with less RAM and older video cards/chips usually do not run full Ubuntu, but run Xubuntu or Lubuntu well.
I am running 64 bit Ubuntu but with fallback or gnome-panel instead of Unity on my 2006 Toshiba. It has 1.5GB of RAM and what ever Intel video chip was standard then. I purchased it two weeks before Vista as I knew I did not want Vista based on all the reviews.

---

### Post by RobGoss on 2015-05-23
Do you want to dedicate this machine to Ubuntu?

if this is the case and depending what your specs are you might have a choose a lighter version of Ubuntu like Oldfred stated.
Once you created a bootable DVD or USB all you need to do is place your DVD or USB drive or disk in and you will have the option to wipe your  existing Drive and install Ubuntu. Very simple and straight forward.

---

### Post by cariboo on 2015-05-23
No matter what you decide to do, you need to reformat your hard drive, which means that Vista won't be a problem.

---

### Post by Vladlenin5000 on 2015-05-23
> **cariboo said:**
> No matter what you decide to do, you need to reformat your hard drive, which means that Vista won't be a problem.

Exactly, whatever is in the drive won't be a problem. However, the drive itself might. It's part of a refurbished computer so most likely pulled from some other system, ie, not new.

I would test it before anything else because of this:
> The backup copy was on the HD, which I already tried repairing from, and reinstalling from to no avail.

This and the "corrupted Vista" may have a common denominator: a failed or failing drive.

---

### Post by greg82 on 2015-05-23
I've been going on the assumption its not a failing drive, but rather a  boot problem that occurred when my niece and nephew altered some windows  files. 
The fact Vista didn't reinstall effectively from the HD backup, didn't really surprise me, nor the HP tech who suggested Win 7. 

I bought this laptop brand new for my mom some years back, here's the [specs]("http://support.hp.com/us-en/document/c01550112") , and I believe it has 2 gigs of ram. 
She's  not tech savvy, but I was told Ubuntu is as user friendly these days as  Windows, and that rather than purchase a dusty old copy of Win 7 or 8, 
this was the way to go.

I'm not trying to suggest its not the HD failing, but remaining hopeful its not, until the other potential issues are ruled out.

---

### Post by cariboo on 2015-05-23
If you have a system running Ubuntu already, it may be best to create a bootable usb device on it, then use the usb device to boot to the desktop on the laptop, then once at the desktop go to the dash and type in:

```
disks
```

click the menu icon in the upper right corner, and select SMART Data & Self Tests, this will show you something similar to the screenshot.

**Note** If you don't have Ubuntu or one of the derivatives installed on another system, you better do that first, as you are going to be your mother's support system. :)

---

### Post by greg82 on 2015-05-24
> **cariboo said:**
> If you have a system running Ubuntu already, it may be best to create a bootable usb device on it, then use the usb device to boot to the desktop on the laptop, then once at the desktop go to the dash and type in:

```
disks
```

click the menu icon in the upper right corner, and select SMART Data & Self Tests, this will show you something similar to the screenshot.

**Note** **If you don't have Ubuntu or one of the derivatives installed on another system, you better do that first, as you are going to be your mother's support system**. :)


Do you mean "support system" during installation, or because there will likely be glitches and problems to overcome once installed and beyond ?

---

### Post by Mark Phelps on 2015-05-24
> there will likely be glitches and problems to overcome once installed and beyond ? 

Exactly -- as you will most likely be the SOLE person providing any and all Linux support, once you install it on that PC.

Also, as others have mentioned, it's very possible that the Vista "corruption" resulted from a failing drive -- which is not going to work any better using a Linux distro.

---

### Post by monkeybrain20122 on 2015-05-24
Well there is only one way to find out. Try it! I don't see what would be lost if Vista is corrupt anyway. It could be a hard drive problem, in that case too bad (or you may replace the hard drive or install Ubuntu on an external drive and boot from there) , but it may not be and it can work.

And I don't see any problem that you will be the sole person providing support,  if it works it is a bonus  or the laptop would be going to the landfill anyway. It is a really good opportunity to mess around having a expendable laptop like that, your friend may just let lose on it and learn a few things in the process if it works at all. Doubt that you would be  expected to provide premium support.

---

### Post by mattharris4 on 2015-05-24
> **greg82 said:**
> I've been going on the assumption its not a failing drive, but rather a  boot problem that occurred when my niece and nephew altered some windows  files. 
The fact Vista didn't reinstall effectively from the HD backup, didn't really surprise me, nor the HP tech who suggested Win 7. 

I bought this laptop brand new for my mom some years back, here's the [specs]("http://support.hp.com/us-en/document/c01550112") , and I believe it has 2 gigs of ram. 
She's  not tech savvy, but I was told Ubuntu is as user friendly these days as  Windows, and that rather than purchase a dusty old copy of Win 7 or 8, 
this was the way to go.

I'm not trying to suggest its not the HD failing, but remaining hopeful its not, until the other potential issues are ruled out.

According to the link you provided this computer came with 3072MB of RAM which would be approximately 3GB.  Have you removed RAM for some reason or is the same RAM in the computer that it came with from the factory?

Assuming your belief that the computer only has 2GB of RAM is incorrect (since you sound unsure) and it still has the factory 3GB of RAM (and also has a 2GHz Dual Core Intel CPU, it Passmarks at 1042) you should be able to run Ubuntu on it.  If the RAM has been changed and it truly only has 2GB of it Ubuntu will not run properly browsing some websites so the RAM amount is crucial here.  

Ubuntu with Unity is not very intuitive to run anyway, Xubuntu and Lubuntu (lighter Canonical OSes) are easier to use IMO especially since she is not tech savvy and is used to Windows.  It is relatively easy to create icons on the screen for the programs she uses in the lighter Canonical OSes and they will certainly do 98% what your mother needs done, there are a handful of sites that require the Windows OS including Vimeo and I know of one one that even demands Internet Explorer 11 or 12 to play their videos properly, that is not happening on Linux but that number is quite small -- I think that has to do with admins of those sites keeping people from copying their videos at all costs and they feel they cannot do that if a person is using Linux.  YouTube plays fine on any Canonical OS using Firefox (with the Pepper Flash program) or Chrome.  Netflix would not run properly on my desktop (the videos kept cutting out and freezing, they claim it will run using Chrome) but that may be because of the outdated Pentium 4 CPU I am running on it.  Yes, you can run the lighter Canonical OSes on a computer designed to run the full Ubuntu OS and that is what I recommend in this case.  Be sure to install the 32 bit version, if you attempt to install a 64 bit OS you will get nowhere with it on this computer.  I would use Unetbootin to create a bootable USB stick to create your install media, be sure to pick version 14.04 32 bit.  You can search for their site on Google, there is a Windows version.  

I think you can also use the "Try Ubuntu/Xubuntu/Lubuntu" function to test the hard drive through the terminal before attempting an install.  Here are instructions:  [http://neanderslob.com/2013/10/06/how-to-check-the-health-of-ones-hard-disk-a-step-by-step-pictoral-tutorial/](http://neanderslob.com/2013/10/06/how-to-check-the-health-of-ones-hard-disk-a-step-by-step-pictoral-tutorial/) .  The pictorial is from a Ubuntu install but the commands can be used in the lighter OSes and the output will be the same.

---

### Post by monkeybrain20122 on 2015-05-24
> **mattharris4 said:**
> 

Ubuntu with Unity is not very intuitive to run anyway, Xubuntu and Lubuntu (lighter Canonical OSes) are easier to use IMO especially since she is not tech savvy and is used to Windows. .

Not really, I have installed unity for a few non tech savvy people and they love it. I find a smart phone or a tablet much less intuitive but most non tech people have no issue using one. People who complain about Unity are not the basic users, but intermediate users who have gotten used to the Windows interface and have a certain workflow. New users start from a clean slate and wouldn't have so many habits that need to be overcome to use a new UI.

Also even 2 Gs is sufficient to run unity, though xfce would be smoother, but there is no need to go lubuntu unless one likes the LXDE interface (I don't and xubuntu is more polished and less buggy comparing to lubuntu IMO)

---

### Post by Vladlenin5000 on 2015-05-24
> **monkeybrain20122 said:**
> Not really, I have installed unity for a few non tech savvy people and they love it. I find a smart phone or a tablet much less intuitive but most non tech people have no issue using one. People who complain about Unity are not the basic users, but intermediate users who have gotten used to the Windows interface and have a certain workflow. New users start from a clean slate and wouldn't have so many habits that need to be overcome to use a new UI.

Also even 2 Gs is sufficient to run unity, though xfce would be smoother, but there is no need to go lubuntu unless one likes the LXDE interface (I don't and xubuntu is more polished and less buggy comparing to lubuntu IMO)

+1

My experience with non tech savvy people is exactly the same. As usual, there are users who conflate/confuse "intuitiveness" (or user-friendliness) with "familiarity". Just because someone is used to something it doesn't mean it's best than the alternatives.
Unity has been objectively tested time and time again with several different samples of typical users and always proved to be more productive than any other of the alternatives (other typical Linux DEs, Windows and MacOS). Not perfect, obviously, but the one - and only one - that, IMO, is heading towards the right direction. Microsoft seems to agree but hasn't quite delivered yet, not even with Windows 10. I guess part of the Windows 8.x backslash is merely an example of reaping what has been sowed: Decades of dumbing down its users resulted in those some users coming back to bit them you know where because... Windows 8.x isn't dumb enough and "oh, where's the Start button? How can someone use a computer without a Start button?"

---

### Post by newb85 on 2015-05-24
We on the forum don't really know how tech savvy your mother is. These days, Ubuntu generally is as easy as Windows, but there are things that are done differently than in Windows. Also, as in Windows, there are sometimes bugs or issues to work through. There ate online resources like this firm to help with those, but if you think she'll come to you for answers, you'll have to put in the time to find them. I recommend spending a little time familiarizing yourself with the system before just installing and giving it to her. You should be able to tell her how to keep the system up-to-date, and probably how to install software. Be able to explain what the repositories are.

---

### Post by greg82 on 2015-05-24
Geez, as my first time posting here, the feedback is incredibly enthusiastic to say the least.

In the time it took me to reply to Mark,  5 more posts arrived!

I'll hang with this and see where it leads, I can always just buy a new PC if all else fails, but 

there appear to be too many watching to give up so soon.

Its got 3 gigs of RAM then, as its never been opened up yet.

---

### Post by BlinkinCat on 2015-05-24
> **greg82 said:**
> Geez, as my first time posting here, the feedback is incredibly enthusiastic to say the least.

In the time it took me to reply to Mark,  5 more posts arrived!

I have to agree with you Greg - I think the Ubuntu Forums simply can't be beaten - :)

---

### Post by greg82 on 2015-05-24
> **BlinkinCat said:**
> I have to agree with you Greg - I think the Ubuntu Forums simply can't be beaten - :)


Yeah, I was all set to throw this in the garbage, then did a double take, and Monkey Brain made me realize I should at least try.

Nothing to lose. If it works, and she doesn't adapt to it, at least I'll have a laptop of my own for once. 

I'm off to burn a Live CD, and test this machine as Matt recommended above.

---

### Post by leunam12 on 2015-05-25
I work with old computers all the time and I have installed Ubuntu on some of them and the performance is excellent, as a matter of fact, my personal laptop is an old IBM Thinkpad that came originally with Vista; I have 14.04 installed and it runs pretty smoothly, it has Unity as it's DE. On my Desktop PC running 14.04 as well I removed unity and I now use Cairo-Dock as my desktop environment; it is pretty neat. It is very important that you check the HDD's health before you do anything. Hard drives fail very easy. If your laptop has a COA sticker on the bottom and the product number key is still visible you can re-install Vista and maybe do a dual-boot with Ubuntu, if you wish to do so, send me a personal message and I'll tell you what to do.

---

### Post by mattharris4 on 2015-05-25
> **monkeybrain20122 said:**
> Not really, I have installed unity for a few non tech savvy people and they love it. I find a smart phone or a tablet much less intuitive but most non tech people have no issue using one. People who complain about Unity are not the basic users, but intermediate users who have gotten used to the Windows interface and have a certain workflow. New users start from a clean slate and wouldn't have so many habits that need to be overcome to use a new UI.

Also even 2 Gs is sufficient to run unity, though xfce would be smoother, but there is no need to go lubuntu unless one likes the LXDE interface (I don't and xubuntu is more polished and less buggy comparing to lubuntu IMO)

I have to admit that I figured out how to use Unity quite quickly but considering this user is probably just using her computer for basic internet and word processor IMO Xubuntu or Lubuntu would be easier for her to use as long as her son creates icons on her computer for whatever she uses most.  IME Libre Office will run fine on Xubuntu or Lubuntu once installed, people don't have to live with AbiWord using these OSes so with internet and a quick install word processing is taken care of for her.

Running 2GB of RAM with Ubuntu (or Edubuntu) works on 90% of sites compatible with Linux.  However, I have run into a few that cause a computer with only 2GB of RAM to go into swap (including SFGate which is the main newspaper site for the San Francisco area -- I would suspect other Hearst Corporation newspaper sites would be designed similarly, they own quite a few major newspapers in the US).  In my experience using swap area while surfing the net is worthless, the computer either freezes up completely or slows to a crawl.  That is why if someone has less than 2.5GB of RAM I don't recommend the full Ubuntu OS and steer those people to a lighter OS like Xubuntu.

Finally, lack of RAM is a moot point as the OP's mother's computer has 3GB of it (and a processor likely capable of running Ubuntu smoothly judging by its Passmark score).  However, I still think she would have an easier time with the lighter OSes and they will do what she needs to do just fine.  I also find that Lubuntu is not a whole lot lighter than Xubuntu in personal use.  Using the 32 bit Xubuntu 14.04 LTS my desktop computer uses about 180MB RAM at start-up and between 350 and 1000MB RAM surfing the net and playing music at the same time (disabling Blueman reduced the RAM use by about 30MB, this computer does not have bluetooth so I don't see any reason to leave that on).  On my laptop the 64 bit Lubuntu uses about 250MB RAM at start-up and 350-1250MB RAM surfing the net and playing music at the same time (the 32 bit version would probably use less but my laptop is 64 bit and has UEFI so the 32 bit version is not an option on it).  With both computers the CPU is the bottleneck with the lighter OSes, not RAM.

---

### Post by Vladlenin5000 on 2015-05-25
I really don't see a difference in having the most frequently used programs in the launcher or icons scattered along the desktop, except that the former is better organized, it actually makes sense, and if need you can also have both although that isn't the recommended 'workflow'.
At the end of the day it's all about personal preferences, If you don't like Unity by all means use anything else, there are plenty of choices. The productivity remark I've made earlier nevertheless stands, it has been tested scientifically, it is neither subjective nor down to personal preferences.

That said, please resist the urge to always recommend "anything else but Unity"... This suggestion is directed to _regular contributors_ and _forum staff_ alike. More often than not I've witness such recommendations being made even without knowing the actual hardware specifications. It undermines the great work and the huge effort put in Ubuntu by Canonical to make it a solid and better alternative to all the proprietary counterparts.

And speaking about personal preferences, I don't want to go to a café, take out my laptop, and be perceived as the "old man with the old thing", as the "poor guy who can't cope with the new times therefore he's using an OS from the 90s". I wanna be seen as the vanguardist I am, showing off the most beautiful and functional desktop. Yes, 'eye-candy' matters... Granted, when we're using let's say Scientific Linux, eye-candy is the least of our concerns but for regular users it matters, it matters a lot.

---

### Post by craig10x on 2015-05-25
Most people use smart phones these days, and have at least seen or played with macs in a store, so it isn't so shocking to see and work with a dock with icons (which is really what unity is) and the dash search is easy to understand, so if it will run well on the hardware you are putting it on, i really don't see a problem as was previously said...you can use something else if you choose but i always shake my head when over and over the automatic recommendation is to try an alternate to unity...like the linux beginner is not going to be able to work with it...does everything have to look and act like windows???

Also, as previously mentioned, have the icons on the launcher is a lot NEATER then having them spread all over the desktop... ;)

---

### Post by greg82 on 2015-05-26
Things are getting a bit ahead of me, as all this is foreign to me with the versions, the desktop environments, and years of guaranteed updates, Guaranteed? Isn't it free to begin with?  


I'm just trying to check the health on the HD, as per Matt's suggestion. 

So I burned a live CD and tried to test the hard drive through the terminal before attempting an install.  

Upon typing "sudo apt-get install smartmontools" 

and it quickly jumping to the next prompt on whether to install the files [Y/N], I typed "Y" as instructed,

which was followed directly by a number of failures listed.

[IMG]http://i144.photobucket.com/albums/r178/buddahass/failures_zpsw9pnli4w.jpg[/IMG]

---

### Post by Vladlenin5000 on 2015-05-26
You're right. This was rapidly derailing into an off-topic and recurring discussion. It was our fault entirely, not yours, and I'm sorry for being part of the problem.

OK, back on track... Do you have internet connection? You need it for installing software from the repositories.
Assuming you have then use the last error message's recommend command first - sudo apt-get update - to refresh the software sources. Then use the same command you already tried in order to install the software in that live session.

PS - Yes, it's free and always will be free. The support _for updates_ is what varies. You can count on a new Ubuntu release every 6 months. The current one is 15.04 (April 2015) and will be followed by 15.10 (October 2015). In even years, in April, that release is special because it has long term support (LTS) so the current LTS is 14.04 (April 2014) and the next will be 16.04 (April 2016).
LTS releases are now supported for 5 years whereas all the other interim releases are supported for only 9 months. Support  in this context means having "live" software repositories from where you can download both updates and new software. When a given release reaches the EoL (End of Life) status you can no longer do one or the other (and you shouldn't anyway). However, you can upgrade to newer releases easily and, of course, for free.

---

### Post by monkeybrain20122 on 2015-05-26
> **greg82 said:**
> Things are getting a bit ahead of me, as all this is foreign to me with the versions, the desktop environments, and years of guaranteed updates, Guaranteed? Isn't it free to begin with?  


I'm just trying to check the health on the HD, as per Matt's suggestion. 

So I burned a live CD and tried to test the hard drive through the terminal before attempting an install.  

Upon typing "sudo apt-get install smartmontools" 

and it quickly jumping to the next prompt on whether to install the files [Y/N], I typed "Y" as instructed,

which was followed directly by a number of failures listed.


I don't know if 'disk' is in the live CD, if it is there you can just fire it up to check your hd. Otherwise you can run gparted, it should give you errors if the hd is corrupt.

---

### Post by newb85 on 2015-05-26
I apologize if I added to the confusion.

As for the error messages in post #22, it looks like they all stem from a failure to resolve archive.ubuntu.com, which makes me think it's a DNS server issue (probably your ISP's fault.)  That is, assuming you have internet connection.

You can, of course, change the DNS server at either the router or PC level.
To change it at PC level, open Network Connections from the Dash.  Edit the one you're using.  In the IPv4 tab, switch to "Automatic (DHCP) addresses only" and under DNS Servers, enter at least one that is different from your ISP's.  (e.g., you could use one from Google, 8.8.8.8, or one from OpenDNS, 208.67.222.222)

---

### Post by greg82 on 2015-05-26
> **Vladlenin5000 said:**
> You're right. This was rapidly derailing into an off-topic and recurring discussion. It was our fault entirely, not yours, and I'm sorry for being part of the problem.

OK, back on track... Do you have internet connection? You need it for installing software from the repositories.
Assuming you have then use the last error message's recommend command first - sudo apt-get update - to refresh the software sources. Then use the same command you already tried in order to install the software in that live session.

PS - Yes, it's free and always will be free. The support _for updates_ is what varies. You can count on a new Ubuntu release every 6 months. The current one is 15.04 (April 2015) and will be followed by 15.10 (October 2015). In even years, in April, that release is special because it has long term support (LTS) so the current LTS is 14.04 (April 2014) and the next will be 16.04 (April 2016).
LTS releases are now supported for 5 years whereas all the other interim releases are supported for only 9 months. Support  in this context means having "live" software repositories from where you can download both updates and new software. When a given release reaches the EoL (End of Life) status you can no longer do one or the other (and you shouldn't anyway). However, you can upgrade to newer releases easily and, of course, for free.

Oh its ok Vladlenin, there's been alot of interesting information shared that I would like to read back over, 
or that is, if I'm actually able to install this OS, heh!

I'm just not in the position to reply to all of them at the moment, and even Leunam presented a very inviting solution to pursue, if this HD isn't waxed.
Its quite remarkable really, having such a variety of associated input to pour over, each time I open the thread.

I'll try it again after work today with an ethernet cable plugged in, and hope it can reach around this corpse of Vista to gain access. 

Come to think of it, I did use a small Linex program a year ago, that allowed me to go into my PC at work (with another hosed install of Vista) and much like this 
Live CD, peer through it like a ghost to retrieve files before I reformatted.  Left a real sense that one of these software companies, hailed from an advanced intelligence.

---

### Post by greg82 on 2015-05-27
Well, its slow going, because I ran into things different than what was described in the instructions. 

Ultimately I assume the object is to enable SMART on the hard drive, or rather all the partitions on the HD.

Then run the test on all those drives. Well I'm not convinced they're enabled yet, and not sure which command I need to enter

to enable them all. I can't recall how many partitions it had but pretty sure there was a C and D partition

So I hope they're clear enough to read, because I wasn't gonna type out all that gibberish.

(from top to bottom)

[http://i144.photobucket.com/albums/r178/buddahass/ubuntu/0_zpsf79hnlnx.jpg](http://i144.photobucket.com/albums/r178/buddahass/ubuntu/0_zpsf79hnlnx.jpg)

[http://i144.photobucket.com/albums/r178/buddahass/ubuntu/1_zpscdobqche.jpg](http://i144.photobucket.com/albums/r178/buddahass/ubuntu/1_zpscdobqche.jpg)

[http://i144.photobucket.com/albums/r178/buddahass/ubuntu/2_zpstvj3yczz.jpg](http://i144.photobucket.com/albums/r178/buddahass/ubuntu/2_zpstvj3yczz.jpg)

[http://i144.photobucket.com/albums/r178/buddahass/ubuntu/3_zpsnrkeqegi.jpg](http://i144.photobucket.com/albums/r178/buddahass/ubuntu/3_zpsnrkeqegi.jpg)

[http://i144.photobucket.com/albums/r178/buddahass/ubuntu/4_zpsf8yrn18u.jpg](http://i144.photobucket.com/albums/r178/buddahass/ubuntu/4_zpsf8yrn18u.jpg)

---

### Post by leunam12 on 2015-05-27
Ok, this is what you have to do:
1-Boot from your live USB stick or DVD
2-on the Unity bar on the left you will see, right in the middle, above the Amazon logo, the Ubuntu Software Center button; open it.
3-Search for "gsmartcontrol"
4-There will be no option to install probably, just click on "more info" and on the next screen it will tell you that the package is available from the "Universe" repository. Click on "Use this source".
5-After it's done querying the repository it will give you the option to install it. Install it.
6-Open GsmartControl, it will show you the available drives. the main hard drive is usually the one on the left. If the icon is red, there is nothing else to do; the drive is really bad and you have to replace it.
7-If the icon is gray double-click it and it will open a window with many tabs. 
8-On failing drives some of those tabs are highlighted in pink or red. Look at the error log and see how many errors are recorded.
9-The last tab allows you to perform tests, run the short and the long test.
10-Post results and pictures.

---

### Post by greg82 on 2015-05-27
There were no errors to report on any of the logs.
But the attributes tab was red.


 [http://i144.photobucket.com/albums/r178/buddahass/1-intro_zpsplzkrnsh.jpg](http://i144.photobucket.com/albums/r178/buddahass/1-intro_zpsplzkrnsh.jpg)

[http://i144.photobucket.com/albums/r178/buddahass/2_zpshq1ubcow.jpg](http://i144.photobucket.com/albums/r178/buddahass/2_zpshq1ubcow.jpg)

[http://i144.photobucket.com/albums/r178/buddahass/4-extended%20test_zpsvfdbwbks.jpg](http://i144.photobucket.com/albums/r178/buddahass/4-extended%20test_zpsvfdbwbks.jpg)
[URL="http://http://i144.photobucket.com/albums/r178/buddahass/4-extended%20test_zpsvfdbwbks.jpg"]
[/URL][http://i144.photobucket.com/albums/r178/buddahass/4-extended%20test_zpsvfdbwbks.jpg](http://i144.photobucket.com/albums/r178/buddahass/4-extended%20test_zpsvfdbwbks.jpg)

[URL="http://i144.photobucket.com/albums/r178/buddahass/5-both%20tests2_zpsqv18rslh.jpg"]http://i144.photobucket.com/albums/r178/buddahass/5-both%20tests2_zpsqv18rslh.jpg


[/URL]

---

### Post by leunam12 on 2015-05-27
My humble opinion is that if any of the attributes is showing red the best thing to do is try to get all your data off the disk and replace it. But let's see what other users with more knowledge have to say

---

### Post by greg82 on 2015-05-27
Geez, this place cleared out in a hurry. Maybe the writing is on the wall...and nobody wants to be the bearer of bad news. 

Hey thanks leunam, I checked the bottom of the laptop and the Win Vista COA sticker is there. 

Also,  if this is my [current HD,]("http://amzn.com/B001GV5XFO") do you have any idea if upgrading to [this one]("http://amzn.com/B006KYYBMI") would pose any problems?

---

### Post by leunam12 on 2015-05-28
No, I don't see any problem.

---

### Post by oldfred on 2015-05-28
Since a Vista era computer is drive PATA or SATA?
You have to have the same.

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

---

### Post by greg82 on 2015-05-28
Hi oldfred,


I'm just going on what the app. displayed it as having, but have no reason to believe it would be inaccurate.


I've changed out HD's in desktops before, but never in a laptop.

I presume its no different aside from the benefit of wiggle room.

  [IMG]http://i144.photobucket.com/albums/r178/buddahass/specs_zpsnvdbmvgz.jpg[/IMG]

---

### Post by greg82 on 2015-05-28
Since this new one is SATA I gather its compatible there, and the size dimensions are basically the same, give or take +0.20 / -0.25 mm,

It will however be my first run in with UEFI which I hope is easier to procure than pronounce.

---

### Post by cariboo on 2015-05-29
> **greg82 said:**
> Since this new one is SATA I gather its compatible there, and the size dimensions are basically the same, give or take +0.20 / -0.25 mm,

It will however be my first run in with UEFI which I hope is easier to procure than pronounce.

I'd make sure what type of drive your system has, being old enough to come with vista installed it may be a Pata drive, the best thing to do is pull the drive and have a look at it. You also shouldn't have to worry about UEFI, again because of the age of the laptop,

---

### Post by oldfred on 2015-05-29
Unless motherboard was designed with UEFI, then you still have BIOS. You cannot upgrade a system that does not already have it. And if a Vista era system it will not have UEFI.
Only some later Windows 7 and all Windows 8 systems are UEFI by default. A very few Windows 7 systems were installed in BIOS mode on hardware that was UEFI.

---

### Post by greg82 on 2015-05-29
Got it! 
Good to know.
One other problem I'm reading about is in regards to the new 4k [byte]("http://www.city-data.com/knowledge/Byte.html")  sectors instead of the "traditional" 512mb sectors, which I will apparently be  facing with this new drive. 
Have you heard of this problem, or has a  reliable workaround been achieved? [LEFT][COLOR=#000000]
[/COLOR][/LEFT]

---

### Post by oldfred on 2015-05-29
All new partitioning tools work the new 4K or SSD drives. Do not use old Windows or Linux tools. Partitions that you write into must be dividable by 8.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by greg82 on 2015-06-03
> **oldfred said:**
> All new partitioning tools work the new 4K or SSD drives. Do not use old Windows or Linux tools. Partitions that you write into must be dividable by 8.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Thanks oldfred for these informative replies.  

I noticed they were chosen to provide a range of various degrees of understanding, to a range of those with various degrees of understanding. 

I'm not sure if I should cap this thread off as answered, and begin another, or trudge on as the process unfolds, having received this new HD, and with it a new chapter of questions.

---

### Post by greg82 on 2015-06-08
Hey guys,

I need to get a file off this old hard drive stored in a folder in Vista. 
Can I do this with the Ubunta Live Disc that's still residing in the CDROM 
running it without installing? Or do I need to download a smaller LIVE utility?

---

### Post by oldfred on 2015-06-08
If system runs ok with Ubuntu. Often full Ubuntu needs a system with better video to run well.

If partition mountable? If drive was broken then no. BIOS first has to see a drive, then system has to mount it.
If BIOS does see drive, but you cannot mount it, then you can try testdisk and if that does not show files photorec which is part of testdisk.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

If NTFS, often Windows tools work better, but some are not free.

 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

