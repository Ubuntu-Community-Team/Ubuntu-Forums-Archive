---
title: "flash player"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by edwin2105z on 2008-04-28
does ubuntu 8.04 come with a flash player cause i've been trying to watch video on you tube and it says that i need flash or java. i try to download but nothing happens. can someone tell me if i'm doing something wrong.

---

### Post by Google Spider on 2008-04-28
Open a terminal and run this command

```
sudo apt-get install ubuntu-restricted-extras
```

This will install Java, flash, mp3 codecs and everything you'll ever need.:guitar:

---

### Post by Sirron on 2008-04-28
You'll need [_flashplugin-nonfree_]("apt:flashplugin-nonfree") and I recommend [_libflashsupport_]("apt:libflashsupport") too, as it fixes a sound issue.

If you've installed an open source flash plugin already, you might need to uninstall that.

---

### Post by shayan_mihiran on 2008-04-28
ubuntu 8.04 come without a flash player. u have to install it :)

Step 1: 
First you need to install alien to convert .rpm to .deb package you can check da link  for complete details
[U]
[http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html](http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html) [/U]

Step 2:
First you need to download the .rpm file from Adobe flash Player down load center.
[http://www.adobe.com/shockwave/download](http://www.adobe.com/shockwave/download)

Step 3:
Now you have flash-plugin-9.0.31.0-release.i386.rpm package convert this to .deb using the following command

Code : sudo alien -k flash-plugin-9.0.31.0-release.i386.rpm

Outputlooks like below

Warning: Skipping conversion of scripts in package flash-plugin: postinst prerm
Warning: Use the –scripts parameter to include the scripts.
flash-plugin_9.0.31.0-release-1_i386.deb generated

Now you need to install this .deb package using the following command

sudo dpkg -i flash-plugin_9.0.31.0-release-1_i386.deb

Selecting previously deselected package flash-plugin.
(Reading database … 174973 files and directories currently installed.)
Unpacking flash-plugin (from flash-plugin_9.0.31.0-release-1_i386.deb) …
Setting up flash-plugin (9.0.31.0-release-1) …

This will complete the installation

---

### Post by edwin2105z on 2008-04-28
i open up a terminal and i put the code in the box. but then it asks for a password but does not let me type my password. this is what it looks like...

edwin2105z@edwin2105z-desktop:~$ sudo aptitude install compizconfig-settings-manager
[sudo] password for edwin2105z:

---

### Post by Sirron on 2008-04-28
it is letting you, it just doesn't show any stars or anything.

Type your password as normal, then press return.

---

### Post by Google Spider on 2008-04-28
> **edwin2105z said:**
> i open up a terminal and i put the code in the box. but then it asks for a password but does not let me type my password. this is what it looks like...

edwin2105z@edwin2105z-desktop:~$ sudo aptitude install compizconfig-settings-manager
[sudo] password for edwin2105z:

uh? I thought you were installing flash :confused:

anyway, it will not show the password on screen. Just type it and hit enter. #-o

---

### Post by Michael.Godawski on 2008-04-28
Flash is not a free software. So you have to install it manually:

[https://help.ubuntu.com/community/RestrictedFormats/Flash?action=show&redirect=Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash?action=show&redirect=Flash)

There are free alternatives like gnash or swf.

---

### Post by SunnyRabbiera on 2008-04-28
> **Michael.Godawski said:**
> Flash is not a free software. So you have to install it manually:

[https://help.ubuntu.com/community/RestrictedFormats/Flash?action=show&redirect=Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash?action=show&redirect=Flash)

There are free alternatives like gnash or swf.

yes, but youtube needs flash9, and gnash is based on flash7

---

### Post by Google Spider on 2008-04-28
I've heard gnash is not ready for everyday use.


> Flash is not a free software
edit: whoa! and how come i didn't pay anyone for my flash plugin?? Am I doing something illegal?

---

### Post by Michael.Godawski on 2008-04-28
Flash is not an open software, but free do download.

And yes gnash has some issues.

---

### Post by edwin2105z on 2008-04-28
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


that is what it told me after i typed in my password.

---

### Post by Sirron on 2008-04-28
You can only have one package manager open at once.

That includes Update Manager and Synaptic. It's easier to just use synaptic than "apt-get".

---

### Post by Wynne G Oldman on 2008-04-28
Try going to "Synaptic Package Manager" and install "Ubuntu Restricted Extras". Then go to the Medibuntu website and follow the instructions on the "Repository How to" page to copy and paste the commands into Terminal. This should enable everything that you need for all multimedia, including allowing you to play/copy encrypted DVD's and ripping to MP3 with Sound Juicer. Hope this helps. 
PS. I'm sure that I didn't have to do anything at all to play Youtube video's with a bog standard installation of Hardy. Perhaps you should try removing the Gnash plugin.

---

### Post by drsaamah on 2008-04-28
Uh... granted gnash isn't perfect, but its still pretty darn good.  It runs youtube videos just fine.  I haven't had adobe flash since Windows because their rpm is crap, and alien doesn't work for me like at all.  The point is, I'm probably a terminal idiot but gnash definitely runs youtube videos.  have you guys installed both 'gnash' and 'mozilla-plugin-gnash'?

---

