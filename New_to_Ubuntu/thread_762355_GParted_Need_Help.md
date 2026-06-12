---
title: "GParted Need Help"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by jivabill on 2008-04-22
I have Ubuntu 7.10 installed and have spent some months tweaking it up to where I want it. I don't want to lose that.  Now I need to run Quicken for a client so I need to put XP on in dual boot.  

So I found the APC tutorial on how to install XP alongside and existing Ubuntu.  Got the file for GParted Live CD from SourceForge, in fact two of them 0.3.4-7 and 12 the latest.

When I try to run the Live CD (burned the file to a CD) the system can not find my video card driver.  Presents me with the screen where it says it could not find the video driver and gives me about 25 choices.  NONE of them are remotely like mine.  in System-Screens and Graphics it says my video card is an Intel 815 and that the driver is "intel experimental modesetting..." and then the name runs off the screen.

So I am stuck at that point.  Tried 10 or so drivers out of the list,none worked.

I have the GParted desktop application installed but it will not let me manipulate the HD partition because it is mounted.  So I felt that I would have to use the Live CD.  Except it don't work.

Any ideas appreciated
Thanks
Bill

---

### Post by TeraDyne on 2008-04-22
Generally, the driver called "vesa" will work on any video card. I know it's worked on all the cards I've used. Have you tried using it?

---

### Post by jivabill on 2008-04-22
Yes, indeed.  The suggestion that the vesa driver would work is in the information displayed where I have been stuck. So first thing I went for was vesa.  Did not work.  ended up with a black screen, no activity.  Finally shut down the box to get out of it.  Next try I read more carefully and discovered control delete backspace to stop X then I was able to back out and restart more gracefully.

---

### Post by gitpik on 2008-04-22
You could try to use gparted from a live session of the ubuntu 7.10 live cd if you have that handy. Just boot with the gutsy cd, then install gparted from the terminal or through synaptic. it installs to System > Administration > Partion editor.

Can't help with the video driver for the gparted live cd though. I haven't got a clue.

---

### Post by sdennie on 2008-04-22
Are you certain that you want to dual boot and not just create a virtual machine with Windows in it or try to run Quicken under wine?  If it's just a single app that you need Windows for, it may be worth it to investigate one of those two options.

---

### Post by jivabill on 2008-04-22
Thanks for your input.  I don't have the 7.10 Live disc, I never downloaded it.  I used the Alternative (not live) install disc.  Thing that happens, I have GParted installed from Synaptic already, when I use it I can see the partitions but they are all locked.  From reading other places I see that this is becasue they are mounted and you can't change a mounted partition, at least so SourceForge says.
Bill

---

### Post by gitpik on 2008-04-22
> **vor said:**
> Are you certain that you want to dual boot and not just create a virtual machine with Windows in it or try to run Quicken under wine?  If it's just a single app that you need Windows for, it may be worth it to investigate one of those two options.

I agree. I just recently tried VirtualBox and it was really easy to get it going.

---

### Post by jivabill on 2008-04-22
Hi Vor, nice to meet you.  Well, thing is, my computers (all three of them) will not run VMWare.  And Quicken is kind of notorious for not working well at all in Wine.  So I reached the conclusion that I need to have a dual boot configuration so I can run Quicken and Quicken Home and Business for my business clients.

I should have done that before I installed Ubuntu, but at the time Win XP had puked and died and I did not consider it.  So now I have to resize my HD to make a space for XP.  So that brings me up to where I am stuck, unable to resize the partition cause GParted Live CD won't run due to the video problem.

---

### Post by Paqman on 2008-04-22
> **jivabill said:**
> From reading other places I see that this is becasue they are mounted and you can't change a mounted partition, at least so SourceForge says.
Bill

Absolutely right. That's why you want to use a LiveCD. If the Gparted LiveCD doesn't support your hardware, but you know that Gutsy does, then downloading and burning the Gutsy LiveCD sounds like the way to go. Gparted is included on it by default, so it effectively does the same job as the Gparted LiveCD.

---

### Post by kansasnoob on 2008-04-22
GITPIK's idea of trying the 7.10 live CD sounds very good to me.

Trying to use GParted from the system menu is almost worthless beyond just seeing what's going on with what partition.

I am wondering though if GParted in the 7.10 Live CD will say anything different than the GParted Live CD? Did you have any issues installing 7.10?

---

### Post by jivabill on 2008-04-22
Hi Kansasnoob and Paqman.  Thanks for the good input.  I think you are right, I do need to download and burn the 7.10 Live CD so I can use the GParted from there.  Makes sense that it should work since the 7.10 system was able to find a driver for my video card when I installed from the Alternative disc.  The install went smoothly and the system has been very stable.  Thanks for the good idea I'll give it a try.

---

### Post by stalkingwolf on 2008-04-22
You could try crossover linux.  It has a free trial.
and it appears that the 2003 version works best.
[http://www.codeweavers.com/compatibility/browse/name/?letter=all;sort%5Bapp_name%5D=ASC;curPos=100]("http://www.codeweavers.com/compatibility/browse/name/?letter=all;sort%5Bapp_name%5D=ASC;curPos=100")

---

### Post by gitpik on 2008-04-22
> **jivabill said:**
> Hi Vor, nice to meet you.  Well, thing is, my computers (all three of them) will not run VMWare.

Hi Bill, any luck yet? Just out of my own personal curiosity, Is it that your hardware specs are too low to support virtualization?

---

### Post by jivabill on 2008-04-22
Hi gitpik, nice to meet you.  When I tried to install VM Ware a message box came up that said my system could not run VM Ware.  Have a Compaq desktop (the compact kind), a Dell Lattitude Laptop, and then an older machine with win98 on it.  Not in the fancy hardware yet here.

---

### Post by forestpixie on 2008-04-22
Don't know whether this is of any interest to you but when I hda problems getting the gparted livecd to work I tried partedmagic and that worked on pcs that gparted wouldn't.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

---

### Post by jivabill on 2008-04-22
Hi forestpixie, thanks for your input.  Well, I downloaded the 7.10 Live CD and burned it to a CD.  And I was able to use GParted from there, it allowed me to resize the partition for Ubuntu, creating space for the XP install.

It appears that my XP Install disc may have some errors on it so I am working on getting that fixed so I can go ahead with the XP Install.  Right now it hangs right after widows setup says "examining your system hardware...".  Have an email out to my son who is an IT Specialist in FL works with windows for corporations a lot.  Hopefully he will have the solution.

---

### Post by redbob on 2008-04-23
Hi, guys. I use Quicken since 1996, so when I migrated to Ubuntu last year, I tried to install Quicken by wine with no success. The best option I found was to run XP into a Virtualbox. Quicken runs very well, with sound and elsemore. I'm using Quicken 2008 Premium. Virtualbox is the best option, since VMWare is heavy to Ubuntu. =D>

---

### Post by bhold on 2008-04-24
> **jivabill said:**
> So that brings me up to where I am stuck, unable to resize the partition cause GParted Live CD won't run due to the video problem.

I also had video problems with the gparted live cd, until I tried selecting the "Configure X" option - works fine now. Hope this helps.

---

### Post by jivabill on 2008-04-24
Hi bhold, thank you for the tip.  I'll give it another try and make the Configure X selection.  I'll have a report soon.
bill

---

### Post by jivabill on 2008-04-24
Working with GParted off the Live CD for 7.10, I can see that I don't understand all I know about it.

When I get the screen showing the file systems and the slider I see that the main partition, the whole HD 186 gb is set so that I can resize it.

But the other two Linux partitions swap and ext3?  anyway the other two have little padlocks on them.  And I assume that means they can not be changed.

Can someone enlignten me what is going on there?  I thought with GParted off the Live CD that I would be able to do anything I wanted to the file system including erase all of it and format the HD.  Obviously I don't know what I am doing.

Any suggestions or info?:confused:
thanks

---

