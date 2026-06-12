---
title: "[SOLVED] having trouble with linksys wireless"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by nightingale42 on 2008-08-28
i'd like to preface this by saying that i am an 'absolute beginner' here.  i just set up a duel boot with windows xp and ubuntu 8.somethingorother last night and haven't played around with it much.  apparently i can 'enter commands' but i don't even know where i would go to do that.
i have a linksys wireless usb device that ubuntu isn't recognizing.  i read a bit in these fourms and they seem to suggest that i should get ndiswrapper.  so, i got it sitting on my desktop - i open the 'install' file and it's giving me instructions that i don't understand.  ex - "Make sure there is a link to the kernel source from the modules
directory." Where is that??????  and "The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file."

what??????

and how am i supposed to 'login as root'?

these are just examples, the whole file sounds greek to me.  can someone please help me out here?
i've looked through the forums, but again, i'm having a hard time understanding what they might be telling me to do.  maybe a link to some sort of basic operation of ubuntu would help. >_>

---

### Post by dmedell on 2008-08-28
to log in as root in ubuntu you have to use the command:

sudo su

you then need to enter you password

:guitar:

---

### Post by erudite on 2008-08-28
Using "sudo su" can be dangerous if you don't know what you are doing.

Ok to enter commands like "sudo su" you go applications > Terminal.  This is where you enter commands.

The first thing you should do for wireless drivers is go to System > Administration > Synaptic Package Manager...enter your password.  Then search ndisgtk.  This is ndiswrapper however it has a graphical user interface "GUI" which makes it easier.  You probably shouldn't try and install from the source just yet...which is what you are doing with that install file.  If you need to install it is best to use Synaptic for the moment.

Edit: [Here]("https://help.ubuntu.com/7.04/basic-commands/C/index.html") is a link to some basic commands you will probably need to know.  Good to see you trying Ubuntu btw.

---

### Post by SunnyRabbiera on 2008-08-28
Actually the best way to solve this is to ignore the source code version of ndiswrapper you may find and use these packages:
[http://packages.ubuntu.com/hardy/ndiswrapper-common](http://packages.ubuntu.com/hardy/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk)

download them via windows and then in ubuntu you can just transfer them over.
It should provide you with ndiswrapper and a graphical front end.
Also try installing the mintwifi package too you can find it here:
[http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

> **erudite said:**
> Using "sudo su" can be dangerous if you don't know what you are doing.

Ok to enter commands like "sudo su" you go applications > Terminal.  This is where you enter commands.

The first thing you should do for wireless drivers is go to System > Administration > Synaptic Package Manager...enter your password.  Then search ndisgtk.  This is ndiswrapper however it has a graphical user interface "GUI" which makes it easier.  You proabably shouldn't try and install from the source just yet...which is what you are doing with that isntall file.  If you need to install it is best to use Synaptic for the moment.

Yes but synaptic is no use if you dont have a connection to begin with.

---

### Post by erudite on 2008-08-28
Well he can always plug an ethernet cable in until he has wireless if he has one...

---

### Post by crjackson on 2008-08-28
> **nightingale42 said:**
> i'd like to preface this by saying that i am an 'absolute beginner' here.  i just set up a duel boot with windows xp and ubuntu 8.somethingorother last night and haven't played around with it much.  apparently i can 'enter commands' but i don't even know where i would go to do that.
i have a linksys wireless usb device that ubuntu isn't recognizing.  i read a bit in these fourms and they seem to suggest that i should get ndiswrapper.  so, i got it sitting on my desktop - i open the 'install' file and it's giving me instructions that i don't understand.  ex - "Make sure there is a link to the kernel source from the modules
directory." Where is that??????  and "The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file."

what??????

and how am i supposed to 'login as root'?

these are just examples, the whole file sounds greek to me.  can someone please help me out here?
i've looked through the forums, but again, i'm having a hard time understanding what they might be telling me to do.  maybe a link to some sort of basic operation of ubuntu would help. >_>

Forget about the file on your desktop.  

Plug in a wired internet connection and do this if you can...

Look at your top panel (menu bar).  Click on the following:  System>Administration>Synaptic Package Manager

Once that is loaded, go to the search box and search for ndiswrapper.  There are 3 packages you need to tick the check box on to install what you need 1) ndiswrapper 2) ndiswrapper utilities 3) gtk menu for ndiswrapper / windows wireless.

Mark the check box for each, and then click the apply button.  Everything needed from the package manager will be installed automatically.

Next get your windows driver cd out for the usb wireless card and report back.  Once this is done, we'll load up your windows driver.

---

### Post by SunnyRabbiera on 2008-08-28
> **erudite said:**
> Well he can always plug an ethernet cable in until he has wireless if he has one...

true, but we dont know the conditions he/she is in.

> **crjackson said:**
> Forget about the file on your desktop.  

Plug in a wired internet connection and do this if you can...

Look at your top panel (menu bar).  Click on the following:  System>Administration>Synaptic Package Manager

Once that is loaded, go to the search box and search for ndiswrapper.  There are 3 packages you need to tick the check box on to install what you need 1) ndiswrapper 2) ndiswrapper utilities 3) gtk menu for ndiswrapper / windows wireless.

Mark the check box for each, and then click the apply button.  Everything needed from the package manager will be installed automatically.

Next get your windows driver cd out for the usb wireless card and report back.  Once this is done, we'll load up your windows driver.

yes but as I said synaptic is useless if they dont have a connection already.

---

### Post by crjackson on 2008-08-28
> **SunnyRabbiera said:**
> true, but we dont know the conditions he/she is in.



yes but as I said synaptic is useless if they dont have a connection already.

Yes, I know that.  But you said it while I was typing so I wasn't privy to your comments.  I know we don't know if he has a connection yet, but if he does he'll have a place to start.

---

### Post by SunnyRabbiera on 2008-08-28
as to the original poster you may want to try linux mint if you feel wireless is too much of an issue to set up via ubuntu.
Linux mint is based on ubuntu but has built in tools to make transition easier (like ndiswrapper)
[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)
thats the download page if you are interested

---

### Post by nicedude on 2008-08-28
Don't use root login and instead use sudo in front of commands that require root privileges to work. Logging in as root when you say you are a new Ubuntu user is a recipe for disaster and you can break your system in 2 seconds. Just thought I would point out that there are good reasons why no one is supposed to even tell people how to login as root in the forums.

---

### Post by nightingale42 on 2008-08-28
hey, sorry, i should have mentioned that.  i'm hooked up to the internet right now (wired) in ubuntu.  i'm currently trying to find that linksys cd, but this place is a mess.  i also forgot to mention that the linksys model no. is WUSB54GC.  not sure if you really need that though
last time i tried using the disk it wouldn't read in ubuntu - i take it it will now that i've got the ndiswrapper thing installed?
thanks for the warning about root lol

---

### Post by crjackson on 2008-08-28
> **nightingale42 said:**
> hey, sorry, i should have mentioned that.  i'm hooked up to the internet right now (wired) in ubuntu.  i'm currently trying to find that linksys cd, but this place is a mess.  i also forgot to mention that the linksys model no. is WUSB54GC.  not sure if you really need that though
last time i tried using the disk it wouldn't read in ubuntu - i take it it will now that i've got the ndiswrapper thing installed?
thanks for the warning about root lol

Great - Did you install all the items I mentioned?

---

### Post by nightingale42 on 2008-08-28
yep, all installed and i found the cd.
btw, is that a ferret in your avatar?  he looks possessed
? what do i do now? it still won't read the exe file - do i have to open ndiswrapper? if so, how and where?

---

### Post by nightingale42 on 2008-08-28
hello? can someone help me out with this last little bit?

---

### Post by crjackson on 2008-08-28
> **nightingale42 said:**
> yep, all installed and i found the cd.
btw, is that a ferret in your avatar?  he looks possessed
? what do i do now? it still won't read the exe file - do i have to open ndiswrapper? if so, how and where?

Sorry for slow response I'm at work right now.  Yes it's a ferret.  He was yawning.

If that exe file can be extracted, we are looking for an *.inf and a *.sys file to be loaded into ndiswrapper.  If you have a windows system, it may be easier to extract from a booted windows system.

If the answer is no, then you can open the synaptic package manager again and search/install cabextract.

I've never used it, so you'll have to search around a little to find the command line usage to extract the needed files.

If that doesn't work, you need to find the files online to install.  I would do all this for you, but I'm a little busy at the moment.  Sorry I don't have time right now, hopefully someone else will jump in with some exact instructions.  If not, I'll check back in a while and see where we are at.

---

### Post by nicedude on 2008-08-28
Yes you need a driver .inf file instead of an .exe I believe. You always can try downloading a XP driver from Linksys as well and see if you can find an .inf file that way and then point Ndiswrapper to it. But I think you will have to extract the files from the .exe installer to get it done but maybe not so check out Linksys's driver download pages.

---

### Post by nightingale42 on 2008-08-28
i don't know how to 'point ndiswrapper' to it.  i can't even figure out where it is.  i'm trying searches, but they are running at an extremely slow pace.

the cd opens up with several different files, some bs (such as the adobe extra) and some not (there's a file labeled 'drivers').  there is only one .inf file in the main folder - the autorun for the setup.exe.  
the 'drivers' folder contains a .cat, .inf, and a .sys.  all are named 'rt73'.  
there is also a utility folder with .dll s , .cab, .bin, and others that i'm not familiar with.  it has two exe's - the 'setup' and one with my model 'number'.  
do i want the files in the drivers folder? if so - what do i do with them.

---

### Post by nightingale42 on 2008-08-28
another quick question.  if i click and drag something to the desktop, have i just created a shortcut, copied the file, or moved the file?

---

### Post by nicedude on 2008-08-29
If you drag something from a folder to your desktop you will be moving it to the desktop. When you said in the driver directory there was a .inf and other rt73 files  those are the files you need to make your wifi work so I would say just copy and paste the driver directory to your desktop and then in Ndiswrapper you select browse for the file and go to desktop and then into the driver folder and select the .inf file and see if it then installs.

Oh if you are dragging something from a CD it of course will just be copied since the CD is read only, but when you drag something from your system to another drive etc it will be moved unless it takes root permission to move the file in question. I believe that is basically the behavior.


Hope you get it going and if you do be sure to mark this thread as solved so others & I can see you did.

---

### Post by nightingale42 on 2008-08-29
ok, i'm really completely  new - can you tell me step by step how to get to Ndiswrapper? i am soooo not used to the file system ubuntu uses

---

### Post by nicedude on 2008-08-29
I am pretty sure it will have a shortcut in one of top menu bar Applications but I don't know which submenu as I don't use Ndiswrapper. But if you can't find it there then just open a terminal ( top menu bar Applications -> Accessories -> Terminal ) and type the following

ndiswrapper


it may take sudo ( sudo gives a command root privileges ) to run correctly if so 

sudo ndiswrapper

Also if that is not the correct command you can find out what a command is by typing in a terminal some of its letters that you know and then press the tab key a couple of times and the system will list all commands that contain those letters, here is an example to try.

While in a terminal type "gnome" without the quotes and then press tab a couple of times and you will get a ton of commands that start with gnome as there first characters. Here is part of the ouput I get when I do it.

gnome-about                            gnome-power-manager
gnome-about-me                         gnome-power-preferences
gnome-appearance-properties            gnome-power-statistics
gnome-app-install                      gnome-screensaver
gnome-app-install-helper               gnome-screensaver-command
gnome-at-mobility                      gnome-screensaver-preferences
gnome-at-properties                    gnome-screenshot
gnome-at-visual                        gnome-search-tool
gnome-audio-profiles-properties        gnome-session
gnome-autogen.sh                       gnome-session-properties
gnome-calculator                       gnome-session-remove
gnome-character-map                    gnome-session-save
gnome-codec-install                    gnome-settings-daemon
gnome-commander                        gnome-sound-properties
gnome-control-center                   gnome-sound-recorder
gnome-default-applications-properties  gnome-system-log
gnome-desktop-item-edit                gnome-system-monitor
gnome-dictionary                       gnome-terminal
gnome-display-properties               gnome-terminal.wrapper
gnome-doc-common                       gnome-text-editor
gnome-doc-prepare                      gnome-theme-thumbnailer
gnome-doc-tool                         gnome-thumbnail-font

You could use this same technique with "ndis" without quotes as the text to type and then press tab as that should list everything that starts with those 4 letters and might help you figure out what the Ndiswrapper command you need to use is to start it up.


PS I am assuming you installed Ndiswrapper already as you will have to do that as well since it is not installed by default.

---

### Post by SunnyRabbiera on 2008-08-29
actually if you are able to install ndisgtk all that might not be needed, it has a very good interface for installing the .ini files that are needed to run your wireless unit.
but here is another consideration you may need to unzip the exe file and turn the contents into a folder, there is a few packages to do this:
cabextract
unshield
unzip

actually this guide here might be of help, sure it is probably a different model then what you have but its basic principal applies:
[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper))

---

### Post by nicedude on 2008-08-29
Yes just install the one that sunny said to, Sorry I couldn't remember what all frontends there are for Ndiswrapper since I never use it. And sunny he already has found the driver directory with .ini files in it so he has the driver he needs he just needs to make sure he has Ndis program and then run it and point it to the .inf files it needs. Which is good because extracting an .exe to get what he needs would be one more big hurdle that apparently he will now not have to jump :-)

I am probably going to sleep soon as it is 2am here so sunny maybe if you are around for awhile you can help this guy get ndis to try and load the driver he has. I also am no good at knowing anything more about Ndis than what it is & why it exists. I choose to use Linux based madwifi drivers for my wifi so I can have neat features ( like packet injection :-) ) but I also see that if it works and someone is not interested in hacking that Ndis might do just fine.

Goodluck with your wifi and goodnight all

---

### Post by SunnyRabbiera on 2008-08-29
I just remember I had a heck of a time getting my wireless working so any frustration the original poster has i can sympathize with.
But its not the fault of linux or ubuntu, its linksys who keeps their crap windows only.

---

### Post by nightingale42 on 2008-08-29
erm... what opens .ko files? -_-  i'm off to bed myself - will try to finish this up tomorrow.  thanks for all the help people :)

---

### Post by crjackson on 2008-08-29
Okay, I purchased a WUSB54GSC today so that I can try to help you with this.  I couldn't find one that wasn't the speedbooster version so I HOPE the drivers I attached will work.

Download the file I attached to this post and extract it on your desktop.  You need to determine if you have v1 or v2 of the chipset and use the version in the attachment that matches your device.

Once that is determined, goto your menus SYSTEM>(either Administration or Preferences-I haven't installed yet so I don't remember off had) and look for the program marked "Windows Wireless" and click.

You should find some kind of a browse feature, and you use that to browse to the files you extracted from the attachment.  Go to the folder that has the v1 or v2 (whichever you need) and load the *.inf file (the *.sys file MUST be in the same folder, but you only load the *.inf file). Then close the graphical "Windows Wireless" program.

restart your system and if the driver(s) I provided are the correct ones for your particular device, you should be able to receive wireless internet (after you provide a wpa key assuming it's a password protected connection).

If these aren't the correct drivers, then I have wasted $29.99 + tax for my efforts.

If I have time this weekend, I'll actually install the device myself and give you a step by step guide if it works and you need it.

Got run, best I can do for now... Good luck

---

### Post by crjackson on 2008-08-29
> **nightingale42 said:**
> i don't know how to 'point ndiswrapper' to it.  i can't even figure out where it is.  i'm trying searches, but they are running at an extremely slow pace.

the cd opens up with several different files, some bs (such as the adobe extra) and some not (there's a file labeled 'drivers').  there is only one .inf file in the main folder - the autorun for the setup.exe.  
the 'drivers' folder contains a .cat, .inf, and a .sys.  all are named 'rt73'.  
there is also a utility folder with .dll s , .cab, .bin, and others that i'm not familiar with.  it has two exe's - the 'setup' and one with my model 'number'.  
do i want the files in the drivers folder? if so - what do i do with them.

I didn't see this before I posted above.  The folder with the rt73.inf and rt73.sys are probably what you actually need (anybody what to buy a Linksys USB wireless dongle I just purchased ;)  )?

Right click on the folder on the cd and then click copy.  Then right click on your desktop and click paste.

Open up the application called "Windows Wireless" (look through your system menus / sub-menus).  Click Add and browse to the folder you copied to your desktop.  Select the rt73.inf file and accept it (press OK possibly, or double click it).

Close the wireless helper, and restart your system.  It's not always necessary to restart, but that's how I do it.

Go to your networking icon in the notification area (top right section) of your upper panel/menu bar.  Click it one time, and you should see your wireless signal (if everything worked correctly).  Select it and put in your password.

Phew!!  I hope this works...  Let me know what happened.

---

### Post by nightingale42 on 2008-08-29
awesome - it works :) well, i still have to find the password, but other than that it's recognizing the hardware :D  can you not return the card?  thanks again.  i can't believe you'd go to that much trouble.

and btw, it was the one from the driver's file that worked.

---

### Post by crjackson on 2008-08-29
> **nightingale42 said:**
> awesome - it works :) well, i still have to find the password, but other than that it's recognizing the hardware :D  can you not return the card?  thanks again.  i can't believe you'd go to that much trouble.

and btw, it was the one from the driver's file that worked.

Great, glad it worked for you.  That makes it worth it for me.  I'll find a use for it, or sell it on ebay.  No big deal...

---

