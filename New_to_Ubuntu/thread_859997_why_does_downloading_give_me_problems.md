---
title: "why does downloading give me problems?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by nayeret43 on 2008-07-15
i just tried downloading google-talk.  when it gets downloaded, i try to open it and it tells me to choose an application to open it.  i do not understand whatsoever that means.  this is my third day using linux-ubuntu.

and i have another problem: there are some internet pages that require internet explorer.  and i tried downloading internet explorer to my ubuntu linux, and for some reason, it doesn't work- meaning that the download fails.

and the third problem:  i tried to download Globe7 (voip), and it "half-downloads".  meaning that it gives me a message like this one:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and then it says this in the dialog box (like where it gives an explanation or something like that):

Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

where it says some index files failed to download, because old ones used instead (at the bottom of the message), that may be because i also have Globe7 in windows (i have a dual-boot).  when it does "half-download" (if i am lucky), then its' icon shows up in Applications --> Internet
but, it won't do anything, kind of like, it's just for show.

someone please help.  thank you! :)

---

### Post by Troll_the_Great on 2008-07-15
First of all, this is LINUX, not WINDOWS! So windows programs don't work here.What type of file did you download? ".exe"? This is a windows executable, and generally doesn't work on linux.You can try wine to install it, but not applications work. Have a look at this links for more info and post back any questions for further assistance:
[http://www.winehq.org/](http://www.winehq.org/)
[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
> Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
That means that your system is looking for your CD-ROM in order to find some programs.Insert your Ubuntu CD, make sure that under System-Administration-Software Sources the cd box is checked, and it should work.
Cheers and welcome to the wonderful linux world!

---

### Post by tatmark1 on 2008-08-21
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


I am getting this same problem. I did what you said and still nothing.

---

### Post by oldos2er on 2008-08-21
Go into System, Administration, Software Sources. Uncheck the CD-ROM box; make sure the boxes under 'Downloadable from the Internet' are checked. Reload the sources list (it should ask you to do this after you close the Software Sources window).

---

### Post by Cheesehead on 2008-08-21
Installing new applications is COMPLETELY DIFFERENT for what you are used to on Windows. And most of your old Windows apps will NOT run under Linux (or Mac or Sun or Unix or anything else).

The old way was Download --> Install --> Run

The new way is Add/Remove --> Run
Or, alternately, Synaptic --> Run
(*Tip: Stick with Add/Remove for the first month*)
Most software comes in *packages* stored in *repositories*, and the Add/Remove *package manager* will install or uninstall it for you.

1) For Google Talk, use Pidgin - it's probably already installed in Applications --> Network
   [http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073](http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073) How do I configure Pidgin for Google Talk?

2) If you absolutely *need* Internet Explorer, you must add an application called WINE first (a Windows compatibility program), then install IE to WINE.

3) For VOIP, try Ekiga - also probably already installed in the same location. There are many other VOIP apps available, including Skype...but they have a slightly different install process since they are proprietary and cannot therefore be hosted in the repositories.

4) The other posts are correct - you have told Ubuntu to load new packages from your CD. Use System-->Administration-->Software Sources to tell the system to load new packages from the online repository instead.

---

### Post by chosenbeans on 2008-08-21
First of all Windows is not Linux. Also, Windows uses what's called .exe which is an executable format limited to Windows only. You will not be able to run these programs in Linux without something like wine.

First thing to do when you install Ubuntu is navigate to Applications>Accessories>Terminal and type the following. > sudo apt-get update

This will update you're sources and shortly after you will be prompted for an update. Be sure to install all the updates which will tell you to restart after it has finished. Be sure to keep you're cd in the drive at all times when you first use Ubuntu since this will solve problems mentioned above. After you have Installed all the updates Go ahead and open terminal again and type > sudo apt-get install wine This will install wine which will do it's best at running .exe files (windows executables). Although wine is not yet perfect it's worth a try and should run older windows applications just fine.


As for globe this sounds like a server issue and not Ubuntu. The globe server seems to be having a problem. I have gotten these errors trying to update Ubuntu the normal way. Eventually I figured out that if I update my sources list using > sudo apt-get update This fixes the issue completely. You will have to do this from time to time but not often. It's good to use the apt-get update command every now and then just for the heck of things. By now you should be able to see if wine will run you're windows applications or not. To find out if your application is supported please refer to [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Gotta go hope this helps....PM me for more help and I will try my best to help.

---

### Post by thebigbluecan on 2008-08-21
If you use Google talk just for instant messages you can configure the program called "Pidgin" and if you want something to check your gmail you can go to add/remove programs and search for CheckGmail    Works fine for me and you don't need wine.

---

