---
title: "HOW-TO: Building amaroK from SVN source"
date: 2005-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by mlomker on 2005-10-22
I've always had odd problems with the version of amaroK that came with Breezy and Hoary.  It is also my favorite application on linux!  For that reason I like to have the very latest version of it installed.  The way to do that is to periodically build it from the latest SVN source.

The amaroK community provides an automated script that makes the process fairly easy, but you have to install a number of development files in order to get it to compile.  This how-to will walk you through that process.

**_Remove any installed version of amaroK_**

```

sudo apt-get remove amarok amarok-arts amarok-xine amarok-gstreamer

```

**_Install necessary development files_**

```

sudo apt-get install kdelibs4-dev subversion unsermake automake1.9 kdebase-dev build-essential ruby
sudo apt-get install libgstreamer-plugins0.8-dev *#gstreamer suppor*t
sudo apt-get install libxine-dev *#xine support*
sudo apt-get install libmp4v2-dev libfaad2-dev *#aac/mp4 tag editor support*
sudo apt-get install libtunepimp2-dev *#recommended-supports lookups for song lyrics, etc.*

```

Download Taglib 1.4 for [i386]("http://mail3.mpr.org/mlomker/taglib-1.4_i386.deb") or [PowerPC]("http://maanskyn.za.net/ubuntu/taglib_1.4-1_powerpc.deb").  If you run another architecture then [download]("http://developer.kde.org/~wheeler/files/src/taglib-1.4.tar.gz") the source and compile your own.

Change to the download directory:
```

sudo dpkg -i taglib-1.4_i386.deb

```

**_Download the script and install amaroK_**

Right click and [download]("http://mail3.mpr.org/mlomker/amarok-svn.sh") the amarok-svn.sh script.  Save or move it to a directory where you can keep the amarok source files in (your home directory is probably the easiest, ~).  The script will create a directory underneath the one that you run it from.

Change to your directory:
```

sudo chmod +x amarok-svn.sh
./amarok-svn.sh

```

Say 'yes' when prompted whether or not to use **sudo** for installation.  You can take the defaults for the rest of the questions.

The first compile process takes a few minutes but future updates (run every few days if you wish) only download the new files and take much less time.  The script automatically downloads/compiles/installs amaroK for you.  You will find an icon in your menu once the installation is complete. 

**Gnome Users:** Reboot.

See [this post]("http://www.ubuntuforums.org/showpost.php?p=553660&postcount=97") if you're interested in mysql support.

_**Troubleshooting**_

[amaroK's main webpage]("http://amarok.kde.org/wiki/index.php/Download")

[wiki for the script]("http://amarok.kde.org/amarokwiki/index.php/AmaroK-svn")

---

### Post by Mrtn on 2005-10-22
I will try it as soon as I get home. What do you need to do to switch to the download directory? I am a newbie to Ubuntu and linux in general so forgive me for asking.

I put mine in a folder in my home directory.. lets say /home/maarten/

How would I change to that folder? :)

---

### Post by mlomker on 2005-10-22
> I put mine in a folder in my home directory.. lets say /home/maarten/


**cd /whatever/dir** to change directories.  [This is]("http://linuxcommand.org") my favorite command-line tutorial.

---

### Post by Dr. Nick on 2005-10-22
> sudo apt-get install kdelibs4-dev libxine-dev libstreamer-plugins0.8-dev

It should be lib**g**streamer-plugins0.8-dev I believe. Thanks for the how to, I am trying it out now

---

### Post by mlomker on 2005-10-22
[QUOTE=Dr. Nick]It should be lib**g**streamer-plugins0.8-dev I believe. [/QUOTE]

Thanks.  Fixed the typo. Let me know how it goes.

---

### Post by comradevik on 2005-10-22
i'm on gnome.. going to try this now because amarok is the best thing ever created. i loved itunes before, but itunes couldn't wake me up in the morning :-)

---

### Post by mlomker on 2005-10-22
[QUOTE=comradevik]i'm on gnome..[/QUOTE]

You could skip the kdebase-dev if you only use gnome (Xine as well if you prefer gstreamer).  It won't hurt to build them though...just adds a couple of seconds to the compile.

---

### Post by Dr. Nick on 2005-10-22
Didnt work or me, gives errors telling me to start dcopserver, Im on gnome btw. 

I think I messed up at the begennig but how can I start over? I deleted the amarok-svn folder but want to get rid of what it already installed and try again.

Any chance to have the script to just compile and not install? I would like to use checkinstall to make a deb for easy removal later.

---

### Post by mlomker on 2005-10-22
Dr Nick, sorry for accidentally editing your post.  That's the second time that I've done that this week.  I shouldn't work on the computer while drinking Guinness, I guess.  ;)

Here's the response that I meant to send:

> Didnt work or me, gives errors telling me to start dcopserver, Im on gnome btw. 

It might be better to post the failed output from the ./configure portion of the script.  I didn't experience this problem.

> I think I messed up at the begennig but how can I start over? I deleted the amarok-svn folder but want to get rid of what it already installed and try again.

There's no easy way to do that because each of those packages installs many other packages due to dependencies.  I test my how-to's using a VMWare virtual machine for this very reason (it can easily be rolled back) but that isn't an option on a normal install.

> Any chance to have the script to just compile and not install? I would like to use checkinstall to make a deb for easy removal later.

I didn't write the script, the amaroK developers did.  The setup isn't configured in a way that checkinstall would work.  It'd take an actual developer (I'm just a systems admin/documenter) to figure that out, I suspect.

---

### Post by souled on 2005-10-22
I installed everything but the kdebase, and when I run the script I get ERROR: get-amarok-svn.sh 1.4 and higher requires kreadconfig, which wasn't found in your $PATH! Any ideas?

Thanks for the HOWTO.

---

### Post by mlomker on 2005-10-22
> and higher requires kreadconfig, which wasn't found in your $PATH! Any ideas?


Sounds like that's a part of KDE's language pack:

```

sudo apt-get install language-pack-kde-en-base

```

Here's a great troubleshooting tool:

```

sudo apt-get install apt-file
sudo apt-file update

```

After installation you can type **apt-file search *filename*** to see what package a file might be in.

---

### Post by Dr. Nick on 2005-10-22
> **mlomker]Dr Nick, sorry for accidentally editing your post.  That's the second time that I've done that this week.  I shouldn't work on the computer while drinking Guinness, I guess.   said:**
> 

No Problem, I was gone at the time :) Admin privleages must be nice, hehe. I didnt mess up at the dependency part, I think it may have been when it asked for options to pass at configure. I found out that using a -r while launching the script resets the configuration so I am now trying again

[QUOTE=souled]I installed everything but the kdebase, and when I run the script I get ERROR: get-amarok-svn.sh 1.4 and higher requires kreadconfig, which wasn't found in your $PATH! Any ideas?

I bet you need kdebase, I have gotten that error before I started using this howto

---

### Post by mlomker on 2005-10-22
>  Admin privleages must be nice, hehe. 

It's actually not hard to become staff around here--just help a lot of people and be polite, etc.  The other admins will notice and bring you up.  I'm always looking for KDE users to join my team and staff are drawn from those teams.

> I bet you need kdebase, I have gotten that error before I started using this howto

I checked the contents of that package and it doesn't mention kreadconfig.  I created this how-to using a box with both ubuntu-desktop and kubuntu-desktop installed.  There's no way for me to test every possible permutation, though.  I kind of expect the first few posters to help me refine the how-to!

Thanks.

---

### Post by souled on 2005-10-22
I installed that language pack, but I still got the same error, so I installed kdebase, and the script seems to be working so far.

---

### Post by mlomker on 2005-10-22
>  kdebase, and the script seems to be working so far.

Thanks!  I'll list it as required.  I thought it might be optional because it's the piece required to integrate amaroK into Konqueror.

---

### Post by Dr. Nick on 2005-10-22
**EDIT**
:) It works, I just re-ran the script and poked aound a bit and it started to work. I imagine most of the problems I had were due to my messy system, It remembered all the settings I had from the repo version so I know it didnt remove all the stuff it should have.

The instrutions provided should be correct then. I may just reinstall or really scrub my system squeaky clean and try again as a few things dont work right, the tray icon launches in another app which is weird and makes it hard to close :)

Thanks and I hope it works easier on a clean system for others.
**EDIT**

---

### Post by mlomker on 2005-10-22
> Don't run gdb, valgrind, etc. against this binary! Use amarokapp.

Did you see [this post]("http://ubuntuforums.org/showpost.php?p=434640&postcount=18") in the other thread?  If it's Nvidia-related then I won't be able to help because I'm an ATI-guy.

---

### Post by Dr. Nick on 2005-10-22
[QUOTE=mlomker]I understand that this problem is related to installing Nvidia's driver.  If you do a search it should turn up a thread or two.  I can't help with that because I'm an ATI guy.[/QUOTE]


It works now, I am going to try and get rid of all it and the kdestuff and try again. I saw instructions about compiling it without opengl to bypass some nvidia errors. I also used the configure command "--without-arts" as mentioned somewhere in the wiki. I think the main problem is just old junk messing it up as I get permission errors at login as well.

Thanks again

EDIT
I still get the dcop error but it loads fine, The system tray icon launces in a seperate windows though, beats me.

I know that the repo version didnt totally uninstall though, It still had my media library when I loaded this version up. 

Guess I need to do some spring cleaning this fall :)

2nd Edit
This version does work alot better as the freezes I previously had are now gone

---

### Post by mlomker on 2005-10-22
> This version does work alot better as the freezes I previously had are now gone

:cool: 

I do a clean reload with every major release.  If you keep your /home on another partition it makes the process pretty simple.  [thread1]("http://www.ubuntuforums.org/showpost.php?p=402461&postcount=2")  [thread2]("http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4")

---

### Post by comradevik on 2005-10-22
# DONE - amaroK successfully installed/updated! Start it from your menu or by typing "amarok".
victor@ubuntu:~$ amarok
bash: amarok: command not found
victor@ubuntu:~$

---

### Post by mlomker on 2005-10-22
[QUOTE=comradevik]bash: amarok: command not found
[/QUOTE]

Did you search for it?  I don't use gnome, but an icon is created under Multimedia in KDE.  The executable goes to /usr/bin, which is normally in the path.

```

sudo updatedb
locate amarok

```

---

### Post by Dr. Nick on 2005-10-22
[QUOTE=comradevik]# DONE - amaroK successfully installed/updated! Start it from your menu or by typing "amarok".
victor@ubuntu:~$ amarok
bash: amarok: command not found
victor@ubuntu:~$[/QUOTE]


What does amarokapp say? I got a shortcut to amarok in "applications-sound and video"


[QUOTE=mlomker]
I do a clean reload with every major release. If you keep your /home on another partition it makes the process pretty simple. thread1 thread2]
[/QUOTE]

I figure I'll end up doing this , moving my home partition this time. Of  course like every time I reinstall I will be tempted to delete that little NTFS partition at the front of my drive :D hehe.

This install has been through hoary and the entire breezy dev cycle, I encountered a few annoyances in the dev cycle that I havent solved yet and figure a reinstall will be faster and better.

---

### Post by comradevik on 2005-10-22
victor@ubuntu:~$ amarokapp
bash: amarokapp: command not found

locate amarok only gives me the amarok folder in my home/victor directory

---

### Post by mlomker on 2005-10-22
> locate amarok only gives me the amarok folder in my home/victor directory

Then I guess it didn't install anything.  You'll need to run the script and watch it closely.  If you don't **sudo** then it might not have rights to actually install the files.

---

### Post by souled on 2005-10-22
Dr. Nick, how did you fix the dcopserver problem? I'm getting that too.

And when I open amaroK, I get a window with the icon in it... Instead of going to the tray a window is opened for the icon.

---

### Post by Dr. Nick on 2005-10-23
[QUOTE=souled]Dr. Nick, how did you fix the dcopserver problem? I'm getting that too.

And when I open amaroK, I get a window with the icon in it... Instead of going to the tray a window is opened for the icon.[/QUOTE]

Word for word description of my problem , couldn't have said it better. I havent fixed it yet, had some other errors before that one that had to be fixed. I may mess with that tomorrow since I couldnt tonight, I too get the windows instead of it going to a tray. If anyone else is trying this how to and gets the same problem and finds a solution please do share. I will post here as soon as I fix either of the 2 errors. 

Souled do you use KDE or gnome? I have an idea to complie the kdebase from source, but I plan to disable alot of un-needed things which would most likely screw up KDE. If it does anything to help the dcop error I could send you a .deb somehow, or just tell you what commands to use, but if you ever wanted to use KDE It would probably cause problems

---

### Post by Dr. Nick on 2005-10-23
[QUOTE=comradevik]victor@ubuntu:~$ amarokapp
bash: amarokapp: command not found

locate amarok only gives me the amarok folder in my home/victor directory[/QUOTE]


What did you choose in the 2nd popup I think it was, It either ask for sudo or something like su -c

If you didnt before use the sudo one

---

### Post by souled on 2005-10-23
[QUOTE=Dr. Nick]
Souled do you use KDE or gnome? I have an idea to complie the kdebase from source, but I plan to disable alot of un-needed things which would most likely screw up KDE. If it does anything to help the dcop error I could send you a .deb somehow, or just tell you what commands to use, but if you ever wanted to use KDE It would probably cause problems[/QUOTE]

If it works, please send. I use Gnome. I will never use KDE, I think it looks so ugly haha, no offense to any KDE users.

---

### Post by mlomker on 2005-10-23
> did you fix the dcopserver problem?

I just loaded gnome on my test box and it works perfectly--icon in the task tray, just as I'd expect.  I'll try reloading a fresh gnome install in the morning without any KDE components and see what the results are.

I spent some time trying to get the SVN version to package as a .deb but I couldn't get checkinstall to do it.

---

### Post by mlomker on 2005-10-23
[QUOTE=souled]If it works, please send. I use Gnome. I will never use KDE, I think it looks so ugly haha, no offense to any KDE users.[/QUOTE]

Why would I be offended?  I always feel pity for the blind.  ;)

---

### Post by fanoodlehey on 2005-10-23
I get

# 2/10 - Checking out multimedia base files.
svn: Can't connect to host 'anonsvn.kde.org': Connection timed out

ERROR: The SVN transfer didn't finish successfully.

My network connection is up and running so I'm guessing this is something to do with my firewall. I use Guarddog. What protocol do I need to open up for SVN to work?

Maybe that's not the problem. Any ideas?
Note: I'm using KDE3.5

Thanks.

---

### Post by fanoodlehey on 2005-10-23
Yes. I confirmed that it was my firewall by disabling it momentarily. Now how do I allow SVN from guarddog?

Thanks for any help.

---

### Post by mlomker on 2005-10-23
> Now how do I allow SVN from guarddog?

[URL="http://svnbook.red-bean.com/en/1.1/ch06s03.html"]
It looks like[/URL] it's TCP 3690.  This how-to isn't about firewalls, though, so I don't want to stray that far off-topic here.  I also have not tested this on KDE 3.5.  I don't know if the beta comes with the right -dev files or not.

---

### Post by souled on 2005-10-23
FYI, My problem about the dcopserver and not docking is fixed... somehow. I restarted my computer and reinstalled kdebase-dev, and fired up amaroK and it's normal now. Not sure as to the cause of the poblem.

---

### Post by comradevik on 2005-10-23
ok i built it.. now  i cant choose mysql in the ocllection setup

---

### Post by fanoodlehey on 2005-10-23
[QUOTE=mlomker][URL="http://svnbook.red-bean.com/en/1.1/ch06s03.html"]
It looks like[/URL] it's TCP 3690.  This how-to isn't about firewalls, though, so I don't want to stray that far off-topic here.  I also have not tested this on KDE 3.5.  I don't know if the beta comes with the right -dev files or not.[/QUOTE]

Sorry, didn't mean to get off topic. Thanks for the info. Regarding KDE3.5, everything seems to have compiled without errors but there are some problems with amarok. I don't seem to be able to see or scan my collection. I'm not complaining though. This is what you get when you stray off the officially released packages. Here's a question I should have asked before I started, how do I uninstall this?

---

### Post by mlomker on 2005-10-23
> Here's a question I should have asked before I started, how do I uninstall this?

I don't know, I didn't write the script.  Have you already tried **make uninstall**?

---

### Post by mlomker on 2005-10-23
> how did you fix the dcopserver problem?

I found a work-around for this problem.  For some reason amaroK won't run properly unless it is run as root.  There are probably just some incorrect file permissions but I'm not going to take the time to figure it out.

If you run **sudo amarok** or configure your icon to gksudo then it should run fine.

---

### Post by souled on 2005-10-23
[QUOTE=mlomker]I found a work-around for this problem.  For some reason amaroK won't run properly unless it is run as root.  There are probably just some incorrect file permissions but I'm not going to take the time to figure it out.

If you run **sudo amarok** or configure your icon to gksudo then it should run fine.[/QUOTE]

This error doesn't occur for me anymore. I just reinstalled kdebase-dev and restarted my computer, and amaroK runs perfectly. I'm not sure why it works now, but it does :D. Thanks for your time and effort.

---

### Post by mlomker on 2005-10-23
> Thanks for your time and effort.

I had the same problem occur on a fresh Ubuntu Breezy install, so I'd expect others will also see the problem.  It doesn't happen when kubuntu-desktop is installed, so there may be another package that'd solve the problem but **sudo** also seems to take care of it.

---

### Post by Dr. Nick on 2005-10-23
[QUOTE=souled]This error doesn't occur for me anymore. I just reinstalled kdebase-dev and restarted my computer, and amaroK runs perfectly. I'm not sure why it works now, but it does :D. Thanks for your time and effort.[/QUOTE]


Hehe same here, a restart later now 0 errors, runs fine as normal user. If I were to guess a file with bad permissions I would say it might be .ICEauthority, in the installation I believe I changed the persmissions on it, then on restart couldnt login till I changed the owner/group back to my username and amarok loaded perfectly after that. Glad it was an easy fix for me and souled and hopefully anyone in the future. I dont even have kdebase-dev installed either

---

### Post by souled on 2005-10-23
So was the installation of amaroK the cause for the .ICEauthority error? Because  I got that too when I restarted and I just changed the owner back to my user.

---

### Post by Dr. Nick on 2005-10-23
[QUOTE=souled]So was the installation of amaroK the cause for the .ICEauthority error? Because  I got that too when I restarted and I just changed the owner back to my user.[/QUOTE]


I think it was, but if I remember I changed it myself using chgrp and chown commands, atleast those 2 commands are in my bash history but oddly I tried to change the owner of it to myself when it should have been already, dont remember where in the installation though, it may have been in a attempt to fix errors that a reboot would have solved for me. I have it set to be owned by my user, and group is my user also, I have read/write permissions for my user and no execute. or "600" permission and it seems to work fine now. 

Sorta funny that we both had the exact same troubles, I thought I was alone :D 

Still working beautifully now with a nice tray icon and no crashes. :KS

EDIT
Sorta funny that a restart worked, Thought that was a windows thing hehe

---

### Post by fanoodlehey on 2005-10-23
[QUOTE=mlomker]I don't know, I didn't write the script.  Have you already tried **make uninstall**?[/QUOTE]

No. Don't know where to do this from. Searched in the amarok-svn folder for uninstall. Couldn't find anything. Then just ran make uninstall in the folder but no luck. I'm really not familiar at all with install/uninstall outside of synaptic and apt-get.

Anyway, I just went ahead and installed amarok again from synaptic and it's working again.

Thanks for the help, it's much appreciated.

---

### Post by mlomker on 2005-10-23
> 
Sorta funny that we both had the exact same troubles, I thought I was alone :D 


I had the same issue with ICEauthority when I rebooted, so clearly the script is doing something to it.  I'll have to add something to the how-to for that.

---

### Post by Dr. Nick on 2005-10-23
I found a crude way to uninstall it. If you install the repo version it will most likely overwrite what the svn did and then uninstall the repo version and alot of it will be gone. I just tried this and amarok is gone now :(

No big deal though, all in the name of testing. Thats what I expected to happen anyway so that was nice :KS 

I am going to run through the walkthrough step by step now and I bet it will work "out of the box" this time through

---

### Post by Dr. Nick on 2005-10-23
Well Dang

I cant get it to install from svn now :(

Get some error 
```
/home/drnick/amarok/amarok-svn/amarok/src/metadata/mp4/taglib_mp4filetyperesolver.cpp:7:17: error: mp4.h: No such file or directory
Error creating ./amarok/src/metadata/taglib_mp4filetyperesolver.lo. Exit status 1.
```

Guess I have a little more work to do. I assume that this is a taglib problem but since I am on 64bit I cant use the one provided so this shouldn't affect the rest of the howto for others I dont think.

---

### Post by Mrtn on 2005-10-24
How do you remove it?

It doesn't work so I want it gone =(

---

### Post by fanoodlehey on 2005-10-24
Well I just installed amarok from the repos using synaptic and this set me up with the non-svn version. Can't really call that an uninstall but it's good enough for me.

---

### Post by mlomker on 2005-10-24
> How do you remove it?

You could try **sudo make uninstall** from within the amarok-svn directory.  Otherwise you could just reinstall the Breezy version--as far as I know the files all go to the same places.

---

### Post by Mrtn on 2005-10-24
Whats that place then? =)

---

### Post by Mrtn on 2005-10-24
make: *** No rule to make target `uninstall'.  Stop.

---

### Post by mlomker on 2005-10-24
[QUOTE=Mrtn]Whats that place then? =)[/QUOTE]

Like I said in the how-to, the script was written by the amaroK developers.  You can try contacting them on their wiki if you like.

---

### Post by Dr. Nick on 2005-10-24
Well I sorta got it back, now I get an error about not being able to launch kmail, if I just ignore that error and leave the box open and move it to another workspace to get it out of the way it will run fine.

I think the howto is as best as it can be since alot of the trouble people have had is due to the script which we have little control over.

My only remaning tips would be to always change iceauthority back to correct owner if you attempt to use the script as it seems to change it fairly early in the process.

If it says its installed but cant find command when running, then scroll up and look for errors, I to was told it was sucessfull when it wasnt, taglib neded to be reinstalled before it was actually sucessfull.

If all else fails then restart and try again, after changing iceauthority of course. :) 

Of course the perfectionist in me wont let me give up quite yet and I will fight this error till my death :KS  ...well maybe not quite.

Hope this HOWTO helps alot of people get it running and thanks again mlomker for writing it up.

---

### Post by dominik on 2005-11-06
i get an error while the script is compiling:

> libtool: link: cannot find the library `/usr/lib/libmad.la'
Error creating ./amarok/src/amarokapp. Exit status 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded. Ask the friendly people in #amarok on freenode for help.
dom@ubuntu:~/amarok$


---

### Post by Dr. Nick on 2005-11-06
[QUOTE=dominik]i get an error while the script is compiling:[/QUOTE]

make sure all the dependencies from the howto are installed, Also I found a package called libmad0 that I have installed and may help you, not sure though since I cant recreate your exact situation. If that doesnt work post back the error message. If you scroll back through do you see any other errors?

---

### Post by mlomker on 2005-11-06
[QUOTE=dominik]i get an error while the script is compiling:[/QUOTE]

Try installing **libmad0-dev**

I find the error odd, though, because I don't have that installed and mine builds fine.

---

### Post by spdfrk on 2005-11-09
I can't install build-essential. I get this error...

build-essential: Depends: gcc (>= 4:4.0) 
                      Depends: g++ (>= 4:4.0) 

Any ideas?

---

### Post by souled on 2005-11-09
[QUOTE=spdfrk]I can't install build-essential. I get this error...

build-essential: Depends: gcc (>= 4:4.0) 
                      Depends: g++ (>= 4:4.0) 

Any ideas?[/QUOTE]

Fire up synaptic and install gcc-4.0 or from terminal type in "sudo apt-get install gcc-4.0"

---

### Post by kazu on 2005-11-09
Just to say thank you for that script and that tutorial.
Good job ! Thank you.
[IMG]http://blog.naktan.info/images/Naruto/Lee.jpg[/IMG]
KaZu

---

### Post by spdfrk on 2005-11-09
[QUOTE=souled]Fire up synaptic and install gcc-4.0 or from terminal type in "sudo apt-get install gcc-4.0"[/QUOTE]

I can't install gcc-4.0 :-(
I get this message in Synaptic (freely translated from swedish... :-) )

gcc-4.0:
  Depends: gcc-4.0-base (=4.0.1-4ubuntu9) but 4.0.2-3ubuntu1 will be installed
  Depends: cpp-4.0 (=4.0.1-4ubuntu9) but 4.0.2-3ubuntu1 will be installed

---

### Post by souled on 2005-11-09
[QUOTE=spdfrk]I can't install gcc-4.0 :-(
I get this message in Synaptic (freely translated from swedish... :-) )

gcc-4.0:
  Depends: gcc-4.0-base (=4.0.1-4ubuntu9) but 4.0.2-3ubuntu1 will be installed
  Depends: cpp-4.0 (=4.0.1-4ubuntu9) but 4.0.2-3ubuntu1 will be installed[/QUOTE]

Whenever you see something depends on something else, install those dependent files. In this case, install gcc-4.0-base and cpp-4.0.

---

### Post by mlomker on 2005-11-09
[QUOTE=souled]Whenever you see something depends on something else, install those dependent files. In this case, install gcc-4.0-base and cpp-4.0.[/QUOTE]

Usually apt-get or Synaptic takes care of that.  You might want to verify that your sources.list is correct.  If it is then it could be a temporary problem in the repositories as well.

---

### Post by webhead on 2005-11-09
Dammit........ so close!  Followed the HOWTO and was nearing the end, when this happened
> 
collect2: ld returned 1 exit status
Error creating ./amarok/src/collectionscanner/amarokcollectionscanner. Exit stat us 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded. Ask the  friendly people in #amarok on freenode for help.


I completed every step upto, *sudo ./get-amarok-svn.sh* and it was upon attempting that step, that the above error occured.  Any ideas?

Thanks for all your help so far guys,

Dan

---

### Post by webhead on 2005-11-09
Anyone?  Help?

---

### Post by mlomker on 2005-11-10
[QUOTE=webhead]Anyone?  Help?[/QUOTE]

This isn't a problem with the how-to...everything in SVN is beta code and sometime it breaks.  It looks like they just added a bunch of features--iPod and Helix...none of which are documented so I'm not sure what dependencies are required to get them to build.

I couldn't compile the last time that I tried, but this morning it appears to be working.  The build at the moment is 479435.

---

### Post by webhead on 2005-11-10
Hmmm..........same error for me this morning.

Could anything else be casuing this for me?

Dan

---

### Post by mlomker on 2005-11-10
> Could anything else be casuing this for me?


Sorry, I'm not a programmer.  I think when it crashes it tells you what IRC channel to contact them on.

---

### Post by stoeptegel on 2005-11-15
@webhead:
I had the same error and asked in irc. :)  
The error pops because taglib 1.4 and 1.3 are installed. You have to eradicate 1.3 first. (note that removing taglib 1.3 will remove other package like k3b)

---

### Post by WetWilly on 2005-11-15
This is cool!

Works great!

---

### Post by henriquemaia on 2005-11-15
[QUOTE=stoeptegel]@webhead:
I had the same error and asked in irc. :)  
The error pops because tablib 1.4 and 1.3 are installed. You have to eradicate 1.3 first. (note that removing tablib 1.3 will remove other package like k3b)[/QUOTE]

Had the same error and corrected doing what you said. Thanks. Now I'm running Amarok-svn.

---

### Post by didit on 2005-11-16
got problem here... :( 


ome/didit/Desktop/amarok-svn/amarok/src/mediabrowser.cpp: In constructor ‘MediaDeviceView::MediaDeviceView(MediaBrowser*)’:
/home/didit/Desktop/amarok-svn/amarok/src/mediabrowser.cpp:976: error: cannot allocate an object of abstract type ‘DummyMediaDevice’
/home/didit/Desktop/amarok-svn/amarok/src/mediabrowser.cpp:155: note:   because the following virtual functions are pure within ‘DummyMediaDevice’:
/home/didit/Desktop/amarok-svn/amarok/src/mediabrowser.h:286: note:  virtual MediaItem* MediaDevice::copyTrackToDevice(const MetaBundle&, bool)
Error creating ./amarok/src/mediabrowser.o. Exit status 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded. Ask the friendly people in #amarok on freenode for help.

---

### Post by mlomker on 2005-11-16
[QUOTE=didit]ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded. Ask the friendly people in #amarok on freenode for help.[/QUOTE]

I'd wait a day and try downloading the next build.  If it still fails then jump on IRC and ask them about it.  I haven't seen that error on my builds.

---

### Post by souled on 2005-11-17
So there's going to be a new build tomorrow?

---

### Post by Suman on 2005-11-17
Excellent HOWTO, works like a charm even for a total newbie like me.

---

### Post by Dr. Nick on 2005-11-17
[QUOTE=souled]So there's going to be a new build tomorrow?[/QUOTE]

svn is never the final version really, It is always the latest bleeding edge version.

This script gets you the newest version which is most likely beta, I am not sure if they update EVERY day or not, but it should update atleast a few times a week.

---

### Post by MemoryDump on 2005-11-17
worked like a charm right away after a fresh ubuntu install !! 

Thxs :p
-MD

---

### Post by Neutrino on 2005-11-18
When i run the script i got this error :

# 8/10 - Configuring. (This will also take a while.)
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: ""
checking build system type... Invalid configuration `""': machine `""' not recognized
configure: error: /bin/sh admin/config.sub "" failed

ERROR: Configuration wasn't successful. amaroK was NOT installed/upgraded. Ask the friendly people in #amarok on freenode for help.


I don't know what to do. 
Any help is welcome.
regards

---

### Post by Rob2687 on 2005-11-19
I installed it but evertime I run it, it says:
```
trying to create local folder /home/robert/.kde/share/config: Permission denied

```

---

### Post by mlomker on 2005-11-19
[QUOTE=Rob2687]I installed it but evertime I run it, it says:
[/QUOTE]

That's odd.  You're running it with **sudo**?

---

### Post by Rob2687 on 2005-11-19
It works when I run with sudo but I thought it was supposed to be able to run without the sudo...

---

### Post by mlomker on 2005-11-19
[QUOTE=Rob2687]It works when I run with sudo but I thought it was supposed to be able to run without the sudo...[/QUOTE]

Perhaps I misunderstood...I thought you were getting a compilation error.  You're saying that you have to **sudo amarok** to get it to run?  That's odd.  I'm not sure from that error message what file has the incorrect permissions.

---

### Post by foxy123 on 2005-11-24
thanks a lot for your how-to. Hopefully amarok-svn is as stable as it is eye-candy!

---

### Post by ShakingSpirit on 2005-11-25
The 'get-amarok-svn.sh' script is out of date now; you should use 'amarok-svn.sh' from [http://speedtest.1go.dk/amarok-svn.sh](http://speedtest.1go.dk/amarok-svn.sh) :)
You can run the script from your home dir as your normal user, and put in your sudo password when it asks for it (that way you don't get any nasty permission errors) :)

---

### Post by foxy123 on 2005-11-25
> **ShakingSpirit]The 'get-amarok-svn.sh' script is out of date now said:**
> http://speedtest.1go.dk/amarok-svn.sh[/url] :)
You can run the script from your home dir as your normal user, and put in your sudo password when it asks for it (that way you don't get any nasty permission errors) :)
shoudl I unistall the amarok built with a previous script before using a new one? And how can I do it?

---

### Post by mlomker on 2005-11-25
> **ShakingSpirit]The 'get-amarok-svn.sh' script is out of date now said:**
> http://speedtest.1go.dk/amarok-svn.sh[/url] :)

Thanks.  I'll update the how-to and that's a nice improvement.

---

### Post by mlomker on 2005-11-25
[QUOTE=foxy123]shoudl I unistall the amarok built with a previous script before using a new one? And how can I do it?[/QUOTE]

They are the same, so no need to remove it.  I deleted the old amarok-svn directory before running the new script for the first time (at least one file had root permissions).

---

### Post by foxy123 on 2005-11-25
[QUOTE=mlomker]They are the same, so no need to remove it.  I deleted the old amarok-svn directory before running the new script for the first time (at least one file had root permissions).[/QUOTE]
thanks, let me try...

---

### Post by souled on 2005-11-26
How come the "Fill in tags using musicbrainz' feature doesn't work? I always get the track wasn't found in the database. I have the libmusicbrainz installed...

---

### Post by mlomker on 2005-11-27
[QUOTE=souled]How come the "Fill in tags using musicbrainz' feature doesn't work? I always get the track wasn't found in the database. I have the libmusicbrainz installed...[/QUOTE]

SVN builds are betas...there will always be things that don't work.  You can ask them on their IRC channel if you wish, but they might not appreciate it...it's a beta.

---

### Post by daobear on 2005-11-27
Hi.  I'm having problems similar to what a couple of others have had.
My first question is this: We download a file called amarok-svn.sh, but the command is ./get-amarok-svn.sh?  I added execute to the file permissions, but hen I type ./get-amarok-svn.sh I get the error:

```

bash: ./get-amarok-svn.sh: No such file or directory

```

So instead I tried
sudo ./amarok-svn.sh

I needed the sudo otherwise it couldn't create the directory /opt/amarok-svn.
It started to install, but when it get to linking to the collection scanner, I get errors:
```

linking ./amarok/src/collectionscanner/amarokcollectionscanner
/bin/sh ./libtool --silent --mode=link --tag=CXX g++ -Wno-long-long -Wundef -ans i -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -g3 -fno-inline -Wformat-security -Wmissing-format-attr ibute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEA N_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -D QT_THREAD_SUPPORT -D_REENTRANT -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib -R /usr/lib -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -o ./amarok/src/ collectionscanner/amarokcollectionscanner ./amarok/src/metadata/libmetadata.la - lqt-mt -lz -lpng -lz -lm -lXext -lX11 -lSM -lICE -lpthread -lkdecore -L/usr/loca l/lib -ltag ./amarok/src/collectionscanner/main.o ./amarok/src/collectionscanner /collectionscanner.o
/usr/bin/ld: warning: libstdc++.so.6, needed by /usr/local/lib/libtag.so, not fo und (try using -rpath or -rpath-link)
/usr/local/lib/libtag.so: undefined reference to `std::ios_base::Init::~Init [in -charge]()@GLIBCXX_3.4'

```

This is followed by many undefine reference errors (I won't list them all here), and then by ```

collect2: ld returned 1 exit status
Error creating ./amarok/src/collectionscanner/amarokcollectionscanner. Exit stat us 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded. Ask the  friendly people in #amarok on freenode for help.
Error: "/tmp/ksocket-daobear" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/tmp/ksocket-daobear" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/tmp/kde-daobear" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
kbuildsycoca running...
Error: "/var/tmp/kdecache-daobear" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-daobear" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-daobear" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
daobear@dhcpo-41-227:/opt$ ICE default IO error handler doing an exit(), pid = 21177, errno = 0

```

I'm not really sure what all this means.  Help?
BTW, I'm using Gnome.

---

### Post by mlomker on 2005-11-28
[QUOTE=daobear]Hi.  I'm having problems similar to what a couple of others have had.
My first question is this: We download a file called amarok-svn.sh, but the command is ./get-amarok-svn.sh? 
[/quote]

They changed the name of the file recently.  I updated that line of the how-to.  Thanks for pointing it out.

> 
I needed the sudo otherwise it couldn't create the directory /opt/amarok-svn.


Perhaps I should recommend running it from /home instead.  It never use to be a problem because the prior script had to be run as sudo.

> 
It started to install, but when it get to linking to the collection scanner, I get errors:


I noticed that Ubuntu recently made those files available, but they installed automatically on my machine during a system update.

Try:

```

sudo apt-get install libstdc++6 libstdc++6-4.0-dev

```

---

### Post by Moobert on 2005-12-04
[QUOTE=mlomker]I don't know, I didn't write the script.  Have you already tried **make uninstall**?[/QUOTE]

use:

sudo `which unsermake` uninstall

---

### Post by simoncullen on 2005-12-06
I am getting this error after running ./amarok-svn.sh in my home directory. To see the full output: [http://amarok.pastebin.com/451821](http://amarok.pastebin.com/451821) 

Does anyone have any idea what could cause this?  It was working perfectly a week ago...  This file "/usr/lib/libstdc++.la" doesn't even exist, although I have all of the requisite libraries installed.

Cheers, Simon

```
linking ./amarok/src/loader/amarok
linking ./amarok/src/collectionscanner/amarokcollectionscanner
/bin/sh ./libtool --silent --mode=link --tag=CXX g++ -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -g3 -fno-inline -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -DQT_THREAD_SUPPORT -D_REENTRANT -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib -R /usr/lib -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -o ./amarok/src/collectionscanner/amarokcollectionscanner ./amarok/src/metadata/libmetadata.la -lqt-mt -lz -lpng -lz -lm -lXext -lX11 -lSM -lICE -lpthread -lkdecore -L/usr/lib -ltag ./amarok/src/collectionscanner/main.o ./amarok/src/collectionscanner/collectionscanner.o
libtool: link: cannot find the library `/usr/lib/libstdc++.la'
Error creating ./amarok/src/collectionscanner/amarokcollectionscanner. Exit status 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded. Ask the friendly people in #amarok on freenode for help.
kbuildsycoca running...
simon@ahimsa:~/amaroksvn$ ICE default IO error handler doing an exit(), pid = 12470, errno = 0

```

---

### Post by mlomker on 2005-12-06
[QUOTE=simoncullen]This file "/usr/lib/libstdc++.la" doesn't even exist, although I have all of the requisite libraries installed.
[/QUOTE]

See the end of post 92 and give that a try.

You should also download the apt-file package...it's super handy in situations like this because it gives you a list of every package that contains the file.  You might have to install a few before you get it right, but it really narrows things down for you.

```

sudo apt-get install apt-file
sudo apt-file update

```

Then:

```

mlomker@mlomkernote:/$ apt-file search libstdc++.la
gcc-snapshot: usr/lib/gcc-snapshot/lib/debug/libstdc++.la
gcc-snapshot: usr/lib/gcc-snapshot/lib/libstdc++.la
lib64stdc++6-4.0-dbg: usr/lib64/debug/libstdc++.la
libstdc++5-3.3-dbg: usr/lib/debug/libstdc++.la
libstdc++6-4.0-dbg: usr/lib/debug/libstdc++.la
libstdc++6-dbg: usr/lib/debug/libstdc++.la
libstdc++6-dbg: usr/lib64/debug/libstdc++.la
llvm-cfe: usr/lib/llvm/cfrontend/lib/libstdc++.la
mingw32: usr/lib/gcc/i586-mingw32msvc/3.4.2/libstdc++.la
pocketpc-g++: usr/arm-wince-pe/lib/libstdc++.la
mlomker@mlomkernote:/$

```

---

### Post by simoncullen on 2005-12-06
...all problems are fixed!  cheers

---

### Post by gk_jam on 2005-12-07
Do you know how to use this method to compile amaroK with MySQL support? I've installed mysql-server-4.1 as well as mysql-common-4.1, & mysql-client-4.1, and the server is started (mysqld is running).

I tried using ./amarok-svn.sh, and when it prompts me for parameters, I use "--enable-mysql". The configure script then searches for mysql, but the console shows this:

```

checking for mysql_config... no

```

and later:

```

 = The following extra functionality will NOT be included:
 =   - aRts-engine
 =   - NMM-engine
 =   - MAS-engine
 =   - Helix-engine
 =   - libvisual Support
 =   - XMMS Visualization Wrapper
 =   - MySql Support
 =   - Postgresql Support
 =   - MusicBrainz Support
 =   - Moodbar Support
 =   - iRiver iFP Support

```

Anyone know why the script wouldn't see mysql_config, and how I can make sure that it's there?


EDIT: I figured out what I was missing, namely libmysqlclient-dev. I had the library files, but not the development files. Once I installed that, I was able to compile with MySQL support using the "--enable-mysql" parameter.

---

### Post by Madhatter14641 on 2005-12-08
[QUOTE=Dr. Nick]Didnt work or me, gives errors telling me to start dcopserver, Im on gnome btw. 

I think I messed up at the begennig but how can I start over? I deleted the amarok-svn folder but want to get rid of what it already installed and try again.

Any chance to have the script to just compile and not install? I would like to use checkinstall to make a deb for easy removal later.[/QUOTE]

When you run the script, run "./amarok-svn.sh -r" . This will reset the script and let you reconfigure all of those options from the beginning. I had a lot of problems when trying to get the AAC tags to work. I reset the bloody thing repeatedly and it ended up working in the end.

---

### Post by mlomker on 2005-12-08
[QUOTE=Madhatter14641]AAC tags to work. I reset the bloody thing repeatedly and it ended up working in the end.[/QUOTE]

You're talking about the MP4/AAC piece?  Did you install any additional packages?  I've been looking for the dependencies on some of these 'extras' and haven't had luck with some of them.

---

### Post by gk_jam on 2005-12-08
I got mp4/aac support to work pretty easily. Just make sure that libmp4v2 dev and faad2 dev packages are installed.

---

### Post by mlomker on 2005-12-08
[QUOTE=gk_jam]I got mp4/aac support to work pretty easily. Just make sure that libmp4v2 dev and faad2 dev packages are installed.[/QUOTE]

Cool.  Added to the how-to.

---

### Post by RDo on 2005-12-13
Works great .... but now my iPod doesn't connect to Amarok. I just get that I don't have a supported device. My iPod is mounted in /media/ipod and changing it to /mnt/ipod doesn't do anything... please help... 

This is the last device I need to get to work... with amarok en aac support witch is working in Amarok now.... so I can say windows goodbye....

---

### Post by mlomker on 2005-12-13
[QUOTE=RDo]This is the last device I need to get to work... with amarok en aac support witch is working in Amarok now.... so I can say windows goodbye....[/QUOTE]

I'm not sure which package is needed for iPod support.  Do you have **gtkpod** installed?

---

### Post by WanderingStar on 2005-12-13
I have Amarok w/ AAC and iPod support up now, thanks to this thread and some reading.  

To get the iPod support you need to get [libgpod]("http://www.gtkpod.org/libgpod.html"). The snapshot there builds clean here - but I have most of the dev packages, so YMMV.  Once you download the snapshot use './configure --prefix=/usr && make && sudo make install' without the quotes to build it. When the script asks for extra flags use --with-mp4v2 --with-libgpod. Should build clean.

---

### Post by RDo on 2005-12-14
Done both.... libgpod installed with the prefixes and gtkpod is installed. GTKpod does seem to work but still no Amarok ipod connection.

---

### Post by WanderingStar on 2005-12-14
Part of the script lists what options its going to actually compile from.  To see it just scroll back through the comilation.  Does it say its going to compile with libgpod support?  Does your iPod appear in Nautilus when you plug it in?  What iPod do you have?  When I got it to work I had to delete every directory in the iPod and use gtkpod to recreate the dirs and basically copy everything over anew.  So that may work.  I had to do it for different reasons, but perhaps it needs to start clean.

---

### Post by uopjohnson on 2005-12-15
[QUOTE=RDo]Done both.... libgpod installed with the prefixes and gtkpod is installed. GTKpod does seem to work but still no Amarok ipod connection.[/QUOTE]
same here.  libgpod built just fine and amarok reported Building with Ipod support when I built it...
but I still get: no supported media device.  
Other than that thanks for the SVN guilde it worked great and now I have mp4 support!

---

### Post by eduardgrebe on 2005-12-16
[QUOTE=mlomker]
[Download]("http://mail3.mpr.org/mlomker/taglib-1.4_i386.deb") the .deb file for taglib 1.4.

Change to the download directory:
```

sudo dpkg -i taglib-1.4_i386.deb

```
[/QUOTE]

Does anyone know of a version of taglib 1.4 compiled for powerpc? My search of the web yielded nothing. The dapper packaged libtag1-dev (1.4-2ubuntu1) seemed it may work, but it depends on a whole host of other dapper packages, and I was afraid of damaging my system by upgrading to all those potentially unstable packages.

Any advice?

---

### Post by mlomker on 2005-12-16
[QUOTE=eduardgrebe]Does anyone know of a version of taglib 1.4 compiled for powerpc? [/QUOTE]

You'll want to compile it yourself.  The DEB that I provide is one that I compiled and used checkinstall to package.

[Grab it here.]("http://developer.kde.org/~wheeler/files/src/taglib-1.4.tar.gz")

---

### Post by sailor420 on 2005-12-16
Excellent, nice guide--worked without a hitch.

Now I just have to decide whether or not it was worth it to install 150MB of stuff for a music player...

---

### Post by mlomker on 2005-12-16
[QUOTE=sailor420]Now I just have to decide whether or not it was worth it to install 150MB of stuff for a music player...[/QUOTE]

Are you kidding?  amaroK is reason enough to run linux.  They actually have their own liveCD these days.

---

### Post by sailor420 on 2005-12-18
[QUOTE=mlomker]Are you kidding?  amaroK is reason enough to run linux.  They actually have their own liveCD these days.[/QUOTE]

AmaroK is quite nice, but I personally never liked the "library" style players like amaroK, iTunes, etc, so it's gonna be a bit before I get used to it...

I do love that it comes with last.fm support included--I struggled for a long time to get that plugin working for XMMS.

---

### Post by M4v3R on 2005-12-18
It worked like a charm. Now amaroK is much more stable than before! Thank you very much for this guide!

---

### Post by Josip Lazic on 2005-12-19
I use amarok-svn.ch script and everything goes OK, but when I run amarok i got this error:

> 
amaroK could not find any sound-engine plugins. amaroK is now updating the KDE configuration database. Please wait a couple of minutes, then restart amaroK.
If this does not help, it is likely that amaroK is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.


I use Ubuntu Breezy, and i tried to use standard ./configure && make && checkinstall but error is still there :(

---

### Post by mlomker on 2005-12-19
[QUOTE=Josip Lazic]I use Ubuntu Breezy, and i tried to use standard ./configure && make && checkinstall but error is still there :([/QUOTE]

I have not idea why you'd do that.  The script handles all of that.  You'll need to pay attention to what modules are being built (the configure step within their script tells you that).  You need at least one of the sound engines to build, of course.

---

### Post by souled on 2005-12-19
Is there a way to add more sites that amaroK checks when searching for album covers and for lyrics?

---

### Post by Josip Lazic on 2005-12-20
[QUOTE=mlomker]I have not idea why you'd do that.  The script handles all of that.  You'll need to pay attention to what modules are being built (the configure step within their script tells you that).  You need at least one of the sound engines to build, of course.[/QUOTE]

I tried The Script AND the old way (./configure && ...).
But problem was solved by searching and removing files that had amarok in its name. There was some orphaned libs.
Now everything works OK.

PS. Sorry because my bad english :(

---

### Post by mlomker on 2005-12-20
[QUOTE=Josip Lazic]PS. Sorry because my bad english :([/QUOTE]

No problem!  I'm glad that you figured it out.

---

### Post by mlomker on 2005-12-20
[QUOTE=souled]Is there a way to add more sites that amaroK checks when searching for album covers and for lyrics?[/QUOTE]

Not that I know of (it uses Amazon), but you could ask them in IRC.  It isn't difficult to Google for the cover and add it in manually.

---

### Post by limit223 on 2005-12-22
Does anyone get built amarok with the new gstreamer 0.8.11?
I've got errors on compilation something:

/home/limit/Documente/Amarok/amarok-svn/amarok/src/collectionscanner/collectionscanner.cpp
/home/limit/Documente/Amarok/amarok-svn/amarok/src/collectionscanner/collectionscanner.cpp: In member function 'void CollectionScanner::scanFiles(const QStringList&)':
/home/limit/Documente/Amarok/amarok-svn/amarok/src/collectionscanner/collectionscanner.cpp:213: warning: name lookup of 'it' changed
/home/limit/Documente/Amarok/amarok-svn/amarok/src/collectionscanner/collectionscanner.cpp:206: warning:   matches this 'it' under ISO standard rules
/home/limit/Documente/Amarok/amarok-svn/amarok/src/collectionscanner/collectionscanner.cpp:209: warning:   matches this 'it' under old rules databasecollectionscanner.cpp 


and then after compilation the program hang on a error like:
[void CollectionDB::createTables(DbConnection*)]

open amarok compiled from SVN:


amarok:   [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(c
onst QString&)]  sqlite3_compile error:
amarok:   [CollectionDB] [ERROR!] no such table: tags
amarok:   [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT
0, 1;
limit@ubuntu:~$ amarok:   BEGIN: ScanController::ScanController(QObject*, bool,
const QStringList&)
amarok:     [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query
(const QString&)]  sqlite3_compile error:
amarok:     [CollectionDB] [ERROR!] table tags_temp already exists
amarok:     [CollectionDB] [ERROR!] on query: CREATE  TABLE tags_temp (url VARCH

amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.0043s
amarok: [ThreadWeaver] Job completed: PlaylistReader. Jobs pending: 1
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.00066s
amarok: [ThreadWeaver] Job completed: PlaylistReader. Jobs pending: 1
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.00065s
amarok: [ThreadWeaver] Job completed: PlaylistReader. Jobs pending: 2
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()

amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.00065s
amarok: [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(con                                st QString&)]  sqlite3_compile error:
amarok: [CollectionDB] [ERROR!] no such table: tags


I'm not really sure that gstreamer would be a problem or mysql but I tried many times to compile svn source and tarball source as well having the same error.


Edit: Must be sqlite ....I can't figure out any solution.

---

### Post by eduardgrebe on 2005-12-23
[QUOTE=mlomker]
[Download]("http://mail3.mpr.org/mlomker/taglib-1.4_i386.deb") the i386 DEB file for Taglib 1.4.  If you run another architecture then [download]("http://developer.kde.org/~wheeler/files/src/taglib-1.4.tar.gz") the source and compile your own.

Change to the download directory:
```

sudo dpkg -i taglib-1.4_i386.deb

```[/QUOTE]

In case anyone is interested, I have compiled and packaged the taglib 1.4 for powerpc. The deb is available from [here]("http://maanskyn.za.net/ubuntu/taglib_1.4-1_powerpc.deb").

---

### Post by cron0 on 2005-12-23
```
unsermake -f admin/Makefile.common cvs
./admin/cvs.sh: line 33: --version: command not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
Error creating cvs. Exit status 1.
Error creating all. Exit status 1.
```

This is what I get when executing the SVN script. Any ideas?
This is the line that appears on line 33:
```
AUTOCONF_VERSION=`$AUTOCONF --version | head -n 1`
```
But **$AUTOCONF** isn't defined anywhere...

Any ideas?

TIA!
cron0

---

### Post by nickless on 2005-12-24
This looks nice, but I have a questions before I start messing around here :D
What will happen with my playlist? Will they survive? :)

---

### Post by mlomker on 2005-12-24
[QUOTE=nickless]What will happen with my playlist? Will they survive? :)[/QUOTE]

It's a beta that I didn't write, so I'm not promising anything.  :p 

Playlists and other preferences are stored in your ~/ and have nothing to do with the application, afaik.

---

### Post by mlomker on 2005-12-24
[QUOTE=cron0]
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
[/QUOTE]

That means that you don't have autoconf installed.  Check in Synaptic.  The current version is 2.59-a3.

---

### Post by mlomker on 2005-12-24
[QUOTE=eduardgrebe]The deb is available from [here]("http://maanskyn.za.net/ubuntu/taglib_1.4-1_powerpc.deb").[/QUOTE]

Thanks, I linked to it.

---

### Post by monotux on 2005-12-30
Is there any way of going back to ordniary amarok after trying this svn-script?
I only tried it since the vanilla amarok crashed on me :(

---

### Post by mlomker on 2005-12-30
Just reinstall Ubuntu's package...the files go to the same place.

---

### Post by 7878ponce on 2006-01-10
Just got it to work!

w00t!

---

### Post by domino on 2006-01-11
I love it! The how-to was excellent. I hope someone can tell me if there is a shoutcast browser included? I listen to many broadcasts and having to add each station can be a task.

---

### Post by flosofl on 2006-01-11
Thanks so much.  This worked perfectly.  I can get (and play) my podcasts, playback my entire AAC library (about 16 GB), manage collection with MySQL, manage my iPod...  This thing rocks!

---

### Post by lionsnob on 2006-01-17
Wow!  This is very neat!  Brought over 7500 aac files from iTunes.  Thanks for the guide and tips from all.

I have a few questions.  Is there any advantage to using MySQL to catalog the music?  I assume there's a performance gain?  Also, how does one enable visualizations?

---

### Post by souled on 2006-01-20
[QUOTE=lionsnob]
Is there any advantage to using MySQL to catalog the music?  I assume there's a performance gain?[/QUOTE]

I would also like to know this...bump.

---

### Post by muted on 2006-01-24
So do you use KDE or Gnome??

Anyways do you know if not using KDE but ie gnome can cause any problems in relation to Amarok... cause i sort of think that is my problem...

---

### Post by muted on 2006-01-24
oh, and this:

> compiling /home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:41: warning: missing initializer for member '_GstCaps::flags'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:41: warning: missing initializer for member '_GstCaps::structs'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:41: warning: missing initializer for member '_GstCaps::_gst_reserved'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:41: warning: missing initializer for member '_GstStaticCaps::_gst_reserved'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:48: warning: missing initializer for member '_GstCaps::flags'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:48: warning: missing initializer for member '_GstCaps::structs'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:48: warning: missing initializer for member '_GstCaps::_gst_reserved'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:48: warning: missing initializer for member '_GstStaticCaps::_gst_reserved'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:59: warning: unused parameter 'data'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp: In function 'GType gst_equalizer_get_type()':
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:59: warning: missing initializer for member '_GTypeInfo::value_table'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp: In function 'void gst_equalizer_class_init(GstEqualizerClass*)':
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:82: warning: unused variable 'gstelement_class'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp: In function 'void gst_equalizer_get_property(GObject*, guint, GValue*, GParamSpec*)':
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/gstequalizer.cpp:216: warning: passing 'float' for argument 2 to 'void g_value_set_int(GValue*, gint)'
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h: At global scope:
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h:49: warning: 'iir_cforiginal10_44100' defined but not used
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h:71: warning: 'iir_cforiginal10_48000' defined but not used
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h:137: warning: 'iir_cf15_44100' defined but not used
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h:169: warning: 'iir_cf15_48000' defined but not used
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h:201: warning: 'iir_cf25_44100' defined but not used
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h:253: warning: 'iir_cf25_48000' defined but not used
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h:305: warning: 'iir_cf31_44100' defined but not used
/home/jacob/Downloads/amarok-svn/amarok/src/engine/gst/equalizer/iir_cf.h:369: warning: 'iir_cf31_48000' defined but not used

during the install / compile / whatever it does...

Meaning??

PS Great guide, much needed!


PPS: My amarok works though :D:D:D

---

### Post by foxy123 on 2006-01-24
[QUOTE=muted]So do you use KDE or Gnome??

Anyways do you know if not using KDE but ie gnome can cause any problems in relation to Amarok... cause i sort of think that is my problem...[/QUOTE]
I use xfce and have no problem. The only issue is that you end up with a load of KDE libraries and stuff to be able to compile amarok.

---

### Post by foxy123 on 2006-01-24
[QUOTE=muted]So do you use KDE or Gnome??

Anyways do you know if not using KDE but ie gnome can cause any problems in relation to Amarok... cause i sort of think that is my problem...[/QUOTE]
I use xfce and have no problem. The only issue is that you end up with a load of KDE libraries and stuff to be able to compile amarok.

---

### Post by muted on 2006-01-24
[QUOTE=foxy123]I use xfce and have no problem. The only issue is that you end up with a load of KDE libraries and stuff to be able to compile amarok.[/QUOTE]
okay... Well, i must say, i was a bit to fast with the problem part.. Amarok 1.4 runs pretty great now, thanks alot!! Id rather this than iTunes / xmms / whatever

:) :) :) Great guide

---

### Post by mlomker on 2006-01-24
[QUOTE=muted]oh, and this:


during the install / compile / whatever it does...

Meaning??
[/QUOTE]

That means it's beta code.  ;)

---

### Post by wall0159 on 2006-01-28
Hi all,

having some problems compiling amarok-svn. Issue is that I can't get ipod support.

I've passed "--with-libgpod" to the script, but it appears that the configure script doesn't detect my installation of libgpod. What's interesting, is that the configure script appears to be looking for libgpod-1.0 - this doesn't exist - I have the latest version installed (0.3.0). Is this a problem?

Anyway, despite it being there, it's not detecting, so "iPod support" goes in the "NOT included" catagory. :-(

I had a quick go at "hacking in" ipod support to the configure.in file, but it's overwritten each time, and I'm not sure where the originals are..

{
btw, these files exist:
/usr/lib/libgpod.so.0
/usr/lib/libgpod.so.0.300.0
}

Any help much appreciated!

Cheers,
-Angus

---

### Post by wall0159 on 2006-01-29
I sorted it :-)

For some reason, the version of libgpod that I installed via synaptic was not detected by the configure script. I installed it from source (from the gnupod site), and recompiled amaroK, and everything is happy happy :-).

Thanks for the pointers in the thread. and thanks to the dev team - amaroK craps on iTunes!!

-Angus

---

### Post by souled on 2006-02-05
I'm trying to compile amaroK, but I get an error saying that Ruby 1.8 or greater isn't installed on my computer. I installed Ruby 1.8 and the dev files, but I still get that error. How can I fix this?

---

### Post by o_fortuna on 2006-02-06
Hm. I used to have this running, but after I installed and began to use kwin (KDE window manager) on GNOME, it stopped working. (It crashed every time it started up. After I restarted, I was able to use the ones from the repos, but 3/4 of my library is mp4/aac). So, I uninstalled it, and then tried to reinstall it. It didn't work, so I've been trying it again and again for the last few days. Here's the error I get:
```
linking ./amarok/src/libamarok.la
/bin/sh ./libtool --silent --mode=link --tag=CXX g++ -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -g3 -fno-inline -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -DQT_THREAD_SUPPORT -D_REENTRANT -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib -R /usr/lib -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -o ./amarok/src/libamarok.la -rpath /usr/lib ./amarok/src/amarokcore/libamarokcore.la ./amarok/src/analyzers/libanalyzers.la ./amarok/src/engine/libengine.la ./amarok/src/plugin/libplugin.la ./amarok/src/statusbar/libstatusbar.la ./amarok/src/metadata/libmetadata.la -lkutils -lkio -lkdeui -lkdecore -lkhtml -lknewstuff -L/usr/local/lib -ltag -lGL ./amarok/src/sqlite/libsqlite.la -ltunepimp ./amarok/src/Options1.lo ./amarok/src/Options2.lo ./amarok/src/Options4.lo ./amarok/src/Options5.lo ./amarok/src/Options7.lo ./amarok/src/Options8.lo ./amarok/src/actionclasses.lo ./amarok/src/app.lo ./amarok/src/atomicstring.lo ./amarok/src/atomicurl.lo ./amarok/src/browserbar.lo ./amarok/src/clicklineedit.lo ./amarok/src/collectionbrowser.lo ./amarok/src/collectiondb.lo ./amarok/src/columnlist.lo ./amarok/src/configdialog.lo ./amarok/src/contextbrowser.lo ./amarok/src/coverfetcher.lo ./amarok/src/covermanager.lo ./amarok/src/pixmapviewer.lo ./amarok/src/cuefile.lo ./amarok/src/dbsetup.lo ./amarok/src/devicemanager.lo ./amarok/src/directorylist.lo ./amarok/src/effectwidget.lo ./amarok/src/enginecontroller.lo ./amarok/src/engineobserver.lo ./amarok/src/equalizergraph.lo ./amarok/src/equalizerpresetmanager.lo ./amarok/src/equalizersetup.lo ./amarok/src/fht.lo ./amarok/src/filebrowser.lo ./amarok/src/firstrunwizard.lo ./amarok/src/htmlview.lo ./amarok/src/k3bexporter.lo ./amarok/src/kbookmarkhandler.lo ./amarok/src/ktrm.lo ./amarok/src/mediabrowser.lo ./amarok/src/medium.lo ./amarok/src/mediumpluginchooser.lo ./amarok/src/mediumpluginmanager.lo ./amarok/src/metabundle.lo ./amarok/src/moodbar.lo ./amarok/src/mydiroperator.lo ./amarok/src/multitabbar.lo ./amarok/src/newdynamic.lo ./amarok/src/osd.lo ./amarok/src/party.lo ./amarok/src/partydialogbase.lo ./amarok/src/playerwindow.lo ./amarok/src/playlist.lo ./amarok/src/playlistbrowser.lo ./amarok/src/playlistbrowseritem.lo ./amarok/src/playlistitem.lo ./amarok/src/playlistloader.lo ./amarok/src/playlistselection.lo ./amarok/src/playlistwindow.lo ./amarok/src/pluginmanager.lo ./amarok/src/podcastsettings.lo ./amarok/src/podcastsettingsbase.lo ./amarok/src/prettypopupmenu.lo ./amarok/src/queuemanager.lo ./amarok/src/refreshimages.lo ./amarok/src/scancontroller.lo ./amarok/src/scriptmanager.lo ./amarok/src/scriptmanagerbase.lo ./amarok/src/scrobbler.lo ./amarok/src/sliderwidget.lo ./amarok/src/smartplaylisteditor.lo ./amarok/src/socketserver.lo ./amarok/src/statistics.lo ./amarok/src/streamprovider.lo ./amarok/src/systray.lo ./amarok/src/tagdialog.lo ./amarok/src/tagdialogbase.lo ./amarok/src/tagguesser.lo ./amarok/src/tagguesserconfigdialog.lo ./amarok/src/threadweaver.lo ./amarok/src/tooltip.lo ./amarok/src/tracktooltip.lo ./amarok/src/trackpickerdialog.lo ./amarok/src/trackpickerdialogbase.lo
grep: /lib/libattr.la: No such file or directory
/bin/sed: can't read /lib/libattr.la: No such file or directory
libtool: link: `/lib/libattr.la' is not a valid libtool archive
Error creating ./amarok/src/libamarok.la. Exit status 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded.
```
Does anyone know how to get through this problem? Or what the problem even is?

EDIT: Er.... never mind. Reinstalling libattr and libtool did the trick. :) Yay.

---

### Post by mlomker on 2006-02-07
[QUOTE=souled]I'm trying to compile amaroK, but I get an error saying that Ruby 1.8 or greater isn't installed on my computer. I installed Ruby 1.8 and the dev files, but I still get that error. How can I fix this?[/QUOTE]

I got that error for the first time this morning.  It looks like you need to install the package called **ruby** (which also installs the ruby1.8 package) for it to work.

---

### Post by souled on 2006-02-07
[QUOTE=mlomker]I got that error for the first time this morning.  It looks like you need to install the package called **ruby** (which also installs the ruby1.8 package) for it to work.[/QUOTE]

Yeah I figured that out. Thanks for the reply.

---

### Post by sailor420 on 2006-02-08
This worked and installed fine, and updated fine several times, but the upgrades seem to have stopped working as of about a month ago. I got the newest version of the script and the same thing is happening. Here's the last few lines and the error:

```

./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o): In function `~Tag':
/home/ravenel/INSTALLS/amarok-svn/amarok/src/metadata/m4a/mp4itunestag.cpp:34: multiple definition of `TagLib::MP4::Tag::~Tag()'
./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o):/home/ravenel/INSTALLS/amarok-svn/amarok/src/metadata/mp4/mp4tag.cpp:43: first defined here/usr/bin/ld: Warning: size of symbol `TagLib::MP4::Tag::~Tag()' changed from 184 in ./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o) to 119 in ./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o)
collect2: ld returned 1 exit status
Error creating ./amarok/src/libamarok.la. Exit status 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded.

```

Any ideas?

---

### Post by cwhitmore75 on 2006-02-09
Tried installing following the instructions in the first post and received the following error when compiling...

```
ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded.
kbuildsycoca running...
OggS-SEEK: at 704 want 47096 got 23104 (diff-requested 46392)
OggS-SEEK: at 47040 want 1032 got 0 (diff-requested -46008)

```

Any ideas?

Thanks in advance!

---

### Post by desperado666 on 2006-02-09
For those who have problems building amarok 1.3.8 i advise german automatix [http://forum.ubuntuusers.de/topic/16639/](http://forum.ubuntuusers.de/topic/16639/) 
its able to install the latest amarok build 1.3.8
more features are installation of 
openoffice 2.01
firefox 1.5.0.1
thunderbird 1.5
and alacarte (instead of smeg)

---

### Post by wondering_jew on 2006-02-09
Nice... Amarok works great with my iPod now; it wouldn't from the repositories. Only thing is the transcoding doesn't seem to work right. Still better than banshee and much much better than gtkpod.

---

### Post by Josef K. on 2006-02-09
[QUOTE=mlomker]That means that you don't have autoconf installed.  Check in Synaptic.  The current version is 2.59-a3.[/QUOTE]

actually I've it installed and got the same error :-k

---

### Post by angkor on 2006-02-09
Had to drop in and thank you for the Howto. Amarok is my favourite music player but the Breezy version was quite buggy on my system. The new version fixes that. After recompiling it to include ipod support I'm a _very_ happy man. Just tested file transfer to the ipod and it works great. :D :D 

thanks again

---

### Post by shadow07 on 2006-02-21
[EDIT] I fixed my issue as I did not read post #104.[/EDIT]

But, I do have a problem.  I have taglib-1.4 installed, and Amarok will not compile now.  I keep getting the following output at the final phase of the build process:

```
/usr/bin/ld: Warning: size of symbol `TagLib::MP4::Tag::~Tag()' changed from 119 in ./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o) to 184 in ./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o)
./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o): In function `TagLib::MP4::Tag::isEmpty() const':
/home/chris/amarok-svn/amarok/src/metadata/mp4/mp4tag.cpp:46: multiple definition of `TagLib::MP4::Tag::isEmpty() const'
./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o):/home/chris/amarok-svn/amarok/src/metadata/m4a/mp4itunestag.cpp:160: first defined here
/usr/bin/ld: Warning: size of symbol `TagLib::MP4::Tag::isEmpty() const' changed from 19 in ./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o) to 276 in ./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o)
./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o): In function `TagLib::MP4::Tag::Tag()':
mp4tag.cpp:(.text+0x0): multiple definition of `TagLib::MP4::Tag::Tag()'
./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o):mp4itunestag.cpp:(.text+0x0): first defined here
/usr/bin/ld: Warning: size of symbol `TagLib::MP4::Tag::Tag()' changed from 148 in ./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o) to 341 in ./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o)
./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o): In function `Tag':
/home/chris/amarok-svn/amarok/src/metadata/mp4/mp4tag.cpp:31: multiple definition of `TagLib::MP4::Tag::Tag()'
./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o):/home/chris/amarok-svn/amarok/src/metadata/m4a/mp4itunestag.cpp:24: first defined here
/usr/bin/ld: Warning: size of symbol `TagLib::MP4::Tag::Tag()' changed from 148 in ./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o) to 341 in ./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o)
./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o): In function `~Tag':
/home/chris/amarok-svn/amarok/src/metadata/mp4/mp4tag.cpp:43: multiple definition of `TagLib::MP4::Tag::~Tag()'
./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o):/home/chris/amarok-svn/amarok/src/metadata/m4a/mp4itunestag.cpp:34: first defined here
/usr/bin/ld: Warning: size of symbol `TagLib::MP4::Tag::~Tag()' changed from 119 in ./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o) to 184 in ./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o)
collect2: ld returned 1 exit status
Error creating ./amarok/src/libamarok.la. Exit status 1.

```

I have removed taglib-1.4 and re-installed it to no sucess.  Any ideas/suggestions?

---

### Post by mlomker on 2006-02-22
[QUOTE=shadow07]I have removed taglib-1.4 and re-installed it to no sucess.  Any ideas/suggestions?[/QUOTE]

Has it ever compiled for you?  If so, then I'd try deleting the amarok-svn folder and downloading everything again.  I have had to do that a couple of times over the last few months.  I assume it has to do with some changes they are making on their end.

Their IRC channel is your best bet for support.

---

### Post by Jeff Eklund on 2006-02-22
Hi and thanks for the howto. After being dissapointed that the Kubuntu team only released packages for dapper of the new beta, I decided to compile the SVN-version. However, it looks like I'm missing a file?
```
In file included from ./amarok/src/engine/akode/akode-engine.h:12,
                 from /home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:11:
./amarok/src/engine/akode/akode-scope.h:24:26: error: akode/player.h: No such file or directory
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:12:27: error: akode/decoder.h: No such file or directory
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:190:2: warning: no newline at end of file
./amarok/src/engine/akode/akode-scope.h:31: error: 'aKode::Player' has not been declared
./amarok/src/engine/akode/akode-scope.h:32: error: expected class-name before '{' token
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:23: error: expected class-name before '{' token
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:27: error: 'struct aKode::Player::State' has not been declared
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In destructor 'virtual AkodeEngine::~AkodeEngine()':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:57: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual bool AkodeEngine::init()':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:65: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:66: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:67: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:69: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual bool AkodeEngine::load(const KURL&, bool)':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:77: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual bool AkodeEngine::play(uint)':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:85: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual uint AkodeEngine::position() const':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:101: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:104: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual void AkodeEngine::stop()':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:112: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:113: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual void AkodeEngine::pause()':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:119: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:120: error: incomplete type 'aKode::Player' used in nested name specifier
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:120: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:121: error: incomplete type 'aKode::Player' used in nested name specifier
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:121: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual void AkodeEngine::setVolumeSW(uint)':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:129: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual void AkodeEngine::seek(uint)':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:135: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual Engine::State AkodeEngine::state() const':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:141: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:143: error: incomplete type 'aKode::Player' used in nested name specifier
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:144: error: incomplete type 'aKode::Player' used in nested name specifier
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:146: error: incomplete type 'aKode::Player' used in nested name specifier
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:147: error: incomplete type 'aKode::Player' used in nested name specifier
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:148: error: incomplete type 'aKode::Player' used in nested name specifier
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual bool AkodeEngine::event(QEvent*)':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:170: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:175: error: invalid use of undefined type 'struct aKode::Player'
./amarok/src/engine/akode/akode-engine.h:14: error: forward declaration of 'struct aKode::Player'
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp: In member function 'virtual Engine::State AkodeEngine::state() const':
/home/jeff/amarok-svn/amarok/src/engine/akode/akode-engine.cpp:150: warning: control reaches end of non-void function
Error creating ./amarok/src/engine/akode/akode-engine.lo. Exit status 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded.

```
This line alerts me:
```
./amarok/src/engine/akode/akode-scope.h:24:26: error: akode/player.h: No such file or directory
```
Has anyon else gotten this error? Should I try it again in a few days when the SVN source (probably) has been updated?
Thanks for the howto!


EDIT: Never mind. all I needed was some akode-dev-files from apt. I figured it was the akode.h-file from the SVN_source that was missing. not some other file on my computer...

---

### Post by shadow07 on 2006-02-22
@mlomker:

Yes, I have successfully built it via SVN and the script.  But, when I compiled it the first time (and the only successful time since then), it didn't not have iPod support.  I will remove the amarok-svn folder and try again.  I have been using the "amarok-svn.sh -r" command.  But, I will complete remove the folder and try again.

---

### Post by shadow07 on 2006-02-22
[Edit]Never mind.  I got it working.  For some reason I didn't install taglib.  It compiles completely now.  It's just time to see if iPod support is working.[/Edit]

OH HELLA YEAH!!!!  It's working now!!!  I just wish I would read clearly and s l o w enough.  Thanks for the script.

---

### Post by Randomskk on 2006-02-22
I want to get 1.4 working, primerily for the iRiver support, although right now just getting it working would be good :P
It compiles happily, although tells me that the following will not be included:
```
==========================
 ===  amaroK - PLUGINS  ========================================================
 ==========================
 =
 = The following extra functionality will NOT be included:
 =   - aRts-engine
 =   - aKode-engine
 =   - NMM-engine
 =   - MAS-engine
 =   - Helix-engine
 =   - libvisual Support
 =   - XMMS Visualization Wrapper
 =   - MySql Support
 =   - Postgresql Support
 =   - MP4/AAC Tag Write Support
 =   - Moodbar Support
 =   - iPod Support
 =   - iRiver iFP Support
 =
 = The following extra functionality will be included:
 =   + GStreamer-engine
 =   + xine-engine
 =   + Konqueror Sidebar
 =   + MusicBrainz Support
 =
 ===============================================================================

```

Anyway, it installs and I go to run it, it just crashes... not put off, I run it from terminal and the last message / the error seems to be:
```
amarok: END__: App::App() - Took 1s
amarokapp: symbol lookup error: /usr/lib/libamarok.so.0: undefined symbol: _ZN6TagLib7FileRef19addFileTypeResolverEPKNS0_16FileTypeResolverE

```

In /usr/lib:
```
adam@random:~$ vdir /usr/lib/libamarok*
-rwxr-xr-x  1 root root     1717 2006-02-22 18:22 /usr/lib/libamarok.la
lrwxrwxrwx  1 root root       18 2006-02-22 18:23 /usr/lib/libamarok.so -> libamarok.so.0.0.0
lrwxrwxrwx  1 root root       18 2006-02-22 18:23 /usr/lib/libamarok.so.0 -> libamarok.so.0.0.0
-rwxr-xr-x  1 root root 41635436 2006-02-22 18:22 /usr/lib/libamarok.so.0.0.0
```

Not sure how to fix this. The other thing would be how to get iRiver support working once it is fixed, but I'd like to get 1.4 working regardless...


Thanks for any help :)

---

### Post by Jeff Eklund on 2006-02-22
Hi! I've encountered another problem. I've recompiled anmarok (./amarok-svn.sh -r) a couple of times nw, but when I try to add extra parameters, it's always ignoring me and going for the defaults anyway. I get to step eight when I enter a couple of extra attributes, such as ifp and ipod-support but the script always goes for this:
```
 ==========================
 ===  amaroK - PLUGINS  ========================================================
 ==========================
 =
 = The following extra functionality will NOT be included:
 =   - aRts-engine
 =   - NMM-engine
 =   - MAS-engine
 =   - Helix-engine
 =   - libvisual Support
 =   - XMMS Visualization Wrapper
 =   - Postgresql Support
 =   - MP4/AAC Tag Write Support
 =   - Moodbar Support
 =   - iPod Support
 =   - iRiver iFP Support
 =
 = The following extra functionality will be included:
 =   + aKode-engine
 =   + GStreamer-engine
 =   + xine-engine
 =   + MySql Support
 =   + Konqueror Sidebar
 =   + MusicBrainz Support
 =
 ===============================================================================

```
Could I be doing something wrong? Any ideas?

---

### Post by Randomskk on 2006-02-22
To get the iRiver thing working, it seems you need to apt-get:
libifp-dev
libifp4
ifb-line
ifb-line-libifp
libusb-dev

Some of the ifb packages may not be needed, but with all of those it adds iRiver iFP support to my included part.

My amaroK still doesn't work though! >:|

---

### Post by Randomskk on 2006-02-22
I found [this](http://amarok.kde.org/amarokwiki/index.php/FAQ#amaroK_cannot_be_started_complaining_about_undefined_symbols) on the amaroK wiki, which seems to define my problem.. no idea how to go about fixing it, however!

```
adam@random:~$ ldd `which amarokapp` | grep qt
        libqt-mt.so.3 => /usr/lib/libqt-mt.so.3 (0x00002aaaad754000)

```

---

### Post by Jeff Eklund on 2006-02-22
[QUOTE=Randomskk]To get the iRiver thing working, it seems you need to apt-get:
libifp-dev
libifp4
ifb-line
ifb-line-libifp
libusb-dev

Some of the ifb packages may not be needed, but with all of those it adds iRiver iFP support to my included part.

My amaroK still doesn't work though! >:|[/QUOTE]
Thanks! For the record, those are
ifp-line and ifp-line-libifp. Those two seem to be in conflict though. I installed the first one and re-ran the SVN-script. it added IFP-support to the list. But nothing else. Am I guessing this will be a case of guess-and-install-dev-packages to get all of this running?
Have anyone gotten this new "moodbar" to work? Sounds cool, so I'd like to try it.

---

### Post by Randomskk on 2006-02-22
Oops yeah, mixed up the p and b >.<
And it seems likely, unfortunately. Add random dev packages until it works :P

..I'm still trying to find the one to fix my problem :(
I wonder if it's to do with 64bit libs... hm.

---

### Post by GreeDy on 2006-02-22
Hello.

I'm having problem with AmaroK-SVN's collection. I have lots of japanese music in .mp3 and .flac format and every file which have hiragana/katakana/kanji on it's tag or filename or even in folder name doesn't show in collection. But if I browse and add them from "Files" tab to playlist the characters shows just fine and file plays just fine. TagLib is version 1.4, so I don't think that is causing it..

Can anyone tell me how to fix this problem? 
Thanks in advance.

---

### Post by Jeff Eklund on 2006-02-22
By using the old and allmigthy "install-dev-packages-until-it-works"-method, I've gotten Iriver and xmms-visualization-wrapper support. The wrapper for XMMS needed som dev files from XMMS, of course.

---

### Post by Randomskk on 2006-02-22
Well, as the SVN didn't seem to work I downloaded the source tarball and compiled that... exactly the same error.
I tried the "klik" version of it, and it exits on load although I can't be sure of the error... it looks like the same thing though.

Anyone got any ideas? It's probably a messed up libqt thing, do you think? I really want to get it working :(

---

### Post by mlomker on 2006-02-23
[QUOTE=Randomskk]
```
adam@random:~$ ldd `which amarokapp` | grep qt
        libqt-mt.so.3 => /usr/lib/libqt-mt.so.3 (0x00002aaaad754000)

```[/QUOTE]

Mine points to what seems to be the same file, from the libqt3-mt package.  The version number on mine in Synaptic is 3:3.3.4-8ubuntu5

---

### Post by mlomker on 2006-02-23
[QUOTE=GreeDy]Can anyone tell me how to fix this problem? 
Thanks in advance.[/QUOTE]

It's a beta and probably a bug.  Try their IRC channel.

---

### Post by Randomskk on 2006-02-23
Alright! I got it! turns out I still had taglib 1.3.1 from apt, so removing that then rebuilding 1.4, recompile amarok-svn and it works!!!
Thanks so much, it looks really good! :D

---

### Post by Jeff Eklund on 2006-02-23
Did you get all the functionality to work? Like the moodbar and mp4-support? What libraries do you have installed?

---

### Post by Randomskk on 2006-02-23
I didn't get it all, because I didn't find I needed it...
mp4 tag editing I don't think, moodbar nope... I might try and get more items for it tomorrow, but this link might help you (helped me):
[http://docs.kde.org/development/en/extragear-multimedia/amarok/requirements.html](http://docs.kde.org/development/en/extragear-multimedia/amarok/requirements.html)

It shows what libs are needed for what.

---

### Post by Jeff Eklund on 2006-02-24
Okey, how do I uninstall the program when I installed it with SVN? a regular make uninstall?
I thought I'd try this method to see if I got some more functionality out of it [http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10](http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10)
;-) Bless Kubuntu Germany.

---

### Post by shadow07 on 2006-02-24
@Randomskk:

I ran into the very same issue.  It was because I didn't have taglib1.4 installed.  Once I installed the package, re-compiled amarok, it worked flawlessly.  I would STRONGLY recommend that you delete the "amarok-svn" folder created in your home directory before you attempt to re-compile from SVN with the script.

---

### Post by melat0nin on 2006-02-24
I get this error when running the script:

# 1/11 - Checking out base files.
ICE default IO error handler doing an exit(), pid = 10053, errno = 0


Then the program appears just to hang. I'm on a network behind a proxy.  Perhaps that has something to do with it?  Any ideas?

---

### Post by melat0nin on 2006-02-24
I just rebooted and now my GNOME is buggered, it comes up with an error saying my session has lasted less than 10 seconds (!) then returns me to the session login screen.  It also gives me an error, here it is:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "laurence"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntulaurie:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntulaurie:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntulaurie:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:7898): WARNING **: Unable to read ICE authority file: /home/laurence/.ICEauthority


I can't get into ubuntu properly at the moment (I'm running the failsafe terminal, with which i manually opened Firefox to send this).

Please help!!  My Linux is kaput at the moment!!

---

### Post by melat0nin on 2006-02-24
..and I get this error when running synaptic from the failsafe terminal:

(synaptic:9775): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
bash: syntax error near unexpected token `:'


ANy idea what this means?  What's happening to my box? :(

---

### Post by mlomker on 2006-02-27
[QUOTE=melat0nin]ANy idea what this means?  What's happening to my box? :([/QUOTE]

That use to happen way back when but I haven't seen this for a while.  I'd have to assume that your install wasn't up-to-date with patches.  In any case, you have to change the permissions on that file.

```

sudo chmod 777 /home/laurence/.ICEauthority

```

---

### Post by mlomker on 2006-02-27
[QUOTE=Jeff Eklund]Okey, how do I uninstall the program when I installed it with SVN? a regular make uninstall?[/QUOTE]

Why would you or isn't the SVN working?  The SVN is 1.4 and a newer version than anything that is packaged.

To answer your question, there isn't a way to remove it that I'm aware of.  If you install the DEBS it'll just overwrite the SVN version.

---

### Post by Randomskk on 2006-02-27
Go to ~/amarok-svn and type "sudo unsermake uninstall" and it will uninstall...

---

### Post by vassalle on 2006-03-06
hi.. first of all.. thanks for the script mlomker!
Managed to install it fine but i have two problems..
1) alarm-clock aint working.
2) cant fetch cover from amazon..

weird ehh? ive tried googling for it, even searched the amarok website.. cant seem to find anything like this one before..

anyway, im using dapper (uptodate) and a custom version of firefox, called swiftfox if that matters. im connected to the internet via lan (DHCP). I also can fetch lyrics after enabling the script for it. BUt those two problems mentioned above, ive been splitting hair to find the solution. Help Please? :D

---

### Post by mlomker on 2006-03-07
[QUOTE=vassalle]BUt those two problems mentioned above, ive been splitting hair to find the solution. Help Please? :D[/QUOTE]

You're running a beta of amaroK on a beta of Ubuntu and wondering why everything doesn't work right?  :-k 

Your best bet is their IRC channel, but I expect things to be broken here and there when I run betas.

---

### Post by jetpeach on 2006-03-09
I can't seem to download the script, can someobody post a link that works or update the one in the first post?
Thanks!
jet

Edit: This might be an easier solution for many people, with [a description of how to get 1.4 in the repositories]("http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10").  Had to tweak around with my libgpod for some reason, and darn, it's beta1 not beta2.  But at least it's working!

---

### Post by mlomker on 2006-03-15
[QUOTE=jetpeach]I can't seem to download the script, can someobody post a link that works or update the one in the first post?
[/QUOTE]

That's their official link, but you are right that it is down.  I'll host a copy of the script on my server.

As far as the DEBs go...the SVN isn't much more trouble and it's always current.

---

### Post by cabber on 2006-03-15
I got this error after installing from the instructions in this thread:

```
# DONE - amaroK was successfully installed/updated! Start it from your menu or by typing "amarok".
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
matt@ubuntu:~$ ICE default IO error handler doing an exit(), pid = 3229, errno = 0

```

Any thoughts

---

### Post by cabber on 2006-03-15
Quick question:

When I import my iTunes files (mp4) into the amaroK application it states that these files are "not playable".  I installed this:

```
sudo apt-get install libmp4v2-dev libfaad2-dev #aac/mp4 tag editor support
```

during my install.

Is there a codec I can use to play mp4/AAC  files in amaroK?  I followed the instructions on the 1st page of this thread and having problems.  Thanks.

---

### Post by JeanJaques on 2006-03-16
Thanks for the tutorial!
I've compiled it, and it starts up fine, but when I try to add some music to my playlist  amarok just freezes, till I close it with the taskmanager. Building the database doesn't quite work either.. Anyone knows what I'm doing wrong? or is this just a bug in amarok?

Edit: I'm working with dapper

---

### Post by mlomker on 2006-03-17
I'd recommend that you guys get in touch with them on their IRC channel...they provide great support there.  I personally only use a handful of amaroK's features.

---

### Post by Rizado on 2006-03-18
```
sudo apt-get install libgstreamer-plugins0.8-dev #gstreamer support
```I doubt this will work as amarok requires gstreamer 0.10. Aleast it doesn't for me.

---

### Post by X3n0n on 2006-03-23
Great how-to! Thank you very much! I was looking for the latest amaroK for a long time! Like a piece of cake!

---

### Post by mrgnash on 2006-03-28
Sadly since the last build I checked out, Amarok stopped working for me and I had to downgrade :(

This is the error I get during the svn build process: 

```
./amarok/src/.libs/libamarok.so: undefined reference to `TagLib::FileRef::addFileTypeResolver(TagLib::FileRef::FileTypeResolver const*)'
collect2: ld returned 1 exit status
Error creating ./amarok/src/amarokapp. Exit status 1.

```

---

### Post by sinaen on 2006-04-02
Hi it seems i dont have the right repositories, ive got my buddy to give me his apt-get list but it doesnt have much more stuff than i do

anyway here's my error message> sinaen@Neko:~$ sudo apt-get install kdelibs4-dev subversion unsermake automake1.9 kdebase-dev build-essential ruby
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
ruby is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-dev: Depends: kate (= 4:3.4.3-0ubuntu4) but 4:3.4.3-0ubuntu6 is to be installed
               Depends: kdesktop (= 4:3.4.3-0ubuntu4) but 4:3.4.3-0ubuntu6 is to be installed
               Depends: kicker (= 4:3.4.3-0ubuntu4) but 4:3.4.3-0ubuntu6 is to be installed
               Depends: konqueror-nsplugins (= 4:3.4.3-0ubuntu4) but 4:3.4.3-0ubuntu6 is to be installed
               Depends: konqueror (= 4:3.4.3-0ubuntu4) but 4:3.4.3-0ubuntu6 is to be installed
               Depends: ksysguard (= 4:3.4.3-0ubuntu4) but 4:3.4.3-0ubuntu6 is to be installed
               Depends: kwin (= 4:3.4.3-0ubuntu4) but 4:3.4.3-0ubuntu6 is to be installed
  kdelibs4-dev: Depends: kdelibs4c2 (= 4:3.4.3-0ubuntu1) but 4:3.4.3-0ubuntu2 is to be installed
                Depends: kdelibs-bin (= 4:3.4.3-0ubuntu1) but 4:3.4.3-0ubuntu2 is to be installed
                Depends: libarts1-dev (>= 1.4.0) but it is not going to be installed
                Depends: libcupsys2-dev but it is not going to be installed
                Depends: libopenexr-dev (>= 1.2.1) but it is not going to be installed
                Depends: libqt3-mt-dev (>= 3.3.3) but it is not going to be installed
                Depends: libssl-dev but it is not going to be installed
E: Broken packages
sinaen@Neko:~$     

and my apt-get list > 
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy main restricted universe

#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted

#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse

#skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free



---

### Post by lazyd2 on 2006-04-02
When I try to use the "xine" engine nothing plays....it only works with gstreammer engine. Any ideas?

Thanks for the "How-to"

---

### Post by mlomker on 2006-04-03
[QUOTE=lazyd2]When I try to use the "xine" engine nothing plays....it only works with gstreammer engine. Any ideas?
[/QUOTE]

Xine is actually the only engine that I use, so I doubt it is a general problem.  When you get the list of modules that it is going to build, does it include the Xine engine?  I've actually never been able to get podcasts to work right using gstreamer (sounds like the Chipmunks), so kind of the opposite problem for me.  Sound, in general, is a bit buggy under linux.

---

### Post by john naked on 2006-04-06
The svn script/install goes swimmingly.  I've got Amarok sitting in my menu bar.  However, when I try and run it, I get this far:
```
amarok:         BEGIN: virtual bool XineEngine::init()
amarok:           [xine-engine] 'Bringing joy to small mexican gerbils, a few we eks at a time.'
amarok:           [xine-engine] w00t/home/raynorse/.kde/share/apps/amarok/xine-c onfig
*** glibc detected *** free(): invalid pointer: 0xf6c57008 ***
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
amaroK: [Loader] amarokapp probably crashed!
```

I realize SVn can be unstable, but this looks much like the error I was getting using the Amarok that came with Breezy.  Should I just wait a day or too and get the latest SVN, or is there another option?

(btw. first post.  I trashed my OS X volume partioning it for my Ubuntu install about 13 hours ago and have since recovered most of the data and switched over to Linux entirely.)

---

### Post by sinaen on 2006-04-09
help. i still havent found any solution here. and i really want amarok to use with my ipod

---

### Post by Randomskk on 2006-04-09
For all of you who are having it crash, try starting "amarokapp" instead of "amarok" - I can't see a difference but beta3 is working for me right now.

---

### Post by gibson on 2006-04-10
wow. thanks. sorted out 2 of my problems...

1. Amarok in repos was very slow
2. my sound was really bad (i am very picky about tone)  howver, i use xine instead of gstreamer now and it is perfect.

thanks again :)

---

### Post by mlomker on 2006-04-10
[QUOTE=sinaen]help. i still havent found any solution here. and i really want amarok to use with my ipod[/QUOTE]

Try the IRC channel...that's where they provide support.

---

### Post by Tristam on 2006-04-10
having the same problem as someone else did..

```
# DONE - amaroK was successfully installed/updated! Start it from your menu or by typing 'amarok'.
tristam@pallokala:~$ amarok
bash: amarok: command not found

```

Everything goes fine, it asks for sudo and bla bla bla.. but doesnt really install anything.. I get no errors :(

---

### Post by sinaen on 2006-04-10
[QUOTE=mlomker]Try the IRC channel...that's where they provide support.[/QUOTE]


uhm i cannot even get past the first install. check a couple of pages back it seems i don't have the repositories that i need to install all the packages that ar needed to compile the latest amarok source :(

---

### Post by sinaen on 2006-04-10
now i know why. its because the ppl forgot to tell me to upgrade to breezy..... :/

---

### Post by sinaen on 2006-04-11
now the whole script works but i cannot find amarok anywhere on my system when its finished..

---

### Post by stoeptegel on 2006-04-12
[QUOTE=sinaen]now the whole script works but i cannot find amarok anywhere on my system when its finished..[/QUOTE]

What does 
$ which amarok [enter]
say?

Sometimes after an installation you have to restart X to get the app integrated in de menu's, if that's what you meant.

---

### Post by mlomker on 2006-04-12
[QUOTE=sinaen]now the whole script works but i cannot find amarok anywhere on my system when its finished..[/QUOTE]

There might be something wrong with your system paths.  If **which** doesn't find it then try:

```

sudo updatedb
locate amarok

```

---

### Post by Tristam on 2006-04-13
[QUOTE=mlomker]There might be something wrong with your system paths.  If **which** doesn't find it then try:

```

sudo updatedb
locate amarok

```[/QUOTE]

Nah.. I dont think that's it. I have the same problem (everything goes well and the script installs amarok fine) but after the install amarok is nowhere to be found in the system.. And I tried updating and searching for it, found nothing than the amarok-svn directory and some cached cdcover images..

There has to be something wrong with the script :) Atleast 3 people have the same problem.. I tried this HOWTO few months ago with gnome though, and it worked fine. Guess I'll have to use 1.3 for now.. Having some bugs / recource hogging with that :(

---

### Post by eco751 on 2006-04-17
[QUOTE=mrgnash]Sadly since the last build I checked out, Amarok stopped working for me and I had to downgrade :(

This is the error I get during the svn build process: 

```
./amarok/src/.libs/libamarok.so: undefined reference to 
`TagLib::FileRef::addFileTypeResolver(TagLib::FileRef::FileTypeResolver const*)'
collect2: ld returned 1 exit status
Error creating ./amarok/src/amarokapp. Exit status 1.

```[/QUOTE]The problem might be multiple versions of TagLib.  ([see here]("http://article.gmane.org/gmane.comp.kde.amarok.devel/4044/match=taglib+fileref+addfiletyperesolver+filetyperesolver+const"))

I had a similar error upon using **make** after a flawless **./configure**.   To fix things I uninstalled TagLib - dev via apt, since the source there was TagLib 1.3, and then I re-installed (make install) TagLib 1.4 from source.

Then I was able to make and install without any issues.  Currently running the latest amaroK 1.4-SVN.


[QUOTE=Tristam]There has to be something wrong with the script :) Atleast 3 people have the same problem.. I tried this HOWTO few months ago with gnome though, and it worked fine. Guess I'll have to use 1.3 for now.. Having some bugs / recource hogging with that :([/QUOTE]The script isn't really 100% required if you're willing to dig a little deeper.  I just followed the [amaroK wiki's Anonymous SVN Install HOWTO]("http://amarok.kde.org/amarokwiki/index.php/Installation_HowTo#From_Anonymous_SVN") without too many issues.

All the dependencies are stated in the **multimedia/amarok/README** file.  [This]("http://www.waningsun.net/wiki/index.php?title=AmaroK_from_source_HOWTO") is how I did it, if you want to compare your problems with mine.

---

### Post by sinaen on 2006-04-21
[QUOTE=mlomker]There might be something wrong with your system paths.  If **which** doesn't find it then try:

```

sudo updatedb
locate amarok

```[/QUOTE]


well it does only find amarok in my home path. all the svn source :)
but nothing in my system at all

checking about libtag. i saw that 1.4 are into the apt-repositories

---

### Post by d351GuJu on 2006-04-21
Thanks you so much!  It installed properly after couple of tries :D

---

### Post by adamkane on 2006-04-23
Try this with amarok v1.3.8 or v1.3.9 before you decide you need amarok-svn to get a working amarok.

Install alsa-oss.
Install taglib-1.4.

-----

As suggested by others, you can add the czessi repository to obtain the latest amarok 1.4.0 beta.

---

### Post by kookookachooo on 2006-04-26
i finished and i rebooted, wheres the app? and also thanks for the how to

---

### Post by SqRt7744 on 2006-04-27
hello!.... this is linux.  We don't have to reboot all the time!  Isn't that one of the reasons we left windows?  That said, gnome users need only type
```

killall gnome-panel

```
into a terminal window to make amarok appear under Applications->sound&video.

Also, if I may make a suggestion to gnome users:  it is generally a good idea to have all your sound outputs use esd (enlightened sound daemon) as the engine.  It is the gnome way.  (aRts is the KDE way).  So under settings->configure amarok->engines, select esd.  It is good to be consistent, and esd should do all the sound mixing from different apps, as long as they use esd!

Finally, Dapper users shouldn't install the taglib debian package in the how-to, it prevents amarok from being able to build your collection!  There is a version in the repos, libtag1c2a and libtagc0.  Install them instead.

Thanks!

---

### Post by adamkane on 2006-04-27
This is a Breezy sub-forum. It should be assumed you are using Breezy.

---

### Post by kookookachooo on 2006-04-27
[QUOTE=SqRt7744]hello!.... this is linux.  We don't have to reboot all the time!  Isn't that one of the reasons we left windows?  That said, gnome users need only type
```

killall gnome-panel

```
into a terminal window to make amarok appear under Applications->sound&video.

Also, if I may make a suggestion to gnome users:  it is generally a good idea to have all your sound outputs use esd (enlightened sound daemon) as the engine.  It is the gnome way.  (aRts is the KDE way).  So under settings->configure amarok->engines, select esd.  It is good to be consistent, and esd should do all the sound mixing from different apps, as long as they use esd!

Finally, Dapper users shouldn't install the taglib debian package in the how-to, it prevents amarok from being able to build your collection!  There is a version in the repos, libtag1c2a and libtagc0.  Install them instead.

Thanks![/QUOTE]


Awsome thanks and also I was also wondering what command to use to restart the script, I think I f-ed up. Is it '-r'? '--restart'? If someone could give the whole command It'd be a great. Thanks in advance

---

### Post by El_Virdi on 2006-04-28
[QUOTE=SqRt7744]

Finally, Dapper users shouldn't install the taglib debian package in the how-to, it prevents amarok from being able to build your collection!  There is a version in the repos, libtag1c2a and libtagc0.  Install them instead.

Thanks![/QUOTE]

Thaks a lot for the tip, mate, i had that problem and it was really anoying ;)

---

### Post by WillFerrellLuva on 2006-04-29
Hi,

Im using dapper, and I followed the advice about taglib, but I get this error:

./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o):/home/chris/amarok-svn/amarok/src/metadata/mp4/mp4tag.cpp:43: first defined here
/usr/bin/ld: Warning: size of symbol `TagLib::MP4::Tag::~Tag()' changed from 167 in ./amarok/src/metadata/.libs/libmetadata.a(mp4tag.o) to 106 in ./amarok/src/metadata/.libs/libmetadata.a(mp4itunestag.o)
collect2: ld returned 1 exit status
Error creating ./amarok/src/libamarok.la. Exit status 1.

edit: I can compile it including "--with-gstreamer10" but if i try to include "--with-mp4v2" I get the above error.  So for now I can't edit aac tags

Any ideas?

---

### Post by WillFerrellLuva on 2006-05-03
(bump)

anybody else have this problem?

---

### Post by Magneto on 2006-05-05
very disappointing - amarok died with qpainter errors then after installation via this method it crashes my system when i try to use the first time use wizard :smh:

this is why I use winblows all the time now- cant find a good media player that will track my 400gb of music without crashing or having problems with various types of music

---

### Post by damaged on 2006-08-26
I got up to the final part of the howto and then this error appears when I run the script.

ERROR: amaroK-svn requires kdialog, which wasn't found in your $PATH!

I'm a complete noob so please be gentle.

---

### Post by Logic* on 2006-08-29
I'm having trouble installing kdelibs4-dev. I've attached the details in a text file. 



Anyone got any ideas? Thanks

---

### Post by koholint1000 on 2006-10-22
No offence mlomker, like, but the scripted install file seems to have COMPLETELY VANISHED OFF OF THE FACE OF THE EARTH!!!

It wont download; it says "page not found",

im trying the manual one now; ill see if thaty's any good. Straight from the repositories didnt work at all, so this is probably my last hope for me and my zen-micro-photo!

---

### Post by ShiftyPowers on 2006-11-02
Koholint1000

the script can also be found through here

[http://amarok.kde.org/wiki/Amarok-svn]("http://amarok.kde.org/wiki/Amarok-svn")

worked like a charm for me

---

### Post by CodyJarrett on 2006-11-15
> **Logic* said:**
> I'm having trouble installing kdelibs4-dev. I've attached the details in a text file. 



Anyone got any ideas? Thanks

It's in kdebase-bin

---

### Post by cubanresourceful on 2007-04-14
im having troube with compiling on Edgy. It says it cannot find Ruby installed, when in fact it is installed. Sorry for posting after long time, but its better than making new thread, no?

---

### Post by henriquemaia on 2007-06-13
> **cubanresourceful said:**
> im having troube with compiling on Edgy. It says it cannot find Ruby installed, when in fact it is installed. Sorry for posting after long time, but its better than making new thread, no?

You have to install the package ruby1.8-dev. I had the same issue and solved it by doing that. Hope it helps.

---

### Post by henriquemaia on 2007-09-11
This is still helpful for Gutsy. At least for those who love to have always the latest amarok.

---

### Post by dasbooter on 2007-09-25
Well I hosed my system by accident trying to compile amarok. It is my own fault but some know the scenario. Removing conflicting packages to install the dependencies for compiling amarok did the damage. 

Anyways I fixed the damage but wondered if any one out there might take pity on me and post a package that would conflict with my feisty install. I am really trying to get esd support that is the purpose for all this.

 Thanks all, and I dont think I could go through compiling again unless somebody can really tell me about how to do this in feisty.

---

### Post by Brian031168 on 2007-12-02
Hi 

I'm having a problem, after following all the instructions I get to typing ./amarok-svn.sh and I get this response:

```
brian@emery-laptop:~/amarok$ ./amarok-svn.sh
./amarok-svn.sh: line 1: !DOCTYPE: No such file or directory
./amarok-svn.sh: line 2: syntax error near unexpected token `<'
'/amarok-svn.sh: line 2: `<HTML><HEAD><TITLE>The page cannot be found</TITLE>

```

Any ideas?

---

### Post by rami85 on 2007-12-03
i cant even download the file, dead link :|

---

### Post by rami85 on 2007-12-03
> **Brian031168 said:**
> Hi 

I'm having a problem, after following all the instructions I get to typing ./amarok-svn.sh and I get this response:

```
brian@emery-laptop:~/amarok$ ./amarok-svn.sh
./amarok-svn.sh: line 1: !DOCTYPE: No such file or directory
./amarok-svn.sh: line 2: syntax error near unexpected token `<'
'/amarok-svn.sh: line 2: `<HTML><HEAD><TITLE>The page cannot be found</TITLE>

```

Any ideas?

use this link [http://amarok.kde.org/wiki/Amarok-svn](http://amarok.kde.org/wiki/Amarok-svn)

---

