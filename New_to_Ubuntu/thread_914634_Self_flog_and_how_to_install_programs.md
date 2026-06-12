---
title: "Self flog and how to install programs"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by CraziestOzzy on 2008-09-09
I must say to start with, Ubuntu is the easiest Linux install distribution and recognized all my hardware...where others failed on one point or another. If you don't like to read my self flog, scroll down to the QUESTION :lolflag:

*Now for the self-flog*...I am an old fart, who grew up with the first Apple computers in the early 80's and had to learn BASIC programing to get anywhere useful. Punch cards were all the rage :guitar: 
Back then, the best game ever was Pong and I haunted the arcades much later when Space Invaders appeared for the first time.
Microsoft *cough* Windows '95, '98 and XP were the genre of operating systems I am proficient in. I liked Win95 as it was easy to work with (assuming the "blue screen of death" didn't get in your way). With Win95, I was able to work within DOS (MSDOS at times) to control the OS, delete useless programs (bells and whistles) and add others.
As time progressed, the Microsoft Windows OS became increasingly harder to manipulate and control, getting to the point now where you (the end user) are TOLD and forced to like it or lump it...and not to mention the viruses. Microsoft's Vista was the last straw for me...completely archaic and intrusive - an OS that offers no privacy, no control and so slow (due to a phenomenal number of spyware applications running behind the scenes) that it was time for me to move on.
I had tried during the era of WINXP to "change over" to Linux, but spent more time at the keyboard than running and using actual programs. How times have changed in the last year...*end of self flog.*

**QUESTION:** What is the "normal" process of installing a compressed software package under Ubuntu pilfered from the internet?
I seem to be suffering from "writer's block" and cannot understand the typical process of configuring, compiling and installing a given software...and once installed, I can't seem to remember how to create and configure an Icon on my desktop that points to an installed program that will actually execute it.
My last biggest hangup, is that of installing programs under and as ROOT user. Some self installing programs I have require ROOT privileges. I admit that most software I have downloaded has not taken into account the fact that an install under Ubuntu as ROOT is different from the typical (Debian) OS. This leads to many "permission denied" lines or "directory not found" under a terminal window during an install, despite using SUDO. It seems that SUDO only points to my user account and not the actual ROOT directory when installing? If I somehow managed to to install a program within ROOT as ROOT (following some of terminal commands suggested here and in other websites)...I am denied access to that program from my normal user account, despite changing the permissions for those programs.

...better stop here before I confuse you more :confused:

---

### Post by Bucky Ball on 2008-09-09
> What is the "normal" process of installing a compressed software package under Ubuntu pilfered from the internet?All depends what it is and if it will run in Linux. Windows programs will not unless you run them under Wine, and then not always.

When you install a program it winds up in the Applications drop down in the appropriate category, you drag it from there and drop onto the desktop. That creates an icon, 'shortcut' if you like.

Programs are generally added through going Applications->Add/Remove, find the program (application) you are after, tick it, apply, and it is installed. 

If you are talking about downloading and installing a tar.gz or some other form of compressed file, that info is findable on the net.

Your root problem could be that Ubuntu just doesn't understand the filetype you are trying to install. It sounds like you are trying to install your Windoze programs. That, as I say, will not happen without Wine. If it is a self installing program for Linux, you should be able to double click it and it will install.

Linux is not Windoze and takes a different approach you will soon get used to. :)

---

### Post by Faolan84 on 2008-09-09
To install or remove software we suggest that you use Synaptic if you are using Ubuntu:
on the menu:
system > administration > synaptic package manager

If you want packages that are a little more up to date or maybe some popular software that may not be in the repositories try get-deb.net

Also if you want better multimedia capabilities such as flash and MP3 to go the Medibuntu site and follow their instructions.

---
If you're using a the command line to download from the official repositories then you'll want to use apt-get which is used as thus
apt-get install program
apt-get remove program
apt-get purge program

However, it is advised you use Synaptic instead, it's much easier plus you can better search for what you are looking for.

Also there isn't a decent pong game for Linux of all things :( Maybe someone could hack one up. I'm too tired otherwise I'd do it on post it. But we have all sorts of other cool programs, but if you're looking for warez you will not find many for Linux because of the fact most distros use their own software repositories, from which all of the software is supposed to be safe to use.

---

### Post by Faolan84 on 2008-09-09
The above poster mentions WINE which is an "emulation layer" that lets you run some Windows programs. You should note that this will not always be successful but it does work for Sim City 4, Age of Empires I & II, and Kyodai Mahjongg, so it should work fairly well depending on how exotic your program is and whether or not it was developed using sane programming standards -- for example Deli Player 2 doesn't work.

However you will find that for most general needs we have a native application that will run much better and be more stable so unless it's something you absolutely need like MS Office because of work or something you absolutely this kicks the kaiser like a game you can't live without, go with the stuff in the repos.

Also what may work in one version of WINE may not work in the next but then might be fixed again in a later version, so it is more of a caveat but the project is becoming more stable and I haven't had any problems like that in a couple years, but it's important to know if you're going to rely on it.

---

### Post by CraziestOzzy on 2008-09-09
My apologies...should have made it clear that I am attempting to install some "tar.gz" and not Windows ".exe". Thanks for the quick replies...very informative.
I have thought of the possibility of using Synaptic to install the programs I have downloaded, without going through the sometimes confusing processes required by each author of the programs I wish to use. I think I am stumbled by the complexity of a manual install and probably need some eye candy or a Linux guide for dummies book. The programs I have, are not available within the typical repositories. 
Is it possible to "cheat" and direct Synaptic to a tar.gz on my desktop and install from there...assuming that the program is compatible for such a task?
The programs I seek to run are involved with Finite Element electromagnetic tasks. I tried CAELINUX but needed more than what they offered and plus had some hardware issues with their OS that gave me a headache to solve.

---

### Post by Bucky Ball on 2008-09-09
This page will help you out. If your file is on your desktop, put it manually (drag and drop) into a folder so you know where it is. (you could create one).

This should get you going. You need to open a terminal by going Applications->Accessories->Terminal. Don't fret, easy.

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

In the step where it says path to software, use the folder where you put it before or issue this command in a terminal:

**locate name_of_your_tar_file** (as in BestGameEver.tar.gz)

If you tar.gz is in /home/usergames then cd to that, as in:

[B]cd /home/usergames/
[/B] 

 Let us know how you go. If you can find the repository you tar.gz came from, yes, you can add that to your software sources, but that is another issue.

Thanks [Faolan Devyn Aodfin]("http://ubuntuforums.org/member.php?u=212233"), sorry if I wasn't too clear there about WINE, but turns out to be irrelevent in this case anyhow! \\:D/

---

### Post by jerome1232 on 2008-09-09
To compile programs you always need the build-essential package (installable via synaptic)

I would like to emphasize a step in the tut
> 
# 3: Read INSTALL / README file    

# 3: Read INSTALL / README file    

# 3: Read INSTALL / README file    

# 3: Read INSTALL / README file

Usually/sometimes they tell you exactly what dev packages you need to install, and they usually tell you what commands to run, what to do if you get a particular error etc... (depending on quality of the authors documentation :))

I ran into one INSTALL file that contained. "on the todo list" That's frustrating lol.

one note, when they say you need xxyy package, it means you need the xxyy-dev package (installable via synaptic) to compile the program. If you are stuck on a particular program provide a link to it so we can try compiling it and/or look over the readme and give you tips, knowing what steps you have taken helps alot as well

---

