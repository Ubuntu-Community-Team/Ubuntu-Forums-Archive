---
title: "Absolute NOOB. 8.04 64 won't install. Help. Pics inside."
date: 2008-06-10
forum: New to Ubuntu
---

### Post by flak_monkey on 2008-06-10
I am an absolute NOOB at linux. I've used Ubuntu once, I am tired of using Maya in xp because of all of the errors it has with drivers and crap. One video card driver will work with Maya but screw up games, and the other way around. I hate it. I have

2x Opteron 250
Tyan Thunder K8WE
3gb DDR 400 
a bunch of SATA hard drives (I have set aside a partition for Linux but I do not know how to choose where to install to)
Nvidia 7800GTXOC 
Creative Audigy 4 Pro.

Top of the line (3 years ago, hehehehe)

I want to put Ubuntu on. I can't get it to install. Can somebody walk me through this step by step? I have read a lot of stuff and I didn't understand any of it. 

I took some pictures of the install. It's a lot of gibberish with a few error messages. Is this normal? What should I do? Is my hardware even compatible?

[IMG]http://farm4.static.flickr.com/3133/2568998144_0b9ec4fc15_b.jpg[/IMG]
[IMG]http://farm4.static.flickr.com/3275/2568996892_0c7fb45644_b.jpg[/IMG]
[IMG]http://farm4.static.flickr.com/3131/2568997406_dd3e4bc4e9_b.jpg[/IMG]

It makes screens like this for a good 10 minutes. I don't know if it's supposed to look like this or not.

HELP!

Chris

---

### Post by gr4nf on 2008-06-10
Did you get the 64 of 32 bit version of Linux?

secondly, try going into the bios/setup (there should be instructions to do this on the opening screen of startup) and seeing if boot from CD is an option above your hard drives in the boot order.

---

### Post by JoshuaRL on 2008-06-10
Sorry dude, I'm not seeing any pictures.  You can use the Manage Attachments button on the post page to add them to your post.

---

### Post by gr4nf on 2008-06-10
Nono, there are pictures. Its a problem on your end.

---

### Post by wannadumpwindows on 2008-06-10
If you burned your own disc, you might try it again at the slowest possible speed. Also a good idea to compare the MD% sums of your disc and then one from the Ubuntu site. Those are the two simplest things to try first. You'd be surprised how many bad burns there are . . . . .

---

### Post by wannadumpwindows on 2008-06-10
> **gr4nf said:**
> Nono, there are pictures. Its a problem on your end.

Yeah, I can see all the pics over here too.

---

### Post by bob16 on 2008-06-10
hey i know what your problem is

it hapenned with me when i was trying to install gusty

insted of choosing install, try safe graphics mode

its going to work trust me

---

### Post by gr4nf on 2008-06-10
@JoshuaRL:

Use CTRL+U to view page source. That will tell you if your browser is failing.

---

### Post by jimv on 2008-06-10
Unless you're going to use more than 4 gigs of RAM, use the 32 bit version.  64 bit version is a headache for compatibility with drivers and some programs.

---

### Post by JoshuaRL on 2008-06-10
> **gr4nf said:**
> Nono, there are pictures. Its a problem on your end.

Okay then, I'm behind a work firewall right now.  Thanks for letting me know.

> **jimv said:**
> Unless you're going to use more than 4 gigs of RAM, use the 32 bit version.  64 bit version is a headache for compatibility with drivers and some programs.

I disagree with that.  I have 64bit on mine, and have hardly any problems.  Seriously, only one or two things in totality can be traced to using 64bit instead of 32bit.  Especially on Hardy, 64bit installs are super easy.  If you have the processor, you may as well use it.  We're heading there anyway, may as well jump ahead of the curve.

You will see a slight increase in day-to-day computing (very slight for some) and up to 30% faster on intensive computing like encoding, compiling, and 3D modeling.  This isn't like Windows where you're limited at almost every software choice.

---

### Post by flak_monkey on 2008-06-10
> **gr4nf said:**
> Did you get the 64 of 32 bit version of Linux?

secondly, try going into the bios/setup (there should be instructions to do this on the opening screen of startup) and seeing if boot from CD is an option above your hard drives in the boot order.
While I'm a NOOB to linux, I am an experienced PC technician. 

Yes, I have the x64 disk. 

Yeah, my BIOS is set to boot from CD, it's the only way that the Tyan board will boot from CD with SATA drives attached. It's a picky motherboard. I get the Ubuntu screen where it asks me what it wants to do, "Try without installing," and other options. 

I heard somebody mention try installing without ACPI but I do not know how to turn that off.

---

### Post by flak_monkey on 2008-06-10
> **jimv said:**
> Unless you're going to use more than 4 gigs of RAM, use the 32 bit version.  64 bit version is a headache for compatibility with drivers and some programs.I will be using MAYA 64, for modeling, rendering, and animating. I might as well use windows if I'm going to use 32 bit 0S.

---

### Post by flak_monkey on 2008-06-10
> **bob16 said:**
> hey i know what your problem is

it hapenned with me when i was trying to install gusty

insted of choosing install, try safe graphics mode

its going to work trust me

That's where these pics came from. Is this normal to see in an install? Or is it graphical like windows? I don't even know how it's supposed to look, how long it takes, etc.

---

### Post by gr4nf on 2008-06-10
The ubuntu install is a live cd as well as an install. You could try the alternate install instead, which has no GUI, and might be easier on the system.

---

### Post by flak_monkey on 2008-06-10
> **gr4nf said:**
> The ubuntu install is a live cd as well as an install. You could try the alternate install instead, which has no GUI, and might be easier on the system.
I am getting the same messages with the GUI Safe install option and acpi=off and noacpi checked. 

Is it supposed to look like this when it installs? 

it keeps adding new lines to that screen for about ten minutes. The cd drive isn't being read from. I don't really know what it should look like. 

You know, for something that's supposed to be so much better and so revolutionary, hell at least windows will install almost every time.

---

### Post by CyberCowboy on 2008-06-10
Second using the alternate install CD, I had trouble with Hardy on a 64 bit quad core chipset with the live CD, but Alt worked fine.

Also as a sidenote I HIGHLY recommend when you get to the partitioning portion of the setup to do a manual partition and to make a seperate /home directory.  The reason for this is so that if you screw something up and have to re-install all of your personal setting are in a seperate partition that you can select to not format.

If you need help with setting the seperate /home let me know.

---

### Post by flak_monkey on 2008-06-10
> **CyberCowboy said:**
> Second using the alternate install CD, I had trouble with Hardy on a 64 bit quad core chipset with the live CD, but Alt worked fine.

Also as a sidenote I HIGHLY recommend when you get to the partitioning portion of the setup to do a manual partition and to make a seperate /home directory.  The reason for this is so that if you screw something up and have to re-install all of your personal setting are in a seperate partition that you can select to not format.

If you need help with setting the seperate /home let me know.

ah so there's an alternate CD? Interesting. I'll try that.

How do I get the other CD? i don't see it on the site.

---

### Post by JoshuaRL on 2008-06-10
> **flak_monkey said:**
> I am getting the same messages with the GUI Safe install option and acpi=off and noacpi checked. 

Is it supposed to look like this when it installs? 

it keeps adding new lines to that screen for about ten minutes. The cd drive isn't being read from. I don't really know what it should look like. 

You know, for something that's supposed to be so much better and so revolutionary, hell at least windows will install almost every time.

First of all, they're suggesting you burn an Alternate CD to install with.  You need to go back to the [download page](http://www.ubuntu.com/getubuntu/download) and right below where it says "Download Now" you need to check the Alternate CD box.  That will get you the ISO you need.

Second, the term "better" is really subjective.  For some, Ubuntu or Linux may not be better.  But for me and most here, Windows is definitely not better.  Installations are always difficult and any given OS will do different things with different hardware.  And I've had more problems with fresh Windows installs than Ubuntu personally.

The thing you need to remember is that you have probably had many years using and manipulating Windows.  The way you think about how software should work is through that mindset.  Not that I'm asking this of you, but if you had devoted that much time to GNU/Linux, then you would be just as frustrated with a fresh Windows install.  Ubuntu is not Windows.  Windows is not Ubuntu.  You'll need to forget some hard-won lessons on how to do things and how an OS thinks.  Sorry, but it may be harder for you to switch then for someone that has no computer experience at all.

But the good news is that you seem smart and willing to learn.  In fact, you surprised me with how fast you picked up the boot-time options and how to put those in.  Just that little thing can sometimes give people fits.

Now, let's try the Alternate CD and see if that works.

---

### Post by flak_monkey on 2008-06-10
> **JoshuaRL said:**
> First of all, they're suggesting you burn an Alternate CD to install with.  You need to go back to the [download page](http://www.ubuntu.com/getubuntu/download) and right below where it says "Download Now" you need to check the Alternate CD box.  That will get you the ISO you need.

Second, the term "better" is really subjective.  For some, Ubuntu or Linux may not be better.  But for me and most here, Windows is definitely not better.  Installations are always difficult and any given OS will do different things with different hardware.  And I've had more problems with fresh Windows installs than Ubuntu personally.

The thing you need to remember is that you have probably had many years using and manipulating Windows.  The way you think about how software should work is through that mindset.  Not that I'm asking this of you, but if you had devoted that much time to GNU/Linux, then you would be just as frustrated with a fresh Windows install.  Ubuntu is not Windows.  Windows is not Ubuntu.  You'll need to forget some hard-won lessons on how to do things and how an OS thinks.  Sorry, but it may be harder for you to switch then for someone that has no computer experience at all.

But the good news is that you seem smart and willing to learn.  In fact, you surprised me with how fast you picked up the boot-time options and how to put those in.  Just that little thing can sometimes give people fits.

Now, let's try the Alternate CD and see if that works.

I understand that they aren't the same. I just have been used to making windows my slave for so long, it's frustrating being thrown into something that doesn't behave as expected when people talk it up. Believe me, I used Ubuntu with Houdini and it was great. And FAST. I've used it with Maya as well and it blows windows out of the water. I'll use windows for everything but work. But I need to be able to put linux on a resume.

---

### Post by JoshuaRL on 2008-06-10
> **flak_monkey said:**
> I understand that they aren't the same. I just have been used to making windows my slave for so long, it's frustrating being thrown into something that doesn't behave as expected when people talk it up. Believe me, I used Ubuntu with Houdini and it was great. And FAST. I've used it with Maya as well and it blows windows out of the water. I'll use windows for everything but work. But I need to be able to put linux on a resume.

Don't worry about it, it's just something to keep in mind.  I've had plenty of my own problems, and times I wanted to put my boot through the mainboard.  But we all do want to help, and hope you get what you want from Ubuntu.  And since you do know so much about Windows, I'm sure you appreciate the security and software update architecture that GNU/Linux has.  In my opinion, they are lightyears ahead of Microsoft.

---

### Post by flak_monkey on 2008-06-10
Okay, now it works with the alternate version. HOWEVER. 

I have a LiteOn SATA DVD-R combo drive. The installer doesn't know what to do about it. 

I also have no floppy drive.

So I need to figure out a way to get the proper drivers for the cdrom so it can "detect and mount"


Lite-on DVDRW LH-20A1S
Chris

---

### Post by JoshuaRL on 2008-06-10
Is the install finished?  If so, what part of the DVD drive doesn't work?  For that kind of hardware the automagical detection usually works, even if it complains some.  If it doesn't we can see what there is to do, but you might give it a try.

---

### Post by CyberCowboy on 2008-06-10
Agree with Joshua this may complain during install but seems to work afterwards, I've also got a lite-on DVD-R SATA and it worked fine for me,   Do you know what model it is you have?

---

### Post by flak_monkey on 2008-06-10
> **JoshuaRL said:**
> Is the install finished?  If so, what part of the DVD drive doesn't work?  For that kind of hardware the automagical detection usually works, even if it complains some.  If it doesn't we can see what there is to do, but you might give it a try.

It says the install cannot be completed because it cannot detect and mount the cd drive. I don't know what to tell it to look for when it starts asking. I'm just sort of guessing at what it wants. But I don't have a floppy. It doesn't seem to see that I have a cd drive I guess.

---

### Post by flak_monkey on 2008-06-10
> **CyberCowboy said:**
> Agree with Joshua this may complain during install but seems to work afterwards, I've also got a lite-on DVD-R SATA and it worked fine for me,   Do you know what model it is you have?
Lite-on DVDRW LH-20A1S

---

### Post by JoshuaRL on 2008-06-10
What errors does it give you?  Are there a list of drivers to choose from?  The cables are all seated correctly right?  Is it by any chance connecting to a IDE port through a IDE-to-SATA adapter?

---

### Post by flak_monkey on 2008-06-10
> **JoshuaRL said:**
> What errors does it give you?  Are there a list of drivers to choose from?  The cables are all seated correctly right?  Is it by any chance connecting to a IDE port through a IDE-to-SATA adapter?
I'll try again with a different CD drive. I've got a million sitting around at my parents' house and at work.

---

