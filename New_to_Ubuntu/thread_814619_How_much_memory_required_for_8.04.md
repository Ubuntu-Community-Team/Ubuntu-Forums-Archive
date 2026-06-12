---
title: "How much memory required for 8.04?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by archer6 on 2008-05-31
I will be installing Ubuntu 8.04 on one of my laptops and would like to know what the optimum (not minimum) amount of memory should be? 

Going forward I plan on using this as my main OS and want to insure that I have enough memory for the future. 

Thanks!.....:)

---

### Post by Zacariaz on 2008-05-31
I have found that my 1 gig of ram doesn't quite cut it, and I run xubuntu which should be "lightweight".
Of course it also has to do with what you use your computer for, but I would recommend at least 1 gig and preferably 2.
I'm no exactly and expert tough.

---

### Post by abn91c on 2008-05-31
My installation is happy with 512MB on a wubi install, dell dimension 2400 and dell inspiron 1000

---

### Post by tamoneya on 2008-05-31
my laptop runs with 2GB and has zero performance issues.  I also have a server which has 1.5 GB and it is fine with the exception of the graphics but that is a separate issue.  I would say make sure you have 1.5 or more only since I have no experience with less.

---

### Post by anjilslaire on 2008-05-31
well, it also depends on your other system specs, to see what the bottlenecks are. No point in having 2 gigs or ram if you have a 800mhz cpu, for example.

---

### Post by Sef on 2008-05-31
> well, it also depends on your other system specs, to see what the bottlenecks are. No point in having 2 gigs or ram if you have a 800mhz cpu, for example.

It also depends on what you want to do.  If you are just using it for email, surfing, and word processing, then 512 mb ram will be enough.  So what are you going to use?

---

### Post by Joeb454 on 2008-05-31
I've found 1GB to be plenty enough for a standard users - such as web surfing, document writing etc. :)

---

### Post by TWO on 2008-06-01
> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    *

      700 MHz x86 processor
    *

      384 MB of system memory (RAM)
    *

      8 GB of disk space
    *

      Graphics card capable of 1024x768 resolution
    *

      Sound card
    *

      A network or Internet connection

Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation. 

> Recommended for visual effects

Visual effects provide various special graphical effects for your desktop to make it look and feel more fun and easier to use. If your computer is not powerful enough to run visual effects, you can turn them off and will still have a usable Ubuntu desktop.

Visual effects are turned on by default if you have a graphics card which is supported. For information on supported graphics cards, see DesktopEffects.

    *

      1.2 GHz x86 processor
    *

      384 MB of system memory (RAM)
    *

      Supported graphics card (see DesktopEffects)


They're the recommended system requirements according to ***[COLOR="Cyan"][this]("https://help.ubuntu.com/community/Installation/SystemRequirements")[/COLOR]***



I personally have 1.6GHz processor, with 1GB of memory and a 80GB HDD on a Dell Inspirion 1300 laptop. The only sluggishness I experience on Ubuntu are with the occasional buggy program or with Flash on the internet. Also, with new distros like Hardy Heron, there tends to be a a few weeks or where things might not seem as smooth, but once the updates come through, it gets better, I find...

---

### Post by Famicommander on 2008-06-01
My grandmother runs Xubuntu comfortably on a 1.4ghz Celeron with 384MB of RAM.

My computer has 768, and I haven't had a single issue.

---

### Post by bumanie on 2008-06-01
The minimum according to Canonical is 384mb of ram. I have hesrd of a couple of people claiming to be running 8.04 on less ram, but 384mb is the official minimum.

---

### Post by archer6 on 2008-06-01
> **archer6 said:**
> I will be installing Ubuntu 8.04 on one of my laptops and would like to know what the optimum (not minimum) amount of memory should be? 
Going forward I plan on using this as my main OS and want to insure that I have enough memory for the future. 

I realize now that I failed to include some important info in my original request as well as using the wrong title. 

The Title Should Read "How much memory is optimum for 8.04?"

It's being installed on my _ThinkPad T60_
2.0 GHz Core Duo
2.0 GB Ram
100 GB 5400 rpm HD (main drive with XP already installed)
120 GB 5400 rpm HD (in ultra bay for Ubuntu 8.04 OS)
ATI X1400 graphics
Intel WiFi card
 
Initially I used my old R51e ThinkPad (1.5 Celeron, 756mb ram 40GB 4200rpm drive gma shared graphics) to try out Ubuntu, I immediately liked it and now I'm going to move forward.

The Goal: 
Setup this dual boot configuration on my ThinkPad T60, so that I can run XP Pro, or Ubuntu natively, as needed, and gradually migrate to Ubuntu for as much of my work as possible. 

How I Will Use It For Work:
I have a few windows apps, like Maya, that demands resources, as I use it for design work and thus will have to stay with that program until something comes along as the Linux equivalent. I must also use Outlook and my BlackBerry desktop manager in the windows environment. I will be using Ubuntu for all other kinds of work, some of which will be graphics intensive, and more. Being so new to Ubuntu I've yet to have a chance to find all the programs I will be using.

Any suggestions are greatly appreciated. 

Thanks!
Archer

---

### Post by Joeb454 on 2008-06-01
I'm running on 2GB RAM, and currently have a few tabs open in Firefox, Transmission is running, and I have Xchat open, and here's my free -m

```
             total       used       free     shared    buffers     cached
Mem:          2005       1660        345          0         56       1029
**-/+ buffers/cache:        574       1431**
Swap:          486          0        486

```

So Apparently I'm using 574MB of my RAM :p I also have a VM of Ubuntu 8.10, which I can afford to Give 1GB RAM which is nice :D

---

### Post by sayakb on 2008-06-01
Firefox is a bad resource hog. Plus, every applet on the panel, every screenlet appear as python processes and eat up memory. My dad's laptop with 1GB RAM is at 75%-80% RAM usage when he's usually working. My laptop with 2G RAM never goes above 50.. now it is 42%.
So 2GB is recommended, and 1GB is good enough. Ofcourse, the minimum requirement constraint doesn't apply here :)

---

### Post by archer6 on 2008-06-01
> **Joeb454 said:**
> I'm running on 2GB RAM, and currently have a few tabs open in Firefox, Transmission is running, and I have Xchat open, and here's my free -m

```
             total       used       free     shared    buffers     cached
Mem:          2005       1660        345          0         56       1029
**-/+ buffers/cache:        574       1431**
Swap:          486          0        486

```

So Apparently I'm using 574MB of my RAM :p I also have a VM of Ubuntu 8.10, which I can afford to Give 1GB RAM which is nice :D

Wow, that's an eye opener. 
So for my education, what is the first line indicate? As it appears that you are reading the usage and remaining ram from the second line correct?
Then the third line being Swap file in which you are using O at the moment.

---

### Post by Joeb454 on 2008-06-01
Yep using 0 swap file :)

And the first line includes stuff that may be cached etc.

---

### Post by sayakb on 2008-06-01
You can adjust swap usage by changing [swappiness]("http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php"). Changing swappiness to 10 on >1GB RAMs improves overall performance.

---

### Post by buntunub on 2008-06-01
> **archer6 said:**
> I realize now that I failed to include some important info in my original request as well as using the wrong title. 

The Title Should Read "How much memory is optimum for 8.04?"

It's being installed on my _ThinkPad T60_
2.0 GHz Core Duo
2.0 GB Ram
100 GB 5400 rpm HD (main drive with XP already installed)
120 GB 5400 rpm HD (in ultra bay for Ubuntu 8.04 OS)
ATI X1400 graphics
Intel WiFi card
 
Initially I used my old R51e ThinkPad (1.5 Celeron, 756mb ram 40GB 4200rpm drive gma shared graphics) to try out Ubuntu, I immediately liked it and now I'm going to move forward.

The Goal: 
Setup this dual boot configuration on my ThinkPad T60, so that I can run XP Pro, or Ubuntu natively, as needed, and gradually migrate to Ubuntu for as much of my work as possible. 

How I Will Use It For Work:
I have a few windows apps, like Maya, that demands resources, as I use it for design work and thus will have to stay with that program until something comes along as the Linux equivalent. I must also use Outlook and my BlackBerry desktop manager in the windows environment. I will be using Ubuntu for all other kinds of work, some of which will be graphics intensive, and more. Being so new to Ubuntu I've yet to have a chance to find all the programs I will be using.

Any suggestions are greatly appreciated. 

Thanks!
Archer

Gawd I love Google!

Check [this]("http://usa.autodesk.com/adsk/servlet/item?siteID=123112&id=9683256") out. Turns out, your app works beautifully on Linux, and has for quite a long time. Your system specs are far more than what both Maya, and Linux require, so your way under the line there. [Here]("http://download.autodesk.com/us/maya/qualcharts/maya_70_linux.html") are the specs required for running it on Linux, provided by Autodesk.

K for an Outlook replacement, Novell's Evolution, which comes stock with Hardy, will do the trick quite nicely. Not too sure about Blackberry support, but Evolution quite easily handles everything else ive thrown at it (from a business persons standpoint) pretty well. Note: there is a learning curve here to get it to do everything Outlook can - not much of one, but its different. You will find, as I have, that there really is not much, if anything, that Linux cant do on the Business side. This is so, because of major players like Red Hat and Novell, who have grown massive businesses on both the Corporate IT side, and the Client side for daily business use. Interoperability is the key for Open Source, and the reason for its success, very unlike Proprietary counterparts who try to make it very difficult to play nicely with other systems.

---

### Post by archer6 on 2008-06-01
> **Joeb454 said:**
> Yep using 0 swap file :)

And the first line includes stuff that may be cached etc.

Excellent, it all makes sense now. ...:)

Thanks!

---

### Post by archer6 on 2008-06-01
> **LinuxIsInnovation said:**
> You can adjust swap usage by changing [swappiness]("http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php"). Changing swappiness to 10 on >1GB RAMs improves overall performance.

Swappiness, now there's a word that makes me laugh...and I love to laugh. Thanks for the link !....:)

If I'm not careful, I will be to speed pretty quickly here...heh!

This is a terrific forum, lucky me......:lolflag:

---

### Post by Joeb454 on 2008-06-01
No problem :)

---

### Post by archer6 on 2008-06-01
> **buntunub said:**
> Gawd I love Google!

Check [this]("http://usa.autodesk.com/adsk/servlet/item?siteID=123112&id=9683256") out. Turns out, your app works beautifully on Linux, and has for quite a long time. Your system specs are far more than what both Maya, and Linux require, so your way under the line there. [Here]("http://download.autodesk.com/us/maya/qualcharts/maya_70_linux.html") are the specs required for running it on Linux, provided by Autodesk.

Brilliant, I'm glad YOU were thinking, as I was asleep at the wheel....:)  
It's all this excitement really, as I'm just thrilled and super eager to put windows in my rear view mirror. Not only am I excited about Linux and most specifically Ubuntu, but I've found this great forum populated by some really terrific people that are very helpful, courteous, and knowledgeable.

Thanks for your research!....:)

---

### Post by philinux on 2008-06-01
Here's system monitors view of things. I've only got firefox open at the moment and I'm running compiz. However I've had open office, google earth and some other stuff open today. They are probably cached.

---

### Post by archer6 on 2008-06-01
> **philinux said:**
> Here's system monitors view of things. I've only got firefox open at the moment and I'm running compiz. However I've had open office, google earth and some other stuff open today. They are probably cached.

Thanks! That was a great screen shot, nice and large so I could really study it and be able to get a real feeling for the numbers. I'm still waiting for the 2nd hard drive to arrive so I have not done the install yet, therefore this is the first I've seen of this screen. 

All this is simply too good to be true! The amount of help, feedback and ideas I have received from the wonderful people on this forum is simply outstanding. I am so excited about this Ubuntu Linux project, I'm embarking on, and so glad that I just happened upon Ubuntu. I can see that this OS will provide me with a great deal of flexibility, terrific learning opportunities, to the point where I will not get bored anytime soon. 

Your contribution is appreciated...Thanks!...:)

---

### Post by spiderbatdad on 2008-06-01
I have nothing useful to add, but post count is post count!

---

### Post by archer6 on 2008-06-01
> **spiderbatdad said:**
> I have nothing useful to add, but post count is post count!
And I gave you a Thanks because of your honesty, and humor!
See.... everyone wins.

Cheers....:)

---

### Post by Joeb454 on 2008-06-01
> **spiderbatdad said:**
> I have nothing useful to add, but post count is post count!

I didn't think you'd actually do it, but I guess I was wrong :p

---

### Post by halitech on 2008-06-01
with what you are thinking about running, I wouldn't recommend it but I just installed 8.04 on a P3 866 with 256 meg of RAM and a 20 gig drive and it is running okay for me. I say okay with it being subjective due to the fact that it will be used for my 8year old son to go on PBSKids.org and other kids sites and will not be doing any heavy work. I haven't had a chance to test it with running a video or anything else but it does install and run.

---

### Post by Joeb454 on 2008-06-01
I'd go with 512MB RAM minimum - if you wanted Ubuntu, though 256MB should be plentiful for Xubuntu, which uses XFCE, not Gnome

---

### Post by archer6 on 2008-06-01
> **halitech said:**
> with what you are thinking about running, I wouldn't recommend it but I just installed 8.04 on a P3 866 with 256 meg of RAM and a 20 gig drive and it is running okay for me.

This is the amazing aspect of Ubuntu, is the small amount of resources required. Especially if one just wants to revive and older computer for web browsing and some writing. 

Cheers.....:)

---

### Post by archer6 on 2008-06-01
> **Joeb454 said:**
> I'd go with 512MB RAM minimum - if you wanted Ubuntu, though 256MB should be plentiful for Xubuntu, which uses XFCE, not Gnome

It's too late, I'm already fully invested in Ubuntu.....:)

And no thanks to resource hogging windows (sheesh I hate to use that reference here) I've got plenty of memory. Like 2GB.

I'm fast approaching a complete elimination of windows, full implementation of Ubuntu and the countdown starts NOW!....;)

Cheers

---

### Post by Joeb454 on 2008-06-01
Not just Ubuntu - but Linux in general :D

And I keep Windows around, just in case :) Though I've not booted into it for ages

---

### Post by halitech on 2008-06-01
> **archer6 said:**
> This is the amazing aspect of Ubuntu, is the small amount of resources required. Especially if one just wants to revive and older computer for web browsing and some writing. 

Cheers.....:)

I agree, I've also got an old P2 300 that I had 192Meg of RAM in and installed Suse 10.2 just for the heck of it to see if it would work and it did, granted it was slower then molasses going up hill in the middle of winter but it did run ~L~  I find it interesting to see just what the modern distros will do on a box that has long been relegated to the scrap heap in the windows world, seems no matter what there is a version that will run on old hardware as long as it is above a 486

---

### Post by archer6 on 2008-06-01
> **Joeb454 said:**
> Not just Ubuntu - but Linux in general :D

And I keep Windows around, just in case :) Though I've not booted into it for ages

True, that's what I understand is Linux in general is great with managing resources. Even though I like to make fun of it, Windows has served me well in the past. So in my case I will tuck it away in my office somewhere out of sight....

I became aware of the Ubuntu distro at just the right time for me, when I was ready for a change, as I have no interest whatsoever in Vista, as well as the fact that I tend to plan well in advance. While I have had an awareness of Linux for quite some time, however I did not see a distro that had a particular appeal. Nor did I have the time, and of course timing is everything. Thus I'm now going for Ubuntu because of all the reasons most developers & enthusiasts that I know move into Linux, and that's because I can make it mine. An endless opportunity to create, which suits me just fine.....;)

---

### Post by CrimsonEclipse on 2008-06-01
I'm using 512meg just fine with an AMD 1400+ (2.4ghz)

How do you get that resource page?

CE

---

### Post by Joeb454 on 2008-06-01
Which resource page?

---

### Post by buntunub on 2008-06-01
> **archer6 said:**
> Brilliant, I'm glad YOU were thinking, as I was asleep at the wheel....:)  
It's all this excitement really, as I'm just thrilled and super eager to put windows in my rear view mirror. Not only am I excited about Linux and most specifically Ubuntu, but I've found this great forum populated by some really terrific people that are very helpful, courteous, and knowledgeable.

Thanks for your research!....:)

No problem. Thats exactly what these forums are for. Also, thanks for the tip about swappiness by previous poster. Never thought of trying that before, but it really makes a difference.

---

### Post by Victormd on 2008-06-01
> **archer6 said:**
> It's being installed on my _ThinkPad T60_
2.0 GHz Core Duo
2.0 GB Ram
100 GB 5400 rpm HD (main drive with XP already installed)
120 GB 5400 rpm HD (in ultra bay for Ubuntu 8.04 OS)
ATI X1400 graphics
Intel WiFi card

I have ubuntu running on an AMD Athlon 2800+ w/ 1GB RAM, a P4 3.2 w/ 2GB RAM, and a laptop core2duo w/2GB RAM, and Ubuntu runs fine on all of them!!! I'd say 512 to 1GB should be more than enough...

---

### Post by CrimsonEclipse on 2008-06-01
> **Joeb454 said:**
> Which resource page?

The one that shows memory use, cpu use, page swap, etc

CE

---

### Post by CrimsonEclipse on 2008-06-03
Never mind, found it.

CE

---

