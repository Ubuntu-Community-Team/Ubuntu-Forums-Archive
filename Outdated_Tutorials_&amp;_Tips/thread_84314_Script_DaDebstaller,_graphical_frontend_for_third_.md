---
title: "Script: DaDebstaller, graphical frontend for third party .deb's"
date: 2005-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by dabear on 2005-10-30
**This tool is not in development anymore, please look at Gdebi for Ubuntu Dapper Drake instead!**


Some months ago I was thinking; what is ubuntu currently missing? A graphical frontend to third party debs offcourse, so I made one for myself. It works, but it isn't the most well-written script you will see (lots of dirty hacks and bugs). 

When a buddy of mine today complained that you «can't just double click the deb to install the f* program, like you can in Windows», I just gave him my script, and he suggested that I shoul post it here  :p This script was (and still is) my first attempt ever at a GUI (gtk) in python, so be nice with it:) 

Notes: [list]
[*]I am using the English and Norwegian version of Breezy, if **you are not**- please report to me
if «dpkg -I /path/to/a/debfile.deb» returns these section names localized: 'Package', 'Version', 'Section' and 'Description'. They aren't localized in the Norwegain version, but if you find yours are, DO NOT- I repeat- DO NOT use this script. Thanks
[*] There seems to be some issues left with upgrading and degrading packages
[*] Does not handle dependencies
[*]I know I have som bugs left
[/list]

**Installing**:
1.download the tar.gz file:
```

wget http://ubuntuforums.org/attachment.php?attachmentid=3268&stc=1&d=1130720167

```
2.extract and put  dadebstaller in /usr/sbin/ : 
```

gunzip dadebstaller.gz
tar -xvf dadebstaller.tar
cd dadebstaller/
sudo cp dadebstaller /usr/sbin/

```
Restart X by pressing ctrl + alt + backspace.
Download a deb of any kind, right click on it and select «properties». Now select  the «add» tab and «Use a custom command». Write «dadebstaller» and select «add». Make sure the radio-button is checked to use dadebstaller as the program for opening .debs

screenie:
[[img]http://img257.imageshack.us/img257/3663/screenshotdadebstaller6fc.th.png[/img]](http://img257.imageshack.us/my.php?image=screenshotdadebstaller6fc.png)

**This tool is not in development anymore, please look at Gdebi for Ubuntu Dapper Drake instead!**

---

### Post by emendelson on 2005-10-30
Have you looked at debins, which is found here:

[http://programmer-art.org/debins](http://programmer-art.org/debins)

It may already do what you are trying to do here...

---

### Post by Haegin on 2005-11-02
A useful little program - I haven't tested it fully but it seems nicer to use than debins (I have just tried both) and it gives more information on the package.
Thanks

---

### Post by Dracontopes on 2005-11-02
Great job, this is one of the features we need in Ubuntu IMO :)

---

### Post by PatrickMay16 on 2005-11-05
Nice... This thing sounds useful to me, though I'd like to ask this before I try installing it. Will it work OK with Hoary, or is this for Breezy only?

---

### Post by dabear on 2005-11-05
It is not tested on hoary at all, but I don't see why it shouldn't work. Except for system commands, python apps are generally very portable

---

### Post by pjgl2 on 2006-02-15
I am interested  in using DaDebstaller, and wondered if there had been any updates since the first posting. Especially wrt to the lack of extended display of Info and `crashing' when reinstalling


Many Thanks

---

### Post by dabear on 2006-02-15
[QUOTE=pjgl2]I am interested  in using DaDebstaller, and wondered if there had been any updates since the first posting. Especially wrt to the lack of extended display of Info and `crashing' when reinstalling


Many Thanks[/QUOTE]
Hi. Most problems has been solved, and I was planning to release v 0.2 along with a name change some time ago, but I haven't had any time to continue the project I'm afraid. I don't see much point in continuing either, as gdebi is coming for dapper soon, with a much better backend (python-apt) & a nice UI too.

---

### Post by pjgl2 on 2006-02-15
I would be very interested in v 0.2. I have looked at gdebi, but we are interested in having the functionality on a knoppix based system where space is very limited. DaDebstaller's small size and low level of dependancies would be useful. Would you be willing to post the code under your gpl for us to look at?

Regards

---

### Post by muzaki on 2006-03-04
i follwed instruction ,and getting no errors,...

but when  i try to install deb package (easycam2) i got these :

root@kodo9:/usr/sbin# ./dadebstaller "/home/dilli/Desktop/easycam2.deb"
Traceback (most recent call last):
  File "./dadebstaller", line 354, in ?
    main()
  File "./dadebstaller", line 332, in main
    DebstallerGUI()
  File "./dadebstaller", line 202, in __init__
    if self.debObj.upgradable():
  File "./dadebstaller", line 102, in upgradable
    if  (not self.isInstalled()) or self.__equalVersion(): return False
  File "./dadebstaller", line 85, in isInstalled
    if (dpkg_query == 'No packages found matching ' + package) \
IndexError: list index out of range


what does it mean??:confused:

---

### Post by benplaut on 2006-03-04
why do yuo have to restart X?

---

### Post by dabear on 2006-05-27
[QUOTE=benplaut]why do yuo have to restart X?[/QUOTE]
There were some problems with a command or something, don't really remember :p
--

Anyway folks, look at gdebi, this project is alpha software and unmaintained as gdebi is here. Going to ask a mod to close this thread now :)

---

