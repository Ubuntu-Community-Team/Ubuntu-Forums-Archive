---
title: "really newbie! want to migrate to ubuntu. help please"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by ziedrich on 2008-06-08
Hi, nice to meet u all ^^. im still newbie here about ubuntu. I want to migrate from windows to ubuntu. I want to ask "some"question.

1. I'm now using dual booting ubuntu and windows xp(not wubi). what's the different between using wubi or dual booting? 

2. I want to install build essensial but it said depends libc6-dev.. so i went to libc6-dev to install it, but it said depends libc6. so i went to libc6 but it has already installed.. so how i can install build-essensial?

3.when i wanted to install anjuta IDE using add/remove applications. it always said "Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?" and when I wanted to add another package the same things happen.

4.I wanted to install from .tar i have extracted them, but when I typed ./configure the following command was written

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

I don't know whether i have all dependencies. how to know whether i have all dependencies or not. thanks all ^^.

---

### Post by Rocket2DMn on 2008-06-08
1. Wubi installs Ubuntu to a file within windows, not a true separate partition.  It can be installed/uninstalled from within windows like a program.  A dual boot creates real partitions on the drive and we use GRUB to choose between the OSes.

2. Go to System->Administration->Software Sources and enable Universe and Multiverse Repositories (the top 4 boxes should probably be checked).

3.  Number two will likely fix this

4. This will be OK after you 
```
sudo apt-get install build-essential
```
What is it your are trying to install from a tarball?

---

### Post by nebu on 2008-06-08
1. wubi will install ubuntu in your windows partition(ntfs) like any other software... whereas in dual boot you will have to repartition your hard drive  to make space for ubuntu......


furthermore... in a wubi install --- the windows bootloader is the one in use whereas in dual boot u can use grub.... 

in a wubi install u will also be able to uninstall ubuntu like u do any other software

check out wikipwedia for more details

---

### Post by ziedrich on 2008-06-08
wow thanks alot to both of u..

when i open my system software source, i've already checked all the box, so I change the server to main server. and it all works. thanks ^^.

now i want to ask 
what is the alternative of this s/w that u recommend:
Borland/Dev-C C++ =
Microsoft VIsual Studio.Net =
Netbeans =
Download manager =
utorrent =
CD/DVD tools/burner =
Magic Iso =
Winrar =
Winavi video converter =

thanks ^^.

---

### Post by Rocket2DMn on 2008-06-08
Borland/Dev-C C++ = gcc is the open source C compilter, g++ is part of that (for C++)
Microsoft VIsual Studio.Net = .NET is a windows platform so you can't really program for it in linux.  You can write programs that work with GTK, libraries are available in different languages.
Netbeans = Eclipse is available for programming in Java.  C++ addon is also available.  There are also addons for other languages, though I'm not sure how good they are.
Download manager = Errr... firefox?
utorrent = Azureus (Java based, a little heavy), BitTorrent, ktorrent, rtorret, etc.
CD/DVD tools/burner = K3b (requires some KDE libraries).  Brasero disc burner should be available by default.
Magic Iso = What does this do, make ISOs?  Sorry, can't help you here, though I'm sure there are some.
Winrar = If you right click any file/folder you can select Create Archive.  You can then choose from a number of different archive types including zip, rar, tar (and tar.gz which is gzip compressed).  You can also use terminal to zip/rar/tar/gzip.
Winavi video converter = Sorry, no help here.

Also see:
[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.osalt.com/](http://www.osalt.com/)

---

### Post by ziedrich on 2008-06-08
> **Rocket2DMn said:**
> Borland/Dev-C C++ = gcc is the open source C compilter, g++ is part of that (for C++)
Microsoft VIsual Studio.Net = .NET is a windows platform so you can't really program for it in linux.  You can write programs that work with GTK, libraries are available in different languages.
Netbeans = Eclipse is available for programming in Java.  C++ addon is also available.  There are also addons for other languages, though I'm not sure how good they are.
Download manager = Errr... firefox?
utorrent = Azureus (Java based, a little heavy), BitTorrent, ktorrent, rtorret, etc.
CD/DVD tools/burner = K3b (requires some KDE libraries).  Brasero disc burner should be available by default.
Magic Iso = What does this do, make ISOs?  Sorry, can't help you here, though I'm sure there are some.
Winrar = If you right click any file/folder you can select Create Archive.  You can then choose from a number of different archive types including zip, rar, tar (and tar.gz which is gzip compressed).  You can also use terminal to zip/rar/tar/gzip.
Winavi video converter = Sorry, no help here.

Also see:
[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.osalt.com/](http://www.osalt.com/)

thanks. another question i want to install wine
i used sudo auto-apt run ./configure

but when the checking reached checking for X 
it said : 
Package libgtk-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk-perl has no installation candidate

so i downloaded the libgtk-perl but it said error : dependencies is not satisfiable libglib 1.2.. i went to synaptic and when i searched I only found libglib 1.2-dbg ,-dev, ldbl and were already installed.. please help me T_T.

---

### Post by halln on 2008-06-08
properties/add/remove/change the drop down menu to all open source/search for wine/apply/bingo!

---

### Post by Rocket2DMn on 2008-06-08
I prefer to get wine direct from their repositories, see here - [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)
You certainly don't have to compile it from source!

---

### Post by ziedrich on 2008-06-08
ngg.. so is it better to download from add/remove applications than from source file? 
How if I don't connected to the internet? if i use add/remove, it depends on the internet doesn't it? btw, if i use dvd repo should i connect to the internet too? or the dependencies are already there?

---

### Post by macness on 2008-06-08
> **ziedrich said:**
> ngg.. so is it better to download from add/remove applications than from source file? 
How if I don't connected to the internet? if i use add/remove, it depends on the internet doesn't it? btw, if i use dvd repo should i connect to the internet too? or the dependencies are already there?

it's always better to use add/remove or synaptic because you will always have your software up-to-date.  I hardly ever resort to compiling it unless there's an update that I desperately want or if something is not available in the repositories.:)

Now of course this works great when you're connected to the internet... otherwise ... YIPES!  You'll need to check for dependencies every time.  You can find what package dependencies are needed @ packages.ubuntu.com.

Is dvd repo a package?:confused:

---

### Post by cariboo on 2008-06-08
Not connecting to the internt may be why you are having so many problems, you may be using outdated files on your dvd repository. The repositories are updated almost daily.

Jim

---

### Post by Rocket2DMn on 2008-06-08
Most people prefer to use Synaptic Package Manager (from System->Administration), it is a great tool for installing packages.  If your computer doesn't have internet connection, it can be very difficult to get updates or updated packages, but there are options.
The first option is to use an Alternate Install cd or a DVD installer as a repository (I don't think the LiveCD works as a repository, though it might these days).  Simply put the CD into the drive and go to System->Administration->Software Sources to add the cd as a repository.  The terminal command to enable it would be
```
sudo apt-cdrom add
```
Here are some useful links:
[https://help.ubuntu.com/community/InstallingSoftware#head-14060f8896fc0efa378412ca379a89c8c332da14](https://help.ubuntu.com/community/InstallingSoftware#head-14060f8896fc0efa378412ca379a89c8c332da14)
[https://help.ubuntu.com/community/Synaptic/Offline](https://help.ubuntu.com/community/Synaptic/Offline)
[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

Some of them are a little confusing or strange, but you don't need to make it complicated.  The easiest thing to do is plug into the internet if possible, get your system setup the way you like it, then disconnect from the web and don't worry too much about updates.  If you get a chance later, you can connect and download updates.  IF you find that you need to install other programs, try just getting the .deb file from the repos and transferring it to the offline machine.  If other dependencies are needed you can get those, too.  If it just gets too complicated, try some of the more advanced methods.

---

### Post by ziedrich on 2008-06-08
wow, i c so it essential needs to connect to the internet to add/remove s/w.. dvd repo means dvd repositories include all universe,multiverse,restricted,and main. i don't know is it a package or source file, because i don't have it. he8. 

btw when i Used wine, i wanted to open adobe dreamweaver CS3 but it wouldn't open. after clicked it nothing happen, but when i clicked adobe photoshop cs3, it was loaded but only the opening and then.. closed.. is it because wine is not perfect right now?

---

### Post by avtolle on 2008-06-08
Wine is indeed "not perfect". There is a place to view Windows programs that run under Wine, but I don't have the link. A Google search would no doubt find it for you.

---

### Post by Rocket2DMn on 2008-06-08
> **ziedrich said:**
> wow, i c so it essential needs to connect to the internet to add/remove s/w.. dvd repo means dvd repositories include all universe,multiverse,restricted,and main. i don't know is it a package or source file, because i don't have it. he8. 

btw when i Used wine, i wanted to open adobe dreamweaver CS3 but it wouldn't open. after clicked it nothing happen, but when i clicked adobe photoshop cs3, it was loaded but only the opening and then.. closed.. is it because wine is not perfect right now?

That's right, wine is far from perfect. For program compatibility, see [http://appdb.winehq.org/](http://appdb.winehq.org/)
For those specific programs:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=76](http://appdb.winehq.org/objectManager.php?sClass=version&iId=76)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)
They don't seem to work very well under wine.  If you are set on using these programs, you need to keep a dual boot system, or run Windows inside of a Virtual Machine (VM).  For help on setting up a VM, see [http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux) (this requires more RAM since you are essentially running two operating systems at once, so it is not very useful on computers more than a few years old).

---

### Post by ziedrich on 2008-06-08
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

when i saw that sites, the table shows install? and Runs? i dont get it what those mean. if i want to use wine should i install the s/w to wine virtual drive? or just can run from another partition (windows partition).

btw if i want to move my Ubuntu to another harddisk, should I download again what I have installed? because if I install from add/remove it automaticly installed in my system. or in add/remove s/w we can save the package to reinstall the s/w? 

and i use ubuntu in my asus w7j, why the sound is too small even i maximized the player n my audio. could it be a problem with the driver?

sorry if i asked a lot of questions >.<. thanks all.

---

### Post by Rocket2DMn on 2008-06-08
You need to install to you wine virtual drive because this is where the program looks for windows libraries.  It is unlikely to work by running it from the windows partition.

Basically, people are saying that some parts of the process works, like the program will install, but after that, they can't actually use it.  This might be because it shows in the taskbar for a second, then just disappears.  If you run the program from terminal, you will get a whole bunch of output, but unless you are troubleshooting, it isn't much good.  Since we know these programs don't really work, we won't try that.

There are methods to move an entire Ubuntu installation to another disc, which is called ghosting.  You usually need a separate program for this.  This moves all your programs, data, configurations, etc. to another drive without having to reinstall.  If you have to do this, you should start another help thread so somebody with more experience with that can help you out.

For your sound, there should be a little sound icon in one of your taskbars.  Right click that and select Open Volume Control.  This is very similar to the one in windows where you can adjust different channels, like Master.  Remember, there are different devices, check File->Change Device to be sure you are using the same one select in System->Preferences->Sound.  You may need to fiddle around a bit to get it right.

---

### Post by ziedrich on 2008-06-11
i c. thanks!Now I can't click ctrl+f to search words in my mozilla firefox in ubuntu. but if I click Edit and then click Find it works, but why I can't use ctrl+f? Both Mozilla 3 and mozilla 2 not working using ctrl+f.

btw can i auto-mount my another partition when ubuntu startup?

---

### Post by billgoldberg on 2008-06-11
utorrent = standard installed transmission is good, else -> deluge
CD/DVD tools/burner = brasero installed by default, or else K3b
Winrar = p7zip-full
Winavi video converter = winff (google for winff and download the ubuntu .Deb) (you'll need the ffmpeg package from the medibuntu repo before you install it though, see note)



Note: 
You might want to check some of the links in my sig, like "media" before you start installing programs.

---

### Post by ziedrich on 2008-06-14
I want to ask, what are the differetns between GNOME and KDE? I've installed amarok, and it was written for KDE. but i can still use it with GNOME. what's different with GNOME and KDE?

when a s/w was installed in windows, it goes to Program Files (default), so where was that installed s/w goes in Ubuntu?

Can I pass the password permission for administrative task? so, i don't need to input password again n again. if i can, how?

sorry i have to repost this.

I can't click ctrl+f to search words in my mozilla firefox in ubuntu. but if I click Edit and then click Find it works, but why I can't use ctrl+f? Both Mozilla 3 and mozilla 2 not working using ctrl+f.

btw can i auto-mount my another partition when ubuntu startup?

---

### Post by Rocket2DMn on 2008-06-14
Gnome and KDE are two different desktop environments - different interfaces to interacting with the desktop.  Just like Gnome looks different from Windows, KDE looks different from both of them.  It's all a matter of preference, but most people use Gnome since it is the default with Ubuntu.  When people use KDE, we call that Kubuntu.

When you install software, it can usually be accessed from the Applications menu in the upper left part of your screen in Gnome.  Non-GUI programs will not be here, you have to run those from terminal.

You cannot get around the password entry to administrative tasks - this exists to remind you that you are working in an area that can affect your computer, not just general user preferences, and that caution should be taken when fiddling around in that area since it can have the potential to cause problems or harm to your system if you use incorrect settings.

For these last two questions, you should start new threads in the Absolute Beginner Talk section of the forums - [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

Good luck, and welcome to Ubuntu.

---

### Post by ziedrich on 2008-06-15
So the differents between GNOME and KDE is their interfaces, not with their s/w? I mean, KDE can use same s/w that GNome use and vice versa?

I've installed Eclipse via terminal not from remove/add application. I can use eclipse, but its'not in Application menu. So what is that mean?

thanks!

---

### Post by Rocket2DMn on 2008-06-15
Some applications are independent of the desktop environment, but some are designed to run in specific ones.  Ex: amaroK is designed for KDE, GParted and gedit are designed for Gnome.  Eclipse is independent.
You can run apps from the other desktop environment as long as you have their libraries installed, so the first time you install something for the opposite environment, it will have dependencies on possibly hundreds of megs of libraries which will be automatically downloaded through Synaptic (or apt-get).

---

### Post by rpisharody on 2008-06-15
zeidrich, 

For making the ISO images of CDs you have, you can use the dd command in GNU/Linux

Here's the command

```
dd if=/dev/scd0 of=location_to_save_the_file
```

where  "/dev/scd0" is the name of my CD Device.
Just run the "mount" command in the terminal to find out the name of your CD Drive. It'll show a name similar to "/dev/scd0 mounted at..."

you may have to prefix the dd command with sudo

And inorder to mount the created ISO Image file, use

```
mount -o loop -t iso9660 /dev/scd0 /path_where_to_be_mounted
```

where /dev/scd0 denotes the drive. 

You can browse your ISO contents from /path_where_to_be_mounted

Regards,
rpisharody

---

### Post by ziedrich on 2008-06-16
> **Rocket2DMn said:**
> Some applications are independent of the desktop environment, but some are designed to run in specific ones.  Ex: amaroK is designed for KDE, GParted and gedit are designed for Gnome.  Eclipse is independent.
You can run apps from the other desktop environment as long as you have their libraries installed, so the first time you install something for the opposite environment, it will have dependencies on possibly hundreds of megs of libraries which will be automatically downloaded through Synaptic (or apt-get).

btw I can run eclipse, but it's not in application menu, can I apply Eclipse to Applications?

btw I can't suspend my notebook using ubuntu.. it says error bla8.. and I can't return to desktop.. so i have to shut it down T_T... please help..
(or it's because i don't use swap space? (I'm using swap file))

I've downloaded template for openoffice, how can I add it to openoffice?

Many2 thanks^^.

---

### Post by Rocket2DMn on 2008-06-17
For your Eclipse menu problem, right click the Applications menu and hit Edit Menus.  Under Applications, make sure the Programming menu is enabled by looking inside of it to enable something within it (like Eclipse).

You should start new threads for your suspend and OO.org problems.  Good luck!

---

### Post by ziedrich on 2008-06-17
thanks!
I've enabled Programming but still there is no Eclipse in Programming Menu.. So I added it up to programming menu manually.. and it works. but the Icon isn't eclipse icon.. can I change the icon?

---

### Post by Rocket2DMn on 2008-06-17
> **ziedrich said:**
> thanks!
I've enabled Programming but still there is no Eclipse in Programming Menu.. So I added it up to programming menu manually.. and it works. but the Icon isn't eclipse icon.. can I change the icon?

Yes, get to the Edit Menus, choose Programming and right click the Eclipse entry.  Choose Properties.  Now click the icon on the upper left, and it will popup with a window to Browse icons.  Copy and paste in 
```
/usr/share/pixmaps/eclipse.png
```
then click OK.  Close the Properties window, and you should now have the icon.

---

### Post by ziedrich on 2008-06-20
wow. thanks. btw why when I play .3gp, .wmv file with totem, or vlc, it doesn't have a sound? could i have to install another file?

---

### Post by Rocket2DMn on 2008-06-20
Yes, you need extra codecs.  See [uhelp]community/Medibuntu[/uhelp] for more information.  You will be interested in w32codecs and libdvdcss2.

---

### Post by ziedrich on 2008-06-22
I've installed w32codecs.. but it still won't work.. after installation should I do anything else?

---

### Post by Rocket2DMn on 2008-06-23
You may need to start a new thread for your sound problems, I'm not very good with those questions, unfortunately.  You can post here in the Absolute Beginners section or try the Multimedia & Video forum - [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)
Good luck.

---

