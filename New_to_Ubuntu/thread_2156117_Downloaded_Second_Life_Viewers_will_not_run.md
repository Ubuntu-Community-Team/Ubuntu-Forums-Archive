---
title: "Downloaded Second Life Viewers will not run"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by superstargoddess on 2013-06-20
I've tried the official version, Catznip, and Exodus Viewers.  I install them using their install.sh file and the install goes fine and I find them in the applications folder.  I mark them as run as executable since if I don't they open in a text edit program.  However, when I try to run them, I get the little white spinner that spins for a few seconds then nothing happens.  The proograms don't start, nothing happens, I get no error messages.

I installed Google Chrome on my own and it worked fine, but for some reason, I can't get any Second Life Viewer to work!  On Ubuntu 13.04, fresh install, all computer parts are high grade so there should be no problems in that department.

---

### Post by JamesProg on 2013-06-21
I have verified the same on Zorin and Ubuntu, both versions of the 13.04 Ubuntu OS. There seems to be some problem, nautilus, the default file manager, does not have a "run" option and when you try to execute, launch, run the secondlife or other secondlife viewer program launcher(yes I verified that the execute was turned on) it will simply open the text file in an editor. So tried to add the launcher to the menu and run it from there and it simply fails to run.  There is something really wrong with 13.04.  In the 12.04 I could run secondlife, kokua and other Second Life viewers with no problems.  I also had a time getting the amd/ati video card installed on Zorin which seems to have defaulted to supporting the open source drivers(really stupid) I did finally manager to get the full amd proprietary drivers working in all their glory(the ones from AMD) and I verified it 100%- it works fantastically.  I have tried both the default and beta version of AMD's proprietary drivers and neither will allow SL to work- I do not believe it has anything to do with the drivers.

13.04 is in the final release so there is no excuse for something as extreme and frustrating as this to be going on.  Anyone that gets it to work please let me know right away. I will be working on it around the clock until I do.

> **superstargoddess said:**
> I've tried the official version, Catznip, and Exodus Viewers.  I install them using their install.sh file and the install goes fine and I find them in the applications folder.  I mark them as run as executable since if I don't they open in a text edit program.  However, when I try to run them, I get the little white spinner that spins for a few seconds then nothing happens.  The proograms don't start, nothing happens, I get no error messages.

I installed Google Chrome on my own and it worked fine, but for some reason, I can't get any Second Life Viewer to work!  On Ubuntu 13.04, fresh install, all computer parts are high grade so there should be no problems in that department.

---

### Post by JamesProg on 2013-06-21
Just a quick update- still doesn't get Second Life running quite, but it does force nautilus to run the "shell script"(the file you run when you try to run Second life or other viewer).  Just go to the Nautilus or file manager preferences... sometimes available by alt-f10, In my case I just clicked the little widget looking wheel/sprocket icon at the end of the file manager icons- and clicked preferences-- you want to get to a tab for file manager preferences that says "behavior" and simply change the selector under "executable Text Files" to "Run executable text files when they are opened" instead of the "View executable text files when they are opened" default idiocy.  It's maddening because when I go into the text terminal and try to run the file it also kicks me out and tell me I have to add 32 bit libraries-- well no you don't if you are using a 64 bit OS and the Second Life viewer/browser is also 64bit- best way to got but only a few of the alternative viewers actually provide a 64 bit compiled version and in my experience only the Kokua 3.5 or above are stable enough to use well..  I added them anyway but it doesn't run no matter what I do. If you have a 64 bit version of linux and want to have a chance at running a 32 bit viewer you will have to install the 32 bit libraries- even then you will likely have more problems than if you install a 64 bit viewer... aside from running slower... Linux does one thing extremely well and that is 64 bit so for the most part you are best off installing the 64 bit version of Ubuntu or other linux with any computer bought in recent years.  They say if you are Windows 8 compatible but really you could have bought your computer several years before anyone even thought of Windows 8 and still have a full 64 bit CPU.  AMD64 and Intel i3/i5/i7 and many other CPUs are 64 bit.  The CPU is the main brains of the computer on one multi-chip/chip that is put on your motherboard with a big fan glued to it with thermal paste and metal brackets.  The CPU is the source of much of the heat in your computer in addition to the GPU or otherwise known as video card.  CPU stands for Central Processor Unit and GPU stands for Grapic Processor Unit-- providing all of the video/photographic information you see on your monitor in addition to the sound if you use a HDMI cable and play sound over the monitor's speakers..  When I double click/run the icon in nautilus following the above change it just does nothing whatsoever.  It looks like we cannot run some "shell scripts" in 13.04 for some reason.  I will keep working on it.

---

### Post by JamesProg on 2013-06-21
As an alternative to the above option -- open terminal window of your choice (application menu>> Accessories >> Terminal) or alt-f2 and type in terminal.. from the normal prompt- no need to be sudo or super user- just type this: [FONT=Ubuntu Mono]gsettings set org.gnome.nautilus.preferences executable-text-activation ask <ENTER>  this will make it so when you double-click a program file like the Secondlife shell script it will give you a choice of whether to run or open the file as a text file.[/FONT]

---

### Post by hreichgott on 2013-06-21
Can you open a terminal, navigate to the directory where the secondlife executable is, and type ./secondlife

That would be a way to run it without bothering with Nautilus or the menus.

---

