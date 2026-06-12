---
title: "CCleaner equivalent for Linux?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by mingle on 2008-07-12
Hi,

Being a Windows user too, I was wondering if there's a program similar to "CCleaner" (on Windows XP) for Linux?

For those not familiar with it, CCleaner tidies up temp files, logs, caches, the registry, etc. 

Cheers,

Mike.

---

### Post by iaculallad on 2008-07-12
That can be done using the terminal:

```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by jimmy the saint on 2008-07-12
does that do more than just stray packages?  I was under the impression that apt only dealt with packages, not with temp, log, cache and other files that can add up over time.

---

### Post by Tuxoid on 2008-07-12
click: System>Administration>Synaptic Package Manager

enter your account password

in the bottom left corner of the window, you should see a set of buttons. Click 'Status'

then, in the list above, click "Installed (auto removable)"

right click all the entries, marking them all for 'complete removal'

---

### Post by nycste on 2008-07-12
great posts guys, thanks i was wondering the same thing myself

Question
> **Tuxoid said:**
> click: System>Administration>Synaptic Package Manager

enter your account password

in the bottom left corner of the window, you should see a set of buttons. Click 'Status'

then, in the list above, click "Installed (auto removable)"

right click all the entries, marking them all for 'complete removal'

im doing this right now i dont have "Installed (auto removable)"

instead i have 
ALL
Installed
Installed (local or obsolete)
Not installed
Not installed (residual config)

---

### Post by iaculallad on 2008-07-12
> **jimmy the saint said:**
> does that do more than just stray packages?  I was under the impression that apt only dealt with packages, not with temp, log, cache and other files that can add up over time.

The apt-get GUI utility does NOT deal with temp files, as in files located on your /tmp directory (w/c is actually removed whenever you logout/reboot/shutdown your computer) and log files, it only deals with the cache files location on your /var/cache/apt/archives directory.

Additional info:

The apt-get **clean** option of apt-get removes everything except lock files from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. Thus, if you need to reinstall a package APT should retrieve it again.

The **clean** option of apt-get deletes all your downloaded cache located at /var/cache/apt/archives.

The **autoclean** option of apt-get removes only package files that can no longer be downloaded.

---

### Post by mcduck on 2008-07-12
> **jimmy the saint said:**
> does that do more than just stray packages?  I was under the impression that apt only dealt with packages, not with temp, log, cache and other files that can add up over time.

Temp files and caches are cleared automatically by the system. Logs are rotated automatically, removing old log files to make room for new ones. And there is no regsitry so there's no need to clean one.. ;)

Apart from Apt's cached files there really isn't much to clean. :D

---

### Post by ibuclaw on 2008-07-12
+1 mcduck

Although I see some rc packagages installed on the OP's system.

When you uninstall packages, make sure you purge them ;)

Run this
```
export PACKAGES=$(dpkg -l | awk '{if ($1 == "rc") print $2" "}' | tr -d '\n')
[ -n "$PACKAGES" ] && sudo aptitude purge $PACKAGES
```
If nothing happens, you are free from left over residual config.

[EDIT]
Also, consider yourself lucky that hardy has fixed all temp files in your $HOME folder from overflowing too!
In Gutsy, it wasn't unusual to see your .thumbnails cache storing 300+MB of images.
So there is even less to worry about now too...

Regards
Iain

---

### Post by Tom--d on 2008-07-12
> **nycste said:**
> great posts guys, thanks i was wondering the same thing myself

Question


im doing this right now i dont have "Installed (auto removable)"

instead i have 
ALL
Installed
Installed (local or obsolete)
Not installed
Not installed (residual config)

Installed (local or obsolete) is you installing a .deb which is not in the Repository.
Not installed (residual config) is where you have uninstalled something but there are still configuration files somewhere. 
Right click that package in Synaptic, and chose Mark for a complete removal. that will sort that problem :)

Installed (auto removable) is where a certain package has no meaning to be installed. Nothing is needing that package. Sometimes they are left over when uninstalling a program. 
Just remove them, its safe to :)

---

### Post by nycste on 2008-07-12
> **Tom--d said:**
> Installed (local or obsolete) is you installing a .deb which is not in the Repository.
Not installed (residual config) is where you have uninstalled something but there are still configuration files somewhere. 
Right click that package in Synaptic, and chose Mark for a complete removal. that will sort that problem :)

Installed (auto removable) is where a certain package has no meaning to be installed. Nothing is needing that package. Sometimes they are left over when uninstalling a program. 
Just remove them, its safe to :)

thx but i cannot right click any packages in "not installed" there are like 100 things inside this section, if i right click an actual file name my only options are "mark for installation" and "properties"

i did however attempt to remove a virtualbox entry in not installed (residual config) but i got an error trying to do so the error is 

"E: virtualbox: subprocess post-removal script returned error exit status 1"

thx for any help

---

### Post by ibuclaw on 2008-07-12
What output is produced when you run this command in the terminal? (Copy [Ctrl+C] and paste it [Ctrl+Shift+V]).
```
dpkg -l | awk '{if ($1 == "rc") print $2}'
```
**dpkg -l** lists all installed and residual config packages on your system in one long string of output.
**awk** parses the output to give human readable information.

Regards
Iain

---

### Post by nycste on 2008-07-12
i followed these steps

You have installed a lot of applications, uninstalled them.  A lot of times when you apt-get remove all those dependencies stay behind.  There are a lot that think aptitude is the answer but I have found that when you aptitude remove an application it removes stuff you don't want removed.   Ubuntu has a few methods that will free up disc space and make your OS lean and fast.

First thing first there is a few commands that can clean up your disc.  I will explain them as we go.  First command is the package autoclean.  What autoclean does is remove partial packages from the system.  To use autoclean type the following command in a terminal:

sudo apt-get autoclean

Then enact the package clean command.  What this commnad does is to clean remove .deb packages that apt caches when you install/update programs.  To use the clean command type the following in a terminal window:

sudo apt-get clean

You can then use the autoremove command.  What the autoremove command does is to remove packages installed as dependencies after the original package is removed from the system.  To use autoremove tye the following in a terminal window:

sudo apt-get autoremove

Next step is to install the gtkOrphan GUI.  What gtkorphan does is to find packages that were once used but no longer have any purpose.  Be careful as to not remove the Gstreamer packages as they are for mp3 encoder/decoding and DVD playback.  Do not remove them.  To install gtkOrphan type the following in a terminal windowt:

sudo apt-get install gtkorphan

You will then be able to use gtkOrphan by going to System--->Administraion--->Remove orphaned packages.  It is pretty self-explanatory.  After you have completed the recommendations of this article you should have a slick clean Ubuntu OS.

i then reopened the synaptic package manager and there are a far fewer items listed in status options

ALL
Installed
-tons listed

Installed (auto removable)
-libxalan110
-liberces27
-python-eyed3

Installed (local or obsolete)
-acetoneiso2
-asunder
-eyed3
-id3mtag
-libogmrip0
-libpurple0
-ogmrip
-pidgin
-pidgin-data
-thoggen
-virtualbox

Not installed
-well self explan

^so i was able to remove the virtualbox item, i then ended up reinstalling it with the updated newer deb package and all appears fine as it lacks to showup again!

^things appear much much cleaner, and i think in general i lack understanding on these topics tomuch to care about them yet and might mess something up soon haha but i enjoy it anyways


ok i followed your advice and well there was no output file or anything visible i ented command in terminal and nothing happened
```
dpkg -l | awk '{if ($1 == "rc") print $2}'
```

thanks

---

### Post by oldsoundguy on 2008-07-12
Linux is a much better housekeeper than Windows by thousands of miles!

CCLeaner gets the stuff in Windows that any activity leaves behind, but it is not 100% even if you set it up with the added stuff to remove.

Windows has amnesia, and the majority of the time re-booting will NOT clean it.
Linux, on the other hand, does not save the garbage to look over it again and to fill up your drive .. in most instances just control/alt/backspace will reset.  BUT sometimes, you MAY have to re-boot.  Either way, you are not starting out with a tractor-trailer full of garbage to remove, just the junk bag you have hanging in your car!

Linux is NOT Windows.  Things you have to do in Windows to keep it running are no longer needed in any form of Linux.

---

### Post by nycste on 2008-07-12
> **oldsoundguy said:**
> Linux is a much better housekeeper than Windows by thousands of miles!

CCLeaner gets the stuff in Windows that any activity leaves behind, but it is not 100% even if you set it up with the added stuff to remove.

Windows has amnesia, and the majority of the time re-booting will NOT clean it.
Linux, on the other hand, does not save the garbage to look over it again and to fill up your drive .. in most instances just control/alt/backspace will reset.  BUT sometimes, you MAY have to re-boot.  Either way, you are not starting out with a tractor-trailer full of garbage to remove, just the junk bag you have hanging in your car!

Linux is NOT Windows.  Things you have to do in Windows to keep it running are no longer needed in any form of Linux.

very nice and simple summary haha

---

### Post by diego898 on 2008-08-07
When I try to do sudo apt-get autoclean I get this output

> diego@Zeus:~$ sudo apt-get clean
diego@Zeus:~$ sudo apt-get autoclean
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
diego@Zeus:~$ sudo apt-get install gtkorphan
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Can anyone tell me why this is?

---

### Post by arpanaut on 2008-08-07
Do you have any package manager open,,, i.e. Synaptic, Add/Remove etc.
If so close them and try again,

---

### Post by Atomic Dog on 2008-08-07
> **oldsoundguy said:**
> Linux is a much better housekeeper than Windows by thousands of miles!

CCLeaner gets the stuff in Windows that any activity leaves behind, but it is not 100% even if you set it up with the added stuff to remove.

Windows has amnesia, and the majority of the time re-booting will NOT clean it.
Linux, on the other hand, does not save the garbage to look over it again and to fill up your drive .. in most instances just control/alt/backspace will reset.  BUT sometimes, you MAY have to re-boot.  Either way, you are not starting out with a tractor-trailer full of garbage to remove, just the junk bag you have hanging in your car!

Linux is NOT Windows.  Things you have to do in Windows to keep it running are no longer needed in any form of Linux.

Again.  This says it all.

---

### Post by diego898 on 2008-08-07
> **arpanaut said:**
> Do you have any package manager open,,, i.e. Synaptic, Add/Remove etc.
If so close them and try again,

You're right. Thank you for that. What a simple problem! 

Anyway, I installed the gtkorphan and when I click on it in system admin there is an option to 
"show all orphaned packages, not just the ones in libs section"

with that clicked I have 112 packages

with that unclicked I have 15 packages

The problem is I am unsure as to which ones to keep or delete. Is it safe to delete all 112? Or only the 15? What should I do?

---

### Post by Sef on 2008-08-07
> The problem is I am unsure as to which ones to keep or delete. Is it safe to delete all 112? Or only the 15? What should I do?

You could delete all 112, and be ok.

---

### Post by diego898 on 2008-08-07
Started new thread for problem not related to this thread

[http://ubuntuforums.org/showthread.php?p=5542191#post5542191](http://ubuntuforums.org/showthread.php?p=5542191#post5542191)

---

### Post by Andrew.Z on 2008-12-24
[QUOTE=mingle;5369119]Being a Windows user too, I was wondering if there's a program similar to "CCleaner" (on Windows XP) for Linux?

For those not familiar with it, CCleaner tidies up temp files, logs, caches, the registry, etc.[/quote

[BleachBit is like CCleaner for Linux](http://bleachbit.sourceforge.net).  Today it cleans up the temporary files, logs, and cache for many popular Linux apps, and soon it will support the equivalent of Linux registry cleaning.  For those who don't believe that is useful, take a look in ~/.local and /var (as simple examples).

---

### Post by hamofgrey on 2008-12-24
Hi there,

Here is a good HOW-TO on cleaning up Ubuntu. Although I never tend to bother so much, I normally do a clean install every 6 months when the new Ubuntu version is out and keep my data in a shared partition and obviously on a external hard drive when backing it up :-)

Enjoy....

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by smuggly on 2008-12-24
Heres A Good How To!!


[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

I Use This Regular It Works Great.......smuggly  Mst Of Did It @ The Same Time:)

---

