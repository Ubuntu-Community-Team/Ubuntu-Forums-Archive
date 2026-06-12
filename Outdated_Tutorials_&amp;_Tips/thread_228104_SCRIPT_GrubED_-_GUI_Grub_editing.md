---
title: "SCRIPT: GrubED - GUI Grub editing"
date: 2006-08-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Tomosaur on 2006-08-02
========================================================================
[COLOR="Red"]NOTE: THERE IS A BUG IN GRUBED WHICH MAKES IT DANGEROUS ON GUTSY. I AM WORKING TO FIX IT, BUT PLEASE DO NOT USE IT ON GUTSY FOR THE TIME BEING.[/COLOR]
 
 
NOTICE: **Mirrors for Spanish GrubEd**
Please note that the Spanish version of GrubEd has not yet been updated to the latest version, and as such will not contain bug fixes released recently. If anybody is able to translate the latest version, then I'd appreciate the help :)
[GrubEd_es]("http://files.myopera.com/pacmanman/ubuntu/GrubEd_es.tar.gz").
 
Once again, thanks to pacmanman for the translation :) Here's his [Blog]("http://my.opera.com/pacmanman/blog/").
===========================================================================
 
GrubEd is a little **(UPDATE: NOW 'QUITE BIG')** script I wrote which gives users a nice GUI to alter their grub settings. It is a vastly modified version of my earlier, non-GUI script.
 
Using GrubEd, you'll be able to alter your grub settings at the touch of (a few) buttons! It currently supports:
 
**Default menu item editing**: Set Grub to boot into whichever OS you want through a handy menu.
 
**Timeout editing**: Set the timeout to whatever you feel like. Displays a confirmation box if you set it below 3 seconds.
 
**Disable the timeout**: Always getting caught out? Just disable the timeout!
 
**Hide Grub**: Hide or unhide the Grub menu depending on your current settings.
 
**Change custom colour settings**: Set grub to a colour scheme of your choice!
 
**Add a Grub splash screen**: Make Grub display an image as it's background!
 
**Enable / Disable memtest86**: Don't want it? Scrap it :P
 
**Change the number of kernels Grub shows**: Confused by a big list of the same OS? Simply change the number of kernels to keep your list tidy!
 
**Direct Edit**: Shows your entire Grub settings file for easy editing.
 
**Reboot**: Reboot your machine to test your new settings.
 
**Backup**: Back up your current Grub settings. I reccommend you use this first!
 
**Restore**: Easily restore your backed up Grub settings file.
 
There's also a handy help file to tell you how to use the script properly.
 
Here's the text of the README to tell you how to install / uninstall / use:
```

README
============
Thanks for downloading the GrubEd script.
If you are simply updating the script from an older version, then remember to UNINSTALL your current version
before you INSTALL the new one. If the 'uninstall' script fails to work, try using the 'uninstall_old_version' script instead.
 
INSTALLATION:
 
From the terminal, cd to the directory this help file is in, and type:
sudo ./install
Installation from then on is automatic. 
 
The install script will check for certain programs, which GrubEd relies upon
to function normally. If any of these programs are not available, then the user will be informed.
 
======================================================================
 
USAGE:
 
To use this script, you need root permissions. If you have sufficient user privileges, you can type:
 
gksudo grubed
 
You will be asked for your password. This is the same password as you 
use to login. If the login is successful, you will be shown the default GrubEd menu.
 
Alternatively, you can paste the example launcher, named 'Launch GrubEd' on to your desktop or Gnome panel.
Double clicking it should bring up a gksudo box for you to input your password.
 
======================================================================
 
UNINSTALLATION:
 
You can uninstall the script completely by opening a terminal and typing:
 
sudo /usr/share/doc/grubed/uninstall
 
Please note that this will not remove any backups of your Grub menu, 
nor any images from /boot/grub/images.
 
======================================================================

```Notes: 
 
The script makes use of zenity, a program which displays dialog boxes. Make sure you have zenity enabled on your system.
 
Screenshots and download attached at the bottom of this post.
 
I have tested this script and it works fine on my system. However, I'm only one person and I can't test this on a massive variety of setups. Therefore, I will not be held responsible if anything goes wrong while using this script. Make use of the backup ability provided.
 
Here's todays changelog: 4th July 2007:
 
```

Changelog for GrubEd
Latest changes at top, all changelogs dated.
 
Version 1.1 - released 17 Sep '07
Made GrubEd function more gracefully:
    No more 'Do you want to perform a new task?'
Made the update-grub process more integral to the various tasks for which it was required:
    Users are now asked directly to update grub, not relied upon to remember to do it later.
GrubEd now asks users to pick a new default OS to boot from after the boot menu has been altered.
Removed some garbage hash (#) characters from the changelog. Can't really remember why I put them there in the first place!
Altered the licence to make it less confusing.
 
#################################
Version 1.0 - released 4 July '07
Fixed a bug which meant splash images with underscores in their title were accepted but not used
This also marks the 1.0 release of GrubEd
 
#################################
6 May '07
Updated the installer script to be more helpful.
    It now scans for all the software it depends upon using the 'which' 
    command. If any piece of software is missing, it informs the user.
    This was requested numerous times. Unfortunately, it won't 
    automatically download and install these packages - maybe in the 
    future.
 
Fixed a bug in the enable/disable splash feature, which would cause users 
  to see a non-fatal error message if they enabled or disabled the splash 
  screen via the command line.
 
Renamed all of the files to lower-case. Now instead of launching via 
  'gksudo GrubEd', you should just use 'gksudo grubed'.
 
#################################
23 October '06
 Changed temporary files to be stored in /tmp/
    Thanks to 'mssever' @ ubuntuforums.org for pointing this out!
 
 Got rid of superfluous comments.
 
#################################
20 October '06
Fixed a very serious bug with the direct-edit option. Closing the
direct-edit box using the window-close button would destroy menu.lst,
thus making booting impossible. Sorry for the wait!
 
#################################
27 August '06
Fixed a bug with changing the default OS. This bug seemingly didn't 
affect everyone, but the fix is a bit cleaner anyway.
 
#################################
11 August '06
Added ability to fiddle with splash screen!
    --NOTE--A few things. Images must be 640x480, 14 colours ONLY, and in .xpm.gz format.
        GrubEd, however, can only check the file format. You need to take care of the
        size and colours yourself.
        Custom colours and splash images can be fiddly to get working together properly.
        I personally prefer to use just one or the other, but it's up to you. Go nuts.
        Like the custom colours, this spans several functions, so I've commented them to
        Make them stand out if you want to mess with them.
 
#################################
10 August '06
Added a quick check for /boot/grub/
    --NOTE--On ubuntuforums.org, lots of people seem to be playing around with multiple installs of grub
        While not wanting to cripple functionality, I don't want to be held responsible for them messing
        their system up. Now, the script will check for /boot/grub/, and if it's not present, exits.
        I have no idea what the repurcussions of multiple /boot/grub/ directories is, and I don't particularly
        want to find out.
Removed all reference to the re-order menu feature in the code, but kept a version back which includes it.
    --NOTE--I see no reason why anyone would want to do this. The problem is not only in implementing it, but
            the changes just simply will not last if you use any of the other options.
Added an 'installer'. It copies GrubEd to /usr/bin, and makes a documentation directory at /usr/share/doc/grubed.
Included an example Launcher. Paste it onto your desktop/panel/whatever to use it.
Made an 'uninstaller'. It will live in /usr/share/doc/grubed/.
    --NOTE--Usage is 'sudo /usr/share/doc/grubed/uninstall'
 
#################################
06 August '06
More code optimisation - I left in a lot of trash from the original source (1st version),
so this update is essentially just a cleanup. Total download size was halved :/
Removed excess references to zenity, which was bloating script size.
    --NOTE--Now there are two functions to handle success / error notifications.
         They are called 'success' and 'noChange' respectively. Use these to call
         up a success / cancel notification when necessary.
Scrapped the 'newTask' function in favour of a scripted while loop.
Renamed the help file to GrEdHelp.txt
Slight alterations to references to help file due to possible conflict.
 
#################################
05 August '06
Changelog / Fixlog added as of Sat 5 Aug '06:
Fixed an irritating bug were Direct Edit mode would always patch, even if no changes made.
Tidied up code a little.
  Added ability to run update-grub, which replaces your existing menu.lst.
    --NOTE--This must be run for 'Automagic' settings to be finalised. Any function which replaces such a setting 
            MUST notify the user. It will not run automatically because it replaces a lot of settings,
               therefore it should be left to user discretion. List these in a changelog as '--AUTOMAGIC--'.
  Added ability to enable or disable the memtest86 option. --AUTOMAGIC--
  Added ability to change the number of kernels displayed by Grub. --AUTOMAGIC--
  Added full colour-scheme options.
    --NOTE--This is a pretty nifty little option but it spans several functions due to it's relatively
         complicated nature. Grub uses a 'NON-SELECTED / SELECTED' setup, with both forms having a 'foreground' and
         'background' colour, in that order. In other words, two seperate colour schemes need to be chosen.
         The following three lines should help you understand more easily, the third being the format grub's menu.lst uses.
            NOT-SELECTED-ITEMS            SELECTED-ITEMS
       foreground / background        foreground / background
          blue/black                light-green/magenta

```Download attached below, visitors must log in before the forum will allow you to download. Registration is free and spamless :)

---

### Post by Thund3rstruck on 2006-08-03
It would be great if the script parsed the items in menu.lst (with RegEx) and provided the list in a checkedListView or something. If you're going to have to open menu.lst to find out which item to make default anyways then you're probably going to just edit it manually then. 

Good job though...

---

### Post by Tomosaur on 2006-08-04
Luckily for you, I just added that feature last night :D

EDIT: Uploaded the new version - you can now select your OS from a list, among other new features.

---

### Post by shof2k on 2006-08-04
Nice!  Stuff like this should go straight into a release. Nearly anything that helps a 'normal' user away from the command line is good.  

GRUB editing is fiddly and with so many newbies using dual booting systems a GUI grub is a boon :)

---

### Post by Tomosaur on 2006-08-04
Perhaps if it was a compiled program something like this would be included, but I seriously doubt the Ubuntu team would ever include a 3rd party script.

---

### Post by nickpaton on 2006-08-04
Thanks for a great script Tomosaur!

I'm familiar with placing application shortcuts on the Desktop via right click on the Desktop and "Create launcher..." and browsing to the application in the normal way etc.

But how do you actually carry out your instructions to configure the launcher to launch the 'sudo sh GrubEd.sh' script?

"GrubEd.sh" resides in my Home/nick/ directory.

Many thanks

---

### Post by Tomosaur on 2006-08-04
Right click, 'Create Launcher'. Name it whatever you like. I just use 'GrubEd'. In the 'command' bit, just type 'sudo sh /home/nick/GrubEd.sh', set the drop down box to 'Application', and click the box which says 'Run in terminal'. Set your icon to whatever, and click ok. Then I just dragged my newly created launcher onto my top Gnome Panel. Left click, and when the terminal pops up, just enter your password normally. Once you exit the script, the terminal will automatically close.

---

### Post by nickpaton on 2006-08-04
Obvious really!! Worked perfectly.

Thanks & take care - Nick

---

### Post by Tomosaur on 2006-08-05
New, more poweful, updated version ready for download. First post contains list of changes and current features.

---

### Post by Thund3rstruck on 2006-08-05
> **Thund3rstruck said:**
> It would be great if the script parsed the items in menu.lst (with RegEx) and provided the list in a checkedListView or something. 

Update: Thanks for the edit! Much more effective now

---

### Post by Tomosaur on 2006-08-06
Sorry for rebumping but I had to update again - there was a possible conflict with another program, so I caught that and fixed it. If you're getting weird behaviour, I would recommend you delete your current version and download the latest. This is mostly an optimisation update, no new features this time. For anyone editing this script for their own needs, certain things in the program have been re-written and a few extra (mostly cosmetic) functions added. The changelog above should explain a bit more.

Again, nothing really new added this time, just a few alterations to the code. The help file has also been renamed to something a little more GrubEd specific, to help with a problem I'm currently experience myself (but which isn't relevant if you follow the installation instructions above).

---

### Post by Tomosaur on 2006-08-09
NEW UPDATE: 09 August 06:

Changelog:
```

#10 August '06
#Added a quick check for /boot/grub/
#	--NOTE--On ubuntuforums.org, lots of people seem to be playing around with multiple installs of grub
#		While not wanting to cripple functionality, I don't want to be held responsible for them messing
#		their system up. Now, the script will check for /boot/grub/, and if it's not present, exits.
#		I have no idea what the repurcussions of multiple /boot/grub/ directories is, and I don't particularly
#		want to find out.
#Removed all reference to the re-order menu feature in the code, but kept a version back which includes it.
#	--NOTE--I see no reason why anyone would want to do this. The problem is not only in implementing it, but
#	        the changes just simply will not last if you use any of the other options.
#Added an 'installer'. It copies GrubEd to /usr/bin, and makes a documentation directory at /usr/share/doc/grubed.
#Included an example Launcher. Paste it onto your desktop/panel/whatever to use it.
#Made an 'uninstaller'. It will live in /usr/share/doc/grubed/.
#	--NOTE--Usage is 'sudo /usr/share/doc/grubed/uninstall'

```

Completely remove your current version before using this, installation and usage is significantly different in this version.

Once installed, you can delete the initial folder.

The download includes a launcher which you can copy to your desktop or panel, since quite a few people have been having trouble using shortcuts to use GrubEd.

---

### Post by loserboy on 2006-08-11
nifty, thanks for showing me this, howto is easy to follow...even for me  :)

---

### Post by Uncle Spellbinder on 2006-08-11
> INSTALLATION:

From the terminal, cd to the directory this help file is in, and type:
sudo ./install
Installation from then on is automatic.


Please forgive the ignorance of the following question. How do I "cd to the directory"?  :oops:

---

### Post by Tomosaur on 2006-08-11
When you open a terminal, you will begin in your home directory. Let's say your user name is 'spellbinder', then your home directory would be:
/home/spellbinder/

Now, let's say when you unzipped the file, it created a folder in /home/spellbinder/Desktop/GrubEd

In the terminal, you would type the following command:
```

cd ./Desktop/GrubEd

```

The dot just means 'here', so quite literally, that command says 'start here, go to Desktop, go to GrubEd'.

When you're in the GrubEd folder, you would type 'sudo ./install' and everything should work from there :)

cd basically just means 'Change Directory'.

---

### Post by Uncle Spellbinder on 2006-08-11
@ Tomosaur

Been using Ubuntu for nearly 8 months. I can't believe I've never needed that command (hence my embarrassing question).  

Thanks. Worked well. :D

---

### Post by Tomosaur on 2006-08-11
Haha no worries, everyone's gotta learn somehow :P

---

### Post by Uncle Spellbinder on 2006-08-11
This is quite nice. Backed everything up then changed colors. And as I've not logged on to Windows in nearly a month, changed the default OS to Ubuntu. 

Now, If there were something as easy as this script for the boot screen, I'd be in Linux heaven. :)

---

### Post by Tomosaur on 2006-08-11
Hehe, well, we'll see. I don't know much about editing the boot screen, but right now I'm working on letting people select a grub splash image (and I even included my own, aren't I nice :P). Hopefully it'll be ready for download later tonight, just trying to get one last problem fixed.

---

### Post by loserboy on 2006-08-11
no kidding, maybe i'm retarded but no matter what i try for usplash i can't get it to work..

---

### Post by Uncle Spellbinder on 2006-08-11
> **Tomosaur said:**
> ...I'm working on letting people select a grub splash image (and I even included my own, aren't I nice :P). Hopefully it'll be ready for download later tonight, just trying to get one last problem fixed.

Yeah! Closer and closer to "Linux Heaven". :D

---

### Post by GavinX on 2006-08-11
> **Uncle Spellbinder said:**
> Yeah! Closer and closer to "Linux Heaven". :D
Ditto! =D>

---

### Post by Tomosaur on 2006-08-11
Roight, that was quicker than I'd though :D

[Here's the update](http://www.csc.liv.ac.uk/~cs5tjh/GrubEd/GrubEd.zip)

Here's the changelog:
```

#11 August '06
#Added ability to fiddle with splash screen!
#	--NOTE--A few things. Images must be 640x480, 14 colours ONLY, and in .xpm.gz format.
#		GrubEd, however, can only check the file format. You need to take care of the
#		size and colours yourself.
#		Custom colours and splash images can be fiddly to get working together properly.
#		I personally prefer to use just one or the other, but it's up to you. Go nuts.
#		Like the custom colours, this spans several functions, so I've commented them to
#		Make them stand out if you want to mess with them.

```

Installation is exactly the same, you don't need to remove your existing version if you have used the install script before, this update should just overwrite it. If you're still using an old version (before 10 August), you should completely remove it before updating this one.

Updating the first page.....NOW

---

### Post by loserboy on 2006-08-11
update works perfect,  just in case you didnt know

---

### Post by Uncle Spellbinder on 2006-08-11
"Failed to read grub image. press any key to continue."

Custom Colours disabled. Do I need to place the image you provided in the /boot/grub folder?

---

### Post by Uncle Spellbinder on 2006-08-11
Got it! I placed the *images* folder you provided in */boot/grub*. Works *PERFECTLY*!

Thanks. =D>

---

### Post by Uncle Spellbinder on 2006-08-11
Nevermind.

---

### Post by Tomosaur on 2006-08-11
Woops, there was a tiny bug in the installer, fixed now :P

---

### Post by loserboy on 2006-08-11
hey have you thought about doing version numbers :)

---

### Post by Tomosaur on 2006-08-12
I had thought of it, but there doesn't seem much point. I'll look into that usplash thing (or whatever it's called). You want to be able to change the splash you see on the loading screen, right? (The one where it says 'Ubuntu' and has a progress bar?)

---

### Post by loserboy on 2006-08-12
> the splash you see on the loading screen, right?

yea exactly, theres stuff out there..but i can't seem to make it work

initially though i said that because i thought when you said grub splash you meant the boot splash...my misunderstanding

---

### Post by Tomosaur on 2006-08-12
Hmm, changing the usplash is a little more complicated than I expected it to be. I have an idea to extend GrubEd to be more of a general configurator (basically, just put a new menu as the main, and have people select GrubEd to configure GRUB, or a different option to configure something else). I'm gonna lurk around a bit and see what people are having problems with.

The problems with changing the usplash are:
1) I don't understand the actual requirements for a usplash image, and so can't throw one together myself to test it. If anyone can explain the requirements in more detail than are in the Ubuntu wiki, I'd be very grateful.
2) I'm wary of implementing anything which will edit a user's system at kernel-level, which seems to be a requirement for changing the usplash. It could get dangerous, you see. I have a laptop I guess I could mess around with different kernels and dodgy usplash names, so it's not completely out of the realm of possibility, but it will likely take a bit longer to get any release of the script with usplash editing options.
3) The way a usplash works will be changing when Edgy is released, according to some stuff I found floating on the internets. I'll have to poke around and see if usplash images will port properly to Edgy, and if not, figure out a way round it.

---

### Post by loserboy on 2006-08-12
well.... theres [this]("http://www.ubuntuforums.org/showthread.php?t=82835")

anyway i'm happy as ever with grubEd the way it is (I hate waiting on the stupid os selection)

---

### Post by Tomosaur on 2006-08-12
Cheers for the link, that's more useful than the wiki :P

---

### Post by PingunZ on 2006-08-12
Does it have support for [gfxboot]("http://ubuntuforums.org/showthread.php?t=179540") ?

---

### Post by Tomosaur on 2006-08-12
EDIT: Did a search for gfxboot.

Nope, I'm afraid this is just completely different. It uses the default grub which comes with Ubuntu. I may look into a bit more and see if anything is possible, but as it is now, this script will not give any gfxboot specific editing methods. It looks as though gfxboot uses /boot/grub/menu.lst, so maybe this will stll work if you're using gfxboot, but I have had no experience with gfxboot myself, so I don't really know.

---

### Post by MyBigToe on 2006-08-12
im getting an error when trying to insall

```
andrewa@aroom2-desktop:~/Desktop/GrubEd$ ./install
ls: /usr/share/doc/grubed/: No such file or directory
ls: /boot/grub/images/: No such file or directory
Installing GrubEd to /usr/bin/ ...
install: cannot create regular file `/usr/bin/GrubEd': Permission denied
Done
Setting up splash image...
Making image directory at /boot/grub/images ...
mkdir: cannot create directory `/boot/grub/images/': Permission denied
cp: target `/boot/grub/images/' is not a directory: No such file or directory
Done.
Setting up documentation...
Making documentation directory at /usr/share/doc/grubed/ ...
mkdir: cannot create directory `/usr/share/doc/grubed/': Permission denied
Done.
Copying Documentation and uninstall script.
install: target `/usr/share/doc/grubed/' is not a directory: No such file or directory
install: target `/usr/share/doc/grubed/' is not a directory: No such file or directory
install: target `/usr/share/doc/grubed/' is not a directory: No such file or directory
install: target `/usr/share/doc/grubed/' is not a directory: No such file or directory
install: target `/usr/share/doc/grubed/' is not a directory: No such file or directory
Install completed successfully! Type 'gksudo GrubEd' to begin using GrubEd.
There is a Launcher file which you can copy to your Desktop or Gnome panel in the same directory as this script.

```

---

### Post by Tomosaur on 2006-08-12
You need to run the install script as sudo. I actually cheated with the install script, even if it fails you get a success message, sorry about that :P

Anyway, use the sudo command to install, thus:
```

sudo ./install

```

---

### Post by MyBigToe on 2006-08-12
awesome, works now.

Thankyou very much!

---

### Post by pierrem-m on 2006-08-13
G'day Folks!

A great little utility which makes selecting which kernel to boot much easier!

And I like the idea of a splash script but I've struck a problem with it.

When I set the image to show I lose my colours. I go back to white letters in a black rectangle with the splash image behind the rectangle and, naturally, no highlighting.

Any ideas?

Also, is it possible to edit Grub so that it shows which kernel is which? (i.e. the distro name in backets). 

I have Ubuntu, Kubuntu, Edubuntu and Xubuntu all on the one HDD and, whilst I've noted down which hda is which it'd really nice to have the distro names listed next to the individual kernels.

I'll be away until Fri with (SOB!) no Internet access so please excuse any lack of reply to replies.

Keep up the good work!

Regards

Peter

---

### Post by Tomosaur on 2006-08-13
Unfortunately, you can't get a splash image and custom colours to play nicely together. It's a GRUB problem rather than anything wrong with the script, so you either need to put up with it, or just use one or the other.

As for your kernel names, it should automatically list the actual distrobution, followed by the kernel version, eg:

Ubuntu, kernel 2.6.15-26-386

However, the menu item names are arbitrary. You could call it 'I LOVE LINUX OMG', and as long as you specified the other options, it would work perfectly fine. Currently, the only way to do that kind of thing using this script is to use the 'Direct Edit' option. Scroll down to where you'll find all of the actual menu items. The line which says 'title' is fine to edit to whatever you like. Just don't use any bizarre characters. You must, however, keep the word 'title' :P.

---

### Post by bulldog on 2006-08-13
> **Uncle Spellbinder said:**
> This is quite nice. Backed everything up then changed colors. And as I've not logged on to Windows in nearly a month, changed the default OS to Ubuntu. 

Now, If there were something as easy as this script for the boot screen, I'd be in Linux heaven. :)

Maybe you should have a look at this one?
[http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper](http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper)

It's very easy to do and I use it myself for some time now.
The only thing is,when you get another kernel,you should place "vga=792" at the end of the new kernel line because when grub is updated it removes it.

---

### Post by Uncle Spellbinder on 2006-08-13
> **bulldog said:**
> Maybe you should have a look at this one?
[http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper](http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper)

It's very easy to do and I use it myself for some time now.
The only thing is,when you get another kernel,you should place "vga=792" at the end of the new kernel line because when grub is updated it removes it.

It's good, I'm just no fan of Ubuntu brown/orange. My main reason for using *xorg-aiglx + compiz (Quinn packages)* was to get as far away from brown/orange as possible.

---

### Post by fazofazo on 2006-08-13
good,thank you

---

### Post by Tomosaur on 2006-08-15
ARGH! I just realised there was another (pretty bad) bug in the installer, which the last bug-fix created. For a lot of people, this would have meant the installer didn't work at all.

Anyway, it's fixed now. Sorry if it caused any problems!

---

### Post by kinematic on 2006-08-20
this would be a great addition to other distro's......gotta love the gpl ;)

---

### Post by Tomosaur on 2006-08-20
Technically it's not really GPLd. The page I made about it: [Click on GrubEd](http://www.csc.liv.ac.uk/~cs5tjh/) does have a 'kind of' licence, which essentially just says it's free and you can modify it etc, but it's not the GPL, mostly because I can't be bothered going through the GPL with a fine tooth-comb myself :P

---

### Post by kinematic on 2006-08-20
so then you won't mind if i try to get it working on pclinuxos ;)

---

### Post by Tomosaur on 2006-08-20
Nope, feel free, just keep the comments at the top intact plz :)

---

### Post by kinematic on 2006-08-20
will do.
looked over the script and it looks like it should work on pclos.....i'll have a go at it later this week.
but anyway...thnx,it makes it faster to edit grub.....well done :D

---

### Post by tokez on 2006-08-20
this is perfect since I have been having some problems with my grub recently.

been trying to get xp to boot from first harddrive secondary partition to no avail.

loaded the script and selected xp as default, and the progress bar doesnt show ANYTHING :( look into it, perhaps it has trouble with non-first partiton?

---

### Post by Tomosaur on 2006-08-21
Hmmm, odd. The script works simply by counting the number of menu items, rather than scanning your hard drives, so your problem may well be something to do with your menu.lst file. Have you tried choosing 'Direct Edit'? If you scroll down, you should be able to see the actual menu items. If you can't fix it, or don't know what to do, just paste it up here and I'll have a look over it.

---

### Post by neko18 on 2006-08-21
Thanks for the script, It works well for me.

---

### Post by beameup on 2006-08-22
Tomosaur. Nice work. Thanks a bunch. 

IMHO: Need to get this into Edgy somehow.

---

### Post by Sam Liu on 2006-08-25
thanks tomasaur for this script!

---

### Post by Crosbie on 2006-08-26
I'm having a bit of trouble with choosing the default OS to load.  After selecting my OS choice there's no confirmation message or option to go back to tasks; and when I check, via direct edit, the change has failed.  I thought it might be to do with changing the number of kernels available first, but I tried again later and still the same behaviour.  Any idea what's up here?

---

### Post by Tomosaur on 2006-08-26
Hmmm. The script makes use of vi to write to menu.lst. Do you have vi installed?

One thing which MAY cause a problem (although it shouldn't really) would be trying to alter the default OS before you ran 'update-grub'. Perhaps if you try running 'update-grub' before you try to change the default OS it would work. I'll have a look through the code now and see if theres anything obvious, but as far as I'm aware there's nothing that should be causing this - unless perhaps you managed to get the script running without root privileges (which again, should be impossible provided you didn't alter the script).

---

### Post by loserboy on 2006-08-26
hey i'm having problems changing my default boot, and disabling memtest.
i'm pretty sure it has something to do with me recently installing kubuntu on  another partition.  any suggestions? lemme know if you need menu.lst or anything.

---

### Post by Tomosaur on 2006-08-26
Yeah, throw the menu.lst my way please. If you have two /boot/grub/menu.lst files (one on each partition), send them both please, I'll see if anything obvious jumps out.

---

### Post by Toxicity999 on 2006-08-26
Fancy! I won't lie though the actual UI could be way more efficient choosing an option like that is just a bit annoying, now I know Zenity is limited for sure. But, until we get a nice out-of-the-box tool to mess with grub with a flashy frontend this surely is doable.

---

### Post by Crosbie on 2006-08-27
> **Tomosaur said:**
> Hmmm. The script makes use of vi to write to menu.lst. Do you have vi installed?

One thing which MAY cause a problem (although it shouldn't really) would be trying to alter the default OS before you ran 'update-grub'. Perhaps if you try running 'update-grub' before you try to change the default OS it would work. I'll have a look through the code now and see if theres anything obvious, but as far as I'm aware there's nothing that should be causing this - unless perhaps you managed to get the script running without root privileges (which again, should be impossible provided you didn't alter the script).

Vi seems to work from a terminal, and I see that the launcher uses gksudo so that ought to give me root... interestingly I tried using another little script which was also failing, until I figured out that I needed to sudo it. :)

I haven't tried running 'update-grub' first off (without making any changes) - but would this be necessary anyway?

Other operations seem to work fine, btw - eg, reducing the number of kernels, once I'd run update-grub.

---

### Post by Tomosaur on 2006-08-27
Hmmmm. I've found something which could theoretically be causing a problem, but from the looks of it, it wouldn't be causing THIS problem :P

Anyway, would you be so kind as to paste your menu.lst file here for me? It's in /boot/grub/ if you can't find it.

---

### Post by Crosbie on 2006-08-27
OK, here we go:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default   6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdc2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

The only possible irregular thing AFAICS might be the two very similar XP entries at the end.

---

### Post by Tomosaur on 2006-08-27
Hmm, that's even more confusing. The thing which I thought may be causing the problem was the 'Other Operating Systems' menu item. The script simply assumes that that line is there - removing it could cause an error. I'd overlooked it completely before now. In any case, I really can't see why this problem is occuring, particularly if all of the other editing methods are working too. Did you download the script from the link on the FP of this thread? I know there's a few websites that are mirroring it, but I don't know which version they're using or anything.

---

### Post by Crosbie on 2006-08-27
From this thread.  

Just re-checked, and I still have the same issue.  Gksudo box comes up as per usual.  The other script reports the default unchanged.

Can I run it from a terminal and get diagnostics of some sort?

Okay, done that:

```
/usr/bin/GrubEd: line 72: 7
8 - 1 : syntax error in expression (error token is "8 - 1 ")

```

Hope that helps.  Here's the function it points to:

```
list_menu(){
#List a menu of installed operating systems. Double click to set default.
grep ^title $G_MENU | grep -v "Other operating systems" > avail && vi -e -c %s/^title/\ / -c :%le0 -c :wq! avail
OS_SEL=$(cat avail | zenity --list --width=400 --height=200 --title="Available Menu Items" --column "Operating Systems" --text="Choose an OS:")
if [ -n "$OS_SEL" ]
then
  MENU_ITEM=$(( $(grep ^title $G_MENU | grep -n $OS_SEL$ | grep -o ^[[:digit:]]*) - 1 ))
  DEF_LINE=$(grep  -n ^default $G_MENU | grep -o ^[[:digit:]]*)
  DEF_CURR=$(grep ^default $G_MENU | grep -o [[:digit:]]*$)
  vi -e -c "$DEF_LINE"s/"$DEF_CURR"/"$MENU_ITEM" $G_MENU -c :wq | zenity --progress --auto-close --title="New Default" --text="Progress:"
  success
fi
rm avail
}
```

Line 72 is the line staring MENU_ITEM=$...

---

### Post by Tomosaur on 2006-08-27
Right so it's just a numeric issue then. Replace that function with this:
```

list_menu(){
#List a menu of installed operating systems. Double click to set default.
grep ^title $G_MENU | grep -v "Other operating systems" > avail && vi -e -c %s/^title/\ / -c :%le0 -c :wq! avail
OS_SEL=$(cat avail | zenity --list --width=400 --height=200 --title="Available Menu Items" --column "Operating Systems" --text="Choose an OS:")
if [ -n "$OS_SEL" ]
then
  MENU_ITEM=$(grep ^title $G_MENU | grep -n $OS_SEL$ | grep -o ^[[:digit:]]*)
  let "MENU_ITEM = $MENU_ITEM - 1"
  DEF_LINE=$(grep  -n ^default $G_MENU | grep -o ^[[:digit:]]*)
  DEF_CURR=$(grep ^default $G_MENU | grep -o [[:digit:]]*$)
  vi -e -c "$DEF_LINE"s/"$DEF_CURR"/"$MENU_ITEM" $G_MENU -c :wq | zenity --progress --auto-close --title="New Default" --text="Progress:"
  success
fi
rm avail
}

```
That should work for you!

---

### Post by Crosbie on 2006-08-27
Hm, no, same error I'm afraid... checked that the script has saved with the replacement code, and AFAICT it has.

(Thanks for trying though - hope you can keep it up! :) )

---

### Post by Tomosaur on 2006-08-27
Really? Did you completely replace the function with the one I just posted?

---

### Post by Crosbie on 2006-08-27
> **Tomosaur said:**
> Really? Did you completely replace the function with the one I just posted?

Yep, the entire list_menu function from line 66 to line 80.  There's an extra line 73, right?  That's the only difference I can see.

---

### Post by Tomosaur on 2006-08-27
Well there's a slight difference in line 72 but yeah, basically. I really don't understand what's happening here. Both versions of that function have worked / are working perfectly for me. I just ran a debugging trace thingy and all of the numerical stuff is working out alright for me. Do you have problems with any other programs / scripts?

---

### Post by Crosbie on 2006-08-27
> **Tomosaur said:**
> Well there's a slight difference in line 72 but yeah, basically. I really don't understand what's happening here. Both versions of that function have worked / are working perfectly for me. I just ran a debugging trace thingy and all of the numerical stuff is working out alright for me. Do you have problems with any other programs / scripts?

Okay, I was being a bit of an idiot and working on the version in the GrubEd folder within my /Home.  Just applied the change to the usr/bin version and it now apparently works.  Hurrah!  It does give this error message, however:

```
/usr/bin/GrubEd: line 73: let: MENU_ITEM = 7
8 - 1: syntax error in expression (error token is "8 - 1")

```

---

### Post by Tomosaur on 2006-08-27
Ok, try changing line 73 (the line with 'let' to:
```

let MENU_ITEM=$MENU_ITEM-1

```
Essentially just remove the spaces. See if you still get the 8-1 error.

---

### Post by Crosbie on 2006-08-27
Okay, cool - needed to remove quotes too (or perhaps instead).  No error message now.  Thanks very much for your help! :)

For reference, here's the working version of that function:

```
list_menu(){
#List a menu of installed operating systems. Double click to set default.
grep ^title $G_MENU | grep -v "Other operating systems" > avail && vi -e -c %s/^title/\ / -c :%le0 -c :wq! avail
OS_SEL=$(cat avail | zenity --list --width=400 --height=200 --title="Available Menu Items" --column "Operating Systems" --text="Choose an OS:")
if [ -n "$OS_SEL" ]
then
  MENU_ITEM=$(grep ^title $G_MENU | grep -n $OS_SEL$ | grep -o ^[[:digit:]]*)
  let MENU_ITEM=$MENU_ITEM-1
  DEF_LINE=$(grep  -n ^default $G_MENU | grep -o ^[[:digit:]]*)
  DEF_CURR=$(grep ^default $G_MENU | grep -o [[:digit:]]*$)
  vi -e -c "$DEF_LINE"s/"$DEF_CURR"/"$MENU_ITEM" $G_MENU -c :wq | zenity --progress --auto-close --title="New Default" --text="Progress:"
  success
fi
rm avail
}
```

---

### Post by Tomosaur on 2006-08-27
Awesome, I'll zip it and put it on the front page. Cheers for letting me know there was bug :)

EDIT: Done, fixed version on first page.

---

### Post by loserboy on 2006-08-29
here we go sorry it took so long for reply, i think i see the problem already though, i just dont know how to fix it, my menu.lst for kubuntu and ubuntu are different, maybe cuz on dif hard drive? anyway if thats true i would much rather use the original grub cuz kubuntu is just for playing around with.


```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb5 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb5 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb5 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb5 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

Edit: oh yea this the list i see from kubuntu

---

### Post by Tomosaur on 2006-08-29
Try changing the 'groot' line to
groot=(hd1,4)

---

### Post by loserboy on 2006-08-29
weird, that didn't do anything at all that I can tell

edit: do i have to run update-grub somehow?

---

### Post by Tomosaur on 2006-08-29
Maybe, but I don't think it's absolutely necessary. Couldn't hurt to try though. Make sure both menu.lst files have their groot lines pointing at the partition where GrubEd is, otherwise your changes will probably be nullified.

---

### Post by loserboy on 2006-08-29
hmm....  
i didnt run GrubEd again yet, was changing the groot on the menu.lst just suppose to allow GrubEd to work?
which also brings the question...how many grubs do i have installed lol

---

### Post by Tomosaur on 2006-08-29
Unless you set Grub up in a specific way, you'll still only have 1 Grub installed (on your MBR). However, you have two grub folders, both containing different configurations. You need to make both configurations (or menu.lst files) point to the partition on which GrubEd lives, because GrubEd can only see the menu.lst file on the partition it is on. Grub needs to know which configuration file to use, so if you have two menu.lst files pointing the grub root (groot) as two different places - well, you can imagine why it's getting confused. If it's simply a problem with GrubEd not actually making the changes (ie, you tell it to change the default to 4, but it stays on 2), then download the latest version from the first page of the thread and try that.

---

### Post by loserboy on 2006-08-29
i'm at work now and have have to test it later, but i doubt its GrubEd, cuz everything worked till i installed kubuntu so i guess it just changed the path or whatever.  thanks for the help

also just to confirm what your saying, if this goes properly i should be able to use GrubEd from gnome even though kubuntu is on a dif hdd, right as long i did what you said?

sorry for all this i'm just slightly nervous screwing with grub.

---

### Post by Tomosaur on 2006-08-29
GrubEd will only alter the menu.lst file of the partition it is installed on. If you have Ubuntu and Kubuntu installed, then using it on Ubuntu will only alter the menu.lst on the Ubuntu partition, and using it on Kubuntu will only alter the menu.lst on the Kubuntu partition.

---

### Post by loserboy on 2006-08-29
ok then that must be whats wrong because nothing i do in ubuntu is effecting the grub that i see at bootup, like GrubEd or direct edit of menu.lst

should i just reinstall grub from ubuntu?

btw this is the men.lst from ubuntu

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color blue/black light-blue/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sdb5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb5 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by Tomosaur on 2006-08-30
Weird - Kubuntu doesn't show up on your Ubuntu menu.lst. You may want to run 'sudo update-grub' to see if it adds it properly.

As long as your menu.lst file is there - GrubEd should be able to alter it - regardless of whether or not Grub then notices your changes. If GrubEd isn't changing anything at all - then that's a bit more confusing. Do you have a 'weird' setup? Is your /boot on a different partition or something like that?

---

### Post by loserboy on 2006-08-30
good question ill look when i get home, i really don't know. I use the standard install for ubuntu and kubuntu, so i would think it would b at default, as far as partitions go ubuntu has its own hd with normal partitions for /, home and swap.

kubuntu is on a hd with xp, but if i recall is default as well just root and swap.

edit: ok i updated grub, no dif.
im just gonna reinstall grub and see what happens, hey if i screw something up it won't be the worst thing ive ever done

---

### Post by mothafukaa on 2006-09-26
ok, so , im pretty much a noob 
well, im a complete noob when it comes to linux, i JUST installed linux on my machine for the first time
well, i dont know how to install 
all i know is my  grubed is on my desktop, and i dont get what it means by "From the terminal, cd to the directory this help file is in, and type:
sudo ./install'
what i dotn get is the "cd to the directory"
plz help help

---

### Post by Tomosaur on 2006-09-27
The term 'cd' is a command you can type into the terminal to move between different directories/folders on your hard drive. When you load up a terminal, it will start in your home directory. Since grubed is on your desktop, you'd type this:

cd Desktop/GrubEd/

And it SHOULD take you to the GrubEd folder. The cd command is one of the main terminal functions, you should learn how to use it.

---

### Post by mssever on 2006-09-27
> **mothafukaa said:**
> ok, so , im pretty much a noob 
well, im a complete noob when it comes to linux, i JUST installed linux on my machine for the first time
well, i dont know how to install 
all i know is my  grubed is on my desktop, and i dont get what it means by "From the terminal, cd to the directory this help file is in, and type:
sudo ./install'
what i dotn get is the "cd to the directory"
plz help help

You might consider reading [http://linuxcommand.org](http://linuxcommand.org) for more info.

---

### Post by uk_sphinx on 2006-09-28
thnx i only just got it.
apologize if you sent it yesterday.
cheers

---

### Post by rbraswel on 2006-09-29
I just got ubuntu and having trouble installing grubed.  I unzipped the zip file and it is on my desktop.  When I got into the terminal to run sudo ./install it doesnt recognize the path and if I double-click the install file in the Grubed folder it ask to run but it does nothing.  Can anyone point me in the right direction?

---

### Post by Tomosaur on 2006-09-29
The ./install is relative to where you are. The instructions assume you are within the GrubEd directory, but when you first open a terminal, it will put you in your home directory. Here are the steps you need to take to install GrubEd in your situation:
```

Open a terminal:
cd Desktop/GrubEd
sudo ./install

```

---

### Post by munozm on 2006-10-19
Hello:

I installed the script and all I changed was "Change the number of kernels Grub shows" to 3 I believe.  Now when I bootup, I get to grub but nothing is listed.  I try and type boot but it just gives me an error message, I believe it's looking for a file name.  How do I boot back up so I can restore the grub?  I did make a backup with the script before making a change.

Thanks for your help.

---

### Post by mssever on 2006-10-19
You can boot from the Live CD, mount your regular partition, and restore from there.

---

### Post by Tomosaur on 2006-10-19
**EDIT: BUG FIXED, fixed version on first page.**

---

### Post by munozm on 2006-10-19
mssever:  Thanks for the response.  I booted up on live cd.  I was able to mount the partition.  I tried to run the script again but it mentioned there was no grub.  I was just trying to run the script to restore the original settings.  Is there anyway to restore the menu.lst?  Or recreate it so I can boot up?

---

### Post by munozm on 2006-10-20
With a little further investigation, I found the backup file in /boot/grub (makes sense).  I just renamed the backup file and all is well.  Thanks.

---

### Post by mssever on 2006-10-20
[LEFT]**[FONT=Arial Black]Bug report:[/FONT]**
[/LEFT]
 
The function list_menu() beginning on line 60 could potentially clobber a file. It could also leave a file hanging around if GrubEd gets killed without having a chance to clean up after itself. The problem is the redirection to avail. If a file named avail already exists, it will be overwritten, then deleted.

I suggest inserting the following before line 62: ```
avail="/tmp/GrubEd-avail-$(date +"%Y%m%d%H%M%S%N")"
``` and replacing all subsequent occurances of avail with $avail. Using this filename will accomplish several things: 1) it's canonical to put temp files in /tmp. 2) If GrubEd dies an untimely death, the residual file will automatically deleted on reboot (when /tmp is cleaned). 3) It's extremely unlikely that any files will get clobbered. (A paranoid version would also make sure that the file doesn't exist before writing it.) 4) Because the filename includes a timestamp, it prevents symlink attacks.

Perhaps it would also be best to use absolute paths in $G_MENU and friends (line 490 *ff*)? That would obviate the need to cd to the proper directory, and be a little more robust, IMHO.

I also suggest changing line 493 to ```
P_FILE="/tmp/GrubEd-patch-$(date +"%Y%m%d%H%M%S%N")"
``` for the same reasons as stated above.

---

### Post by Tomosaur on 2006-10-20
Thanks for the suggestions, I'll take it on board. The code is pretty sloppy, since this started out as a one-off script for myself which I just kept adding to. I've slowly worked through trying to clean stuff up, but I'm pretty busy at the moment (hence the drop in updates). I'll try and iron out more of the issues soon.

---

### Post by Tomosaur on 2006-10-23
Alright, made above reccomendations into latest version. Thanks for pointing them out, mssever :)

Also removed junk comments.

---

### Post by fatdaddy on 2006-10-24
Tomosaur

Thanks for the great program.

Just updated my 6.06 to 6.1 and the update had set the grub to .i386 rather than the generic (k7smp) kernel as the default boot.  Knowing just enough to destroy my install your program probably saved me hours of flailing around.

So I did not know it you had been updated that currently your program works with 6.1 beta/rc or whatever it is today, but it does and I know because i rebooted and checked the changes I had made, time and kernel and both were applied properly.

---

### Post by VividHazE on 2006-11-05
Great script Tomosaur! It worked for me perfectly in Ubuntu 6.10, I thought I was going to have to try and alter the grub file manually, loads of cool features i never would have worked out how to do too. :D Thanks a bunch, can't wait for your python version with more features!

---

### Post by bryanb on 2006-11-16
Worked like a charm! Thanks a bunch!! :)

---

### Post by japc126 on 2006-11-17
When i use the "gksudo GrubEd" command, it asks me for my password. I enter it, something seems to be loading and then... nothing

I decided to enter it again and it didn't ask for a password, the terminal said: "sudo: GrubEd: command not found"

please help

---

### Post by Tomosaur on 2006-11-18
japc126, I've PMd you with some instructions on how to fix this. One of them should work :)

---

### Post by annabozhinova on 2006-11-21
hallo.
i cannot install grubed,
zenity is allready installed ,
after my password-nothing happens,pasting the "launch grubed"icon onto the desktop-nothing,
what i do wrong??
is it GrubEd or grubed??

---

### Post by Tomosaur on 2006-11-21
It's 'GrubEd', so the command you type, or use in a launcher is:
```

gksudo GrubEd

```

---

### Post by WIVO_Riley on 2006-11-29
Tomasaur- you are DA MAN!!

I just installed Ubuntu tonight- first Linux try, and I'm diggin it big time.  The grub bothered me- my system is a core 2 with XP Pro on it for the wife and kids, and I dual OS'd it today, and wanted to change the grub so it's easier on them (until they transition over, lol)

Many thanks to you- **NOTE to ALL** if you read and read and read, the instructions are spot on- start at the last page and work back a few.

Linux ultra n00b  --- for now ;)

Riley

---

### Post by damvcoool on 2006-12-04
Just one question.

Why no to make this project part of ubuntu?
or at least on the repositories, or making a .deb and posting it here.

---

### Post by birdie101 on 2006-12-11
Hi Tomasour

I'm having the same issues as Japc126 with my install of Dapper.

Any chance of posting the instructions you PM'd Japc126?

Thanks heaps
Luke

---

### Post by Tomosaur on 2006-12-11
Here's what I sent, nothing too advanced really:

[QUOTE=Tomosaur]
If GrubEd did not install properly, then this problem can occur, but there's a few things you can do.

1) Open up a terminal and type (case-sensitive):
```

ls /usr/bin/GrubEd

```

If it says file not found, then GrubEd was not installed. If this is the case, make sure you extracted the GrubEd zip file. If you did, there should be a GrubEd folder. Change directory into that folder (cd GrubEd) and type:
```

sudo ./install

```

If this doesn't work, you may need to set permissions on the install script:
```

chmod 755 ./install

```

and then run it (sudo ./install).

The installation procedure should let you know if GrubEd installs successfully.

2)If GrubEd is installed, but your machine still tells you that it can't be found, then this suggests that your PATH isn't set up right. To fix this, type this in the terminal:
```

export PATH=$PATH:/usr/bin

```

Then try running GrubEd again. If this fixed your problem, you'll need to add the above line to your .bashrc file, which is in your home directory. The dot in front of it means it is hidden, so to open the file you have to type:
```

sudo nano ~/.bashrc

```

and paste the export command into it at the bottom.

One of the above should solve your problem. If neither do, then you may have something more seriously wrong happening.[/QUOTE]

Try that, then if it still doesn't work, just post back here :)

---

### Post by misGnomer on 2006-12-12
Is GrubED compatible with [Super GRUB](http://supergrub.forjamari.linex.org/)?

I suppose the menu.lst editing works the same way but updating GRUB itself probably not as Super would be replaced by the standard release. Any other issues to expect?

---

### Post by Tomosaur on 2006-12-12
I wouldn't recommend it myself. I've never bothered using super GRUB, and didn't have it in mind when writing GrubEd. Feel free to try it though, would be interesting to see the results.

---

### Post by firer_av on 2006-12-14
Great Script.Really Very useful and your work is appreciable:) .Thanks

Bye

-AV

---

### Post by adrian15 on 2006-12-18
> **misGnomer said:**
> Is GrubED compatible with [Super GRUB](http://supergrub.forjamari.linex.org/)?

I suppose the menu.lst editing works the same way but updating GRUB itself probably not as Super would be replaced by the standard release. Any other issues to expect?

Hello. What do you mean by is GrubED is compatible with Super GRUB ?

GrubED is an editor of menu.lst of your own computer. Super Grub Disk does not create or modify any menu.lst. It only generates some sort of on-the-fly menu.lst from the cdrom when you run it.

When you reinstall grub to the mbr from SGD you do not install SGD's grub but your own's grub.

What was you idea though? It may be interesting.
Maybe you have to managed to install supergrub's grub into your hard disk?

Hello to GrubED developer ;) Tornosaur.

adrian15

---

### Post by darth logan on 2006-12-28
Hey Tomosaur!

Great utility, works like a charm - just wanted to give props!

- Logan

---

### Post by Frak on 2006-12-29
Great job Tomosaur!

---

### Post by dhaupin on 2007-01-15
Thanks bro

---

### Post by maddog39 on 2007-01-22
Where is the source code for this program. In linux, its pretty much expected to have access to the source code. All of us dont use x86, etc. :/

---

### Post by Tomosaur on 2007-01-23
The source code IS the program, it's a BASH script :/

---

### Post by dave37 on 2007-02-11
Thanks for a great program, have been looking all over for something like this

---

### Post by kngcrntrd on 2007-03-08
Just a quick question...  When the GRUB menu is hidden, how do you switch between OS's?  Great job, by the way!

---

### Post by Frak on 2007-03-08
> **kngcrntrd said:**
> Just a quick question...  When the GRUB menu is hidden, how do you switch between OS's?  Great job, by the way!
Press ESC within 3 seconds of the GRUB prompt.

---

### Post by kngcrntrd on 2007-03-08
Nevermind.... just press escape to access GRUB menu... should have tried it out before I asked... sorry

---

### Post by Beatsake on 2007-03-13
What does this mean?

I type gksudo GrubEd  and get this.  Is my X Broken? I tried to install Beryl Desktop and get similar errors so good chance it's not related to your script I just don't have the knowledge to figure it out.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/bin/GrubEd: line 18: zenity: command not found


Thank you for any responce

---

### Post by Frak on 2007-03-13
> **Beatsake said:**
> What does this mean?

I type gksudo GrubEd  and get this.  Is my X Broken? I tried to install Beryl Desktop and get similar errors so good chance it's not related to your script I just don't have the knowledge to figure it out.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/bin/GrubEd: line 18: zenity: command not found


Thank you for any responce
in the terminal
```
sudo aptitude install zenity
```
Hope that works

---

### Post by Beatsake on 2007-03-17
Thank You Frak I'm not sure what that did it still has X errors but the GrubEd script runs now

---

### Post by Antilavista on 2007-03-26
Worked a treat here. I now have a nice Grub bootscreen.

Thanks Tomosaur

---

### Post by Frak on 2007-03-26
> **Beatsake said:**
> Thank You Frak I'm not sure what that did it still has X errors but the GrubEd script runs now
Oh, yes, I'm sorry, I forgot to respond, forget those Errors. Those errors are just telling you, that you don't have a Toshiba Tablet PC, as they were put in there to make sure that X fit the screen correctly. Don't worry about them.

---

### Post by oliverh on 2007-03-28
I'm a linux noob and am not even running Ubuntu. Two strikes against me.. ;)

So I recently installed PCLOS next to my XP install, and everything worked like a charm. Grub worked great, I'm up and running. Then, I decided I wanted to install another OS from a large fruit company. heh. No problems there. Of course, it doesn't come up in my bootloader. In order to facilitate my not destroying my boot sequence, I read up a bunch on Grub and ran across your script. It looks great... but I'm running KDE. I've tried to search for a way to make it run in KDE and was unable to find a solution. Is this possible without recompiling it?

Anyway, if this can't be done, back to the manual editing plan. :) Thanks,

Oliver

---

### Post by Tomosaur on 2007-03-28
> **oliverh said:**
> I'm a linux noob and am not even running Ubuntu. Two strikes against me.. ;)

So I recently installed PCLOS next to my XP install, and everything worked like a charm. Grub worked great, I'm up and running. Then, I decided I wanted to install another OS from a large fruit company. heh. No problems there. Of course, it doesn't come up in my bootloader. In order to facilitate my not destroying my boot sequence, I read up a bunch on Grub and ran across your script. It looks great... but I'm running KDE. I've tried to search for a way to make it run in KDE and was unable to find a solution. Is this possible without recompiling it?

Anyway, if this can't be done, back to the manual editing plan. :) Thanks,

Oliver

It's a script, no compilation necessary :)

You will need zenity to run it though, and you will need to use whatever the KDE version of gksudo is (I think it's kdesu?). Zenity is available from the repos, but it may download some other gnome libs.

---

### Post by cecilpierce on 2007-04-18
is there anyway to make GrubEd screen size bigger ?

---

### Post by Tomosaur on 2007-04-19
> **cecilpierce said:**
> is there anyway to make GrubEd screen size bigger ?

The GUI for GrubEd is controlled through Zenity, which by default simply restricts itself to the smallest size it needs to be. It's possible there's a size parameter, but I can't remember off the top of my head. If you fancy taking a look at the zenity documentation ('man zenity' in the terminal), you may be able to find something relevant. If you do find something, you can go through the GrubEd script yourself and change the sizes. If you don't feel confident doing that then I'll take a look in a few days and see what can be done. I can't look myself at the moment as I don't have access to my own computer (stuck with Windows for the time being!).

Thanks for the interest :)

---

### Post by You bunt to? on 2007-04-19
> **Tomosaur said:**
> 
The script makes use of zenity, a program which displays dialog boxes. Make sure you have zenity enabled on your system.


As an absolute beginner (to Linux) this is the sort of sentence that really puts me off. Couldn't your
script make a test to see if "zenity" is "enabled" (whatever "enabled" means) ?

---

### Post by Frak on 2007-04-19
In the terminal
```
sudo aptitude install zenity
```

---

### Post by cecilpierce on 2007-04-19
Thanks Tomosaur,
I looked at GrubEd and its over my head what to do. Looked at man page, same thing.
I can strech the screen but the next one goes back to the original size.
Thanks again for the great prg, cant wait for the splash editor !
cecil pierce

---

### Post by mssever on 2007-04-20
> **You bunt to? said:**
> As an absolute beginner (to Linux) this is the sort of sentence that really puts me off. Couldn't your
script make a test to see if "zenity" is "enabled" (whatever "enabled" means) ?

Zenity is installed by default with Ubuntu. Tomosaur, perhaps you could revise your howto to reflect that. The only people who don't have zenity are those who have explicitly removed it. (I suppose that some other distros might not include zenity by default.)

---

### Post by Tomosaur on 2007-04-21
> **mssever said:**
> Zenity is installed by default with Ubuntu. Tomosaur, perhaps you could revise your howto to reflect that. The only people who don't have zenity are those who have explicitly removed it. (I suppose that some other distros might not include zenity by default.)

Thanks for the info, I'll keep it in mind.

Most of you may have noticed that I haven't released any updates to GrubEd for a while now. I've been very busy since just before Christmas last year and haven't really had time to work on anything except uni projects. The python, 'more universal' version is indefinately delayed for the time being for this reason, I just can't spend any time on it at the moment.

You bunt to?:
> 
As an absolute beginner (to Linux) this is the sort of sentence that really puts me off. Couldn't your
script make a test to see if "zenity" is "enabled" (whatever "enabled" means) ?


It's perfectly possible, sure. The problem is in the fact that GrubEd is currently being used on a variety of distributions. The exact method of getting and installing zenity may vary depending on distribution. If you're using Ubuntu (ie, not Kubuntu or Xubuntu), then GrubEd should work fine without any extra setup.

If zenity is not installed on your system (you can check by typing 'dpkg -l zenity' in the terminal, or typing 'zen' and hitting tab twice, then checking the list of programs that is displayed. If zenity is not there, then you need to install it), then you can install it using the command Frak gave (provided you're using an Ubuntu variant). 

If that command returns an error, then you need to install zenity from here:
[http://directory.fsf.org/zenity.html](http://directory.fsf.org/zenity.html)

I'll update the information in the help pages some time this week, though, and try to make the installation process a bit more 'automatic'. Thanks for the interest in GrubEd though :)

---

### Post by Nightmist on 2007-04-23
First of all, I am running Kubuntu and had to do 'sudo apt-get install zenity' to get it to work. I can't recall having had anything to do with Zenity in the past (removing or otherwise).

Secondly, the splash screen was nice, but I get the black square right smack in the middle with all the menu options in. The splash screen can only be seen around the edges where there is nothing going on.

Thirdly, custom colours didn't work. Instead of showing colours, it showed nothing. I had to blindly choose between the options without seeing what I had selected.

Any ideas why this is so?

[EDIT: After removing custom colours the splash screen covered the whole screen, and everything looked dandy! (even if the text was just in black and white) I guess I'll try again at a later date. Now I will hunt for awesome splash screens!]

---

### Post by Tomosaur on 2007-04-23
> **Nightmist said:**
> First of all, I am running Kubuntu and had to do 'sudo apt-get install zenity' to get it to work. I can't recall having had anything to do with Zenity in the past (removing or otherwise).

Zenity makes use of GTK+, so it is not shipped by default with Kubuntu, which uses KDE as it's environment. I will work on getting the installer script to detect zenity and any other dependencies and offer to download and install it, but I have no date penned for the updated version, as I'm pretty busy at the moment.

> 
Secondly, the splash screen was nice, but I get the black square right smack in the middle with all the menu options in. The splash screen can only be seen around the edges where there is nothing going on.
I'm fairly sure this only happens when you try to use custom colours with a splash screen. Grub behaves bizarrely when you enable both, so I'm afraid it's an either/or situation. Just having colours enabled will cause this problem, in my experience (regardless of whether you actually alter the colours it uses) so try disabling colours and seeing if that improves things. The help file should contain a little more information.
> 
Thirdly, custom colours didn't work. Instead of showing colours, it showed nothing. I had to blindly choose between the options without seeing what I had selected.

Any ideas why this is so?

Again, if you have a splash and custom colours at the same time, this kind of thing happens. The behaviour is unpredictable at best, and as it's a grub issue (not a GrubEd issue), there's not much I can do about it I'm afraid, aside from recommend you use either a splash, or custom colours, but not both.

There are other bootloaders you could experiment with which provide more customisation options. For example, you could take a look at [GfxBoot](http://ubuntuforums.org/showthread.php?t=208855)

---

### Post by Nightmist on 2007-04-23
Yeah, I edited my post right as you posted I guess. I found out the same as you, but glad to have it confirmed.

Nice work, by the way. Next thing would be an easier way to edit the various menu options in the Grub menu, but I guess someone already requested that :)

Thanks.

---

### Post by Kaobear on 2007-04-23
A nice and simple script that does exactly what it says it does.  A refreshing thing to be sure.

---

### Post by You bunt to? on 2007-04-23
> **Tomosaur said:**
> 

You bunt to?:


It's perfectly possible, sure. The problem is in the fact that GrubEd is currently being used on a variety of distributions. The exact method of getting and installing zenity may vary depending on distribution. If you're using Ubuntu (ie, not Kubuntu or Xubuntu), then GrubEd should work fine without any extra setup.

If zenity is not installed on your system (you can check by typing 'dpkg -l zenity' in the terminal, or typing 'zen' and hitting tab twice, then checking the list of programs that is displayed. If zenity is not there, then you need to install it), then you can install it using the command Frak gave (provided you're using an Ubuntu variant). 

If that command returns an error, then you need to install zenity from here:
[http://directory.fsf.org/zenity.html](http://directory.fsf.org/zenity.html)

I'll update the information in the help pages some time this week, though, and try to make the installation process a bit more 'automatic'. Thanks for the interest in GrubEd though :)

Thanks! Your program worked like a dream!

---

### Post by bobbymack on 2007-04-29
Friggin' FANTASTIC!
Too easy...
Thank you!
=D>

---

### Post by Tomosaur on 2007-04-29
> **bobbymack said:**
> Friggin' FANTASTIC!
Too easy...
Thank you!
=D>

Thanks for the kind words :)

---

### Post by Ubunteador on 2007-05-02
I dunno if you are still working with GrubEd (since the last messages are a year old!). I just wanted to thank you VERY much for this excellent work: it makes me wish to know more in order to (someday) give back something to the ubuntu community! THIS is the truly spirit of the whole open-source thing! 
I'll try to translate something, or make some art, or just get you guys some coffee..!
Keep up the good work, Tomosaur!

---

### Post by Tomosaur on 2007-05-02
> **Ubunteador said:**
> I dunno if you are still working with GrubEd (since the last messages are a year old!). I just wanted to thank you VERY much for this excellent work: it makes me wish to know more in order to (someday) give back something to the ubuntu community! THIS is the truly spirit of the whole open-source thing! 
I'll try to translate something, or make some art, or just get you guys some coffee..!
Keep up the good work, Tomosaur!

:O They're not a year old, the last messages are only about a few days old! The first version was released August last year I think it was.

Anyway - I haven't done anything much on GrubEd recently, but that's only because I've been very busy with other things. I have a list of things that need to be fixed / improved in GrubEd, and once I'm free for the summer I should be able to get those done. I was also working on a Python version, but I had to put it on hold for a number of reasons, not least because the Ubuntu devs may be getting rid of Grub once Grub 2 is released.

Thanks for the encouragement though :) The good think about GrubEd is that as it's a script, you can just open it inside a text editor and see how it works. This should help you learn how scripting works at least - although I'm afraid I'm not a very tidy person, so if it looks messy, then you'll have to forgive me. One of the things I need to do to GrubEd is to tidy up the underlying script :P

---

### Post by eduardoeltortuga on 2007-05-04
thanks so much for all your hard work! Finally got everything set up and I learned a lot as well. Works like a charm:)

---

### Post by Tomosaur on 2007-05-06
Ok, update is now available. The installer script will now tell you if zenity, or any of the other required programs, is missing. Unfortunately, it doesn't auto-download and install anything missing.

If you already have an older version of GrubEd, you will need to uninstall it before installing the new version. An uninstaller for the old version is provided in the download.

---

### Post by macehouse on 2007-05-23
[B][SIZE="4"]Ok I have been a avid Microsoft supporter and have been bata testing for them for years but recently I got so fed up with hang ups, glitches and the fact they are charging so much for Vista Ultimate is crazy. So I came across some cool video on YOUTUBE for Ubuntu 7 and loved it so I installed it on my second hard drive creating a dual boot. Everything installed perfectly and smoothly. I love it. 

Now can someone please give me clear step by step instructions on how to install grubed............I downloaded the zip file and extracted it to my desktop in Ubuntu. Now when I read the install instructions in this thread I just dont get it. Please help me.

Brad :( [/SIZE][/B]

---

### Post by muggins on 2007-05-23
Yes I would also like to be able to use this program also only I can't figure out how to download/install it onto my computer (xubuntu) either.

---

### Post by Tomosaur on 2007-05-24
Ok, here's the instructions:

1) Download the grubed.zip file.
2) Extract this file, you should be left with a folder called 'grubed'.
3) Open up a terminal, and change to this grubed directory. If you've never used the terminal before, the command to change directory is 'cd' (just like in the Windows command line). The command to list the contents of a directory is 'ls' (it's essentially the same as 'dir' on Windows).
4) Once inside the grubed directory, type the following command:
```

sudo sh ./install

```
You will be asked for your password. Type it in (although you won't see it being typed, so make sure you spell it correctly!), and the install script will begin installing everything. If there are any problems, the install script will tell you what you need to do, but there shouldn't be any if you're using an ordinary Ubuntu install.

Once grubed is installed, you should be able to launch it using the launcher provided (you can just copy and paste it onto your desktop / panel / whatever). You can also run it from the command line by typing 'gksudo grubed'.
Good luck!

EDIT:

A normal Ubuntu install should already have everything in place for the install script to function properly. Kubuntu and Xubuntu may require you to manually install zenity (the installer script will inform you if zenity is not installed). Zenity is available in the repositories, so just use Add/Remove or Synaptic to install it.

---

### Post by Farhan on 2007-05-24
yay! awesome script! expecting a full fledged GUI with better navigation options and data collection methods to replace the current one. thanks a lot mate!

---

### Post by Hillbilly Tilley on 2007-05-25
I am having trouble getting the splash screen to work.  I do not have the custom color enabled.  I get an error of cannot read the xxx file.  

Any suggestions?

---

### Post by Medieval_Creations on 2007-05-25
Looks good.  Didn't have a chance to test it, will more this weekend. :)
1 question, I skimmed the thread, but didn't catch anything on it.
What's the requirements on Grub background images again?

---

### Post by Tomosaur on 2007-05-26
The requirements for background images can be found in the help file, which you can access via the main grubed menu.

@ Hillbilly -
The script will only recognise .xpm.gz extensions on images. This is not a REAL grub restriction (ie, it's only the script which enforces this), but it tends to save a lot of headaches. Again, the help file should tell you all you need to know.

---

### Post by cosmoshell on 2007-05-28
slpash screen isent working giving me cant find eror

---

### Post by Hillbilly Tilley on 2007-05-29
I have tried using images with that extension with the correct resolution as stated in the help file...Still nothing, getting the same error.  I cannot even get the supplied image file to display.

---

### Post by Tomosaur on 2007-05-30
Strange. Choose the direct edit option from the GrubEd menu, and copy and paste the displayed file here please.

---

### Post by Hillbilly Tilley on 2007-05-30
Here is what shows up in my direct edit option
```
splashimage (hd1,1)/boot/grub/images/splash.xpm.gz
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cc407a27-2e85-4332-ac1e-b4126ad03587 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cc407a27-2e85-4332-ac1e-b4126ad03587 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cc407a27-2e85-4332-ac1e-b4126ad03587 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cc407a27-2e85-4332-ac1e-b4126ad03587 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cc407a27-2e85-4332-ac1e-b4126ad03587 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by Tomosaur on 2007-05-31
When you receive the error message, is this an error message given by GrubEd, or is it an error message you receive when you boot your computer?

Sorry for the questions, I'm in the process of moving and my own computer is packed away for the time being, so it's difficult to test stuff. Added to this I'm going to be living on a boat all next week so I can't really help you out during that time.

From the information you just gave, it looks like everything should just work. Did you use the installer script to install GrubEd?

---

### Post by Hillbilly Tilley on 2007-05-31
I installed the script using the directions in the readme file, ie sudo ./install.  I get this error during boot  **Failed to read splash image ((hd1,1) /boot/grub/images/splash.xpm.gz) press any key to continue** when you hit a key it takes you to the grub window less the splash.

---

### Post by vbmds on 2007-06-09
The image has to be 14 colours only. Refer to this HOWTO: [http://ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash+image]("http://ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash+image")

---

### Post by Tomosaur on 2007-06-09
Thanks for the info Hilbilly - I'll get my computer unpacked and set up probably tomorrow, and I'll take a look and see if I can work your problem out.

---

### Post by Tomosaur on 2007-06-27
Hillbilly - 

I discovered the cause of the problem, and I apologise for not getting back to you sooner.

It is not actually a bug in GrubEd which causes this issue, it's just a result of the previous update. In the last update I altered the names of many of the GrubEd files, but I'd completely forgotten that this included the splash image aswell. If you take a look at the splash image in your /boot/grub/images folder, you'll see that it's actually called 'grubed_splash.xpm.gz'.

Now, use the direct edit function of GrubEd and, provided you haven't already changed it, you'll see that the first line references a file called splash.xpm.gz. Simply change that line to reference grubed_splash.xpm.gz, and the problem should disappear. You could also do this by simply using the 'change splash image' function in the splash menu of GrubEd, which will allow you to just double click the correct file.

So anyway, it is all my fault for being so forgetful, but the solution is pretty simple.

For new users of GrubEd, you won't have this problem, it only affects people who had used an old version.

---

### Post by Hillbilly Tilley on 2007-06-29
This did not fix my problem...I have tried to change the splash to another image, then direct edit to make sure that file was named correctly, but still same error just different file name.

---

### Post by Tomosaur on 2007-06-29
> **Hillbilly Tilley said:**
> This did not fix my problem...I have tried to change the splash to another image, then direct edit to make sure that file was named correctly, but still same error just different file name.

Ok, can you paste the output of the following two commands:

```

ls /boot/grub/images
cat /boot/grub/menu.lst | grep "splash"

```

---

### Post by Hillbilly Tilley on 2007-06-30
This is what came up when I ran both commands

```
barry@barry-laptop:~$ ls /boot/grub/images
52421-white_tree.xpm.gz     56961-grub-splash.xpm.gz  grubed_splash.xpm.gz
53373-NightOfUbuntu.xpm.gz  58022-ubuntu-grub.xpm.gz
barry@barry-laptop:~$ cat /boot/grub/menu.lst | grep "splash"
splashimage (hd1,1)/boot/grub/images/splash.xpm.gz
# defoptions=quiet splash
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=cc407a27-2e85-4332-ac1e-b4126ad03587 ro quiet splash

```

Thanks for the help
                               Barry

---

### Post by Tomosaur on 2007-06-30
Yeah, I can see the problem. Your grub is looking for an image called splash.xpm.gz, but there is no such image in your /boot/grub/images folder.

GrubEd SHOULD work when you select a new image, and I really can't understand why it isn't working. However, the following should fix your problem.

Open GrubEd, and use the Direct Edit function. Find the line which begins with "splashimage" (it should be the first line in the file) and change it to read:

```

splashimage (hd1,1)/boot/grub/images/grubed_splash.xpm.gz

```

Click ok, and make sure you receive the 'Changes successful' message. Next time you reboot you should see grub load with the grubed splash. When you use GrubEd in the future you should have no problems simply using the 'change splash' feature.

If it doesn't work (but it should), then don't hesitate to get back to me and I'll see what else I can do.

---

### Post by mahiyar on 2007-07-01
I have always carried out changes to grub by hand. This little programme is very good for beginners and I believe should be included in the original install. Congrats  Tomasaur.

---

### Post by Hillbilly Tilley on 2007-07-03
I pasted the line into the script and everything worked fine.  Then I changed the splash image and the same error reappeared.  I tried to change the splash to several different images, which were of the correct format, and get the same error just with the different image name.  Weird!

Thanks for trying

---

### Post by moredhel on 2007-07-03
This is /exactly/ what I have been looking for for a while! Well, more accurately, what I have been looking for for my brother as I no longer duel-boot, but still ^_^ .

---

### Post by Tomosaur on 2007-07-03
> **Hillbilly Tilley said:**
> I pasted the line into the script and everything worked fine.  Then I changed the splash image and the same error reappeared.  I tried to change the splash to several different images, which were of the correct format, and get the same error just with the different image name.  Weird!

Thanks for trying

Well, I took another look, and I've fixed the bug which caused the problem. The new version is available on the first page of this thread :)
Thanks for bringing it to my attention.

---

### Post by loserboy on 2007-07-21
hey Tom I was gonna ask the Automatix team to add your package to their script, but I thought I'd ask you first you you would mind if they did.

---

### Post by Tomosaur on 2007-07-21
> **loserboy said:**
> hey Tom I was gonna ask the Automatix team to add your package to their script, but I thought I'd ask you first you you would mind if they did.

Sure, they can add it if they feel like :)

---

### Post by Shin_Gouki2501 on 2007-07-22
Hello i installed Ubuntu to aExternal HD ( USB) i got always stuck with a GRUB error ( i think STage 1.5... ( GRUB 2 !!)
Would ur script allow me to edit the problem at the boot process?
wbr Shin Gouki

---

### Post by Tomosaur on 2007-07-23
> **Shin_Gouki2501 said:**
> Hello i installed Ubuntu to aExternal HD ( USB) i got always stuck with a GRUB error ( i think STage 1.5... ( GRUB 2 !!)
Would ur script allow me to edit the problem at the boot process?
wbr Shin Gouki

GrubEd is only an editor for the grub menu - and as such it means that if grub isn't working at all, then GrubEd will also not work properly (or, more accurately, you won't get any benefit from using it since Grub will not be working.).

GrubEd does have a direct edit option so that you can mess about with the grub menu by hand, but this is no different from opening the menu.lst file in a text editor - and also means that you must know exactly what to change.

---

### Post by Shin_Gouki2501 on 2007-07-23
ah thx for telling me :)
i wait then till GRUB 2 :)

---

### Post by akash1221 on 2007-08-09
Very cool script!

Makes it a breeze to do anything grub related!

Thanks for all your work!

Akash

---

### Post by olskar on 2007-08-09
This script doesnt work in gutsy..atleast not changing the default OS..

---

### Post by Tomosaur on 2007-08-09
> **olskar said:**
> This script doesnt work in gutsy..atleast not changing the default OS..

I haven't tried gutsy out yet - when I do I'll be sure to update the script to account for any changes.

However - does Gutsy use grub 2? I know it's supposed to be making an appearance sometime soon.

---

### Post by brolzwerver on 2007-08-10
hi

Looks nice, but I have some troubles installing the script. (I think) I followed the instructions exactly, but I get this back after typing in the password (and thus the start of the install?):

```
lb@lb-desktop:~/Desktop/grubed$ sudo sh ./install
./install: 23: deps[1]=zenity: not found
./install: 24: deps[2]=vi: not found
./install: 25: deps[3]=grep: not found
./install: 26: deps[4]=diff: not found
./install: 27: deps[5]=patch: not found
Checking dependencies...

./install: 37: Syntax error: Bad substitution

```

What is wrong?

Thanks in advance
L

P.S.: Please keep in mind I'm completely new to Ubuntu when you reply... :)

---

### Post by Tomosaur on 2007-08-10
> **brolzwerver said:**
> hi

Looks nice, but I have some troubles installing the script. (I think) I followed the instructions exactly, but I get this back after typing in the password (and thus the start of the install?):

```
lb@lb-desktop:~/Desktop/grubed$ sudo sh ./install
./install: 23: deps[1]=zenity: not found
./install: 24: deps[2]=vi: not found
./install: 25: deps[3]=grep: not found
./install: 26: deps[4]=diff: not found
./install: 27: deps[5]=patch: not found
Checking dependencies...

./install: 37: Syntax error: Bad substitution

```What is wrong?

Thanks in advance
L

P.S.: Please keep in mind I'm completely new to Ubuntu when you reply... :)

Hmm - that's an odd one. If the install script can't find one of the needed programs, then it will inform you, but that error looks like the script itself is wrong. Did you download the script from the first page of this thread?

If the install script is set to be executable you can run it using 'sudo ./install' rather than 'sudo sh ./install'. In my experience, using the sh command can cause problems, but I've never seen this particular issue before. If you don't know whether the script is executable, just type:

```

chmod +x ./install

```

while in the same directory as the install script.

Try running it without the 'sh' and see if that works.

Unfortunately I won't be able to look into this until late next week, as I'm going to be very busy over the weekend and much of the week. Sorry!

---

### Post by brolzwerver on 2007-08-11
> **Tomosaur said:**
> Hmm - that's an odd one. *[...]*

If the install script is set to be executable you can run it using 'sudo ./install' rather than 'sudo sh ./install'. In my experience, using the sh command can cause problems, but I've never seen this particular issue before. If you don't know whether the script is executable, just type:

```

chmod +x ./install

```

while in the same directory as the install script.

Try running it without the 'sh' and see if that works.
*[...]*
Thanks, this way it worked!

---

### Post by 1uniquegeek06 on 2007-08-19
How do I install this script?

I download the GrubEd.zip to my home/nicky/

How do I run the installment?

---

### Post by Tomosaur on 2007-08-20
> **1uniquegeek06 said:**
> How do I install this script?

I download the GrubEd.zip to my home/nicky/

How do I run the installment?


The file should be called 'grubed.zip' if you want the latest version, which has several bug-fixes.

Anyway, you should be able to double-click the .zip file then choose where to extract it. Once you've done that, open up the terminal, and use the 'cd' command to change directory to wherever the unzipped files are. For example, if you unzipped the file to "/home/nicky/grubed", you would type:

```

cd /home/nicky/grubed

```

From there, use the following commands to install the script:
```

chmod +x ./install
sudo ./install

```

You will be asked for your password, but you won't see it being typed, so be sure to spell it correctly.

Once the script is installed, you can close the terminal window, hit alt+f2, then type 'gksudo grubed'. You can create a launcher if you wish, just be sure to use 'gksudo grubed' as the command to launch it.

---

### Post by TeaSwigger on 2007-09-07
Tomosaur, thank you for the superb tool :D Now that I know how to edit GRUB I don't need a GUI but it was absolutely instrumental in helping me to understand GRUB and get the "courage" to jump in there.

After the deserved praises, one thought and an insignificant "bug" to offer in further feedback:

- If you first set which OS to boot by default, and then choose how many kernels to display when there are more than one available, the default boot number is not updated. For instance if you had a dual boot like this:

linux 2.6
(recovery)

linux 2.5
(recovery)

other line

Open Winder View 200x

...and you set it to open the Winder by default. It'd number it as 5 if I'm not mistaken. That's great, but if you then went and had it edit it for one kernel version you'd have no number 5 and the Winder at number 3, but the menu.lst would still have default set to non existant number 5... hope the explanation makes sense...

Finally the "bug". If running grubed from konsole in kubuntu I get this non-fatal and evidently insignificant error:

```
(zenity:6445): Gdk-CRITICAL **: gdk_drawable_copy_to_image: assertion `src_y >= 0' failed
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!
```

Don't know what it means, but grubed works perfectly despite it. :) Again, thanks for the nifty tool.

---

### Post by Tomosaur on 2007-09-07
Thanks for the feedback! I'll take a look over the weekend and put the fixed version up on here :)

The error message is new to me, but I will try and find the cause of the problem :)

---

### Post by bone2006 on 2007-09-07
Things like this really should be in the release.  Most people know that a high percentage of people dual boot with windows. For a user who wants windows to be the default option that boots up, they will have to edit grub, which most people would prefer a gui frontend instead of editing an asci file

---

### Post by FerhatBingol on 2007-09-16
Tomosaur, wonderful script. Fixed a lot of my need and I have added a small link to here from my blog. 

I hope more people find out about it. 

Now, all we need is a brave guy/gal to code the dual screen :D

---

### Post by Tomosaur on 2007-09-17
> **TeaSwigger said:**
> Tomosaur, thank you for the superb tool :D Now that I know how to edit GRUB I don't need a GUI but it was absolutely instrumental in helping me to understand GRUB and get the "courage" to jump in there.

After the deserved praises, one thought and an insignificant "bug" to offer in further feedback:

- If you first set which OS to boot by default, and then choose how many kernels to display when there are more than one available, the default boot number is not updated. For instance if you had a dual boot like this:

linux 2.6
(recovery)

linux 2.5
(recovery)

other line

Open Winder View 200x

...and you set it to open the Winder by default. It'd number it as 5 if I'm not mistaken. That's great, but if you then went and had it edit it for one kernel version you'd have no number 5 and the Winder at number 3, but the menu.lst would still have default set to non existant number 5... hope the explanation makes sense...

Finally the "bug". If running grubed from konsole in kubuntu I get this non-fatal and evidently insignificant error:

```
(zenity:6445): Gdk-CRITICAL **: gdk_drawable_copy_to_image: assertion `src_y >= 0' failed
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!
```Don't know what it means, but grubed works perfectly despite it. :) Again, thanks for the nifty tool.

Righty ho, update is now available (check the first page of this thread :) ).

The problem about the default boot not being updated still isn't 'fixed' - but GrubEd will at least now prompt users to re-select the default boot option after the OS list has been modified using the options GrubEd provides. Hopefully this will mean people won't get caught out, but it's not an ideal solution. Hopefully this will just be a temporary solution to the problem - if users don't just ignore the warnings then hopefully the should be fine.

Obviously, if users use the Direct Edit option to change their boot list, then they're on their own!

As for the GTK error, I couldn't reproduce it :S

The part about not using '/sbin/update-grub' I think is down to you having messed up paths. Try the following command in the terminal:
```

echo $PATH

```If /sbin/ appears BEFORE /usr/sbin/, then I think that's the cause of your problem. To fix it, open ~/.bashrc in a text editor, then at the bottom of the file, copy the output of the above command into an export instruction, but make sure /usr/sbin comes before /sbin. So, for example, you would use:
```

#Fix the PATH variable to look for user programs before system programs
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```Then save your .bashrc file, log out, then log back in again. Hopefully the update-grub problem will not appear again.


There are some other things I've found which I want to fix, but none of them are all that serious - just usability stuff really (as a special bonus, I've finally removed the annoying 'Do you want to perform a new task?' box :P).

Hope that helps you out!

Tom

Oh, and Ferhat - thanks for the kind words and publicity :)

---

### Post by yowshi on 2007-09-21
i tried to remove the low latency option from the grub that was installed with my nvidia drivers and it wouldnt get rid of it

---

### Post by master_kernel on 2007-09-21
By the looks of it, this project is still active; congrats!

Tomosaur, please visit [http://ubuntuforums.org/showthread.php?p=3376011](http://ubuntuforums.org/showthread.php?p=3376011) and add your program to the list of the best of the Ubuntu community.

---

### Post by TeaSwigger on 2007-09-21
> **Tomosaur said:**
> Righty ho, update is now available (check the first page of this thread :) ).

The problem about the default boot not being updated still isn't 'fixed' - but GrubEd will at least now prompt users to re-select the default boot option after the OS list has been modified using the options GrubEd provides. Hopefully this will mean people won't get caught out, but it's not an ideal solution. Hopefully this will just be a temporary solution to the problem - if users don't just ignore the warnings then hopefully the should be fine.

Obviously, if users use the Direct Edit option to change their boot list, then they're on their own!

As for the GTK error, I couldn't reproduce it :S

The part about not using '/sbin/update-grub' I think is down to you having messed up paths. Try the following command in the terminal:
```

echo $PATH

```If /sbin/ appears BEFORE /usr/sbin/, then I think that's the cause of your problem. To fix it, open ~/.bashrc in a text editor, then at the bottom of the file, copy the output of the above command into an export instruction, but make sure /usr/sbin comes before /sbin. So, for example, you would use:
```

#Fix the PATH variable to look for user programs before system programs
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```Then save your .bashrc file, log out, then log back in again. Hopefully the update-grub problem will not appear again.


There are some other things I've found which I want to fix, but none of them are all that serious - just usability stuff really (as a special bonus, I've finally removed the annoying 'Do you want to perform a new task?' box :P).

Hope that helps you out!

Tom

Oh, and Ferhat - thanks for the kind words and publicity :)

Thanks Tom. The echo $PATH command gave me the exact same line as you suggest, so no need to change it. Though that leave the gtk / grub error stuff unexplained I guess. I'm using Kubuntu but don't know if that's relevant. Well important thing is it works anyway :)

---

### Post by path_finder on 2007-09-22
I am having a gigabye k8ns nvidia nforce3 250 mother board. I edited my grub by changing menu.lst file. 
Now its says "cant read splash image (hd0,3)" (when booting)
Can someone help me please ..!

---

### Post by TeaSwigger on 2007-09-22
> **path_finder said:**
> I am having a gigabye k8ns nvidia nforce3 250 mother board. I edited my grub by changing menu.lst file. 
Now its says "cant read splash image (hd0,3)" (when booting)
Can someone help me please ..!

Just to be clear, did you use GrubED to set it? Most likely either the splash image file is the wrong format, its name or location isn't specified, it is at the wrong location, or the notation of where to find it (that's the (hd0,3) part, 0 referring to the hard drive and 3 the partition) is incorrect. The line specifying what image to use and where it is would be at the top of the /boot/grub/menu.lst file you can check this file in a text editor or by the "direct edit" option in GrubEd. As always be careful if editing that file directly. Hope this helps you figure it out.

---

### Post by Tomosaur on 2007-09-22
> **yowshi said:**
> i tried to remove the low latency option from the grub that was installed with my nvidia drivers and it wouldnt get rid of it


At the moment there's no option to remove a specific kernel entry from grub using GrubEd. The best you can do is to just remove the unwanted entry directly from the /boot/grub/menu.lst file.

---

### Post by geekcliff on 2007-10-19
I Just done a clean install of gutsy today, and grubed would not change the default os. Ive just had a search on the net from work and i found a new version of grubed, does anyone know if its been tried on gutsy?

---

### Post by Tomosaur on 2007-10-19
> **geekcliff said:**
> I Just done a clean install of gutsy today, and grubed would not change the default os. Ive just had a search on the net from work and i found a new version of grubed, does anyone know if its been tried on gutsy?

The latest version of GrubEd is always on the first page of this thread - do you have a link to where the version of GrubEd you found is?

I have trouble with my gutsy install so haven't been able to test GrubEd on it yet, but as soon as I've ironed out the problem I'll post here and let everyone know if it works ok. I can't imagine there should be any issues.

---

### Post by geekcliff on 2007-10-19
Ithink the new version came from your web site [http://www.csc.liv.ac.uk/~cs5tjh/GrubEd/](http://www.csc.liv.ac.uk/~cs5tjh/GrubEd/), i cant try it out till monday.

---

### Post by Tomosaur on 2007-10-19
> **geekcliff said:**
> Ithink the new version came from your web site [http://www.csc.liv.ac.uk/~cs5tjh/GrubEd/]("http://www.csc.liv.ac.uk/%7Ecs5tjh/GrubEd/"), i cant try it out till monday.

Ah right - yeah that one should be ok then :P

---

### Post by geekcliff on 2007-10-22
> **Tomosaur said:**
> Ah right - yeah that one should be ok then :P

Just tested it and still not working, it'll change everything bar the defualt OS,
also the launcher wont work, you get a message saying use gksudo gruded.

---

### Post by Tomosaur on 2007-10-22
Thanks for the info - I'll take a look as soon as I can :)

---

### Post by geekcliff on 2007-10-23
I've managed to get it working now by a manual edit, what is happening is, your script does change the default os number, but it puts three dashes in front of the number so grub cant read it, so it just defaults to the standard default,i removed the dashes and all is fine.:guitar:

---

### Post by Tomosaur on 2007-10-23
Ah I see - well, obviously if there's a problem with GrubEd on Gutsy I'll do my best to fix it, so thanks for the heads up. If I can track down the problem I'll release a fix for it as soon as I can :)

Thanks again!

---

### Post by Jasea on 2007-10-26
I too have this problem with Gutsy, but in my case no matter which OS is selected as the default, GrubEd replaces the current NUMBER with -1. So the next attempt to set the OS gives us --1 and so on. Just thought that this might give you a clue when you get around looking at the problem.
Regards John

---

### Post by Gina on 2007-11-29
Good luck in sorting this out :)  I've used GrubEd with Feisty and found it good - it would be great to have it for Gutsy too, particularly for less computer literate users.

---

### Post by Tomosaur on 2007-11-29
As it turns out, I've found the problem, but fixing it is going to take a while :) It's a very annoying little bug involving whitespace and grep - but it should be fixed soon enough :)

Thanks for using GrubEd!

---

### Post by Gina on 2007-11-30
Thanks Tomosaur :)  I've been having a look at both the Gutsy produced grub menu.lst and your GrubEd script.  Will also need a Feisty menu.lst to compare - with an initial look it seems much the same.  

Whitespace can be a headache at times!!  Some years ago when I was programing and taking input from other systems, I found it useful to parse the text to remove excess whitespace first.

Good luck with GrubEd - great stuff :)

---

### Post by Gina on 2007-12-02
I've found an interesting thing...  If I edit the Feisty grub menu.lst while running Gutsy, it fails in the same way.  Editing the Gutsy menu.lst in Feisty works fine.  So it seems it's not a difference in the menu.lst but in the implementation of grep in Gutsy.

---

### Post by Tomosaur on 2007-12-02
Thanks for the heads up! I will take a look and see what I can do.

---

### Post by mssever on 2007-12-02
> **Gina said:**
> I've found an interesting thing...  If I edit the Feisty grub menu.lst while running Gutsy, it fails in the same way.  Editing the Gutsy menu.lst in Feisty works fine.  So it seems it's not a difference in the menu.lst but in the implementation of grep in Gutsy.
There may well be something to that. I have a script of an entirely different nature that relies heavily on grep. After I upgraded to Gutsy, I started getting odd errors (come to think of it, my errors were bash errors, not grep errors). At any rate, I eventually did an end run around the problem by rewriting it in Ruby.

---

### Post by Gina on 2007-12-02
Yes, it could be some other bash function than grep - I'm still investigating, I'm pretty new to Linux and learning to write bash scripts.  Looking into this is good practice :)  I'm retired so don't have work as a time restraint :lol:

---

### Post by Gina on 2007-12-02
I think the problem is in either grep of the pipe function though both seem fine everywhere but one line :- MENU_ITEM=$(grep ^title $G_MENU | grep -n $OS_SEL$ | grep -o ^[[:digit:]]*)

In particular under Gutsy ** $(grep ^title $G_MENU | grep -n $OS_SEL$) **returns no string when used in an **echo** command, so filtering to show only the line number digits also produces nothing and hence a MENU_ITEM of zero.  **$OS_SEL** is correct and **grep ^title $G_MENU**  has been used before..  Running under Feisty procuces the expected results and everything works fine.

(Hope I'm not "treading on any toes" in posting this and that it may be some help)

---

### Post by mssever on 2007-12-02
> **Gina said:**
> I think the problem is in either grep of the pipe function though both seem fine everywhere but one line :- MENU_ITEM=$(grep ^title $G_MENU | grep -n $OS_SEL$ | grep -o ^[[:digit:]]*)

In particular under Gutsy ** $(grep ^title $G_MENU | grep -n $OS_SEL$) **returns no string when used in an **echo** command, so filtering to show only the line number digits also produces nothing and hence a MENU_ITEM of zero.  **$OS_SEL** is correct and **grep ^title $G_MENU**  has been used before..  Running under Feisty procuces the expected results and everything works fine.
I wonder if switching to egrep would help. When using regular expressions that contain anything other than alphanumerics, I always use egrep instead of grep, since egrep produces better results.

---

### Post by Tomosaur on 2007-12-02
Yeah, egrep is definitely a possibility, but I'm keeping my options open for now. I may just switch to sed and be done with it - the current search and replace is more complicated than it needs to be to be honest, I'm just very stubborn :P

---

### Post by Gina on 2007-12-04
I think I've got something working in Gutsy.  It's a little less tidy than the original in that I'm displaying numbers in the OS list.  Try as I might, I can't get grep to search correctly on the string returned by zenity from the OS list.  However, I'm pretty new to bash scripting and may have missed something.  Also I expect my new bit could be made shorter.
```

list_menu(){
#List a menu of installed operating systems. Double click to set default.
grep ^title $G_MENU  > $AVAIL
grep ^title $AVAIL | grep -n ^title > $AVAIL
cat $AVAIL | sed '/Other operating systems/ d' | sed 's/:title	/ /' > $AVAIL # Remove unwanted line
OS_SEL=$(cat $AVAIL | zenity --list --width=400 --height=200 --title="Available Menu Items" --column "Operating Systems" --text="Choose an OS:")
if [ -n "$OS_SEL" ]
then
  MENU_ITEM=$(echo $OS_SEL | grep -o ^[[:digit:]]*) # Strip OS number off
  let MENU_ITEM=$MENU_ITEM-1
  DEF_LINE=$(grep  -n ^default $G_MENU | grep -o ^[[:digit:]]*)
  DEF_CURR=$(grep ^default $G_MENU | grep -o [[:digit:]]*$)
  vi -e -c "$DEF_LINE"s/"$DEF_CURR"/"$MENU_ITEM" $G_MENU -c :wq | zenity --progress --pulsate --auto-close --title="New Default" --text="Progress:"
  success
fi
rm $AVAIL
}
```

---

### Post by Tomosaur on 2007-12-04
> **Gina said:**
> I think I've got something working in Gutsy.  It's a little less tidy than the original in that I'm displaying numbers in the OS list.  Try as I might, I can't get grep to search correctly on the string returned by zenity from the OS list.  However, I'm pretty new to bash scripting and may have missed something.  Also I expect my new bit could be made shorter.
```

list_menu(){
#List a menu of installed operating systems. Double click to set default.
grep ^title $G_MENU  > $AVAIL
grep ^title $AVAIL | grep -n ^title > $AVAIL
cat $AVAIL | sed '/Other operating systems/ d' | sed 's/:title    / /' > $AVAIL # Remove unwanted line
OS_SEL=$(cat $AVAIL | zenity --list --width=400 --height=200 --title="Available Menu Items" --column "Operating Systems" --text="Choose an OS:")
if [ -n "$OS_SEL" ]
then
  MENU_ITEM=$(echo $OS_SEL | grep -o ^[[:digit:]]*) # Strip OS number off
  let MENU_ITEM=$MENU_ITEM-1
  DEF_LINE=$(grep  -n ^default $G_MENU | grep -o ^[[:digit:]]*)
  DEF_CURR=$(grep ^default $G_MENU | grep -o [[:digit:]]*$)
  vi -e -c "$DEF_LINE"s/"$DEF_CURR"/"$MENU_ITEM" $G_MENU -c :wq | zenity --progress --pulsate --auto-close --title="New Default" --text="Progress:"
  success
fi
rm $AVAIL
}
```

Yeah, it definitely seems to be a problem with grep. I've tried every grep-oriented solution I can think of and nothing seems to work right. I think sed is the way forward for now, to be honest.

---

### Post by Gina on 2007-12-05
I've now tested my modifications on the real GrubEd in Gutsy and it seems to work fine.  Most of the other functions work fine except the Direct Edit.  I think the trouble here is the **patch** command but not investigated it yet.  The Desktop Launcher doesn't work in Gutsy - have to use the Terminal.

I've also tested it in Feisty and all fine.

---

### Post by Gina on 2007-12-05
A bit later... re Direct Edit :-

Yes, it seems the **patch** command doesn't work properly in **Gutsy** :(  Editing works if **cp** is used instead of **patch.** - copying the output from **zenity** back into **menu.lst**.

BTW **Restore** doesn't work in **Gutsy** as it does in **Feisty** and again I think the **patch** command is responsible.

---

### Post by Tomosaur on 2007-12-05
Ok, thanks for the heads up. Direct Edit and Backup / Restore seem to work fine for me on Gutsy :S Have you used a different version of patch or anything like that?

---

### Post by Gina on 2007-12-07
I have the release version of Gutsy with all updates applied, so standard version AFAIK.  I'll do some testing of patch and see what happens.

---

### Post by Gina on 2007-12-09
Still looking at patch - meanwhile I've added a couple of extra functions :- direct switching of default OS between Ubuntu and Windows and editing of OS title to add your own comments (easier to use than Direct Edit).

---

### Post by Gina on 2007-12-09
Well... try as I might I can't see why patch doesn't work.  The patch file is correct after editing in zenity and patch gives the expected display when the **-s**ilent option is removed.  But the original file remains unchanged.

Since menu.lst is only likely to be small (even with numerous OS installations) is there any particular advantage of using **patch** rather than **cp** (copy the lot)?

---

### Post by Gina on 2007-12-09
I have tried patch both in a copy of GrubEd and a script of my own with different files - all files in the same directory...  In both cases patch appears to work but the file is **not patched** - no changes occur.  This is the test script :-
```
#!/bin/bash
#Gina testing this script - patchtest.sh

#ALL VARS BELOW ARE PATHS
O_FILE=./oldfile.txt  	#This file created externally
N_FILE=./newfile.txt	#These files created by the script
P_FILE=./patchfile.txt	#

#Edit sequence
zenity --text-info --height=500 --width=600 --editable --filename=$O_FILE > $N_FILE
if [[ $(cat $N_FILE) = "" ]]
then
  echo NoChange
  rm $N_FILE
else
  cat $N_FILE
  diff -s $O_FILE $N_FILE > $P_FILE
  echo "Difference(s)"
  cat $P_FILE
  if [[ $(wc -l "$P_FILE") == "1 $P_FILE" ]]
  then
    echo NoChange
    rm $N_FILE $P_FILE
  else
    #Patch differences between newfile and oldfile
    echo "Patch File"
    cat $P_FILE
    patch $O_FILE $P_FILE | zenity --progress --pulsate --auto-close --title="Patching oldfile.txt." --width=300 --text="Progress:"
    rm $P_FILE $N_FILE
    echo Success
  fi
fi
```

Does anyone have any ideas, please?  Patch would be useful for use with long files.

---

### Post by Tomosaur on 2007-12-09
> **Gina said:**
> Well... try as I might I can't see why patch doesn't work.  The patch file is correct after editing in zenity and patch gives the expected display when the **-s**ilent option is removed.  But the original file remains unchanged.

Since menu.lst is only likely to be small (even with numerous OS installations) is there any particular advantage of using **patch** rather than **cp** (copy the lot)?

Sounds like you've been pretty busy :P

With regards to using patch instead of cp, the original idea behind it was to avoid writing when there were no changes being made. It's really just a personal preference rather than having any real benefit, to be honest. The diff between the two files could be checked regardless of whether patch or cp was used - I just decided to use patch :)

I appreciate all the help - I haven't had any time really to be focus on GrubEd recently (both practical problems and personal stuff going on which means I haven't had the time or the will-power to sit down and just fix it once and for all). If you make whatever changes you think would be good, then just send them on to me and I'll eventually get around to checking them and uploading them on the first page.

To everyone waiting for the fixed version - I apologise for not getting round to it yet, but it should be here soon.

---

### Post by Gina on 2007-12-09
Thanks for your reply, Tomosaur   :):)  Yes, I understand about patch - I would tend to take the same view.  I'll send you the edited version when I've tidied it up.

BTW - I've just tested my patch test script in Feisty and it works perfectly.

---

### Post by Gina on 2007-12-14
I've incorporated my amendments into the GrubEd archive and emailed it to Tomosaur, to check out.  I'm still looking into problems with the launcher and installer (Gutsy seems to need "bash" in the command line to run scripts - ie. "sudo bash *scriptfile*" )  I haven't had a lot of time to work on this lately.

To install the script, I used  ```
sudo bash ./install
```
For the launcher I put the following in a text file and saved it to the Desktop```
#!/bin/bash
gksudo grubed
```The rest of the README seems fine.

I think my launcher could be improved upon - I'm still learning.

---

### Post by Gina on 2007-12-18
A better launcher is produced by right-clicking on the Desktop and choosing **Create Launcher**.  Put **gksudo grubed** in the **Command** box and a suitable name such as **Launch GrubEd** in the **Name** box.  Leave **Type** as **Application**.  **Comment** is optional

---

### Post by saltdawwg on 2008-01-24
Nice work. This is just what I ws looking for. ;)

---

### Post by loserboy on 2008-02-13
any news on a working gutsy version, or anything I can do to help?

---

### Post by Gina on 2008-02-16
Since the author of GrubEd, Tomasaur, hasn't posted about this or contacted me, I presume he doesn't have the time to pursue it.  So I think I should post my edited version of his script and associated files.  I'm attaching **grubed-g.tar.gz**

---

### Post by gtchamp7 on 2008-04-03
I'm new to Linux and the more technical aspects of operating systems and computers in general so I was wondering if GrubEd will work (and how to use) in Windows or if it only works in Linux. I noticed that WinRAR can extract the files.

Also, it was noted that a bug occurs in Ubuntu "Gutsy Gibbon", but what I want to know is if it will work in Ubuntu "Hardy Heron". I know that it has not been released just yet, but I wanted to know if this bug is Ubuntu version specific or applies to all Ubunt releases.

Thank You In Advance

---

### Post by mssever on 2008-04-03
> **gtchamp7 said:**
> I'm new to Linux and the more technical aspects of operating systems and computers in general so I was wondering if GrubEd will work (and how to use) in Windows or if it only works in Linux. I noticed that WinRAR can extract the files.GrubEd is a bash script, so it'll only work in Linux unless you jump through a bunch of hoops. Even then, you'd still have trouble running update-grub to apply the changes.

I know nothing about WinRAR, but probably all it means when it is able to extract the files is that it knows about more archive formats than the standard Windows tools.

---

### Post by bbboB on 2008-04-10
Gina,
Just so you'll know, I had to reinstall my Dapper system this last weekend and tried your version of Grub Edit.
It won't install in Dapper after numerous attempts.  Finally fell back to the earlier version posted by Tomasaur in the first page of this thread.  It worked fine.

---

### Post by jfg69 on 2008-04-13
Gina, just tried your update on my Gutsy64 based [Ultimate Edition]("http://forumubuntusoftware.info/"). The only thing that seems to NOT work is changing the default OS. I have quite a few on my list and it needs to be cleaned up. Not sure if that would have any effect on it.

Thanks, jerry

---

### Post by Tomosaur on 2008-04-14
Just a little heads up guys - I'm really sorry for not having posted for literally months. I've been really busy with uni and other general 'stuff', and just haven't had the time to either fix GrubEd or to pay any particular attention to it.

Apologies to Gina for not getting back to you - I do appreciate the help you've given here!

I finish uni at the end of May so hopefully I will finally be able to get back on track with this, but in the mean-time I have to focus on my dissertation and revision for exams, so I might disappear again for a few weeks!

Cheers,
Tom

---

### Post by Gina on 2008-05-06
> **jfg69 said:**
> Gina, just tried your update on my Gutsy64 based [Ultimate Edition]("http://forumubuntusoftware.info/"). The only thing that seems to NOT work is changing the default OS. I have quite a few on my list and it needs to be cleaned up. Not sure if that would have any effect on it.

Thanks, jerryThank you for that :)  I've got a couple of things to sort out on that script.  I'm afraid I haven't had the time to look at it lately but it's on my list of things to do.  I still have my website to update for Hardy too.  Hopefully I'll manage to do some of these things soon :)

---

### Post by Gina on 2008-05-06
> **Tomosaur said:**
> Just a little heads up guys - I'm really sorry for not having posted for literally months. I've been really busy with uni and other general 'stuff', and just haven't had the time to either fix GrubEd or to pay any particular attention to it.

Apologies to Gina for not getting back to you - I do appreciate the help you've given here!

I finish uni at the end of May so hopefully I will finally be able to get back on track with this, but in the mean-time I have to focus on my dissertation and revision for exams, so I might disappear again for a few weeks!

Cheers,
TomThat's alright Tom - I appreciate you're very busy - been busy myself lately but I'm hoping to get back to it as I said above.

---

### Post by jfg69 on 2008-05-06
> **Gina said:**
> Thank you for that :)  I've got a couple of things to sort out on that script.  I'm afraid I haven't had the time to look at it lately but it's on my list of things to do.  I still have my website to update for Hardy too.  Hopefully I'll manage to do some of these things soon :)

Not a problem on this end, I manually edited what I needed to. Meanwhile, I have moved on to Hardy-based Ultimate Edition x64.

Thanks again!

---

### Post by Gina on 2008-05-28
There is now a GRUB menu editor in the repositories called **QGRUBEditor** which has a rather nice GUI front end.  Use Synaptic (System > Administration > Synaptic Package Manager) with either it's name or "Grub Menu" in the Search box to find it to download and install.

---

### Post by mtcycler on 2008-06-10
I am a complete newbie at Ubuntu, so take it easy on me.

I duel boot Win XP Pro and (more importantly) Ubuntu 8.04 LTS
but at boot up GRUB shows about 6 Ubuntu 8.04s even though they all go to the same OS

Help?
Thanks

PS I run Ubuntu 8.04 LTS Studio Edition

---

### Post by Tomosaur on 2008-06-10
> **mtcycler said:**
> I am a complete newbe at Ubuntu, so take it easy on me.

I duel boot Win XP Pro and (more importanly) Ubuntu 8.04 LTS
but at boot up GRUB shows about 6 Ubuntu 8.04s even though they all go to the same OS

Help?
Thanks

Normally you will have the following in your Grub menu:

1: Ubuntu (You should use this one to boot into Ubuntu)
2: Ubuntu Recovery mode (Goes straight to a terminal)
3: 'Other Operating Systems' label (doesn't actually do anything, just seperates Ubuntu from Windows)
4: Windows.

You may also have one which says 'memtest86' or something similar, which you can use if your computer is behaving weirdly.

Now: If you have more than 2 'Ubuntu' lines, it's probably just that you've got more than one kernel installed (You can read up about the Linux Kernel if you want, but basically it's just the version of Linux that you're using). 

It's not a problem, and in fact it makes sense to have more than one kernel version available to you when you boot your computer, just in case the new kernel version has a problem and you need to go back to one which you know works. Take a look at the numbers on the right hand side of each 'Ubuntu' line - thats the Kernel version number. You will probably see at least 2 different numbers, with the top Ubuntu line being the latest version.

The general advice is - if you're uncertain, then leave it alone :P 

You can get rid of the extra Ubuntu lines if you really want to, but if it ain't broke, don't fix it!

---

### Post by mtcycler on 2008-06-10
Ok, Thanks, I won't worry about it then.

David

---

### Post by rodneyaltam on 2008-06-13
Bro;

I am new in using Ubuntu....Where can I download your GrubEd Editor program.

Thanks....

---

### Post by Tomosaur on 2008-06-14
> **rodneyaltam said:**
> Bro;

I am new in using Ubuntu....Where can I download your GrubEd Editor program.

Thanks....

Hello! Hope you're enjoying Ubuntu.

The editor can be downloaded from the first post in this thread. Please read the information in the first post, as there have been problems with GrubEd on the most recent versions of Ubuntu. In the worst case scenario - you might break the bootloader all together, and the only way to fix such a problem is by knowing how the bootloader works in the first place!

I have not yet tested GrubEd on Hardy Heron, and won't be able to for a little while. The editor should work fine on Ubuntu Feisty Fawn or earlier. If you still want to try GrubEd on a later version of Ubuntu (I wouldn't recommend it!) then please let me know how it goes!

---

### Post by shenoyh on 2008-07-20
Is there a way to assign a hotkey or key combination to each of the grub menu items? 

I don't want to use the arrow keys since sometimes my monitor is turned off at boot time and I just need a key or key-stroke combination to select the OS. 

I did Google around but could not seem to find anything related to this and came here hoping that Grubed may have such an option.

Thanks in advance for the responses.
Harish

---

### Post by mssever on 2008-07-20
> **shenoyh said:**
> Is there a way to assign a hotkey or key combination to each of the grub menu items? 

I don't want to use the arrow keys since sometimes my monitor is turned off at boot time and I just need a key or key-stroke combination to select the OS.
I don't know if such a feature exists, but if it does, the place to look is in the grub documentation. GrubED only handles common use cases.

---

### Post by jespdj on 2008-08-28
The current version of Ubuntu has a [Start-Up Manager](http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html) which you can use to edit GRUB (and other) settings.

---

### Post by rahid on 2008-12-01
GRUB editing is really easy i think now. Especially I use a help from [ubuntu-help.co.cc]("http://ubuntu-help.co.cc"). If you also make the GRUB menu looks good then visit [http://ubuntu-help.co.cc/index.php/ubuntu-help/38-system-tweak/50-ubuntu-grub-boot-loader-editing]("http://ubuntu-help.co.cc/index.php/ubuntu-help/38-system-tweak/50-ubuntu-grub-boot-loader-editing")

---

### Post by onetwothree64 on 2009-05-03
Tomosaur,
Is there another way to invoke the install routine? I've been trying to run the installer from different folders, and each and everytime, no matter where I place the compressed file, I receive a terminal error stating 'no such file or directory exists'. I've tried extracting it into a different folder and cd to that directory but, terminal still can't find it. 
I realize that I'm basically still a newbie, but, your instructions are plain and simple. Its got me stumped.
Does it make any difference that I'm running Kubuntu instead of Ubuntu?
Thanks

---

### Post by Tomosaur on 2009-05-05
Hi onetwothree,

I wouldn't recommend using GrubEd these days - there are much more advanced grub boot editors available now. That said - if you still want to run GrubEd (there's no real reason why you shouldn't - just that it's not all that great compared to others available) - then Kubuntu *might* be causing you problems. Can you provide the actual error message you get, copied from the terminal?

Make sure the script is marked as executable before trying to run it:
```

chmod +x ./install

```

---

### Post by android73 on 2009-07-14
Hi,

I am trying to install this and I keep getting "sudo: ./install: command not found" in the terminal. Am I doing something wrong? I would love to have this setup on my system. Thanks for posting!

---

### Post by android73 on 2009-07-14
Sorry, I did figure it out on my own. thanks again!

---

### Post by ElderPinzon on 2010-03-14
Hi!!

I'm new in Ubuntu and i'm still trying to adjust. For now I'll need W7 around and in my house it's need that it boots as default. I've tried two options, manually searching the menu.lst file in the grub folder and installing GrubED. Neither have worked, ¿what can I do?

---

### Post by dmillerw on 2010-03-15
This program is quite old, and won't even work with GRUB2 (what Karmic and above use)

---

### Post by ronyi on 2010-05-11
When i try to open the tar.gz file it says failed becuase i do not have rights:(

---

### Post by bobert01 on 2010-07-16
i keep getting command not found when trying to install from terminal ... how do i get round this ... im a complete noobie ... can you help me you think ? btw im on ubuntu 10.04 ............

---

### Post by spnoe on 2010-07-31
> **Tomosaur said:**
> When you receive the error message, is this an error message given by GrubEd, or is it an error message you receive when you boot your computer?

Sorry for the questions, I'm in the process of moving and my own computer is packed away for the time being, so it's difficult to test stuff. Added to this I'm going to be living on a boat all next week so I can't really help you out during that time.

From the information you just gave, it looks like everything should just work. Did you use the installer script to install GrubEd?

Could someone explain how I use the CD command in the terminal. Can not get it to work.

Thanks
Steve

---

