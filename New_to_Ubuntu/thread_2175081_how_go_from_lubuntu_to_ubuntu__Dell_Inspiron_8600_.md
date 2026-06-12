---
title: "how go from lubuntu to ubuntu / Dell Inspiron 8600 non-PAE"
date: 2013-09-17
forum: New to Ubuntu
---

### Post by sharon2 on 2013-09-17
I made the installation disk “lubuntu-12.04-alternate-i386.iso” for my old Dell Inspiron 8600(a 32 bit machine) I installed lubuntu (no partitions).. yay!. Was sooo happy and confident: the installed lubuntu boots; its browser connects to Internet. Yay! HOWEVER (:(), the desktop is way different from the one pictured in the user manuals and tutorial screenshots. It's just a blueish screen(with a kind of wavy design in the middle) and a few small icons onthe bottom left (one of which goes to the browser, and one of which lets me logoff or shutdown) and a few small icons on the bottom right.  I believe I attached a jpg that I photographed.
How do I now bring in a full ubuntu with a full desktop – so that I can use it? (as it is now, it's not useful given my ignorance.) I made another disk - “ubuntu-12.04.3-desktop-1386.iso” ?? Is that the one I should use to now upgrade my lubuntu to ubuntu to get the full desktop?
How do I do it? When I now boot, then insert the ubuntu installation disk, nothing happens. Do I have to press some special keys at boot time to get it to go to the ubuntu installation disk?
As you can see, I'm a rank beginner here – I appreciate any help I can get. Maybe I need a special key sequence? … or maybe it's far more complicated … sorry for this elementary question.  I'm totally stuck.
Sharon:confused:

---

### Post by slickymaster on 2013-09-17
See this: [Getting Back to a Pure Ubuntu]("http://www.psychocats.net/ubuntu/pureubuntu")

---

### Post by cmcanulty on 2013-09-17
You have a full desktop you can add panels by right cl the panel and add items or you can add more panels that way also. You can also add whatever you want to the desktop by dragging. Experiment with clicking all the icons and see what's there

---

### Post by vasa1 on 2013-09-17
> **slickymaster said:**
> See this: [Getting Back to a Pure Ubuntu]("http://www.psychocats.net/ubuntu/pureubuntu")
OP says she's a rank beginner. That link is pretty intense.

---

### Post by philinux on 2013-09-17
> **sharon2 said:**
> I made the installation disk “lubuntu-12.04-alternate-i386.iso” for my old Dell Inspiron 8600(a 32 bit machine) I installed lubuntu (no partitions).. yay!. Was sooo happy and confident: the installed lubuntu boots; its browser connects to Internet. Yay! HOWEVER (:(), the desktop is way different from the one pictured in the user manuals and tutorial screenshots. It's just a blueish screen(with a kind of wavy design in the middle) and a few small icons onthe bottom left (one of which goes to the browser, and one of which lets me logoff or shutdown) and a few small icons on the bottom right.  I believe I attached a jpg that I photographed.
How do I now bring in a full ubuntu with a full desktop – so that I can use it? (as it is now, it's not useful given my ignorance.) I made another disk - “ubuntu-12.04.3-desktop-1386.iso” ?? Is that the one I should use to now upgrade my lubuntu to ubuntu to get the full desktop?
How do I do it? When I now boot, then insert the ubuntu installation disk, nothing happens. Do I have to press some special keys at boot time to get it to go to the ubuntu installation disk?
As you can see, I'm a rank beginner here – I appreciate any help I can get. Maybe I need a special key sequence? … or maybe it's far more complicated … sorry for this elementary question.  I'm totally stuck.
Sharon:confused:

Thats how lubuntu is supposed to look. Too be honest the easiest solution since you already have the ubuntu iso would be to install that and wipe lubuntu.

Caveat. Whats the specs of the  machine?

---

### Post by sharon2 on 2013-09-17
Thank you philinux! for your quick response.     ... but that is exactly my idea too.  You said:  "install the ubuntu iso and wipe lubuntu"  My problem is: **How do I do that? ** When do I insert my ubuntu iso disk?  During the boot (of the current lubuntu) or after?  Is there a special key sequence to make lubuntu read the ubuntu iso?  (specs: I have a Dell Inspiron 8600 32 bit machine ... it used to have Windows XP but that was wiped out (by intention!) when I installed lubuntu.

Again, I truly am a beginner with Ubuntu (but not really a beginner with computers).  Have scoured the web to help me go forward ...  I bet there is a simple answer ... if I could only express the problem clearer.  It seems simple.... Sharon

---

### Post by philinux on 2013-09-17
> **sharon2 said:**
> Thank you philinux! for your quick response.     ... but that is exactly my idea too.  You said:  "install the ubuntu iso and wipe lubuntu"  My problem is: **How do I do that? ** When do I insert my ubuntu iso disk?  During the boot (of the current lubuntu) or after?  Is there a special key sequence to make lubuntu read the ubuntu iso?  (specs: I have a Dell Inspiron 8600 32 bit machine ... it used to have Windows XP but that was wiped out (by intention!) when I installed lubuntu.

Again, I truly am a beginner with Ubuntu (but not really a beginner with computers).  Have scoured the web to help me go forward ...  I bet there is a simple answer ... if I could only express the problem clearer.  It seems simple.... Sharon

In lubuntu if you right click on the ubuntu iso it should offer to open with a disk burner. You need to burn "as an image". probably to a dvd as it wont fit on a cd. That will make a bootable dvd.
What are the systems specs.

I'm not familiar with lubuntu either.

---

### Post by mastablasta on 2013-09-17
on boot. Lubuntu is ubuntu with LXDE desktop.

If your computer can handle Ubuntu you can just open software center search for ubuntu desktop and install it.

Linux is modular so there are plenty of various desktops availbale that you can stick to the base operating system (windows always has only one desktop environment). Ubuntu uses Unity with Gnome, Lubuntu uses LXDE, Xubuntu uses XFCE and Kubuntu uses KDE. besides these major ones there are even more desktops and windows managers available. Mate, Cinamon, Open box, E17, IceWM....

---

### Post by Impavidus on 2013-09-17
To convert to pure Ubuntu either wipe the drive and install from a live dvd or use the "Get back to a pure ubuntu" link (which basically says: install ubuntu-desktop and change some other things that aren't really that important).

However, I looked up the specs of that Dell Inspiron 8600:
CPU: Intel Pentium M 1.4 GHz 32 bit
RAM: 512.0 MB (expandable to 2GB)
Graphics: AGP 4x - ATI Mobility Radeon 9000 - 32.0 MB DDR SDRAM

You may be better of with the lighter desktop environment of Lubuntu.

---

### Post by WacoJohn on 2013-09-17
Pardon me if I ramble.  I am no Linux expert, but might be able to explain things on a beginner level.  I hope this doesn't get too long.  As you know, Ubuntu Linux comes in many 'flavors'.  Each one ALSO comes with choices for preconfigured DESKTOPS.  This flavor comes with KDE desktop, that flavor comes with GNOME desktop, and that one with XFCE desktop.  I THINK you have Lubuntu .. with the LXDE desktop ... and for an older computer it is probably quite suitable.  The further up the ladder you go, the more modern machine you need.

In some cases, you can start with one desktop and even switch to a different one ... and you can learn about that later.  Keep in mind, each 'desktop' is highly customizeable.

I believe your problem is more that of a newbie than anything else ... because you can customize just about ANY desktop to your liking.  If you spend enough time with what you have, you will learn how to do this.  I agree, the default desktop you have looks pretty lean and limited ... but if you click on the upper left toolbar button, you will find (all) applications/utilities that are available to you .. much more than are indicated on the desktop.  With those applications, you find Lubuntu to be much more useful than assumed.  It is a very good distribution for beginners ... for reasons I won't go into right now.

Know that you can ADD programs .. UNINSTALL programs, and customize to a great extent .. eventually arriving at a VERY useful installation.  It will take some time to learn it all, and you will make mistakes .. so keep that LUBUNTU CD handy .. you may have to start from scratch a few times as you learn.

My major point I want to make is to advise you to concentrate on one distribution .... ... some come more 'loaded' up with 'stuff' than others ... but as a beginner, you really want to start learning the fundamentals ... and Lubuntu is a GREAT distro to learn from.  Know that different desktops behave differently.  For example, the file manager in Lubuntu and in it's "native" desktop works somewhat differently than Windows File Manager or OTHER Linux distro's file manager ... which is why you want to concentrate on ONE distro at a time .. or you can really get overwhelmed in learning.

Any more questions you have .. I will TRY to answer.

If you want to REPLACE Lubuntu with Ubuntu (from the other CD you have), you can BOOT from that CD and just tell it to install Ubuntu and use the entire disk on the computer.  It will wipe out the hard drive and install itself (Ubuntu) ... but again .. I recommend you stay with Lubuntu for now .. it will serve your needs quite well .... in my opinion.

---

### Post by WacoJohn on 2013-09-17
> **Impavidus said:**
> However, I looked up the specs of that Dell Inspiron 8600:
CPU: Intel Pentium M 1.4 GHz 32 bit
RAM: 512.0 MB (expandable to 2GB)
Graphics: AGP 4x - ATI Mobility Radeon 9000 - 32.0 MB DDR SDRAM

You may be better of with the lighter desktop environment of Lubuntu.

I totally agree with Impavidus.

I am running Lubuntu on an old Compaq Windows ME machine .. 512MB RAM max.  If your computer is RAM expandable to 2GB ... I HIGHLY recommend more than 512MB.  That is only enough to slowly chug along ... give yourself at least 1GB ... and Lubuntu should zoom along well.  Not so with 512MB.  Memory is cheap ... you will not like ANY distro with only 512MB .... it barely performs without more.

---

### Post by philinux on 2013-09-17
If the OP has not put any extra ram in that machine then yes best to stick with lubuntu if it runs ok.

---

### Post by sharon2 on 2013-09-17
Thank you again.  some progress ... but no cigar.  I figured out that to get the computer to boot from the iso DVD (it IS a DVD, not a CD ...), I needed to do the press F12 business during the initial boot.  Doing that, I was given the option of booting from the Hard Drive or from the DVD (ie, my ubuntu iso).  I chose the DVD (of course)  but got "This kernel required the following features not present on the CPU: pae    Unable to boot - please use a kernel appropriate for your CPU"   Rats!!
I'm familiar with this nasty message.  It appeared the first time I tried to boot ubuntu iso.  (That's when I did some net researching on threads like this, and discovered that I probably needed to go to lubuntu.  (which I did and which worked.)  Maybe I should stick with lubuntu?  It seems a shame though.  
Sharon

---

### Post by WacoJohn on 2013-09-17
Sounds like you might be trying to install a 64-bit UBUNTU on a 32-bit CPU.  Either burn a 32-bit iso of your choice, or stick to (32-bit) Lubuntu.

---

### Post by philinux on 2013-09-17
Lubuntu sounds fine for that machine. It is a really good flavour of ubuntu. You just need to get used to it.

---

### Post by philinux on 2013-09-17
> **WacoJohn said:**
> Sounds like you might be trying to install a 64-bit UBUNTU on a 32-bit CPU.  Either burn a 32-bit iso of your choice, or stick to (32-bit) Lubuntu.

In the original post Sharon says its an i386 ubuntu iso.

---

### Post by philinux on 2013-09-17
Sharon if you decide to stick with lubuntu there's plenty of info out there.  

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)

---

### Post by Bashing-om on 2013-09-17
Sharon; Hi !

Let me say of Lubuntu ... I have used 'buntu for years and have experienced several desk top environments .. 
Now my desk top of preference after all these years is indeed "xfce" --- same same as your Lubuntu desk top.
As John advises ... give it a whirl and a bit of time to learn what your capabilities are with that desk top and how to set it up exactly to meet your desires.
We do run Lubuntu in this house, and we are well pleased with it !

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

---

### Post by sharon2 on 2013-09-17
Thank you all!  What helpful and quick responses!  My plan - based on what I learned from you: I will investigate how to acquire more memory (per one response which I cannot now find) AND I will stick with lubuntu (per WacoJohn) for a while.
But, WacoJohn, when you say "click on the upper left toolbar button", you lose me.  My desktop has nothing in the upper part of the screen (right or left) - see attached.  I have only the buttons shown in the attachment.  I want to get and learn GIMP.  But how do I "get" GIMP in the first place.  What is the technique for installing (for example, on my mac, I move the .dmg file from the "Downloads" folder into the Applications folder)
Sharon

---

### Post by Hylas de Niall on 2013-09-17
> **Bashing-om said:**
> Sharon; Hi !

Let me say of Lubuntu ... I have used 'buntu for years and have experienced several desk top environments .. 
**Now my desk top of preference after all these years is indeed "xfce" --- same same as your Lubuntu desk top.**
As John advises ... give it a whirl and a bit of time to learn what your capabilities are with that desk top and how to set it up exactly to meet your desires.
We do run Lubuntu in this house, and we are well pleased with it !

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

'lxde' you mean! ;)  
and WacoJohn meant the *lower* left blue button (where thge windows 'start' would be)*

But yes, Lubuntu is just the thing for a machine of those specs.

[https://help.ubuntu.com/community/Lubuntu](https://help.ubuntu.com/community/Lubuntu)

[https://help.ubuntu.com/community/Lubuntu/Support](https://help.ubuntu.com/community/Lubuntu/Support)

*when you click this a menu will appear, and under one of it's sub-menus you will find Lubuntu Software Centre. open that and you will find Gimp under the graphics heading.

Hope that helps, and enjoy your new system!

---

### Post by Bashing-om on 2013-09-17
Sharon;

That screenshot is a of a standard/default Lubuntu desktop. In your instance the icons to click and start exploring is those in the lower left; The leftmost with the majority of system application access.

The preferred method for starters to install additional software is via the 'buntu software repositories - thousands of applications- ready, tested. validated. virus free. Several ways to access this "repository" -> In your case may I suggest that you become familiar with the utility "synaptic" that is available from clicking that left most icon -> system tools ->synaptic (synaptic is a front end for the underling package management system). Synaptic is a versatile tool that is destructive if misapplied in use !  Read the help files.
A more user friendly application is "Lubuntu Software Center" from that same menu !
A more direct method to obtain software is the direct application of the package manager from the command line. I cannot vouch that "gimp" is fully functional within Lubuntu. There may be a bit of problem with themes and icons (??) due to differing desk top environments and how they are built and implemented.. functionally I would not expect any problem.

If you are in a rush to have "gimp" the fast way to do it is as simple as the terminal command:
```

sudo apt-get install gimp

```
and the good deed is done ! // The system will take care of everything and you have an icon in the applications menu to start the application.
How cool is that !

However, may I caution you to familiarize yourself with Lubuntu, and how to get around in it before venturing forth with other softwares.

[INDENT][INDENT]above all enjoy
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-09-18
The main limitation here is that the computer does not show the PAE flag.

While Lubuntu 12.04 works without PAE it is only supported a month more. After that you have to do some surgery to get a recent version running: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

If this does not sound appealing you could also install the non-PAE version of Bodhi Linux. There's a link in my signature.

---

### Post by verymadpip on 2013-09-19
Would 12.04 non-pae mini-iso plus lubuntu desktop work?
Although that whole process may be a bit overwhelming.

---

### Post by mörgæs on 2013-09-19
Like I said: 12.04 will work but only one month from now.

---

### Post by verymadpip on 2013-09-19
> **mörgæs said:**
> Like I said: 12.04 will work but only one month from now.

Perhaps I need to start a new thread with this for my own clarification.  Anyway:

Installing from the 12.04 mini-iso & then adding whatever DE or WM or whatever does NOT get me 5 years support? (Even 3 would do)!
I suppose that the lubuntu-desktop packages may become outdated...
Do I have that right? 

I ask because I used this route to revive an ancient Compaq TC1000 tablet.
I actually did mini-iso + open box +lxpanel.
The information would be handy for me if not anybody else.

I've started a thread here:
[http://ubuntuforums.org/showthread.php?t=2175646](http://ubuntuforums.org/showthread.php?t=2175646)

---

### Post by Jonathan Precise on 2013-09-19
> **WacoJohn said:**
> I totally agree with Impavidus.

I am running Lubuntu on an old Compaq Windows ME machine .. 512MB RAM max.  If your computer is RAM expandable to 2GB ... I HIGHLY recommend more than 512MB.  That is only enough to slowly chug along ... give yourself at least 1GB ... and Lubuntu should zoom along well.  Not so with 512MB.  Memory is cheap ... you will not like ANY distro with only 512MB .... it barely performs without more.

I disagree with that.
I have an old PC with 495 MB RAM, non-expandable. That computer has the latest LTS release (12.04.3) and running very fast!!! However, that PC supports PAE.

If your PC does not support PAE, try Xubuntu instead, as it has support until 2015 (_**L**_ubuntu 12.04 is strangely not LTS, but _**X**_ubuntu, _**K**_ubuntu, and _**U**_buntu are). Lubuntu only has support until October, 2013. :(

Note: Xubuntu is heavier than Lubuntu.

---

### Post by verymadpip on 2013-09-19
Oh, a few days ago someone (I just can't recall who it actually was) mentioned LXLE in a different thread, which may be useful here:
[http://lxle.net/](http://lxle.net/)

It seems to be an unofficial Lubuntu based LTS op sys.

---

### Post by mörgæs on 2013-09-19
Let's stop the discussion here until original poster returns. 

For LXLE there's several threads in which to participate.

---

### Post by sudodus on 2013-09-20
> **verymadpip said:**
> Perhaps I need to start a new thread with this for my own clarification.  Anyway:

Installing from the 12.04 mini-iso & then adding whatever DE or WM or whatever does NOT get me 5 years support? (Even 3 would do)!
I suppose that the lubuntu-desktop packages may become outdated...
Do I have that right? 

I ask because I used this route to revive an ancient Compaq TC1000 tablet.
I actually did mini-iso + open box +lxpanel.
The information would be handy for me if not anybody else.

Yes, please start a new thread and post a link to it here, so that we can find it easily :-)

Make a good and descriptive title to attract people who are interested and who know about your issues. [COLOR=#696969]I will read it and try to help you.
[/COLOR]

---

