---
title: "how can I install firefox 3 in 7.10 ?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by DO55 on 2008-06-17
hi

now firefox is released . can I install it by using update manager ?

how can I install it if i download it from the web site? because i have download it but its not like windows , in windows i just download EXE file and install it by some clicks 
[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/) 

how long 7.10 will be support ? im asking because my wireless card 3945G is not working with 8.04 [http://ubuntuforums.org/showthread.php?t=765615](http://ubuntuforums.org/showthread.php?t=765615)

---

### Post by RomeReactor on 2008-06-17
Hi. Ubuntu 7.10 has a support cycle of 18 months, so it will be supported until April, 2009. You can install Firefox 3 beta 4 from Synaptic by enabling the backports repository. If you want the use the one you'bve just downloaded, open a terminal (Applications->Accessories->Terminal) and change to the Firefox 3 directory; for example, if the folder is in your desktop:
```
cd Desktop/firefox
```
and:
```
./firefox
```

You don't really need to install it; you can run it from its folder.

---

### Post by oldos2er on 2008-06-17
Read the release notes to find out Firefox 3's dependencies; once these are satisfied, download the archive, extract it, and follow README or INSTALL to install it.

---

### Post by DO55 on 2008-06-17
RomeReactor

old firefox will run when  i do the code , its not the new 3.0

---

### Post by coolbrook on 2008-06-17
If you double click on 'Firefox' in the newly created folder then it will prompt you to run the new version.

---

### Post by RomeReactor on 2008-06-17
Make sure you have [these packages]("http://www.mozilla.com/en-US/firefox/system-requirements.html") installed on your system--look for them in Synaptic.

According to the [instructions]("http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux#Installing_outside_of_a_package_manager"), you should move the 'firefox' folder you extracted from the tar.bz2 package to your home directory, if it's not already there, and run it like this:
```
~/firefox/firefox
```
Otherwise, it will either give you an error or launch the already installed version.

EDIT: The problem is that you still have your **.mozilla** configuration folder in your home directory. In Nautilus, press CTRL+H to see the hidden files and folders, look for **.mozilla** and move it somewhere else, or delete it (this will erase your configuration, including bookmarks). You can then run firefox:
```
~/firefox/firefox
```
Or by first changing to its directory; if the folder is in your desktop:
```
cd Desktop/firefox
```
and:
```
./firefox
```

---

### Post by cariboo on 2008-06-17
I saw over on Ubuntu Planet that the Firefox final release in in the repositories. It may take a while for it to trickle down from the main to the mirrors.

Jim

---

### Post by coolbrook on 2008-06-17
Nice!

---

### Post by JazonEsti on 2008-06-17
Somewhat related:

I installed Ubuntuzilla before. And I was able to get updates for FF2. Today, I got the notification that FF3 is available. So i tried updating but I get the message that no updates are available. 

I tried in the terminal
```
ubuntuzilla.py -a checkforupdatetext -p firefox
```
I get:
```
jason@jason-desktop:~$ ubuntuzilla.py -a checkforupdatetext -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
The version of Firefox currently installed is 2.0.0.14
The latest version available from Mozilla is 3.0
Please refer to the detailed instructions for updating Firefox on our site, http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox .

If you have not yet installed the official Mozilla build with the help of the Ubuntuzilla script, and are still running the repositories version, run this script with '-install' to install the latest Mozilla build of Firefox .

```
But I still cannot update. Using "check for updates."

Any ideas?

---

### Post by RomeReactor on 2008-06-17
Jazon: Try downloading the new version from Mozilla's site and run it as said in my previous post; basically, remove the **.mozilla** folder in your home directory, and then either double click the **firefox** file in the extracted folder and select 'run in terminal', or:
```
~/path/to/firefox/firefox
```
or:
```
cd /path/to/firefox
```
and:
```
./firefox
```

---

### Post by JazonEsti on 2008-06-17
No more need to uninstall via Add/Remove programs? Just delete the folder?

Sorry, I'm relatively new to Linux, was a Windows user.

---

### Post by RomeReactor on 2008-06-17
> **JazonEsti said:**
> No more need to uninstall via Add/Remove programs? Just delete the folder?

Sorry, I'm relatively new to Linux, was a Windows user.

Deleting the **.mozilla** folder will let you run the version you download from Mozilla's site, but will not uninstall the version you installed from the repositories. You can do that in Synaptic if you wish, but it's not really necessary.

---

### Post by JazonEsti on 2008-06-17
Got it. Thanks! Will report what happened when I'm done.

---

### Post by JPBodner on 2008-06-17
Hi all

Since firefox 3 is not in the synaptic installer yet for my 7.04 Ubuntu, I followed all the instructions for the manual download:

1. Installed firefox in my home directory via mozilla.com
2. Removed .Mozilla

And when I go into the new firefox dir and start firefox, I STILL get the old version.   Argh!

And here's a side question:  I'd like to find where the old version is installed.  I want to use the search feature of  Nautilus to help me since I don't know the Linux dir structure well.  So I type "firefox" into the search line and I get nothing.  Why?

Thanks!

---

### Post by RomeReactor on 2008-06-17
Hi JP. The **.mozilla** folder only contains configuration files; to uninstall Firefox go to Synaptic and mark it for 'Complete Removal'. Removing files in Nautilus instead of uninstalling the program will only cause problems.

---

### Post by sagara on 2008-06-17
Had a quick look at the package dependencies in synaptic... Too tired to try to figure it out (too many hits for gtk, glib, etc..)

I'll wait for a kind soul to spill out the details on how to install this (dependencies included) in gutsy.

---

### Post by RomeReactor on 2008-06-17
> **sagara said:**
> Had a quick look at the package dependencies in synaptic... Too tired to try to figure it out (too many hits for gtk, glib, etc..)

Have you tried downloading Firefox from Mozilla's site and running it? Otherwise, you can enable the backports repository and install Firefox 3 beta 4.

---

### Post by JPBodner on 2008-06-17
Thanks for the advice.  I'll try it.  Too bad that following the instructions listed on the firefox site doesn't work!   

I'm still confused as to why the old version is launched when I go into the new folder and click right on the new binary.  Any Linux theory to explain it?

EDIT:  Tried to remove firefox via the synaptic.  It says I have to remove like 10 other programs, including Ubuntu Desktop.  That sounded like a bad idea, so I canceled out.   

I'm sorry to say, that for ease of installation:

Windows: 1 ,  Linux 0    :(  

Jeff

---

### Post by RomeReactor on 2008-06-17
Ubuntu-desktop is a metapackage (an otherwise empty package) that calls on other packages for installation. Though it's useful to have during upgrades, it's safe to remove it; it **won't** actually remove your desktop.

What commands are you using to run Firefox? Where is the folder located?

---

### Post by JPBodner on 2008-06-17
I extracted firefox to a new folder in my home folder:

~/firefox

Then, I do the following from home

cd ~/firefox
firefox

This results in launching the old version.  Same thing happens when I use Nautilus and click "run in terminal" on the file in that folder.  

Jeff

---

### Post by RomeReactor on 2008-06-17
Launching it as just **firefox** will use the version installed in your system; the terminal will search for a 'firefox' executable in a few places--/usr/bin, /usr/local/bin, etc. To make it use the one you downloaded, issue the command like this:
```
cd ~/firefox
```
and
```
./firefox
```
using the **./** tells the teminal to use the one in this directory, instead of looking for the installed system's executables. You can also run it specifying the path to follow:
```
~/firefox/firefox
```
or:
```
/home/YOUR_USERNAME_HERE/firefox/firefox
```

---

### Post by JPBodner on 2008-06-17
It's still loading the older version, which makes no sense to me.  I give up for tonight.  Thanks for the help.

---

### Post by aysiu on 2008-06-17
> **JPBodner said:**
> It's still loading the older version, which makes no sense to me.  I give up for tonight.  Thanks for the help.
Try this link:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Azumangaman on 2008-06-17
I also just can't figure this out.
I tried the stuff a few posts above and it only loaded the old firefox.
When I double click on the Firefox folder its a bunch of random files...
Help?

---

### Post by aysiu on 2008-06-18
> **Azumangaman said:**
> I also just can't figure this out.
I tried the stuff a few posts above and it only loaded the old firefox.
When I double click on the Firefox folder its a bunch of random files...
Help?
Try the link *one* post above.

---

### Post by stig on 2008-06-18
Hello aysiu,
But what about the Ubuntuzilla method for getting Firefox 3? I'm using Ubuntuzilla on my Dapper box to give me Firefox 2.0.0.14 but I've not received any notice of an update to v.3 yet. I did gksudo firefox % to check for an update and it says none available. Will there be a v.3 update soon from Ubuntuzilla? (I can't see anything relevant about Firefox 3 on the Ubuntuzilla web site.)

---

### Post by waspbr on 2008-06-18
You can also use update manager, there already is an update for firefox in the repos

---

### Post by aysiu on 2008-06-18
> **stig said:**
> Hello aysiu,
But what about the Ubuntuzilla method for getting Firefox 3? I'm using Ubuntuzilla on my Dapper box to give me Firefox 2.0.0.14 but I've not received any notice of an update to v.3 yet. I did gksudo firefox % to check for an update and it says none available. Will there be a v.3 update soon from Ubuntuzilla? (I can't see anything relevant about Firefox 3 on the Ubuntuzilla web site.)
I can vouch for the manual install method (copying and pasting commands). I haven't used Ubuntuzilla in over a year, but if I remember correctly, it searches for the latest version available and downloads that off one of the Mozilla mirrors. Maybe the mirrors hadn't fully updated?

---

### Post by stig on 2008-06-18
An interesting coincidence - an Ubuntuzilla notice telling me there was v.3 available popped up at the bottom of my screen. I was working in Firefox at the time and therefore not able to follow it up. When I finished I did gksudo firefox % to open Firefox as root and check for an update but it said there was no update available. I suppose maybe v.3 is classed as something other than an update? I'll have to look back at the Ubuntuzilla web site because it might tell me I have to download the full package rather than update.

---

### Post by aysiu on 2008-06-18
> **stig said:**
> An interesting coincidence - an Ubuntuzilla notice telling me there was v.3 available popped up at the bottom of my screen. I was working in Firefox at the time and therefore not able to follow it up. When I finished I did gksudo firefox % to open Firefox as root and check for an update but it said there was no update available. I suppose maybe v.3 is classed as something other than an update? I'll have to look back at the Ubuntuzilla web site because it might tell me I have to download the full package rather than update.
Yes, Firefox 3 is an *upgrade*, not an *update*. So it'll have to be redownloaded using Ubuntuzilla or some other method.

---

### Post by philinux on 2008-06-18
I hope people back up their bookmarks before deleting folders.

---

### Post by aysiu on 2008-06-18
> **philinux said:**
> I hope people back up their bookmarks before deleting folders.
No one should be deleting the ~/.mozilla folder or anything in it. If anything, it should be copied (for backup purposes), not deleted.

---

### Post by philinux on 2008-06-18
> **aysiu said:**
> No one should be deleting the ~/.mozilla folder or anything in it. If anything, it should be copied (for backup purposes), not deleted.

Hope so.

---

### Post by Iwantu_ubuntu on 2008-06-18
I'm glad I'm not the only one having this problem. I have to say this is absolutely ridiculous!  It shouldn't be so confusing or difficult to upgrade from FF2 to FF3. As someone said, in Windows you can double click on the exe and it upgrades the older version, but why can't something as easy as that be done for Ubuntu/Linux?  I don't want to place it in my home directory, just keep my existing settings and upgrade to FF3 in one shot. ](*,)](*,)

---

### Post by aysiu on 2008-06-18
> **Iwantu_ubuntu said:**
> I'm glad I'm not the only one having this problem. I have to say this is absolutely ridiculous!  It shouldn't be so confusing or difficult to upgrade from FF2 to FF3. As someone said, in Windows you can double click on the exe and it upgrades the older version, but why can't something as easy as that be done for Ubuntu/Linux?  I don't want to place it in my home directory, just keep my existing settings and upgrade to FF3 in one shot. ](*,)](*,)
Then follow the instructions in this link:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

There are many options - you can take whatever is most convenient for you: [list][*]Copy and paste a few commands into the terminal (quickest and easiest way)[*]Use a script to do it for you (quick but a little confusing)[*]Make all the symlinks and copies via point-and-click (takes a really long time)[*]Upgrade to 8.04 (too involved)[/list]

---

### Post by DO55 on 2008-06-18
aysiu 

please can you add firefox 3.0 to the update manager for 7.10 ? so we can upgrade it easily

---

### Post by aysiu on 2008-06-18
> **DO55 said:**
> aysiu 

please can you add firefox 3.0 to the update manager for 7.10 ? so we can upgrade it easily
I have neither the power nor the skills to do that. I assure you that copying and pasting seven commands will take very little time and can be done entirely with your mouse.

---

### Post by DO55 on 2008-06-18
i cant run firefox after copy and past your commands

its give me this error 
Failed to execute child process "firefox" (No such file or directory)

---

### Post by aysiu on 2008-06-18
> **DO55 said:**
> i cant run firefox after copy and past your commands

its give me this error 
Failed to execute child process "firefox" (No such file or directory)
That's odd. Can you paste in this command and see if it launches Firefox? ```
/opt/firefox/firefox
```

---

### Post by DO55 on 2008-06-18
yes its working now by using the code

but its not working by pressing firefox icon , it give me same error

---

### Post by DO55 on 2008-06-18
i change  fire fox icon command from  > firefox %u  to > /opt/firefox/firefox

and now its working :)  its very good browser

---

### Post by JazonEsti on 2008-06-18
> **DO55 said:**
> i change  fire fox icon command from    to 

and now its working :)  its very good browser

How can one update FF3 with that? I use ```
gksu firefox %u
```

---

### Post by ninja senses on 2008-06-18
> **iwantu_ubuntu said:**
> i'm Glad I'm Not The Only One Having This Problem. I Have To Say This Is Absolutely Ridiculous!  It Shouldn't Be So Confusing Or Difficult To Upgrade From Ff2 To Ff3. As Someone Said, In Windows You Can Double Click On The Exe And It Upgrades The Older Version, But Why Can't Something As Easy As That Be Done For Ubuntu/linux?  I Don't Want To Place It In My Home Directory, Just Keep My Existing Settings And Upgrade To Ff3 In One Shot. ](*,)](*,)

X2

---

### Post by aysiu on 2008-06-18
Can you try pasting this code one more time? ```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` If you get an error message, post it back here. If you don't, try the Firefox launcher one more time.

---

### Post by ninja senses on 2008-06-18
since no one is answering in the thread i posted i guess ill post in here...

I lost all my bookmarks,settings,plugins, and add-ons....

heres what i ran in the terminal:

sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
sense@sense-ubuntu:~$ rm firefox-3.0.tar.bz2
sense@sense-ubuntu:~$ sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sense@sense-ubuntu:~$ sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sense@sense-ubuntu:~$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
sense@sense-ubuntu:~$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox

how can I get everything back?


BE CAREFUL PEOPLE

---

### Post by JPBodner on 2008-06-18
back again, and still no luck.  Ubuntuzilla didn't fly.  The script at pyschocats didn't work for me either.  Anyone else out there having these problems, or am I a lost cause?

JB

---

### Post by aysiu on 2008-06-18
> **JPBodner said:**
> back again, and still no luck.  Ubuntuzilla didn't fly.  The script at pyschocats didn't work for me either.  Anyone else out there having these problems, or am I a lost cause?

JB
The script "at" Psychocats *is* Ubuntuzilla.

Why don't you just try copying and pasting [the seven commands at Psychocats](http://www.psychocats.net/ubuntu/firefox#terminal)? It's a lot less work. Just make sure the Firefox .tar.bz2 file is in your home directory.

---

### Post by nichpakaich on 2008-06-19
thanks aysiu, that seven commands is very helpful.
I'm running my FF3 right now, without any problem.

---

### Post by JazonEsti on 2008-06-19
aysiu,

following your advice, how can one update FF3 afterwards?

also, will there be an official FF3 upgrade for Ubuntu?

---

### Post by DO55 on 2008-06-19
aysiu
i used your last code and its working :)

JazonEsti
you dont need , just used last aysiu's code 
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

---

### Post by Jexel on 2008-06-19
when will the final be placed into gutsy backports?

---

### Post by JazonEsti on 2008-06-19
> **DO55 said:**
> aysiu
i used your last code and its working :)

JazonEsti
you dont need , just used last aysiu's code 
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

I used aysiu's commands one by one. But now Firefox crashes upon launch.

When I used
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox 
```

It sends out a message that the directory does not exist. Well i checked and it does exist.

Can the commands be reversed? I think I'll use FF2 for now.

Luckily I have the 8.04 Ubuntu CD. Otherwise I may not have been able to log on at all.

---

### Post by DO55 on 2008-06-19
this how you can edit the icon 

drag and drop firefox icon to the desktop or to the panel 
right click over it
properties
delet the command and add this
/opt/firefox/firefox

---

### Post by JazonEsti on 2008-06-19
> **DO55 said:**
> this how you can edit the icon 

drag and drop firefox icon to the desktop or to the panel 
right click over it
properties
delet the command and add this
/opt/firefox/firefox
Yup I tried that before. It still crashes.

I don't recall any error message in the terminal when I followed Aysiu's commands.

---

### Post by DO55 on 2008-06-19
try to download and install it again 

if you still have the problem you can use the new opera 9.5 until you fix the problem 

[http://www.opera.com/](http://www.opera.com/)

you just select the OS and download it and install it like windows , opera is much much easier to install than  firefox

---

### Post by JazonEsti on 2008-06-19
I repeated the procedure. No errors, but FF still crashes.

Yes I am now using Opera. Installed it using Add/Remove.

---

### Post by aysiu on 2008-06-19
I've tried those instructions myself in Ubuntu 7.10 just this week, so I know they work.

The only reason I can think of the directory not existing is if you didn't put the Firefox .tar.bz2 file in your home directory before using the commands... or if you retyped them instead of copying and pasting them (commands are case sensitive, and the spaces and hyphens all matter).

But to reverse the procedure, paste these commands: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo rm -r /opt/firefox
``` With that very last command, make sure to *paste* it. Retyping it is too risky.

---

### Post by jacksmash on 2008-06-19
I just followed the seven steps and it worked like a charm. Thanks!

---

### Post by JazonEsti on 2008-06-19
> **aysiu said:**
> I've tried those instructions myself in Ubuntu 7.10 just this week, so I know they work.

The only reason I can think of the directory not existing is if you didn't put the Firefox .tar.bz2 file in your home directory before using the commands... or if you retyped them instead of copying and pasting them (commands are case sensitive, and the spaces and hyphens all matter).

But to reverse the procedure, paste these commands: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo rm -r /opt/firefox
``` With that very last command, make sure to *paste* it. Retyping it is too risky.
I used your commands to reverse the process, then did the whole thing again. 

It now works (though Noia theme is not yet supported)! Thank you very much!

---

### Post by oldsoundguy on 2008-06-19
If you REALLY have to have 3 right now, do the install as suggested above .. or you can do as I am doing, waiting for the updates to hit the repositories.
Have already installed it on the Windows boxes I have and it really works nice there .. very quick to say the least!  I LIKE the new bar!!  
(Only issue I had with the Windows boxes was Skype, and a quick visit to their site to download the beta of their new version and all was well!!)

---

### Post by DO55 on 2008-06-20
firefox 3 crash and freeze many times , anyone have the same problem ?

---

### Post by stig on 2008-06-20
If you put "firefox 3" into the Search box on the Absolute Beginners forum here you will see there are many people having problems with Firefox 3. It's always safer to wait and let other people have the problems and sort them out rather than wasting your own time on it!  :)

---

### Post by nanotube on 2008-06-21
fyi, ubuntuzillas latest version, 4.4.9, now works fine for installing the latest ff3 release from mozilla. so if you need it, that option is available.

---

### Post by oldsoundguy on 2008-06-22
nanotube:  Thanks!  Such a simple and elegant and RELIABLE solution!

---

### Post by stig on 2008-06-23
> **nanotube said:**
> fyi, ubuntuzillas latest version, 4.4.9, now works fine for installing the latest ff3 release from mozilla....

Nanotube, but for which versions of Ubuntu? This thread is titled "7.10". What about earlier versions? I'm on Dapper 6.06 and already have Firefox 2.0.0.14 installed via Ubuntuzilla. I keep getting two Ubuntuzilla pop-up notices - one tells me I'm on 2.0.0.12 (untrue) and that I should update to 2.0.0.14, and the other telling me that I should upgrade to version 3. But when I look at the system requirements for Firefox 3 it says I need GKT 2.1 - but Dapper only has GTK 2.0. All very confusing.

(Before anyone says I should upgrade Ubuntu to the latest version, I am running my own home business on Ubuntu and want it as stable as possible so I'm in no rush to upgrade the OS)

---

### Post by oldsoundguy on 2008-06-23
as a suggestion as I did not even know about Ubuntuzilla until this tread,  You could try an EARLIER version of the program .. if you follow the instructions on the home page, you can always uninstall it and try a different version (for instance, the one before the current version does not work in 7.10, but the new one does.)

You are, after all, dealing with a browser, not the kernel.

---

### Post by nanotube on 2008-06-23
> **stig said:**
> Nanotube, but for which versions of Ubuntu? This thread is titled "7.10". What about earlier versions? I'm on Dapper 6.06 and already have Firefox 2.0.0.14 installed via Ubuntuzilla. I keep getting two Ubuntuzilla pop-up notices - one tells me I'm on 2.0.0.12 (untrue) and that I should update to 2.0.0.14, and the other telling me that I should upgrade to version 3. But when I look at the system requirements for Firefox 3 it says I need GKT 2.1 - but Dapper only has GTK 2.0. All very confusing.

(Before anyone says I should upgrade Ubuntu to the latest version, I am running my own home business on Ubuntu and want it as stable as possible so I'm in no rush to upgrade the OS)

well, i aim to have ubuntuzilla work on any version of ubuntu starting from dapper (and it should even work on earlier ones, though i haven't had testing done in those in quite a bit). so... it /should/ work. 

not sure what's up with gtk2.0 vs gtk2.1 dependency - haven't found anyone to test on dapper since ff3 was released - but i think it should be ok.

here's what i suggest: 
back up your firefox profile (and move it out of the way - ff3 doesn't like ff2 profiles...)
```
mv ~/.mozilla ~/.mozilla.bakpre3.0
```

back up your current 2.0.0.14 installation (just in case it doesn't work and you have to go back):
```
sudo mv /opt/firefox /opt/firefox2
```

get the latest ubuntuzilla (4.4.9), install it, then use it to install ff3:
```
ubuntuzilla.py -a install -p firefox
```

follow the prompts

after ubuntuzilla is done, try launching your new firefox3:
```
firefox &
```

and see how it plays out. post back here with results. :)

---

### Post by stig on 2008-06-25
Nanotube, thanks very much for the detailed comments and instructions. I hope to try this soon. My work is a bit critical at the moment which means I haven't got much time but also I don't want to risk being without my browser. But I will try it and I'll report back. I've liked Ubuntuzilla on ff2 because it made it easy to keep up to date with ff security updates etc - especially important if you are running a business!

---

### Post by nanotube on 2008-06-25
> **stig said:**
> Nanotube, thanks very much for the detailed comments and instructions. I hope to try this soon. My work is a bit critical at the moment which means I haven't got much time but also I don't want to risk being without my browser. But I will try it and I'll report back. I've liked Ubuntuzilla on ff2 because it made it easy to keep up to date with ff security updates etc - especially important if you are running a business!

no hurry :) i'm looking forward to getting your feedback. dapper still has about a year's worth of desktop-support-period left in it, and it would be nice to give the dapper users an easy way to run ff3. :)

---

### Post by stig on 2008-06-27
Hi Nanotube,
I've installed the latest Ubuntuzilla (which is now 4.5.0) on my Dapper computer and followed your instructions. It installed Firefox 3 OK but when I try to open Firefox it fails and I get a warning. It says GTK 2.10 or newer is required to use this application and that my system has only GTK 2.8. "Please upgrade your GTK library to use the application". :(

---

### Post by nanotube on 2008-06-27
> **stig said:**
> Hi Nanotube,
I've installed the latest Ubuntuzilla (which is now 4.5.0) on my Dapper computer and followed your instructions. It installed Firefox 3 OK but when I try to open Firefox it fails and I get a warning. It says GTK 2.10 or newer is required to use this application and that my system has only GTK 2.8. "Please upgrade your GTK library to use the application". :(

ah, indeed, i have seen others report this problem by now ([http://ubuntuforums.org/showthread.php?t=841395](http://ubuntuforums.org/showthread.php?t=841395)). try this procedure:

grab feisty's version of gtk here:
[http://packages.ubuntu.com/feisty/libgtk2.0-0](http://packages.ubuntu.com/feisty/libgtk2.0-0)
(probably the i386 .deb - if you are using a 32bit machine - here's a direct link to the deb: [http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb](http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb) )

save it to say, "/tmp"

don't install it - we want to just extract it. 

```
sudo dpkg-deb -x /tmp/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb /opt/gtk2.10
```

so now you have gtk2.10 living in /opt/gtk2.10/usr/lib

now, create a shell script to start firefox using that library. the shell script has the following contents:
```
#!/bin/bash
export LD_LIBRARY_PATH="/opt/gtk2.10/usr/lib"
/opt/firefox/firefox $*

```

run command ```
sudo nano /opt/firefox/startfirefox.sh
```
and paste the above contents into it.

then run command
```
sudo chmod 755 /opt/firefox/startfirefox.sh
```

finally, try starting firefox, run command:
```
/opt/firefox/startfirefox.sh
```

and it /should/ run. give it a shot.

sorry i know the instructions are a bit long... but i hope they are clear enough to follow.

edit: as an alternative to doing all the above manually, here's a shellscript that will do it all for you automatically - take the contents, paste into a text file, save as "gtkfirefoxfix.sh" (e.g), then run as
```
bash gtkfirefoxfix.sh
```

```

#!/bin/bash

wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb -O /tmp/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb
sudo dpkg-deb -x /tmp/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb /opt/gtk2.10
(
cat <<'EOF'
#!/bin/bash
export LD_LIBRARY_PATH="/opt/gtk2.10/usr/lib"
/opt/firefox/firefox $*
EOF
) > /tmp/startfirefox.sh
sudo mv /tmp/startfirefox.sh /opt/firefox/
sudo chmod 755 /opt/firefox/startfirefox.sh
sudo chown root:root /opt/firefox/startfirefox.sh

```

then try it, run
```
/opt/firefox/startfirefox.sh
```
and see if it works.

---

### Post by stig on 2008-06-29
Nanotube, thanks for all the help. I used the shellscript and it installed GTK but when I tried to run Firefox I got this output:

........:~$ /opt/firefox/startfirefox.sh
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/gtk2.10/usr/lib/libgtk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/gtk2.10/usr/lib/libgdk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/gtk2.10/usr/lib/libgdk_pixbuf-2.0.so.0)
peter@ubuntu1:~$

I presume this means another file is required?

---

### Post by Bubba64 on 2008-06-29
If you want a easy install I just downloaded FF3 from the main release site and extracted it to home opened the file and dragged the FF opener to the top panel where it opened the instruction panel where I named it FF3 and it put the icon in the panel. This is only updatable with a manual manipulation, but it is the latest release for Linux from the source.

---

### Post by stig on 2008-06-29
> **Bubba64 said:**
> If you want a easy install...

Bubba, I assume you mean an install on 7.10? Nanotube's instructions above are to help people like myself with installing on Dapper version which isn't straightforward. The thread got onto a different version from the title!

---

### Post by Bubba64 on 2008-06-29
> **stig said:**
> Bubba, I assume you mean an install on 7.10? Nanotube's instructions above are to help people like myself with installing on Dapper version which isn't straightforward. The thread got onto a different version from the title!

You are correct I was just posting a easy install for Gutsy if your still running Dapper it probably is different.

---

### Post by nanotube on 2008-06-29
> **stig said:**
> Nanotube, thanks for all the help. I used the shellscript and it installed GTK but when I tried to run Firefox I got this output:

........:~$ /opt/firefox/startfirefox.sh
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/gtk2.10/usr/lib/libgtk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/gtk2.10/usr/lib/libgdk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/gtk2.10/usr/lib/libgdk_pixbuf-2.0.so.0)
peter@ubuntu1:~$

I presume this means another file is required?

ah hrm... looks like you need a newer glibc as well. 

try this script (it basically does the same thing but also adds glibc to /opt):

```
#!/bin/bash

########
# add-on script for ubuntuzilla, to make firefox3 run on Ubuntu 6.06 (Dapper).
# since ff3 requires gtk 2.10, but dapper comes with gtk 2.8, we need to 
# get gtk 2.10 and point firefox to it. 
# also needs a newer glibc to make gtk2.10 happy.

wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glibc/libc6-i686_2.5-0ubuntu14_i386.deb -O /tmp/libc6-i686_2.5-0ubuntu14_i386.deb
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb -O /tmp/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb
sudo dpkg-deb -x /tmp/libgtk2.0-0_2.10.11-0ubuntu3_i386.deb /opt/gtk2.10
sudo dpkg-deb -x /tmp/libc6-i686_2.5-0ubuntu14_i386.deb /opt/glibc6
(
cat <<'EOF'
#!/bin/bash
export LD_LIBRARY_PATH="/opt/gtk2.10/usr/lib:/opt/glibc6/lib/tls/i686/cmov"
/opt/firefox/firefox $*
EOF
) > /tmp/startfirefox.sh
sudo mv /tmp/startfirefox.sh /opt/firefox/
sudo chmod 755 /opt/firefox/startfirefox.sh
sudo chown root:root /opt/firefox/startfirefox.sh

```

---

### Post by stig on 2008-06-29
I pasted the new script into a text editor and saved it as gtkfirefoxfix2.sh then ran bash gtkfirefoxfix2.sh

Then I tried to launch ff with /opt/firefox/startfirefox.sh but got:

:~$ /opt/firefox/startfirefox.sh
/opt/firefox/startfirefox.sh: line 3:  5274 Segmentation fault      /opt/firefox/firefox $*

Was it correct to run the shellscript when I already had ff3 from running the previous version of the script?

---

### Post by ScissorMeTimbers on 2008-06-29
So does anyone know for sure whether Firefox 3 will be added to the 7.10 repositories as an upgrade?  Other posters above mentioned that they would wait, but the Ubuntuzilla site ([http://ubuntuzilla.wiki.sourceforge.net/#whynorepos](http://ubuntuzilla.wiki.sourceforge.net/#whynorepos)) says:
> Thunderbird, Firefox] Why doesn't Ubuntu just release the latest versions in the official repositories?

That's because it would be a fairly big job. These packages depend on a bunch of other libraries, so upgrading say, Firefox, from 1.5 to 2.x would necessitate also upgrading those libraries, and the software that also depends on them, and testing all of this for bugs, regressions, and other nasties. It may involve as many as several hundred packages that would need to be upgraded and tested. Given that newer versions get released with new Ubuntu releases, going through all this effort is not deemed justifiable.

---

### Post by oldsoundguy on 2008-06-29
scissor, if you read this entire thread, you will find the answer is NO for 7.10 and that the solution is to install Unbuntuzilla.

---

### Post by nanotube on 2008-06-29
> **stig said:**
> I pasted the new script into a text editor and saved it as gtkfirefoxfix2.sh then ran bash gtkfirefoxfix2.sh

Then I tried to launch ff with /opt/firefox/startfirefox.sh but got:

:~$ /opt/firefox/startfirefox.sh
/opt/firefox/startfirefox.sh: line 3:  5274 Segmentation fault      /opt/firefox/firefox $*

Was it correct to run the shellscript when I already had ff3 from running the previous version of the script?

yea, it was just fine to just run the new script - it remakes a startfirefox.sh from scratch, so shouldn't be a problem.
well... it looks like we are not making firefox happy with this. next thing to try would be to compile the latest gtk from source using the libraries and build tools that are available on dapper.

follow these instructions for compiling from source
[http://www.captain.at/howto-run-firefox-3-debian-etch.php](http://www.captain.at/howto-run-firefox-3-debian-etch.php)

(you'll need first to install package "build-essential" if you haven't already, and then try building the source and see what else is missing and install it.)

give that a try, see if it works. post questions if you run into any - and report success if you succeed, of course. :)

---

### Post by stig on 2008-06-30
Nanotube, I made several attempts but ran into problems with all of them. Probably a lot is because I don't know much about programming and especially using the terminal etc. I've run out of time now because I need to get on with my work. Perhaps someone else on Dapper can follow it through? (But the title of this thread probably doesn't bring in people on Dapper!)

I need to get back to where I was with Firefox 2 but I've lost the backup somehow, so I deleted the firefox folder from /opt, then ran Ubuntuzilla and used the manual option to choose v.2.0.0.14. This seemed to go OK but now when I try to start firefox it fails. If I run firefox & in the terminal it gives me:

***@***:~$ firefox &
[1] 10047
***@***:~$ *** glibc detected *** free(): invalid pointer: 0xb7e7984c ***
/opt/firefox/run-mozilla.sh: line 131: 10064 Aborted                 "$prog" ${1+"$@"}

I went to the opt folder and deleted the gtk and glibc6 folders. But it still gives the above response in the terminal (except each time I try it I get different instead of 10047 and 10064.

Any ideas how to put it right?

---

### Post by Teonline on 2008-06-30
Hi all, i did the seven steps and all worked fine but if i launch firefox with root i get firefox3.0 otherwise i get the old one... It can be that i created the folder with root on and so i can't access with my account? How to change this crappy situation? thx alot :D

---

### Post by nanotube on 2008-06-30
> **stig said:**
> Nanotube, I made several attempts but ran into problems with all of them. Probably a lot is because I don't know much about programming and especially using the terminal etc. I've run out of time now because I need to get on with my work. Perhaps someone else on Dapper can follow it through? (But the title of this thread probably doesn't bring in people on Dapper!)

I need to get back to where I was with Firefox 2 but I've lost the backup somehow, so I deleted the firefox folder from /opt, then ran Ubuntuzilla and used the manual option to choose v.2.0.0.14. This seemed to go OK but now when I try to start firefox it fails. If I run firefox & in the terminal it gives me:

***@***:~$ firefox &
[1] 10047
***@***:~$ *** glibc detected *** free(): invalid pointer: 0xb7e7984c ***
/opt/firefox/run-mozilla.sh: line 131: 10064 Aborted                 "$prog" ${1+"$@"}

I went to the opt folder and deleted the gtk and glibc6 folders. But it still gives the above response in the terminal (except each time I try it I get different instead of 10047 and 10064.

Any ideas how to put it right?

did you make sure to start with a fresh profile, after you reinstalled ff2?

---

### Post by oldsoundguy on 2008-06-30
Not sure about this, but I am assuming that if you set the Mozilla programs (I have two, FF3 and Thunderbird) for auto updates in Ubuntuzilla, the "check for update" option IS grayed out in tools, as it checks AUTOMATICALLY when you launch the program.  I did not have the check for option in FF2 when I was running IT on machines as I had it set for auto check also. (and got some of the plug in updates recently.)

---

### Post by stig on 2008-06-30
> **nanotube said:**
> did you make sure to start with a fresh profile, after you reinstalled ff2?

Yes, I had deleted the .mozilla folder. After the install I tried launching ff with the new profile it created. When it failed I then replaced the new profile with a copy of my old ff2 profile. But still it wouldn't launch.

I thought I would clear the files and try again. I've just uninstalled ff2 using ubuntuzilla and got rid of the profile. Then used ubuntuzilla to again install ff2. It all seemed to go OK.

Now it's launching OK. At first I was getting the Mozilla feedback boxes as well each time I launched it. I then replaced the new profile with my old ff2 profile and they don't appear...but I've got my bookmarks, history etc and now I seem to be back with ff2 up and running!

Thanks for all your help nanotube. I will be interested to see if anyone else gets ff3 going OK on Dapper. Good luck with the attempts!  :D

---

### Post by nanotube on 2008-06-30
> **stig said:**
> Yes, I had deleted the .mozilla folder. After the install I tried launching ff with the new profile it created. When it failed I then replaced the new profile with a copy of my old ff2 profile. But still it wouldn't launch.

I thought I would clear the files and try again. I've just uninstalled ff2 using ubuntuzilla and got rid of the profile. Then used ubuntuzilla to again install ff2. It all seemed to go OK.

Now it's launching OK. At first I was getting the Mozilla feedback boxes as well each time I launched it. I then replaced the new profile with my old ff2 profile and they don't appear...but I've got my bookmarks, history etc and now I seem to be back with ff2 up and running!

Thanks for all your help nanotube. I will be interested to see if anyone else gets ff3 going OK on Dapper. Good luck with the attempts!  :D

great to hear you're back up and running :)

sorry we haven't gotten the ff3 on dapper issue solved yet. i'll see if i can scrounge up a dapper tester who has more time to tinker with it - i'll let you know if we achieve any positive results.

---

### Post by stig on 2008-07-02
Nanotube, as you are deeply involved with Ubuntuzila I thought I should inform you of the following. Now that I am back on Firefox 2 (v. 2.0.0.14 on Dapper) I regularly get the update notices (the little boxes at the bottom of the screen) telling me that I am on Firefox 2.0.0.12 and that 2.0.0.14 is available (although I have it installed already).

Also I get another update notice each time telling me that Firefox 3 is available and urging me to go to that version. I was getting these even before I went through the unsuccessful attempt to upgrade to ff3, so it is not due to that.

But the 12-to-14 notice is confusing and the ff3 notice could lead dapper users to get into problems trying to install ff3. I don't know if there is anything you can do on Ubuntuzilla that would correct these anomalies.

---

### Post by nanotube on 2008-07-02
> **stig said:**
> Nanotube, as you are deeply involved with Ubuntuzila I thought I should inform you of the following. Now that I am back on Firefox 2 (v. 2.0.0.14 on Dapper) I regularly get the update notices (the little boxes at the bottom of the screen) telling me that I am on Firefox 2.0.0.12 and that 2.0.0.14 is available (although I have it installed already).

Also I get another update notice each time telling me that Firefox 3 is available and urging me to go to that version. I was getting these even before I went through the unsuccessful attempt to upgrade to ff3, so it is not due to that.

But the 12-to-14 notice is confusing and the ff3 notice could lead dapper users to get into problems trying to install ff3. I don't know if there is anything you can do on Ubuntuzilla that would correct these anomalies.

could you post a screenshot of the 2.0.0.12 -> 2.0.0.14 update message? both of these can't be coming from ubuntuzilla - ubuntuzilla can't be telling you both that you should upgrade to 3.0, and that you should upgrade to 2.0.0.14, it can only be doing one of these (and i'm pretty sure 3.0 is it).

---

### Post by ResumeMan on 2008-07-03
Just wanted to say I did the "seven steps" and it seems like everything worked like a charm. Thanks aysiu, *outstanding* advice as always!

---

### Post by Buzzdee on 2008-07-03
I have to say, I'm a little disappointed and confused since I find it weird that it's not possible to include ff3 in the repositories (yes, I read that quote from the official webpage). But if installing ff3 is as simple as extracting it to ~/firefox, why can't synaptic do that? 
Also, there exist comfortable .deb-files (the setup.exe's of ubuntu, I love them :) ) for Opera, why not for Firefox, since it's even more popular?

(Very off-topic from here on, skip if you should be working as I should...)
I think stuff like that is the reason why Linux isn't popular. I know many people who are very interested, but then they fail in a task such as installing the new web browser and quit - that's so disappointing. Don't get me wrong here, please, I've completely switched to ubuntu for over one year now, I just had to say that, as long as there are unnecessary complications like that, linux won't have a chance to become interesting to public. Sorry for the off-topic... had to be said, I fear.

Bastian

---

### Post by stig on 2008-07-11
> **nanotube said:**
> could you post a screenshot of the 2.0.0.12 -> 2.0.0.14 update message? both of these can't be coming from ubuntuzilla - ubuntuzilla can't be telling you both that you should upgrade to 3.0, and that you should upgrade to 2.0.0.14, it can only be doing one of these (and i'm pretty sure 3.0 is it).

Nanotube, Sorry I've been away and didn't see your message. I'll try to get a screenshot but the ubuntuzilla messages are only up briefly on-screen and it means I need to see them and be able to capture them in that brief time.

What triggers the normal ubuntuzilla update message? It doesn't come up when I open Firefox - it's usually quite a while after opening it. Maybe it comes up at a specific time of day but I haven't noticed that.

---

### Post by nanotube on 2008-07-11
> **stig said:**
> Nanotube, Sorry I've been away and didn't see your message. I'll try to get a screenshot but the ubuntuzilla messages are only up briefly on-screen and it means I need to see them and be able to capture them in that brief time.

What triggers the normal ubuntuzilla update message? It doesn't come up when I open Firefox - it's usually quite a while after opening it. Maybe it comes up at a specific time of day but I haven't noticed that.

hey!
ok, ubuntuzilla update messages are triggered by a cron job in the user's crontab.
you can re-trigger it manually by running
```
ubuntuzilla.py -p firefox -a checkforupdategui
```

also, the latest ubuntuzilla versions should display the update message for longer (basically, until user clicks to hide). what's your version of ubuntuzilla? (ubuntuzilla.py --version)?

and by the way, see this thread, where we are working on getting ff3 on dapper. feel free to try the static-compiled version i posted there to see if it works:
[http://ubuntuforums.org/showthread.php?t=847484](http://ubuntuforums.org/showthread.php?t=847484)

---

### Post by stig on 2008-07-15
I've just seen two messages come up. One was the Firefox update message but the other was Thunderbird. I wonder if this is what I've been seeing before and thought they were both Firefox. The Thunderbird is showing the same numbers as the earlier Firefox, i.e. update from 12 to 14, so I might have confused them. Sorry!  :(

---

### Post by nanotube on 2008-07-15
> **stig said:**
> I've just seen two messages come up. One was the Firefox update message but the other was Thunderbird. I wonder if this is what I've been seeing before and thought they were both Firefox. The Thunderbird is showing the same numbers as the earlier Firefox, i.e. update from 12 to 14, so I might have confused them. Sorry!  :(

aha, ok, that explains it! thanks for the update! :)

---

### Post by stig on 2008-07-16
> **nanotube said:**
> aha, ok, that explains it! thanks for the update! :)

But I'm still getting the ubuntuzilla message saying I'm on 2.0.0.14 and there is a new update available, v.3. I suppose there is no way of stopping this going to Dapper users?

---

### Post by nanotube on 2008-07-16
> **stig said:**
> But I'm still getting the ubuntuzilla message saying I'm on 2.0.0.14 and there is a new update available, v.3. I suppose there is no way of stopping this going to Dapper users?

well, there is - i'd have to make an update to the code. :)

or, you could just edit your crontab and comment out the firefox update checker job 
```
crontab -e
```

---

### Post by cupcake4170 on 2008-11-27
I really wish they had a stable version of Chrome for Linux.

---

