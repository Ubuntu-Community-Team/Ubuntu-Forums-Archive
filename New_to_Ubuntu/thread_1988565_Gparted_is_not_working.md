---
title: "Gparted is not working"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by Wheeladrew on 2012-05-27
I am sorry if this is in the wrong place. It is my first time posting. 
I am on ubuntu 12.04 LTS x64 on a toshiba satellite a665s6095.
After installing gparted, I could click on the icon, and it would prompt for a password, which I gave, then it would flash up for less than a second and then leave. 
I uninstalled and reinstalled and then ran it through the Terminal, here are the results:
> 
andrew@Satellite-A665-S6095:~$ sudo gparted
[sudo] password for andrew: 

(process:26383): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
======================
libparted : 2.3
======================

(gpartedbin:26383): glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: locale::facet::_S_create_c_locale name not valid

Any help would be appreciated.

---

### Post by nipunshakya on 2012-05-27
Not sure about the error, but i would suggest you reinstall gparted. Try the following:

```
sudo apt-get purge gparted && sudo apt-get install gparted
```


Goodluck.
Happy Linuxing

---

### Post by wilee-nilee on 2012-05-27
Also from the terminal use gksudo instead of sudo, it is a graphical shell.

---

### Post by Wheeladrew on 2012-05-29
Hmm same problem. 
> 
andrew@Satellite-A665-S6095:~$ sudo apt-get purge gparted && sudo apt-get install gparted
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 libjpeg62 liboil0.3:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gparted*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 1982 kB disk space will be freed.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en",
	LC_ALL = (unset),
	LC_CTYPE = "en_US.UTF-8",
	LC_COLLATE = "en_US.UTF-8",
	LC_MESSAGES = "en_US.UTF-8",
	LANG = "de_DE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 263038 files and directories currently installed.)
Removing gparted ...
Purging configuration files for gparted ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
locale: Cannot set LC_ALL to default locale: No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 libjpeg62 liboil0.3:i386
Use 'apt-get autoremove' to remove them.
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils kpartx dmraid gpart
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/544 kB of archives.
After this operation, 1982 kB of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en",
	LC_ALL = (unset),
	LC_CTYPE = "en_US.UTF-8",
	LC_COLLATE = "en_US.UTF-8",
	LC_MESSAGES = "en_US.UTF-8",
	LANG = "de_DE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package gparted.
(Reading database ... 262951 files and directories currently installed.)
Unpacking gparted (from .../gparted_0.11.0-2_amd64.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Setting up gparted (0.11.0-2) ...
andrew@Satellite-A665-S6095:~$ 

is the output from the (un/re)installation command(s).

---

### Post by w-sky on 2012-06-14
Same here with Ubuntu 12.04 including all recent updates and a fresh install of gparted. A window quickly opens and disappears again, this is what it says when started from shell:

```
gksudo gparted

(process:6357): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
======================
libparted : 2.3
======================
```

I guess this is not the right place for this topic, it has to be a bug report.

---

### Post by ptn107 on 2012-06-14
Type this in a terminal.  What does it show?
```
locale
```

You may use a workaround for now.  Add this:
```
LC_ALL="en_US.UTF-8"
```
to
*/etc/environment*
and restart.

---

### Post by coffeecat on 2012-06-14
@w-sky, this is not a problem with Gparted, but with your locale or language settings. If you google the "Locale not supported by C library" message you'll see it is seen with other graphical apps. On my system:

```
$ gksudo gparted
======================
libparted : 2.3
======================
```

And Gparted opens and stays open. Also:

```
$ locale
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

```

That latter won't be relevant to you because I'm in the UK, but it might be interesting to see what your locale output is.

A couple of links which might be useful for you for fixing this:

[http://askubuntu.com/questions/33025/locale-settings-are-not-right-how-can-i-reset-them](http://askubuntu.com/questions/33025/locale-settings-are-not-right-how-can-i-reset-them)

And this. Although it's about chrooting, which is not the issue here, it mentions the particular error message:

[https://help.ubuntu.com/community/DebootstrapChroot#Hints](https://help.ubuntu.com/community/DebootstrapChroot#Hints)

---

### Post by w-sky on 2012-07-20
I reckon this bug is fixed finally. The locale command showed that LANG and LANGUAGE were not set correctly on my systen, and I guess that these wrong settings were made by the Language Support module from System Settings: After I had changed regional formats for the first time, I was getting locale error messages from various programs and some (as Gparted) did not even start.

I was not able to fix the error with any of the suggestions above. What finally helped was simple because the bug in the Language Support module seems to be fixed:

In Language Support, I changed language to English only and regional formats to English (US) and made both system-wide.
Then I reverted regional formats to my preference (system-wide).

Anyone who stumbles upon this locale bug, I recommed to try this procedure. But make sure all updates are installed.

---

### Post by Wheeladrew on 2012-09-26
Problem was fixed in an update. It was LANG LANGUAGE probs, though.

---

### Post by AGentGreenland on 2013-04-27
Hey there..

I have the same problem, and I found out, that I can actually just open it by opening the Terminal (ctrl+alt+t), and type 
```
sudo gparted
```
Then, you get to type your Sudo password in the terminal before the program actually opens, and you're good to go...

However, I also made a .sh script, so you can open it by double-click this .sh file that I made. Nothing phoney about it, and you can of course review the code before you open it (right click and open with gedit or other text program)

The .sh file is archived in a .zip file.

Good Riddance :)

---

