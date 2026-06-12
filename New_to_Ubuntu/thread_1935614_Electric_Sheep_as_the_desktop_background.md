---
title: "Electric Sheep as the desktop background?"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by nullified_nostalgia on 2012-03-04
Is there a way to make it so electric sheep is the desktop background?  If so how would I go about doing this?  I was able to do it in microsoft windows so I'm hoping I can do it in lubuntu as well.

Any help is appreciated!

---

### Post by greenpeace on 2012-03-04
hi, it's available for Linux: [http://electricsheep.org/node/51](http://electricsheep.org/node/51)

Looks like you can either install the package normally, or download and install it (a little bit more involved)

---

### Post by nullified_nostalgia on 2012-03-04
> **greenpeace said:**
> hi, it's available for Linux: [http://electricsheep.org/node/51](http://electricsheep.org/node/51)

Looks like you can either install the package normally, or download and install it (a little bit more involved)
I was able to install it via the package manager, however I've so far been unable to make it function as a scrensaver or get any options to make it run as the desktop background.  So far all I've been able to do is make it run in windowed mode.  In maximized windowed mode using the "undecorate" option in the right click menu on the toolbar I've been able to make it fill most of the screen, but I would still like to have desktop functions, such as being able to see desktop icons and the ability to right click on the desktop.  It would also be nice for it to extend under transparent panels so it's basically filling the whole screen with the lubuntu gui running like normal above it.

---

### Post by greenpeace on 2012-03-04
Did you try the second method to install it from source?

There maybe something you can do with compiz to capture the image and put it "behind" other windows

---

### Post by nullified_nostalgia on 2012-03-04
I'm now attempting to install it from source.  I'm following the instructions on [http://electricsheep.org/node/51](http://electricsheep.org/node/51).

Edit:  I "might" have figured this thing out.  After a lot of research I've gone through all the steps and I'm now compiling electric sheep.  I skipped downloading and compiling flam3 though because I'd already installed it from the package manager when I installed electric sheep the first time.  Hopefully that won't be a problem.

---

### Post by nullified_nostalgia on 2012-03-04
After getting it all compiled and installed it put an electric sheep shortcut in the sound and video menu.  Clicking it doesn't do anything though, it causes the screen to flash for a second like somethings going to happen and then nothing happens.  I went ahead and uninstalled flam3, downloaded the source, built and installed it and then tried electric sheep again but it did the same thing.  It's also not in the screensavers list.

Any suggestions on what I could do to get it to work?  I would try uninstalling and reinstalling it since I reinstalled flam3 but I'm unsure how to uninstall something I've installed from the terminal.  I may end up posting on the electric sheep site but I thought I'd ask here first since I've already got this thread going.

Oh and one more question, where does stuff installed from the terminal install to, as in which directory contains the folders for installed programs?

Thanks!

---

### Post by greenpeace on 2012-03-05
> **nullified_nostalgia said:**
> 

Any suggestions on what I could do to get it to work?   I would try uninstalling and reinstalling it since I reinstalled flam3 but I'm unsure how to uninstall something I've installed from the terminal. I may end up posting on the electric sheep site but I thought I'd ask here first since I've already got this thread going.

Have you tried using xwinwrap?  That seems to have worked for some people[1][2]

I'm not sure how much it will help to un/reinstall... I guess you already followed this thread? [2]

> Oh and one more question, where does stuff installed from the terminal install to, as in which directory contains the folders for installed programs?

that can depend on what you have installed... generally they install different parts of the programs to multiple directories.

you can search using the command line:

```
sudo updatedb
locate -i *foo*

```

This will give you all the files that match the string "foo".

If you installed using apt-get or aptitude, then it's very straightforward to uninstall... use the "remove" command.


[1] [http://ubuntuforums.org/showthread.php?t=1142910](http://ubuntuforums.org/showthread.php?t=1142910)
[2] [http://ubuntuforums.org/showthread.php?t=350089](http://ubuntuforums.org/showthread.php?t=350089)

---

### Post by nullified_nostalgia on 2012-03-05
Thanks for the reply.  It looks like I haven't quite gotten that far in the process yet.

Using the command line I've been able to figure out what the problem is but as of yet I've been unable to figure out how to fix it.  When I try to run electricsheep from the command line I get:

```

CElectricSheep( )
CElectricSheep_Linux( )
Startup( )
SetInstallation: /usr/local/share/electricsheep/Scripts
WARNING: Application calling GLX 1.3 function "glXCreateWindow" when GLX 1.3 is not supported!  This is an application bug!
failed to create drawable
X Error of failed request:  BadDrawable (invalid Pixmap or Window paramenter!)
 Major opcode of failed request:  136 (XFree86-DRI)
 Minor opcode of failed request:  7 ( )
 Resource ide in failed request   0x1e00005
 Serial number of failed request:  71
 Current serial number in output stream:  71

```

It looks like I don't have GLX installed properly, or at least don't have the right version of it.  I checked the package manager and I've got the following GLX items installed:

libgl1-mesa-dev
libgl1-mesa-dri
libgl1-mesa-glx

There are several other GLX items that aren't installed on the list though, but I have no idea of what they do.

Also when I try to run electricsheep-preferences from the command line I get:

```

electricsheep-preferences: error while loading shared libraries: libwx_gtk2u_core-2.9.so.3: cannot open shared object file: No such file or directory

```

I'm not sure what that means but I'm guessing it has to do with the GLX issue.

---

### Post by Bobhuber on 2012-03-05
> **nullified_nostalgia said:**
> I was able to install it via the package manager, however I've so far been unable to make it function as a scrensaver or get any options to make it run as the desktop background.  So far all I've been able to do is make it run in windowed mode.  In maximized windowed mode using the "undecorate" option in the right click menu on the toolbar I've been able to make it fill most of the screen, but I would still like to have desktop functions, such as being able to see desktop icons and the ability to right click on the desktop.  It would also be nice for it to extend under transparent panels so it's basically filling the whole screen with the lubuntu gui running like normal above it.
You need to install it along with xwinwrap and xscreensaver.
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
If needed you can get the xwinwrap files here (looks like you already have what you need though if the above works) .

[http://tech.shantanugoel.com/resources/downloads/shantz-xwinwrap.zip](http://tech.shantanugoel.com/resources/downloads/shantz-xwinwrap.zip) 

Then run this.

xwinwrap -ni  -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/electricsheep -window-id WID 

Have fun !

---

