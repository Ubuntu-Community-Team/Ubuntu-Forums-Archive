---
title: "Problems with Ubuntu 8.10/Toshiba Satellite computer"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by svesmeralda on 2008-11-15
I have a two year old Toshiba Satellite computer that has been running Ubuntu, dual booted with XP, since May 2007.  

I upgraded to 8.10 from 8.04.1 recently.  I immediately had problems.  The first thing I noticed was some quirks in the startup screen.  At one point there was some wiggly, colored lines on the screen.  There were additional scroll bars that did nothing like the one that shows the progress of the boot process.  One was colored in Ubuntu Human and the others were without it, just black with the dividing lines.

The desktop seemed to take longer coming up than before and the welcome sound definitely came on later than before.  

The overall performance of the computer was degraded.  Firefox wasn't working as well, and the applets on the menu bar a the top would expand momentarily when clicked.

I had similar problems when I upgraded to Hardy Heron from Gutsy Gibbon.  I  re-installed XP and then installed Hardy Heron from a Live CD.  The problems that showed up in the upgrade did not reappear.

Also power management was poor.  Sometimes the computer would hang at the end of a shutdown and then I would have to manually turn off the computer with the power button.  If I tried to suspend the computer it would not wake up.  I would have to remove AC power and the battery for 30 seconds or so in order to be able to restart the computer.

One last thing, my home folder was set to open with totem.  I was to fix this as I happen to read about that subject in one of the books I have on Ubuntu.

I am immensely pleased with Ubuntu and will never go back to windows on a regular basis, but I am disappointed that I was not able to upgrade to Ibex. though.  There a few things that I can only do on windows, thus I keep it around in the background.  I considered these problems I am having as part of the learning curve of my continuing computer education.

I tried the Live CD of Ibex that I downloaded and it did the same things.  So I am wondering if the problem is with my computer and not Ubuntu.  I am considering buying a new computer pre-installed with Ubuntu.

I re-installed XP and Hardy Heron and am once again a happy Ubuntu user.

Can anyone offer some insight to what maybe happening?

Thanks,

Jim Barber

---

### Post by ohzopants on 2008-11-18
I've been using ubuntu for a while now (since the 5.10 days) and since 7.04 I don't upgrade to the latest version for at least a few months.  I also stopped trying to do upgrades.  I only do clean installs now, since I made a separate partition for my /home directory this is a breeze to do since I don't have to worry about any of my files or my program settings.

The ubuntu devs do great work, but there's only so much they can do.  I find waiting to be the best option.

---

### Post by ibgeorgeb on 2008-11-18
This is just a shot-in-the-dark with the suggestion of how much RAM does your Toshiba have? The more the better. Cheers,

---

### Post by svesmeralda on 2008-11-19
Thanks for the reply.  I actually was going to wait at least a month to upgrade, but I read the release notes, was so excited about the new offerings that I lost my head.  I do not know what is meant by a clean install.  Is that applying the upgrade from the live CD?  I will look into setting up my home directory as you do.  I am still a little ways away from grasping partioning.

The RAM is only 512 MB.  When my budget can allow it, I intend to buy a new computer dedicated to Ubuntu, such as a System 76 with one or two GB of RAM.  I will probably have Windows on it as a virtual machine until I can do everything on Ubuntu.  The Toshiba then will be used for trying out things like MythTV.

Thanks again for the replies.  The Ubuntu forum is a big part in why I like Ubuntu so much, besides the fact that it is just better.

Jim Barber

---

### Post by svesmeralda on 2008-11-19
Thanks for the reply.  I actually was going to wait at least a month to upgrade, but I read the release notes, was so excited about the new offerings that I lost my head.  I do not know what is meant by a clean install.  Is that applying the upgrade from the live CD?  I will look into setting up my home directory as you do.  I am still a little ways away from grasping partioning.

The RAM is only 512 MB.  When my budget can allow it, I intend to buy a new computer dedicated to Ubuntu, such as a System 76 with one or two GB of RAM.  I will probably have Windows on it as a virtual machine until I can do everything on Ubuntu.  The Toshiba then will be used for trying out things like MythTV.

Thanks again for the replies.  The Ubuntu forum is a big part in why I like Ubuntu so much, besides the fact that it is just better.

Jim Barber

---

### Post by Peter09 on 2008-11-19
The applets expanding is part of the scheme (well I've always assumed so) - not sure where its defined.

---

### Post by fiendishfish on 2008-11-19
Hmm... your computer seems relatively new, so I can't see it being a problem with your specs, 512mb ram _should_ definitely suffice.

A clean install is when you wipe EVERYTHING off of your hard-drive and just start from scratch, i.e. Installing Ubuntu from the start, opposed to doing a dist-upgrade.

Perhaps your running LOTS of programs on startup, when it's booted (in your de/wm) try running 'ps' to see which processes are running, or run 'top' which says where all the system resources are being allocated. Beware if the majority of your ram is being used, don't worry, the kernel caches it.

Hope it somewhat helped

-fiendishfish

---

### Post by sonu 1807 on 2008-11-19
I recently installed Ubuntu intrepid on my friend's Toshiba Satellite Laptop. It was a clean install, and is working perfectly. May be you should go for clean install

---

### Post by Peter09 on 2008-11-19
I have a Toshiba Satellite as well which I tend to keep up to date with the bleeding edge - its on Jaunty now.

All of these things are familiar to me as well (for Intrepid). 

For a while I was unable to turn the machine off from standby. It would not resume and holding down the power button caused a momentary off, followed by an immediate power on, back to the standby state. I had to remove the Battery to recover.

I think I resolved this by playing with the power management applet. Making a different selection and then going back to my original one.

---

### Post by svesmeralda on 2008-11-19
I can live the expanding applets if I have to, but I prefer not have it happen.  It is a very minor thing.

Good, now I know what to call what I did.  The only thing I don't like about it is reinstalling Windows.  It takes too much time from my using Ubuntu.  Maybe it would be easier with a virtual Windows.

Jim

---

### Post by Peter09 on 2008-11-19
Yes - try virtualbox, its in the repositories, a good solution as long as you do not want high level graphics. (You may need more RAM though).

---

### Post by svesmeralda on 2008-11-19
I ran ps and then top.

ps had two entries:

PID       tty        time      CMD
7442     pts/0     00:00:00    bash
7461     ps        00:00:00    ps

Firefox, Evolution and Nautilis are  also running.

top:

104 tasks, 2 running, 102 sleeping
cpu  around 99%id and the rest is us and sy
memory  449076K total  385720K used    63356K free    9780K buffers
swap   1317288K total   41748K used  1275540K free  140256K cached

I have run these programs before while doing some beginning bash tutorials.  I do not fully understand what it is telling me yet, but that will come in time.

If I had another computer I wouldn't hesitate to try a clean install of Intrepid, but the Live CD I made had the same problems as the upgrade had so I am reluctant right now.  At the end of the month I will try downloading Intrepid again and see how the Live CD behaves.

It is good to hear another Toshiba laptop is doing well with Intrepid.  I am satisfied with Hardy for now.

Thanks for all the replies it gives me encouragement to keep at it.

Jim

---

### Post by ashishgoel on 2008-11-22
i too have Toshiba Satellite... I installed 8.10 under Wubi in Win XP SP3... i'm having only problem with bluetooth hardware as its not being recognized... Any idea how can I solve it???

---

### Post by svesmeralda on 2008-11-22
> **ashishgoel said:**
> i too have Toshiba Satellite... I installed 8.10 under Wubi in Win XP SP3... i'm having only problem with bluetooth hardware as its not being recognized... Any idea how can I solve it???

I do not have any experience with bluetooth yet.  

What is Wubi?  I am willing to try most anything.

I installed virtual box on Heron and inadvertanly added the 386 kernel  in the process of learning how to do it.  I will be trying a clean install soon of a new live CD of Intrepid as soon as I am done with virtual box and VMware to see if the problems persist.  If it goes okay then I will put Windows on in virtual if I can otherwise I go back to dual boot.

Appreciate all the replies greatly.

Jim

---

### Post by ashishgoel on 2008-11-26
wubi is prog were-in u can install ubuntu inside windows enviornment but able to dual boot it without changing any windows partition etc...

---

### Post by svesmeralda on 2008-12-02
wubi is prog were-in u can install ubuntu inside windows enviornment but able to dual boot it without changing any windows partition etc...

Thanks I will look into that.  If it allows me to boot into Ubuntu without going through windows then it may work for me.

I downloaded Intrepid again and it works much better, but it doesn't have sound so I am still using Hardy.

Jim

---

### Post by samjenkins on 2008-12-02
I am very thankful to find this thread and see that I am not alone!  I downgraded to Intrepid yesterday and now have the following issues most of which have been noted above.  I also have TOSHIBA SATELLITE A-135-S-4666 (originally shipped with Vista).  I have 1GB of RAM and it is definitely not a RAM issue.  My RAM is currently below 57% usage with nine Firefox tabs open and OpenOffice Presentation running. Besides, Hibernation and Restart are completely unrelated to RAM usage.

[LIST=1]
[*]No sound
[*]Restart only logs me out
[*]After being logged out, It will not shut down after selecting the option
[*]I had to hold the power button down to actually turn laptop off
[*]Hibernate seems to mess with wifi applet and requires reboot
[/LIST]

I switched to Ubuntu Hardy Heron after my last Vista Service Pack removed the sleep and hibernate options from my menu.  If I can't figure this out I may just go back to Hardy Heron since it is a Long Term Service version.

---

### Post by svesmeralda on 2008-12-02
> **samjenkins said:**
> I am very thankful to find this thread and see that I am not alone!  I downgraded to Intrepid yesterday and now have the following issues most of which have been noted above.  I also have TOSHIBA SATELLITE A-135-S-4666 (originally shipped with Vista).  I have 1GB of RAM and it is definitely not a RAM issue.  My RAM is currently below 57% usage with nine Firefox tabs open and OpenOffice Presentation running. Besides, Hibernation and Restart are completely unrelated to RAM usage.

[LIST=1]
[*]No sound
[*]Restart only logs me out
[*]After being logged out, It will not shut down after selecting the option
[*]I had to hold the power button down to actually turn laptop off
[*]Hibernate seems to mess with wifi applet and requires reboot
[/LIST]

I switched to Ubuntu Hardy Heron after my last Vista Service Pack removed the sleep and hibernate options from my menu.  If I can't figure this out I may just go back to Hardy Heron since it is a Long Term Service version.
Sam,

Thanks for the info on your problems with Intrepid.  

I recently downloaded Intrepid again and intalled it as a guest on virtualbox and the problems I had before seem to be cleared up, but the sound was disabled.  I haven't been able to spend much time using it, but will be getting back to it soon.

I am going to be doing a fresh re-install in a week or so. First I will try Intrepid as the only OS to see what happens.  The reinstall has nothing to do with Intrepid, just a good time to try it out again.

Jim

---

### Post by samjenkins on 2008-12-14
I have since removed Ubuntu from my laptop.  I first thought I would change to XP, but couldn't find the drivers for it to connect to wifi and the sound again.  So, sadly enough I reinstalled Vista.  I have found all of this to be a huge time waster.  I installed VMPlayer and will run Ubuntu virtually for a while.

I found a full page of sound fixes here in the forum somewhere, but it didn't seem to work for me.

---

### Post by skathmandoo on 2008-12-14
hello everyone. i have a toshiba satellite (M100) too and i recently switched to Ubunto 8.04. i hated my laptop when it had windows xp , however i decided to increase my RAM and installed Ubuntu 8.04...and now m LOVIN IT!! the only problem i seem to be having is connecting my phone thru bluetooth.i know this thread is to do with Ubuntu 8.10 , but i desperately need help! i tried a couple of things that was available on the forum and other websites but its still not workin.m not good with computers let alone linux system..so pls help!! thanks !!

---

### Post by thaumielx72 on 2008-12-14
I also have a Toshiba notebook (A215-S7416).  I have been running it with Ubuntu all year long.  I stated with Gutsy but have recently made the switch to Intrepid.  The first thing I did when I bought it was upgrade the RAM to the max it would take (4GB).  I have found you can never have too much RAM.

For the most part I have been extremely happy with Ubuntu.  I hardly ever boot into VISTA any more.  I agree with other posters that a clean install is always a good idea.  You tend to collect so much junk over time that a clean install reminds you of how good your machine actually is. 
 
Anyway to get to back to my main point: I also was having sound issues with the Satellite and eventually wound up compiling the sound drivers myself.  Sound was just Excellent after that.  It's a bit of work and if you've never dabbled in compiling source then I suppose it's not a solution for you.

But the results are certainly worth the time.

(I should point out here that I have an external speaker system and plug it into the headphones jack.  Boy, I can play music through them and if I had any neighbours they would certainly be complaining.)
:guitar:

---

