---
title: "Start-Up Manager"
date: 2006-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Jimmy_r on 2006-11-08
StartUp-Manager, or SUM, is a python-glade gui tool for configuring some things in grub and usplash.

*****WARNING*****
If you are unlucky, this tool could make your system unable to start. USE IT ON YOUR OWN RISK!
It is tested with Debian and with Ubuntu and Kubuntu, versions Breezy, Dapper(Breezy and Dapper needs version 1.0.2: [http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.2-2_all.deb](http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.2-2_all.deb) ), Edgy and Feisty.

**Installation instructions **
Short: Install the deb from [http://web.telia.com/~u88005282/sum/downloads.html](http://web.telia.com/~u88005282/sum/downloads.html)

Detailed: at [http://web.telia.com/~u88005282/sum/installation.html]("http://web.telia.com/~u88005282/sum/installation.html")

2007-01-04: SUM has got a new home:[http://web.telia.com/~u88005282/sum/index.html]("http://web.telia.com/~u88005282/sum/index.html")

2007-06-19: Bugreports, questions and(soon) possibility to help translate at [https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)

---

### Post by wakady on 2006-11-08
Nice work man
i like it & will test it now :)

---

### Post by Mr. Picklesworth on 2006-11-09
Yes, quite excellent. This is a much-needed config tool.

I say you try to get this in the official repos!

Here's a feature request, if you're still thinking about it:
How about a section to to create a GRUB boot disk? (So I could install GRUB, with the appropriate configuration to boot Ubuntu, to a floppy disk, for instance).

---

### Post by autocrosser on 2006-11-09
You might want to get together with Dennis Kaarsemaker--He created Usplash-Switcher & as far as I know, is planning to include it in Fawn--Sounds like you have some code in common--Dennis was one of the people involved with Usplash development. I have suggested a couple of extra options for Switcher & he asked me to create a Launchpad "bug" for the notes---located at: 
[https://launchpad.net/bugs/70954](https://launchpad.net/bugs/70954)

Edit: The more I look at SUM--the more I think you & Dennis should talk-----

---

### Post by jimbren on 2006-11-15
SWEET

I've been annoyed ever since I did a dist-upgrade to Edgy because I lost my splash screen altogether, along with any boot text.  It also took about twice as long for my machine to boot up for some reason.  I checked the forums, and the boot time issue was shared by other folks who lost their usplash screens.  

I had tried a couuple of solutions posted to the forums, but they didn't work.  Yesterday [I found this post on Debianadmin.com]("http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html"), which talked about the boot up manager.  

I tried BUM with the instructions on debianadmin, and it worked!  I get my splash screen back. I'm still not seeing boot status messages, but boot time is about twice as fast as it was.

And now I don't feel the need to install from CD.


Thanks!


jimbo

---

### Post by Jimmy_r on 2006-11-20
> Nice work man
i like it & will test it now
Thanks. please report any bugs you may find.

> Yes, quite excellent. This is a much-needed config tool.

I say you try to get this in the official repos!

Here's a feature request, if you're still thinking about it:
How about a section to to create a GRUB boot disk? (So I could install GRUB, with the appropriate configuration to boot Ubuntu, to a floppy disk, for instance).

Thanks.
I want to keep sum more "newbie-friendly" than "poweruser-friendly"...
More Gnome than Kde, if you know what I mean...
Still, I will think about it.

> You might want to get together with Dennis Kaarsemaker--He created Usplash-Switcher & as far as I know, is planning to include it in Fawn--Sounds like you have some code in common--Dennis was one of the people involved with Usplash development. I have suggested a couple of extra options for Switcher & he asked me to create a Launchpad "bug" for the notes---located at:
[https://launchpad.net/bugs/70954](https://launchpad.net/bugs/70954)

Edit: The more I look at SUM--the more I think you & Dennis should talk-----


I will look into it.

> 
SWEET

I've been annoyed ever since I did a dist-upgrade to Edgy because I lost my splash screen altogether, along with any boot text. It also took about twice as long for my machine to boot up for some reason. I checked the forums, and the boot time issue was shared by other folks who lost their usplash screens.

I had tried a couuple of solutions posted to the forums, but they didn't work. Yesterday I found this post on Debianadmin.com, which talked about the boot up manager.

I tried BUM with the instructions on debianadmin, and it worked! I get my splash screen back. I'm still not seeing boot status messages, but boot time is about twice as fast as it was.

And now I don't feel the need to install from CD.


Thanks!


jimbo

I'm glad you had use for it.

---

### Post by Jimmy_r on 2006-11-20
Okay, bumped to new version(sum_0.9-1_all.deb). Please try it out, and report any bugs you may find.
Also, you may want to backup your menu.lst if you have not done so already.

---

### Post by Jimmy_r on 2006-11-22
New version(sum_0.9-2_all.deb).
2 Bugfixes done.
0 Known bugs remaining.

---

### Post by Deathmoon on 2006-11-26
:D 
Ok, after hours of trying to get my usplash back I am so glad.  This tool is great!  Thank you!!!

---

### Post by Leonivek on 2006-11-26
> **Deathmoon said:**
>  
Ok, after hours of trying to get my usplash back I am so glad.  This tool is great!  Thank you!!!
Same here!  I lost my usplash a while back and this is the only thing that fixed it!  I tried a lot of other ways described in this forum, too.

Thank you for this great tool! :-D

---

### Post by Chinello Cybernético on 2006-11-27
Hi, to use it, I had to this:

- edit manually the option "vga" in the /usr/bin/startup-manager.py (I put 791)
- insert the color name "blink-red" on 'color_dict' vector in the 'convert_color' method, in startup-manager.py
- insert the color label "Blink-red" two times in the /usr/share/startup-manager/sum.glade

Now I will reboot for test my new conf ;)

---

### Post by pavel_kbc on 2006-11-27
and you didnt come back

---

### Post by dotsi on 2006-11-28
There seems to be something wrong with the script, at least in my case.

When trying to start Start-Up Manager from the menus, it just blinks on the screen and then closes. Starting it from the terminal gives this:

```
$ sudo /usr/bin/startup-manager.py
Password:

(startup-manager.py:10556): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Traceback (most recent call last):
  File "/usr/bin/startup-manager.py", line 649, in ?
    sumGui = SumGui()
  File "/usr/bin/startup-manager.py", line 642, in __init__
    self.update_widgets()
  File "/usr/bin/startup-manager.py", line 568, in update_widgets
    self.timeout_spinner.set_value(Config.timeout)
TypeError: a float is required
```

Any hints?

---

### Post by pavel_kbc on 2006-11-28
wow its seem. its great . i like it . Thank you . by the way its works for me as well i guess . not so sure :P

---

### Post by Jimmy_r on 2006-11-28
> **Chinello Cybernético said:**
> Hi, to use it, I had to this:

- edit manually the option "vga" in the /usr/bin/startup-manager.py (I put 791)
- insert the color name "blink-red" on 'color_dict' vector in the 'convert_color' method, in startup-manager.py
- insert the color label "Blink-red" two times in the /usr/share/startup-manager/sum.glade

Now I will reboot for test my new conf ;)

New version attached(sum_0.9-4_all.deb).
This new version should be able to properly handle the "blink-" option.

Why did you need to specify 791 for vga?
And where(which line) did you specify it?

---

### Post by Jimmy_r on 2006-11-28
> **dotsi said:**
> There seems to be something wrong with the script, at least in my case.

When trying to start Start-Up Manager from the menus, it just blinks on the screen and then closes. Starting it from the terminal gives this:

```
$ sudo /usr/bin/startup-manager.py
Password:

(startup-manager.py:10556): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Traceback (most recent call last):
  File "/usr/bin/startup-manager.py", line 649, in ?
    sumGui = SumGui()
  File "/usr/bin/startup-manager.py", line 642, in __init__
    self.update_widgets()
  File "/usr/bin/startup-manager.py", line 568, in update_widgets
    self.timeout_spinner.set_value(Config.timeout)
TypeError: a float is required
```

Any hints?

Hm, either you have a corrupted "timeout" line, or it has some value which I have not thought about.
Please post your /boot/grub/menu.lst

---

### Post by Sciamano on 2006-11-28
Sweet! I now have the usplash back, that disappeared after upgrading to Edgy Eft! Thanks!

---

### Post by pavel_kbc on 2006-11-28
uninstalled .its not good . dont install this scripts :)

---

### Post by Jimmy_r on 2006-11-29
> **pavel_kbc said:**
> uninstalled .its not good . dont install this scripts :)

?
There is something called reporting bugs. Do you feel like doing so?
What did not work?

Edit: Now i understand:
> **pavel_kbc said:**
> nothing works for me i give up :( ubuntu sucks on few way..
I think the bug just autoclosed, thank you for your cooperation.

---

### Post by dotsi on 2006-11-29
> **Jimmy_r said:**
> Hm, either you have a corrupted "timeout" line, or it has some value which I have not thought about.
Please post your /boot/grub/menu.lst

I solved the case by myself: I had commented out the timeout line at some point, so that must've been it. Without the # Start-Up Manager starts up just nicely. Can this be considered as a bug report of some sort? :)

---

### Post by Jimmy_r on 2006-11-29
> **dotsi said:**
> I solved the case by myself: I had commented out the timeout line at some point, so that must've been it. Without the # Start-Up Manager starts up just nicely. Can this be considered as a bug report of some sort? :)

It surely can. I am looking into it right now.
Edit: New version uploaded. It should be able to handle commented-out timeouts.

---

### Post by Slarty Bardfast on 2006-11-29
Ok, here's what I've got when I try to run SUM. This IS Edgy AMD64, is there known problems with 64 bit? Or would this be something in the menu.lst I need to change? I did notice I had the timeout value set twice but I took the second one out and got the same errors. Here's what it says:

```

(startup-manager.py:9534): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Traceback (most recent call last):
  File "/usr/bin/startup-manager.py", line 728, in ?
    sumGui = SumGui()
  File "/usr/bin/startup-manager.py", line 719, in __init__
    read_config()
  File "/usr/bin/startup-manager.py", line 177, in read_config
    evaluate(line)
  File "/usr/bin/startup-manager.py", line 84, in evaluate
    Config.default_boot=int(strip_line(line, 7, None, True))
ValueError: invalid literal for int(): =0

```

I'm fairly newbish so I hope it's not something way too obvious ](*,) 

Thanks!

---

### Post by Slarty Bardfast on 2006-11-29
Woooahp. ok, nevermind. It looks like this was caused because I had the "Default 0" set in my menu.lst. I commented it out (which'd default to 0 anyway) and it looks like it's working.

Now, let's see if I can get that cheesy Iron Maiden Usplash I had in Dapper back..... :p

---

### Post by Jimmy_r on 2006-11-30
> Woooahp. ok, nevermind. It looks like this was caused because I had the "Default 0" set in my menu.lst
Hm, default 0 should work without problems.

However, the last line in your backtrace:
```
ValueError: invalid literal for int(): =0
```

Leads me to belive that your default line says(notice the '=') :
```
default=0
```
Am I right?
Edit:New version uploaded(sum_0.9-6_all.deb)
It should be able to handle those things.

---

### Post by jcoats on 2006-12-01
I've installed the program and it is listed as being installed ok on my system.  When I try to run it the program opens and then closes immediately.  Any ideas???

---

### Post by jcoats on 2006-12-01
Ignore the problem that I posted above.  When I ran it from the command-line I saw that the error was that /etc/usplash.conf did not exist.  So after "sudo touch /etc/usplash.cong" everything works fine:)

---

### Post by Jimmy_r on 2006-12-02
Ignore it, I will not...
A bug is a bug, expect a fix in the next version.
Edit:Fix uploaded(sum_0.9-6_all.deb)

---

### Post by Jimmy_r on 2006-12-02
A qt4 version is in the works for our KDE-using friends.
Here is a screenshot:
[ATTACH]20360[/ATTACH]
Note that it will not be ready for quite some time, this is just from a preview in qt designer.
Heck, I have not even decided if I will code it in Python and reuse the code from SUM, or do it in C++(before questioning my mental sanity,
note that I started this project for learning and it is about time I see how much of my C++ knowledge has gone AWOL).

Edit:Ok, I will NOT do it in C++... 
I just made an unrelated one-day project in QT/C++ and it made me remember why I did move to Java a few years ago...
C/C++ have their place, and fortunately this is not it :p

---

### Post by Sokraates on 2006-12-04
> **Jimmy_r said:**
> A qt4 version is in the works for our KDE-using friends.

Cool. I've already tried SUM on Kubuntu Edgy and after installing some dependencies for gtk or whatever it worked very well.

Two thumbs up. 

Have you already talked with someone to have SUM included in Feisty? Universe looks realistic, I think.

**Edit:** Okay, I just saw your post to the graphical-grub-spec.

---

### Post by robconscient on 2006-12-05
> **Sokraates said:**
> Cool. I've already tried SUM on Kubuntu Edgy and after installing some dependencies for gtk or whatever it worked very well.

I just installed Kubuntu and would like to use SUM as well. Any chance you could let me know what dependencies I need to install as well? 

Thanks!

Rob

---

### Post by Sokraates on 2006-12-06
I used the right-click-menu to install the *.deb. Right click on the file, choose "Kubuntu Package Menu" -> "Install Package", then an xterm-window will pop up, ask for your password, then the installation will begin.

If you don't have it, there's something wrong with your installation (Kubuntu Package Menu is part of Kubuntu-default-settings since Breezy). But you can nevertheless simply open a console, move to the directory containing the file and type
```
sudo dpkg -i *filename*.deb
```Of course the installation will fail, but the dependencies will be listed. Even better: when using the right-click-menu, the dependencies will be marked for installation, so you don't need to write them down, just start your favorite package-manger and apply the changes (usually I'm using Synaptic but I think in this case I used aptitude and it worked).

---

### Post by pavel_kbc on 2006-12-10
> **Jimmy_r said:**
> ?
There is something called reporting bugs. Do you feel like doing so?
What did not work?

Edit: Now i understand:

I think the bug just autoclosed, thank you for your cooperation.

i am sorry for everything . can i use it with gfxgrub?

---

### Post by Jimmy_r on 2006-12-10
> **pavel_kbc said:**
> i am sorry for everything . can i use it with gfxgrub?

Its ok, i was in a bad mood...

I have never used gfxgrub myself, so SUM will not be able to do any configurations specific for gfxboot.
Using SUM to edit non-gfxboot-related things alongside it should not mess anything up, I think. I cannot guarantee anything though...

---

### Post by xabbott on 2006-12-15
Jimmy_r, just wanted to say thanks. This is an awesome lil app.

---

### Post by earobinson on 2006-12-15
Having problems with the install ```
earobinson@NaN:~/Desktop/downloads$ sudo dpkg -i sum_0.9-6_all.deb 
Selecting previously deselected package sum.
(Reading database ... 196264 files and directories currently installed.)
Unpacking sum (from sum_0.9-6_all.deb) ...
dpkg: dependency problems prevent configuration of sum:
 sum depends on imagemagick; however:
  Package imagemagick is not installed.
dpkg: error processing sum (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sum
```

Im able to fix this by installing imagemagick, just letting you know, I know some installers auto install dependencies

---

### Post by two-sheds on 2006-12-16
I get the following error from gksu -k /usr/bin/startup-manager.py:

Traceback (most recent call last):
  File "/usr/bin/startup-manager.py", line 743, in ?
    sumGui = SumGui()
  File "/usr/bin/startup-manager.py", line 736, in __init__
    self.update_widgets()
  File "/usr/bin/startup-manager.py", line 658, in update_widgets
    self.normal_background_combo.set_active(convert_color(Config.normal_background, 0, False))
  File "/usr/bin/startup-manager.py", line 277, in convert_color
    return color_dict[color]
KeyError: ''

---

### Post by Jimmy_r on 2006-12-17
> **two-sheds said:**
> I get the following error from gksu -k /usr/bin/startup-manager.py:

Traceback (most recent call last):
  File "/usr/bin/startup-manager.py", line 743, in ?
    sumGui = SumGui()
  File "/usr/bin/startup-manager.py", line 736, in __init__
    self.update_widgets()
  File "/usr/bin/startup-manager.py", line 658, in update_widgets
    self.normal_background_combo.set_active(convert_color(Config.normal_background, 0, False))
  File "/usr/bin/startup-manager.py", line 277, in convert_color
    return color_dict[color]
KeyError: ''

New version uploaded. Try it and let me know if it resolves your problem.

---

### Post by two-sheds on 2006-12-17
> **Jimmy_r said:**
> New version uploaded. Try it and let me know if it resolves your problem.

Yes it did.  Thank You.

:)

---

### Post by Nephrolithiasis on 2006-12-20
Jimmy where is the link to the downloadable files?

Neph

---

### Post by jincast90 on 2006-12-20
This looks really neat. Unfortuantly I don't have time for installing it now, but I might have in the weekend.

---

### Post by ezak on 2006-12-20
Nice work Jimmy_r, hope you keep going with this project and hopefully catch the eye of the ubuntu dev team. This tool is exactly what I was looking for most as far as customization goes. There isn't alot of well documented features around the net for a lot of the options here, which makes this tool definately something to keep and progress with. Hope to see the project continue on.

---

### Post by Jimmy_r on 2006-12-21
> **Nephrolithiasis said:**
> Jimmy where is the link to the downloadable files?

Neph

They are attached at the bottom of the first post in this thread.

---

### Post by Jimmy_r on 2006-12-21
> **ezak said:**
> Nice work Jimmy_r, hope you keep going with this project and hopefully catch the eye of the ubuntu dev team. This tool is exactly what I was looking for most as far as customization goes. There isn't alot of well documented features around the net for a lot of the options here, which makes this tool definately something to keep and progress with. Hope to see the project continue on.

Thanks. I have been busy lately, but yesterday I started writing code for the qt version.
Currently I plan to split the code into three packages:sum-base, sum-gtk and sum-qt.
That way I will not have to do a lot of double-work to fix bugs and add new features(and adapt it for grub2 in (hopefully)feisty+1).

Then I need to figure out a better way for kde users and others without gdebi to install it. Probably a repository would be the best way.

---

### Post by n3Cre0 on 2006-12-21
Hehe it ****** up my /boot/grub/menu.lst :)
Luckily I got about 5 backups of it.

Just a little warning ;)

---

### Post by Jimmy_r on 2006-12-21
> **n3Cre0 said:**
> Hehe it ****** up my /boot/grub/menu.lst :)
Luckily I got about 5 backups of it.

Just a little warning ;)

:shock: :-k 

What did it mess up? Could you please post a functional and a "messed up" menu.lst to help me find the bug?

---

### Post by n3Cre0 on 2006-12-26
Ok sure.

So I just installed the latest .deb

This is my heavily modified menu.lst (manually edited partitions + gfxboot).

> gfxmenu /boot/grub/message.snow # the suse can be replaced
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
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=66c622ab-625c-47b3-92a5-640ebe163cb0 ro
# kopt_2_6=root=/dev/sda9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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
# defoptions=quiet splash vga=792

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title           Microsoft Windows XP - Multimedia
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu Edgy Eft - Universiteit
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda8 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu (Recovery Mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda8 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Back|Track 2 Beta - Security 
root            (hd0,6)
kernel          /boot/vmlinuz root=/dev/sda7
initrd          /boot/splash.initrd 
savedefault
boot


Then I edited the resolution when booting en clicked "Close."

---

### Post by n3Cre0 on 2006-12-26
This is my modified menu.lst
> gfxmenu /boot/grub/message.snow # the suse can be replaced
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
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=66c622ab-625c-47b3-92a5-640ebe163cb0 ro
# kopt_2_6=root=/dev/sda9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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
# defoptions=splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,8)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda9 ro splash vga=795
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,8)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda9 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


Dunno if this helps you because I said I had already heavily modified it but you asked 


-- 

SORRY for the double-post.

But I kept getting this ANNOYING message
> You have included 13 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

---

### Post by Jimmy_r on 2006-12-26
Ok, as long as what you were trying to do was to:
[LIST]
[*]change resolution to 1280x1024 24 bit
[*]enable boot text
[/LIST]

Sum behaved just as it should(well, I maybe could add a check for the missing line(see below) and have a warning popup or something...).

What messed up your menu.lst was the update-grub(by Debian) command, which is called from sum.

In your original menu.lst, you missed this line:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

```

Note that it was automatically added to your second("messed up") menu.lst.

That line tells update-grub that any entries below it should not be overwritten.

I recommend(not only for the sake of SUM, the rest of the system uses update-grub too) that you add that line to your menu.lst, above your custom boot entries.
Something like this:

..snip...
```
## ## End Default Options ##

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP - Multimedia
root (hd0,0)
savedefault
makeactive
chainloader +1

```
...snip...

Then everything below the added line should be preserved.

Next, I wonder if the automatically generated boot options were bootable?

If not:
This line:
```
# groot=(hd0,8)
```
Is used in the auto-generation process. It appears as your ubuntu partition should be hd0,7:
```
title Ubuntu Edgy Eft - Universiteit
root (hd0,7)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda8 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

In that case, change groot to reflect this and autogeneration via SUM(and update-grub) should work.

---

### Post by n3Cre0 on 2006-12-26
Wow ty very much on pointing that update-grub out (possibly explains why my system was messed up so badly after a kernel-update).

I thought ## were just comments so I might aswell edit them out.

I'll update my menu.lst asap when I have time.

Thanks again Jimmy_r :)

edit:

> gfxmenu /boot/grub/message.snow # the suse can be replaced
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
default         saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=66c622ab-625c-47b3-92a5-640ebe163cb0 ro
# kopt_2_6=root=/dev/sda9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda9 ro quiet splash vga=795
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda9 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP - Multimedia
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu Edgy Eft - Universiteit
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda8 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu (Recovery Mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda8 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Back|Track 2 Beta - Security 
root            (hd0,6)
kernel          /boot/vmlinuz root=/dev/sda7
initrd          /boot/splash.initrd 
savedefault
boot


After SUM. Do you advise in moving the ubuntu partition lines above the end of.. line?

Thnx again

---

### Post by Jimmy_r on 2006-12-26
Oops :) 
You need to change these lines too to get the right autogeneration:
```
# kopt=root=UUID=66c622ab-625c-47b3-92a5-640ebe163cb0 ro
# kopt_2_6=root=/dev/sda9 ro
```

do a ```
sudo vol_id -u /dev/sda8
``` to get the UUID.

```
# kopt=root=UUID=(YOUR UUID) ro
# kopt_2_6=root=/dev/sda8 ro
```

---

### Post by n3Cre0 on 2006-12-27
Hmm is there something else that SUM modifies except for menu.lst?

Because it was the only thing I messed around with yesterdday and now when I boot Ubuntu I cannot see the splash :(

Judging from the sounds (the loginscreen sound) it does boot, but I just can't see it! It's just a black screen but when I type in my login I can hear the succesfull login sound and but my screen keeps being black  :???: 
When I restart xorg by ctrl shift backspace it stays black.

However I can boot my recovery mode just fine and I copied my backed up xorg.conf and menu.lst to their appropriate places (/etc/X11/xorg.conf & /boot/grub/menu.lst) but when I rebooted and selected Ubuntu I still couldn't see anything. - All I see it the few lines of debugging when you select an OS in grub (with the location etc) and that's all. From then on it's just plain black.

Do you know if SUM caused this? And if so (and if not) do you know a solution? I really need my screen back :'(

EDIT: Ok strange. I just removed (in the bootmenu - select an os and hit 'e' instead of enter) "quiet" and "splash" from my bootoptions and it booted fine now. - with debugging

Dunno what was wrong - anyways I like this much more then just a normal splash screen - now I can actually see what it is processing

---

### Post by steveandarchie on 2006-12-27
It looks like a great idea but I seem to be having problems with it. Is there a simple way of taking this off my system after a botched install? I have Edgy Ubuntu running with an option to start up in an Xubuntu environment.

I followed the install instructions but I double clicked the install.sh file (in true windows fashion) because I couldn't follow the other suggestion. The program doesn't appear as an option and since then the computer won't shut down - it just restarts and I have to pull the plug. I have also lost Synaptic and I'm tole to run 'dpkg --configure -a' to sort it out.

I'm loathe to work my way out of this so I just want rid of it until I know what I'm doing - can't remove it through Synaptic because it's broken.

Many thanks

---

### Post by Jimmy_r on 2006-12-27
> **n3Cre0 said:**
> Hmm is there something else that SUM modifies except for menu.lst?

Because it was the only thing I messed around with yesterdday and now when I boot Ubuntu I cannot see the splash :(

Judging from the sounds (the loginscreen sound) it does boot, but I just can't see it! It's just a black screen but when I type in my login I can hear the succesfull login sound and but my screen keeps being black  :???: 
When I restart xorg by ctrl shift backspace it stays black.

However I can boot my recovery mode just fine and I copied my backed up xorg.conf and menu.lst to their appropriate places (/etc/X11/xorg.conf & /boot/grub/menu.lst) but when I rebooted and selected Ubuntu I still couldn't see anything. - All I see it the few lines of debugging when you select an OS in grub (with the location etc) and that's all. From then on it's just plain black.

Do you know if SUM caused this? And if so (and if not) do you know a solution? I really need my screen back :'(

EDIT: Ok strange. I just removed (in the bootmenu - select an os and hit 'e' instead of enter) "quiet" and "splash" from my bootoptions and it booted fine now. - with debugging

Dunno what was wrong - anyways I like this much more then just a normal splash screen - now I can actually see what it is processing

Well when you change the resolution, sum also changes the /etc/usplash.conf
Then it runs ```
update-initramfs -u
```

If you want your usplash back again later(verbose usplash is possible), make sure /usr/lib/usplash/usplash-artwork.so points to a valid usplash theme, You should be able to do this through SUM. Then play around with the resolutions and color depths until something works.

---

### Post by Jimmy_r on 2006-12-27
> **steveandarchie said:**
> It looks like a great idea but I seem to be having problems with it. Is there a simple way of taking this off my system after a botched install? I have Edgy Ubuntu running with an option to start up in an Xubuntu environment.

I followed the install instructions but I double clicked the install.sh file (in true windows fashion) because I couldn't follow the other suggestion. The program doesn't appear as an option and since then the computer won't shut down - it just restarts and I have to pull the plug. I have also lost Synaptic and I'm tole to run 'dpkg --configure -a' to sort it out.

I'm loathe to work my way out of this so I just want rid of it until I know what I'm doing - can't remove it through Synaptic because it's broken.

Many thanks

This should get rid of everything that was installed:
```
sudo rm -rf /usr/share/startup-manager/
sudo rm /usr/share/applications/startup-manager.desktop
sudo rm /usr/share/icons/hicolor/48x48/apps/startup-manager.png
sudo rm /usr/share/locale/sv/LC_MESSAGES/startup-manager.mo
sudo rm /usr/bin/startup-manager.py
sudo rm /usr/bin/startup-manager-md5.sh
sudo rm /etc/startup-manager.conf
```

However, it is really not recommended to use that install.sh directly.
Use it with checkinstall(described in the first post) if you must.
Perhaps I should add instructions on how to install the package from the command-line too...

But that it broke your system?? NOT expected at all. The install.sh just moves some files to your system and creates a few directories...

What happens if you try the dpkg command that was suggested?

---

### Post by steveandarchie on 2006-12-27
Cheers Jimmy, I'm new to all of this and I was told that I had to be a superuser which I'm about to look up. It may not be this install so I'm sorry for wasting your time if not. Something very odd happened when I installed the new Opera version on the XP part of this box - it seems to have created a partition called RA\OPERA.DL which is now called hdc1 since I removed opera from XP. It looked like a virus as it started filling up when it was mounted. This and I get a fsck 1.39 check at every boot-up is making life a bit difficult so it might be time to reinstall.
 I've so much to learn so I might try to debug it but I'm not keen on powering off the computer too much.
Thanks again.

---

### Post by steveandarchie on 2006-12-27
for 

sudo dpkg --configure -a

I got loads of error messages ending with:

Errors were encountered while processing:
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-style-industrial
 openoffice.org-base
 openoffice.org-style-default
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-writer
 python-uno

It looks from your previous suggestion that Start-Up Manager got nowhere near my system - there's nothing to delete. It looks like my problems lie elsewhere so I could be wasting your time - thanks for your time though.

It looks like I'll be going for a complete reinstallation.

---

### Post by steveandarchie on 2006-12-27
back again - learning quickly

sudo apt-get install -f repaired the synaptic and I then did an auto remove to tidy it up a bit.

---

### Post by Jimmy_r on 2006-12-27
Glad to know it was solved - you scared me there for a moment :)

---

### Post by steveandarchie on 2006-12-28
Cheers Jimmy, there was/is a 32/Magistra.@MM virus on one of the windows partitions - this was why the RA.OPERA/hdc1 partition was going nuts when it was automatically mounted in Ubuntu - and slowing down my live Ubuntu session. I'm going to wipe the partition and maybe try Slax on it. 

The problem of the cycling restart is still there - it happens in XP even though I switched off the auto reboot feature and also in Ubuntu - I thought I might have done something to the GRUB with my half-arsed attempt at installing your program but it seems I din't get close to installing it. I'm pretty sure it is a Grub issue so have you any ideas - maybe I should post elsewhere.:-k

---

### Post by Jimmy_r on 2006-12-28
> **steveandarchie said:**
> Cheers Jimmy, there was/is a 32/Magistra.@MM virus on one of the windows partitions - this was why the RA.OPERA/hdc1 partition was going nuts when it was automatically mounted in Ubuntu - and slowing down my live Ubuntu session. I'm going to wipe the partition and maybe try Slax on it. 

The problem of the cycling restart is still there - it happens in XP even though I switched off the auto reboot feature and also in Ubuntu - I thought I might have done something to the GRUB with my half-arsed attempt at installing your program but it seems I din't get close to installing it. I'm pretty sure it is a Grub issue so have you any ideas - maybe I should post elsewhere.:-k

Hmm, I do not think this has to do with Grub(not that I am 100% sure however). My best guess would be the bios. Perhaps the virus? I checked it and it looks like it does some things to CMOS and Flash BIOS...
However this is out of my league and I think you would get better answers elsewhere.

EDIT: Is there any possibility you could have this virus: [http://www.symantec.com/security_response/writeup.jsp?docid=2000-122014-2500-99]("http://www.symantec.com/security_response/writeup.jsp?docid=2000-122014-2500-99")?
> The virus has a dangerous payload that triggers on December 25 of any year. The payload is designed to overwrite files on the floppy disk, hard disk, RAM disk, and network drives. It also clears the information stored on the BIOS. This payload is similar to the W95.CIH virus.
Just a guess, but it sure sounds like a match...

---

### Post by steveandarchie on 2006-12-28
I only picked up the Magistra.@MM on Aegis - the PC pitstop online check and AVG didn't pick anything up and a topic on here suggests that this may be a mis-diagnosis by Aegis. That said it does seem to be bios related as anything I have tried - taking out and replacing the RAM one by one and putting an old but reliable video card in haven't worked. I'll have another go at it by reflashing the bios myself (need to find the old floppy drive :confused: ) as it performs well otherwise - I just have to pull the plug so it's going to have a short shelf life at this rate.

Thanks for your help.

---

### Post by Lunar_Lamp on 2006-12-28
Very nifty little application. It might be an idea to throw in a default image and usplash theme just to get people started.

---

### Post by Jimmy_r on 2006-12-28
> **Lunar_Lamp said:**
> Very nifty little application. It might be an idea to throw in a default image and usplash theme just to get people started.

Yes, I have been thinking about that.
One idea could be to make sum depend on, or suggest, the package grub-splashimages.
But instead of adding dependencies, I could just add the command ```
sudo apt-get install grub-splashimages
``` to the installation instructions.

Another thing would be the usplash themes. They do not grow on trees(not even on repositories).

I suppose I could create one when I get the time, and add it to this thread...

Edit:Instructions updated.
I remembered I had already made some usplash themes. I linked to them...
They are maybe not the most exciting themes, but I am not an artist and I do not know about any other usplash themes...

Edit2: Added a really nice one I found on gnome-look.org

---

### Post by Lunar_Lamp on 2006-12-28
It may be worth pointing out that the grub images are located in /boot/grub/splashimages as not all may know (perhaps also pointing out that they need to be located on the same partition as the MBR might be useful).

Unfortunately, I seem to have a bug.  I'm trying to use the Usplash theme that you linked to:

[http://www.gnome-look.org/content/sh...?content=50468](http://www.gnome-look.org/content/sh...?content=50468)

I installed it as per instructions and it works just fine... when shutting down my laptop.  However, when booting up it shows the default ubuntu splash.  This is confusing me a lot!  My menu.lst is below in case that's what you need:

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
color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/ubuntu.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=splash vga=792 quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Jimmy_r on 2006-12-29
> **Lunar_Lamp said:**
> It may be worth pointing out that the grub images are located in /boot/grub/splashimages as not all may know (perhaps also pointing out that they need to be located on the same partition as the MBR might be useful).

I do not know if I understand you correctly, but SUM handles installation and uninstallation of the images in /boot/grub/splashimages automatically through the "Manage bootloader themes" button. The user will not even need to know where they are stored.
As for the partitions:SUM will just install the themes to /boot/grub/splashimages. I do not know how to handle any situation where that is not pointing to the currently active grub installation. As I said in the first post:
> It will also most certianly NOT work with Ubuntu if anything else than the ubuntu installer created your grub config files(**ie some other distro is installed after ubuntu and has overwritten the MBR**).
In that case, SUM will not have any effect whatsoever regarding Grub settings. SUM must be used through the ubuntu installation that last overwrote the MBR.

> **Lunar_Lamp said:**
> 
Unfortunately, I seem to have a bug.  I'm trying to use the Usplash theme that you linked to:

[http://www.gnome-look.org/content/sh...?content=50468](http://www.gnome-look.org/content/sh...?content=50468)

I installed it as per instructions and it works just fine... when shutting down my laptop.  However, when booting up it shows the default ubuntu splash.  This is confusing me a lot!  My menu.lst is below in case that's what you need:

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
color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/ubuntu.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=splash vga=792 quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

It has probably only been linked, not included in the initramfs.
You could probably solve it by typing
```
sudo update-initramfs -u
```

You could also do it by opening SUM, choosing another theme and then choosing this theme(usplash-theme-gray) again.

But what instructions did you follow? You should not need to use the instructions from gnome-look since SUM will install the theme automatically for you(download and unpack the theme, then click the "Manage usplash themes" button in SUM, press "add" and choose the file you downloaded.).
Or did you use SUM to install it? In that case we do have a bug. It sounds strange since I installed that theme through SUM myself without problems though.

---

### Post by Jimmy_r on 2006-12-29
I saw you also did not like the "on the world" misspelling.
Here I made a fix:
[Usplash-gray-fix]("http://web.telia.com/~u88005282/storage/usplash-gray-fix.tar.bz2")
[Source]("http://web.telia.com/~u88005282/storage/usplash-gray-fix-sources.tar.bz2")

---

### Post by Lunar_Lamp on 2006-12-29
I did install it via SUM.  If you want any more information to help you troubleshoot it, please ask!

---

### Post by Jimmy_r on 2006-12-29
First, use SUM to uninstall the usplash theme.
Then install the latest version (sum-0.9-9).
Use it to reinstall the theme.
Then select the theme in the combo box.
Close SUM.
Open SUM again and make sure that the theme is still selected in the combo box.
Close SUM and reboot.
If it still does not work, do these commands:
```
ls -l /usr/lib/usplash/
ls -l /etc/alternatives/usplash-artwork.so
```
And post the output.

---

### Post by derby007 on 2006-12-29
Great Application. 
Can u tell me what it does to get the Usplash working again....i was trying for hours to get it to work.

---

### Post by Lunar_Lamp on 2006-12-29
I followed your instructions, and SUM is not retaining the change of Usplash, when closed and reopened it reverts back to the default ubuntu one.  


```
ls -l /usr/lib/usplash/
total 7804
lrwxrwxrwx 1 root root      36 2006-12-29 15:00 usplash-artwork.so -> /etc/alternatives/usplash-artwork.so
-rwxr-xr-x 1 root root 2662415 2006-12-29 13:42 usplash-gray-fix.so
-rwxr-xr-x 1 root root 2662435 2006-12-29 00:43 usplash-theme-gray.so
-rw-r--r-- 1 root root 2643804 2006-10-25 13:40 usplash-theme-ubuntu.so

```

```
s -l /etc/alternatives/usplash-artwork.so 
lrwxrwxrwx 1 root root 40 2006-10-27 14:47 /etc/alternatives/usplash-artwork.so -> /usr/lib/usplash/usplash-theme-ubuntu.so

```

---

### Post by Jimmy_r on 2006-12-29
> **derby007 said:**
> Great Application. 
Can u tell me what it does to get the Usplash working again....i was trying for hours to get it to work.

It is quite simple.
It creates symlinks from /usr/lib/usplash/usplash-artwork.so to /etc/alternatives/usplash-artwork.so which links to the default one(ex. /usr/lib/usplash/usplash-theme-ubuntu.so)
then it does a ```
update-initramfs -u
``` as root.

---

### Post by Jimmy_r on 2006-12-29
> **Lunar_Lamp said:**
> I followed your instructions, and SUM is not retaining the change of Usplash, when closed and reopened it reverts back to the default ubuntu one.  


```
ls -l /usr/lib/usplash/
total 7804
lrwxrwxrwx 1 root root      36 2006-12-29 15:00 usplash-artwork.so -> /etc/alternatives/usplash-artwork.so
-rwxr-xr-x 1 root root 2662415 2006-12-29 13:42 usplash-gray-fix.so
-rwxr-xr-x 1 root root 2662435 2006-12-29 00:43 usplash-theme-gray.so
-rw-r--r-- 1 root root 2643804 2006-10-25 13:40 usplash-theme-ubuntu.so

```

```
s -l /etc/alternatives/usplash-artwork.so 
lrwxrwxrwx 1 root root 40 2006-10-27 14:47 /etc/alternatives/usplash-artwork.so -> /usr/lib/usplash/usplash-theme-ubuntu.so

```

Have you tried to do a ```
sudo update-initramfs -u
```

If that does not work, try to reinstall usplash.

Edit: wait, wait. My bad. the symlinks are not updating. Ignore what i wrote.
I am in a bit of hurry right now... I will respond later...

---

### Post by derby007 on 2006-12-29
Cheers for the reply, it was simple after all.........after all those hours !
Can u tell me if your app will change the Usplash to something else? i dare not try it alone....:(

---

### Post by Jimmy_r on 2006-12-29
> **derby007 said:**
> Cheers for the reply, it was simple after all.........after all those hours !
Can u tell me if your app will change the Usplash to something else? i dare not try it alone....:(

I am not sure if I understand.
Yes, it is able to install and change to a valid usplash .so theme file.
But we could have a bug, so you may want to wait until the issue LunarLamp has is solved.

---

### Post by Jimmy_r on 2006-12-29
LunarLamp, do a ```
sudo update-alternatives --config usplash-artwork.so 
```
A list of options will be listed, is the new theme among them?

---

### Post by Lunar_Lamp on 2006-12-29
No.

```
$ sudo update-alternatives --config usplash-artwork.so
Password:

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.

```

---

### Post by Jimmy_r on 2006-12-29
Hmm, I when I get home to my computer tomorrow, I will check the source code.
I begin to suspect I packaged an old file...

---

### Post by Lunar_Lamp on 2006-12-29
Ok, thanks!

---

### Post by TheeMahn2003 on 2006-12-29
I just thought I'd let you know I have written a [page]("http://ubuntusoftware.info/sum.html") for your software.  I would greatly appreciate you informing me when you have updated your software I would like to keep the most current version on the server.  Great work, I love the program...

---

### Post by Jimmy_r on 2006-12-29
> **TheeMahn2003 said:**
> I just thought I'd let you know I have written a [page]("http://ubuntusoftware.info/sum.html") for your software.  I would greatly appreciate you informing me when you have updated your software I would like to keep the most current version on the server.  Great work, I love the program...

Thanks :) 

I will try to remember to keep you informed.

---

### Post by Jimmy_r on 2006-12-29
OK, Lunar_Lamp.
I checked the source code and could not find anything strange.
I uninstalled sum and downloaded 0.9-9.deb from my own post, just to make sure I had the right one installed.
Then I used it to install a theme I had not installed earlier, just to test.
It worked fine (Unfortunately?):-k 

Try this command:
```
sudo /usr/sbin/update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-gray-fix.so 10
```

---

### Post by Lunar_Lamp on 2006-12-29
I ran that command and rebooted, but no luck.  I've just run the diagnostics you told me to again though, and the symlinks HAVE updated.  I'll try rebooting after doing a sudo update-initramfs -u

If that doesn't work, well, it must be something weird!

---

### Post by Lunar_Lamp on 2006-12-29
Ok, after an extensive series of tests and boots I've deduced that it something to do with the kernels.  If I select the first entry (the one I use) I don't get the selected usplash, but if I use the 3rd entry (generic) I do get the selected usplash.  Here is my menu.lst again:


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
color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/ubuntu.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=splash vga=792 quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=fad10755-4a43-4988-853b-edc8efd75f84 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Jimmy_r on 2006-12-30
There it may be.
When you run the sudo update-initramfs -u command, what is your output?

Is it maybe not updating the -386 initramfs images?

As I remember, ubuntu devs decided to get rid of all specialized(386 etc.) kernels and use one generic instead...
So the easiest way to solve this could be to uninstall the 386 kernel and use the generic(unless you need the 386 one?).

Now for the symlinks:
SUM should call that update-alternatives command automatically when installing a new usplash theme(it does for me at least).
So to test this, could you try to install another theme which you have not installed earlier(for example the ubuntu mce one i linked in the first post), select it as default and see if the symlinks update automatically.

---

### Post by Lunar_Lamp on 2006-12-30
OK, symlinks updated when installing the MCE Usplash.  So that works just nicely now (if there was a problem before at your end it is fixed with 9.9 version).

As for the initramfs update - it only updates a single image, the generic one.  I have my system setup nicely on the 386, and it would be a real hassle to change ;-)  I'm going to have a look through your source-code to see if it would be possible to make it pick up all installed kernels (or at least only act on the one you have currently selected as default).

As a *minor* usability option, you might want to consider an "apply" button rather than just applying (some) things on "close".

---

### Post by Jimmy_r on 2006-12-30
Hm, it is a bit strange. I installed the -386 kernel to test this.
Update-initramfs updated the -386 initramfs properly...

As for the "apply" button, I have been trying to follow the gnome HIG: [http://developer.gnome.org/projects/gup/hig/2.0/windows-utility.html]("http://developer.gnome.org/projects/gup/hig/2.0/windows-utility.html")
> For windows that allow the user to change values or settings, such as property and preference windows, update those values or settings immediately to reflect the changes made in the window. This is known as "instant apply". Do not make the user press an OK or Apply button to make the changes happen, unless either:

    *

      the change will take more than about one second to apply, in which case applying the change immediately could make the system feel slow or unresponsive, or
    *

      the changes in the window have to be applied simultaneously to prevent the system entering a potentially unstable state. For example, the hostname and proxy fields in a network properties window.

If either these conditions affect only a few of the controls in your window, arrange those controls together into one or more groups, each with its own Apply button. Leave the rest of the controls as instant apply.

In fact every setting is changed instantly.

What it does at close, is that it checks if anything that needs update-grub or update-initramfs has been changed. If so, it runs those commands.

If I had an apply button, the user might think that to press "close" without "apply" will discard the changes.
So in that case I would have to scrap the "close" button and add a "cancel" and "ok" button instead.
Suddenly I have four buttons(including "help") and have to redo the action-sensible code...

---

### Post by Lunar_Lamp on 2006-12-30
Yeah, I know that gnome deliberately avoids "apply" buttons.  I suppose there is no logical way to do anything else.  Perhaps when you click "close" a popup saying "please be patient whilst SUM checks stuff out to make sure we don't kill your computer".

This is indeed a weird scenario with the kernel options though.

---

### Post by Jimmy_r on 2006-12-30
> **Lunar_Lamp said:**
> Yeah, I know that gnome deliberately avoids "apply" buttons.  I suppose there is no logical way to do anything else.  Perhaps when you click "close" a popup saying "please be patient whilst SUM checks stuff out to make sure we don't kill your computer".


Hehe, sounds good. I have thought about that too. Expect it in the next version.

---

### Post by Steve S. on 2007-01-01
Jimmy_r: gotta say this thing rocks!  I have been playing with the usplash under edgy for a few weeks now and figured out most of it, but WISH I had found this a few weeks ago!  Very well done!  Love being able to use the gui and saving the command for when I need it...excellent!

---

### Post by rbhigday on 2007-01-03
when I attempted to install this I get the following

> 

rbhigday@richard-laptop:~/sum-0.9$ ./install.sh
mkdir: cannot create directory `/usr/share/startup-manager': Permission denied
mkdir: cannot create directory `/boot/grub/splashimages': Permission denied
cp: cannot create regular file `/usr/share/locale/sv/LC_MESSAGES/startup-manager.mo': Permission denied
cp: cannot create regular file `/usr/bin/startupmanager.py': Permission denied
cp: cannot create regular file `/usr/bin/startupmanager-gtk.py': Permission denied
cp: cannot create regular file `/usr/bin/startup-manager-md5.sh': Permission denied
cp: target `/usr/share/startup-manager/' is not a directory: No such file or directory
cp: cannot create regular file `/usr/share/icons/hicolor/48x48/apps/startup-manager.png': Permission denied
cp: cannot create regular file `/usr/share/startup-manager/startup-manager-icon.svg': No such file or directory
cp: cannot create regular file `/usr/share/applications/startup-manager.desktop': Permission denied
rbhigday@richard-laptop:~/sum-0.9$ 



what did I do wrong?

---

### Post by rbhigday on 2007-01-03
found my error followed direction for old installation and not recent one

Sorry about that.

---

### Post by ike on 2007-01-06
i have a (probably trivial) problem.. i already have a package called "sum" installed (man page says "checksum and count the blocks in a file"). i have tried to remove it and install StartUp Manager again, but it won't go away.

I presume the command for starting StartUp Manager is "sum" also, right? when i run "sum" the other program starts, and not StartUp Manager.

What am i doing wrong?

---

### Post by Jimmy_r on 2007-01-06
> i have a (probably trivial) problem.. i already have a package called "sum" installed (man page says "checksum and count the blocks in a file"). i have tried to remove it and install StartUp Manager again, but it won't go away.

Oops, I will consider changing package name in future versions.

> I presume the command for starting StartUp Manager is "sum" also, right? when i run "sum" the other program starts, and not StartUp Manager.

In fact, the command in the latest version is
```
gksu -k startupmanager-gtk.py
```


<swedish>Lycka till :) </swedish>

---

### Post by HyperY2K on 2007-01-06
I've found a big in SUM: When I switch my usplash-theme with SUM it only works for the shutdown phase. For the bootup phase the new theme is only shown for a second and then the old one is shown for all the rest until gdm startup.
With usplash-switcher it works for me..

Can anybody confirm this bug?

---

### Post by Lunar_Lamp on 2007-01-06
That sounds similar to the bug I had (and wasn't able to solve).  I don't remember the new one flashing up briefly on bootup though.

Are you using a laptop? What is the native resolution etc?  What colour depth are you using?

I think those may be the key questions.

---

### Post by Jimmy_r on 2007-01-06
This is how I understand it:
On shutdown, usplash just follows the symlinks to the theme to use it.
On startup, usplash needs to have the theme compiled into initramfs.
Therefore, this kind of problem should be initrams-related.

Do this command(it is the same as sum issues):
```
sudo update-initramfs -u
```
check the output of that line against the output of this line:
```
uname -r
```
Does the kernel names match?

---

### Post by Lunar_Lamp on 2007-01-06
Idea!

If they do not match - try using the "-k" option.  I've just tried, but am too busy to restart at the moment.  

i.e.

sudo update-initramfs -k $(uname -r) -u

---

### Post by Jimmy_r on 2007-01-06
Perhaps I should change sum to use that command in next version.

---

### Post by Lunar_Lamp on 2007-01-06
I just used that and it worked.  It would seem to be a good idea to add it to your next version!

---

### Post by jpyanowski on 2007-01-06
This app is a blessing for those of us who like to tweak around with the system. A Big THANK YOU for your hard work that will make my play easier now.  :biggrin:

---

### Post by TheeMahn2003 on 2007-01-07
Thanks for the update I have software watching this page for changes :)  I will update the [page]("http://ubuntusoftware.info/sum.html") I wrote for your software to reflect your true home page after I give the entire site a  [face lift]("http://ubuntuforums.org/showthread.php?p=1958652") it is coming in the next few days, I am going to add additional recourses for your software it will take a while once it is up I'll post here so you can view it.  Keep up the good work.  I have also added your software to my custom [repo]("http://ubuntusoftware.info/repos.html").

---

### Post by Jimmy_r on 2007-01-08
Nice.

---

### Post by Saubazi on 2007-01-08
I get:
$ gksu -k startupmanager-gtk.py
Traceback (most recent call last):
  File "/usr/bin/startupmanager-gtk.py", line 439, in ?
    sumGui = SumGui()
  File "/usr/bin/startupmanager-gtk.py", line 432, in __init__
    self.update_widgets()
  File "/usr/bin/startupmanager-gtk.py", line 350, in update_widgets
    self.resolution_combo.set_active(convert_vga(self.grub.get_vga(), 0))
  File "/usr/bin/startupmanager-gtk.py", line 93, in convert_vga
    settings=dic[vga]
KeyError: 785

So wazzup?

---

### Post by TheeMahn2003 on 2007-01-09
> **Jimmy_r said:**
> Nice.

Page is up [corrected]("http://www.ubuntusoftware.info/sum.html") homepage to reflect your new site, only about 2 or 3 hundred more pages to go ;)

---

### Post by Jimmy_r on 2007-01-09
> **Saubazi said:**
> I get:
$ gksu -k startupmanager-gtk.py
Traceback (most recent call last):
  File "/usr/bin/startupmanager-gtk.py", line 439, in ?
    sumGui = SumGui()
  File "/usr/bin/startupmanager-gtk.py", line 432, in __init__
    self.update_widgets()
  File "/usr/bin/startupmanager-gtk.py", line 350, in update_widgets
    self.resolution_combo.set_active(convert_vga(self.grub.get_vga(), 0))
  File "/usr/bin/startupmanager-gtk.py", line 93, in convert_vga
    settings=dic[vga]
KeyError: 785

So wazzup?

It appears as the vga code for your boot screen is "785".
When writing that part of sum, I used [http://www.ubuntuforums.org/showthread.php?p=1541970]("http://www.ubuntuforums.org/showthread.php?p=1541970") (2:nd post)as a reference for boot codes.
As you can see, "785" is not in that table.

So, since I do not want to add more resolutions(If I for example add one more resolution, I will need the codes for every color depth in that resolution or else things will get complicated), I will instead add some code to not set the combo boxes if an unknown number is read.

Just for my curiosity: What resolution and color depth does your number stand for?
The only temporary solution I can think of is that you manually change the vga code in your menu.lst to something sum understands(for example 791).

---

### Post by Saubazi on 2007-01-09
785 stands for 640x480 

I have tried this but to no avail:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

after distupgrade to edgy I got this ugly intermediate splash of edgy whereas
I'd like to have the new one so I came to this thread after searching. I'll give another
vga option a try...

---

### Post by Saubazi on 2007-01-09
Ok here is the deal I tried ubuntu-theme-usplash-mce I got a greyscale ubuntu logo on left upper corner. Hmmm... tried the grey-fix theme and I got back the buttugly old edgy splash?!?!? Now it won't even change again to that grey one even if I again change to "mce" one??

---

### Post by Jimmy_r on 2007-01-10
> 785 stands for 640x480
At which color depth?

> Ok here is the deal I tried ubuntu-theme-usplash-mce I got a greyscale ubuntu logo on left upper corner. Hmmm... tried the grey-fix theme and I got back the buttugly old edgy splash?!?!? Now it won't even change again to that grey one even if I again change to "mce" one??
Ah, this sounds familiar. Do you by any chance happen to have the 64-bit version of ubuntu installed?

---

### Post by Saubazi on 2007-01-10
Yes I have 64bit version - is it the cause and is there a way around?

---

### Post by Jimmy_r on 2007-01-10
There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/usplash-theme-ubuntu/+bug/67545") in usplash on 64 bit which makes it select the lowest resolution theme(which is black and white in the standard theme).

Check this thread(post 14 and forward):[http://www.ubuntuforums.org/showthread.php?t=304673]("http://www.ubuntuforums.org/showthread.php?t=304673")

At this thread is another 64 bit usplash theme attached(1280x1024 only):[http://www.ubuntuforums.org/showthread.php?t=328334]("http://www.ubuntuforums.org/showthread.php?t=328334")

Edit: Also, why you got the edgy "Test screen" when using the ubuntu mce splash is because the themes are compiled. This means that a theme compiled on a 32 bit computer cannot be used on a 64 bit computer without recompiling, and the other way round.
So usplash cannot use the mce splash and reverts to its default, the test screen.

---

### Post by beamo on 2007-01-13
Jimmy_r, thank you for the wonderful program. This has solved all my troubles! :D

---

### Post by Jimmy_r on 2007-01-14
New version...
Well, my todo list is shrinking. Now I only have to write that qt version, and then port the whole kaboodle to grub2...

What I did not get around to doing, are those "Progress notifications" during time-consuming operations (update-initramfs, floppy creation).
To get it right, it seems as I would need to start messing with threads...[-( 
Feel free to send me a patch though ;)

---

### Post by lilmienboy on 2007-01-16
cool

---

### Post by ntetreau on 2007-01-17
This seems like a truely amazing addition to edgy.  Would it be possible to support 1280x800 resolution for widescreen laptop?  Thanks!

Nic

---

### Post by Lunar_Lamp on 2007-01-17
My laptop has native resolution at 1280*800, and I use the 1024*768 for the boot splash without problem.  OK, it would be nice to have 1280*800 natively in there, but just to let you know that it's not essential.

---

### Post by Jimmy_r on 2007-01-17
> **ntetreau said:**
> This seems like a truely amazing addition to edgy.  Would it be possible to support 1280x800 resolution for widescreen laptop?  Thanks!

Nic

When writing that part of sum, i used this thread as a reference:
[http://www.ubuntuforums.org/showthread.php?p=1541970]("http://www.ubuntuforums.org/showthread.php?p=1541970")

For the sake of simplicity, I only used those modes that had full support for 8, 16 and 24 bits color depth.
Otherwise, I would have to edit the contents of the combo boxes depending on what resolution/color depth was selected... 

So, to answer your question: I would add that resolution if I got the codes for 1280x800 at 8, 16 and 24 bits color depth.
But, a quote from the linked thread implies they do not even exist:
> it seems that vesafb doesn't support any resolution not in the table above

---

### Post by shakma on 2007-01-22
Wow!

Jimmy_r, you da man!

Just wanted to thank you for creating your program.  It does EVERYTHING it says is does, and makes the ol' 64-bit edgy grayscale usplash bug a thing of the past!  

Thank you!

This should DEFINITELY be in the official repos!

---

### Post by HyperY2K on 2007-01-22
I've still have a bug. My shutdown screen is changed, but the bootup screen remains the classic ubuntu one (just for one second after grub disappeared the new one shows up)..

---

### Post by Jimmy_r on 2007-01-23
> **HyperY2K said:**
> I've still have a bug. My shutdown screen is changed, but the bootup screen remains the classic ubuntu one (just for one second after grub disappeared the new one shows up)..

That sounds very strange.
Have you tried the latest version(uninstalled package sum and installed startupmanager-gtk), then switched to old theme and back to new theme?

If the correct theme is shown on shutdown, the symlinks are correct, so the only thing it could be caused by would be the initramfs...
As sum now uses Lunar_Lamp's command for creation of initramfs, I have no idea what this could be caused by...

Lets try to track it down:

Open a terminal and issue the command:
```
sudo update-initramfs -k $(uname -r) -u
```

It will output a line.
For example:
```
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
```

Now open your /boot/grub/menu.lst in a text editor.
Locate the section for your default booted system.

Mine is:
```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash $
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

Now check so that the line starting with initrd points to the same file as the output of the update-initramfs command above.

---

### Post by HyperY2K on 2007-01-24
ok thanks for the support. I will check this and post my results.

BTW: Is it possible to participate in the project to implement new features, like a theme preview or similiar things?

---

### Post by Jimmy_r on 2007-01-24
> **HyperY2K said:**
> ok thanks for the support. I will check this and post my results.

BTW: Is it possible to participate in the project to implement new features, like a theme preview or similiar things?

Sure. PM me about any features you want to add, and we will discuss it.

---

### Post by sefkaz on 2007-02-12
i think it has a bug with kernel 2.6.17.11 , SUM make my kernel panic ... it says can't find root (hda0,0) but my menu.lst point it at (hda0,5) so i went back to 2.6.17.10 :D, coz i don't know how to fix that :D , me still a noob :D

-ron-

---

### Post by Jimmy_r on 2007-02-12
> **sefkaz said:**
> i think it has a bug with kernel 2.6.17.11 , SUM make my kernel panic ... it says can't find root (hda0,0) but my menu.lst point it at (hda0,5) so i went back to 2.6.17.10 :D, coz i don't know how to fix that :D , me still a noob :D

-ron-

That sounds strange. SUM should not in any way affect individual kernel options.

Could you please post the contents of your file /boot/grub/menu.lst

---

### Post by Jimmy_r on 2007-02-17
New version...
I cannot make up my mind, the packages have been merged again.

This is because the qt4 version will probably not happen. I lack interest, there are [other efforts]("https://blueprints.launchpad.net/ubuntu/+spec/kubuntu-grubconfig") in that direction, I do not like duplication of work and I managed to lose a portion of the code I had written :(.

I have, however, tested the latest version of sum briefly on Kubuntu Breezy, Ubuntu Dapper and Kubuntu Feisty and it appears to work as good as on Ubuntu Edgy :)

---

### Post by Jimmy_r on 2007-02-18
I got to test sum on debian today, it appears to work good :)

Here is a screenshot(Excuse the swedish, I was running KDE and found no way to change the language for gtk apps):
[ATTACH]25628[/ATTACH]

Hey, something is missing...
Yes, the options for usplash themes. A while ago I changed sum so that if usplash was not found, those options should be hidden. Appears to work :)

---

### Post by jjig99 on 2007-02-20
Accessibility issues
  
    Altough startup-manager aplication is enough accessible for a blind person using a screen reader (like orca), there are one thing, very easy to do, in order to make a better accessibility.

   Startup-manager should use the LABEL_FOR relationship to match each combobox (or button) with the appropiate label.
Using glade this is a very easy issue, because the only thing you have to do is use the accessibility tab in properties window, to fill the 'labelled for' an 'labelled by' entries.
For example, in label8 object, set the entry 'labelled for' field  to 'timeout_spinner.' And, for the timeout_spinner object, set the entry 'labelled by' to 'label8'. In this way, when focus is in timeout_spinner object, an screen reader can spoke something like: 'timeout in seconds .  ten'. Right now, an screen reader only says 'ten'

   If you make those little changes, i can test them.
   Thanks in advance
   Juan Ramon

---

### Post by Jimmy_r on 2007-02-21
Thanks for the tip.
I will do this as soon as I get the time :)

---

### Post by Jimmy_r on 2007-02-22
New version, ready for you to test accessibility support :)

A problem is that glade3 apparently does not support this. I had to load the file into glade2 to do these changes(Who thought multiple un-docked windows was a good idea :()
Then if I load the changed file in glade3 , save it and load it in glade2 again, the accessibility changes are gone...
Looks as if I am stuck with glade2 now :(

---

### Post by ntetreau on 2007-02-24
Hi, for some reason, I can't seem to be able to start SUM anymore, I get this error:

/usr/bin/startupmanager:498: GtkWarning: Unable to locate theme engine in module_path: "pixmap",
  xml=gtk.glade.XML(Config.glade_dir, None ,APP)
Traceback (most recent call last):
  File "/usr/bin/startupmanager", line 581, in <module>
    sumGui = SumGui()
  File "/usr/bin/startupmanager", line 545, in __init__
    if not self.grub.has_update_grub():
AttributeError: Grub instance has no attribute 'has_update_grub'


Nic

---

### Post by Jimmy_r on 2007-02-24
> **ntetreau said:**
> Hi, for some reason, I can't seem to be able to start SUM anymore, I get this error:

/usr/bin/startupmanager:498: GtkWarning: Unable to locate theme engine in module_path: "pixmap",
  xml=gtk.glade.XML(Config.glade_dir, None ,APP)
Traceback (most recent call last):
  File "/usr/bin/startupmanager", line 581, in <module>
    sumGui = SumGui()
  File "/usr/bin/startupmanager", line 545, in __init__
    if not self.grub.has_update_grub():
AttributeError: Grub instance has no attribute 'has_update_grub'


Nic


Yikes, When merging the packages I forgot the preinst and prerm rules to clean out old .pyc and .pyo files...
I am uploading a new package immediately.

Edit: New package uploaded, please try it and see if your problem disappears.

---

### Post by ntetreau on 2007-02-26
Thanks, it starts fine now!!!

Nic

---

### Post by MrWashy on 2007-03-05
Well it seems I'm unlucky because I can't seem to boot.  Not exactly though, I can boot into the recovery console but I'm not really too sure where to go from there.  (I'm extremely new at this and don't want to mess up more than I apparently already have!)

In more detail, my boot process goes like this:
Bios-blah blah blah

Grub starts, and I get the usual menu with the usual choices, ecept with the nifty splash background I used SUM to insert there.

If I boot into the normal Ubuntu it will show the standard loading screen with the nice moving orangy bar.  After that, nothing.  Blank screen, no splash, no login.

If I boot into recovery console it boots just fine; XP boots as well - it's what I'm using to write this.

To me this seems just plain devastating, no hope, all is lost, "doom, despair and agony on me."  I'm guessing this might not be the case since I can get into the console.  

Any suggestions on what I need to take a look at to resolve this?

Many thanks!

Rich W.

---

### Post by MrWashy on 2007-03-06
Got it back!  I was able to restore the login using:

```
dpkg-reconfigure xserver-xorg
```

---

### Post by jjig99 on 2007-03-08
Hi all,

   Thank you very much for the effort you have made in order to the accessibility issues  !!! :) 

   I have downloaded the last version of startupmanager and it looks perfect (at least talking about accessibility, of course). It's a very good application and it's very important that everybody (included blind people or people with other disabilties) have the oportunity to use it.

   Thanks again, and i hope you don't forget blind people in your future releases ;-) 
    Juan Ramón


> New version, ready for you to test accessibility support
> 
> A problem is that glade3 apparently does not support this. I had to load the file into > glade2 to do these changes(Who thought multiple un-docked windows was a good > idea )
> Then if I load the changed file in glade3 , save it and load it in glade2 again, the > > accessibility changes are gone...
> Looks as if I am stuck with glade2 now
> __________________
> SUM, the StartUp-Manager
> 
> Registered Lunux user #404753
> Last edited by Jimmy_r : 1 Week Ago at 10:09 AM.
> Reply With Quote

---

### Post by jjig99 on 2007-03-09
I have wrote some lines about SUM in the Orca's wiki ([http://live.gnome.org/orca)](http://live.gnome.org/orca)), in the section about Accessible Applications ([http://live.gnome.org/Orca/AccessibleApps](http://live.gnome.org/Orca/AccessibleApps))
If you want to add something more about SUM and accessibility, please use this link: [http://live.gnome.org/Orca/SUM](http://live.gnome.org/Orca/SUM)

---

### Post by Leonivek on 2007-03-09
> **jjig99 said:**
> I have wrote some lines about SUM in the Orca's wiki ([http://live.gnome.org/orca)]("http://live.gnome.org/orca%29"), in the section about Accessible Applications ([http://live.gnome.org/Orca/AccessibleApps](http://live.gnome.org/Orca/AccessibleApps))
If you want to add something more about SUM and accessibility, please use this link: [http://live.gnome.org/Orca/SUM](http://live.gnome.org/Orca/SUM)

You may want to edit the first link you provided since the site is case sensitive and lowercase orca doesn't work.  Should be [http://live.gnome.org/Orca](http://live.gnome.org/Orca) . :)

---

### Post by Toadmund on 2007-03-20
```
sudo apt-get install grub-splashimages kubuntu-grub-splashimages
```
In one of the first links it gave this command to put usplash images into SUM, 

unfortunately they are Kubuntu images, so I tried this line:
```
sudo apt-get install grub-splashimages ubuntu-grub-splashimages
```
Didn't work.

Is there, or where, or in a terminal command, do I find ubuntu uspash art that loads itself into SUM?
(edgy 64bit)

---

### Post by Jimmy_r on 2007-03-23
grub-splashimages and kubuntu-grub-splashimages are the only two packages I know about in the repositories that contain Grub artwork.
Just to clarify, that is the art displayed in the bootloader menu.

You seem to want usplash art, and I do not know of any usplash packages in the repositories except the artwork packages for kubuntu and xubuntu.

Overall, there is very little usplash artwork available.
If you go to kde-look.org and gnome-look.org and search for usplash, you will find some.

Problem is some of the themes you find have been made for Dapper and earlier, and will not be compatible with usplash in edgy and forward.
Another problem with Usplash is that the themes are compiled.
This means that if someone distribute a .so file compiled on a 32 bit system, you cannot use it on a 64 bit system and the other way around.

Just so you know, if you get a strange looking test screen after installing some usplash art, it is probably for one of the reasons above.

Good luck.

---

### Post by gosh on 2007-03-27
Thnx! great app

---

### Post by DarkMaTTi on 2007-04-01
When I start SUM, then came this:

matti@matti-desktop:~$ sudo startupmanager
Password:
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-11-generic
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Traceback (most recent call last):
  File "/usr/bin/startupmanager", line 581, in ?
    sumGui = SumGui()
  File "/usr/bin/startupmanager", line 559, in __init__
    self.update_widgets()
  File "/usr/bin/startupmanager", line 464, in update_widgets
    self.resolution_combo.set_active(convert_vga(self.grub.get_vga(), 0))
  File "/usr/bin/startupmanager", line 131, in convert_vga
    settings=dic[vga]
KeyError: 49

I hope for help

thanks

greets DarkMaTTi

---

### Post by Jimmy_r on 2007-04-01
> When I start SUM, then came this:
 
 matti@matti-desktop:~$ sudo startupmanager
 Password:
 Searching for GRUB installation directory ... found: /boot/grub
 Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
 Searching for splash image ... none found, skipping ...
 Found kernel: /boot/vmlinuz-2.6.17-11-generic
 Found kernel: /boot/vmlinuz-2.6.17-10-generic
 Found kernel: /boot/memtest86+.bin
 Updating /boot/grub/menu.lst ... done
 
 Traceback (most recent call last):
 File "/usr/bin/startupmanager", line 581, in ?
 sumGui = SumGui()
 File "/usr/bin/startupmanager", line 559, in __init__
 self.update_widgets()
 File "/usr/bin/startupmanager", line 464, in update_widgets
 self.resolution_combo.set_active(convert_vga(self. grub.get_vga(), 0))
 File "/usr/bin/startupmanager", line 131, in convert_vga
 settings=dic[vga]
 KeyError: 49
 
 I hope for help
 
 thanks
 
 greets DarkMaTTi

Please post the contents of your /boot/grub/menu.lst

---

### Post by spankymasterc on 2007-04-01
crapped up my system.... uninstalled good thing i know how to configure and had a backed up /boot/grub/menu.lst ..... this thing didnt work but good job anywayz...

---

### Post by Jimmy_r on 2007-04-02
> **spankymasterc said:**
> crapped up my system.... uninstalled good thing i know how to configure and had a backed up /boot/grub/menu.lst ..... this thing didnt work but good job anywayz...

Hmm, you dont happen to have a copy of the "crapped up" menu.lst?
I would be glad to know what it messed up, so I can fix the bug.

If not, maybe you could post a copy of your current menu.lst so I can test it myself.

Edit: It does not happen to be caused by the same reason as for n3cre0 earlier in this thread?
> **n3Cre0 said:**
> Hehe it ****** up my /boot/grub/menu.lst :)
Luckily I got about 5 backups of it.

Just a little warning ;)


Does your menu.lst get crapped up in the same way by running ```
sudo update-grub
```?

---

### Post by Jimmy_r on 2007-04-02
DarkMaTTi, I have uploaded a new version. It should fix your problem.

The new package has had it internals shuffled around a bit. It is also built on Debian and not tested on Ubuntu, so please report any errors it may have introduced.

---

### Post by DarkMaTTi on 2007-04-02
thank you, it works perfect.

greets DarkMaTTi

---

### Post by a-musing amazon on 2007-04-15
There seems to be a problem with how Start-up Manager creates a menu.lst entry for your splashscreen if you have a seperate boot partition.

On my PC my /boot partition is on a minimal sda1 (64Mb, EXT2) which is grub (hd1,0) and my main root Ubuntu Edgy partition is on sda2 (10GB, EXT3) which is grub (hd1,1) with /home on sda3 (20GB, EXT3) which is grub (hd1,2). I also have some other OS/Filessystem on other partitions accessible from the grub menu. This means that if I damage the filesystem on my main ubuntu partition it doesn't stop me mounting the other kernel images/filesystems.

However Start-up Manager creates an entry for my splashimage as:

splashimage=(hd0,0)/boot/grub/splashimages/wolf1.xpm.gz

However at the stage where you are running grub, before I've chosen a menu option the /boot subdirectory doesn't yet exist, albeit it does exist on the mounted filesystem which is on sda2, (hd1,1) and is there linked back to sda1, so you would need to change the entry to 

splashimage=(hd1,0)/grub/splashimages/wolf1.xpm.gz

to make it work.

I have found another workround, which maintain the functionality of Start-up Manager, which is, on the mounted sda2 filesystem to 

# cd /boot
#sudo ln -s . boot

This the creates a link so that grub will still find a boot directory containg grub and grub/splashimages.

I'n unclear whether there is a way to check for this setup from within Start-up Manager.

Marjorie

---

### Post by Jimmy_r on 2007-04-15
I was fearing something like this would appear...

In fact, I have no clever way to ensure those (hdx,y) numbers are correct.
What SUM does to get those numbers is that it checks this line in menu.lst:

```
# groot=(hd0,0)
```

And use the values from that line for the splashimage line.
I have no idea how to get that info in a more reliable way...
Unless anyone has suggestions(or code) how to solve this, I am afraid we will have to live with this bug.

---

### Post by vafada on 2007-04-20
is there a way for SUM to also detect other OS (windows)?

before using SUM, my menu.lst would have Windows XP as an option but after using SUM, the windows entry was gone. I have to manually edit menu.lst after using SUM to include windows on the boot options.

still a great application. thanks for developing it ;)

---

### Post by Laterix on 2007-04-20
Screenshots look very promising! Thank you for this application.

---

### Post by vafada on 2007-04-20
also:

[http://web.telia.com/~u88005282/sum/archive/source/startupmanager_1.0.3.tar.gz](http://web.telia.com/~u88005282/sum/archive/source/startupmanager_1.0.3.tar.gz) seems to be broken... i can't extract some of the files (using 7zip in windows), i'll try to extract it in my linux box when I get home.

---

### Post by Jimmy_r on 2007-04-20
> **vafada said:**
> is there a way for SUM to also detect other OS (windows)?

before using SUM, my menu.lst would have Windows XP as an option but after using SUM, the windows entry was gone. I have to manually edit menu.lst after using SUM to include windows on the boot options.

still a great application. thanks for developing it ;)

Hm, SUM should work with a windows boot option, in fact it detects the options directly from menu.lst so it should not really matter what OS it is.
It is NOT supposed to remove boot options at all.

The command update-grub is issued by SUM sometimes. Update-grub is a Debian(and Ubuntu) command which rewrites the menu.lst. It is issued for example at upgrades.
If you have a copy of your original menu.lst, copy it back and run
```
sudo update-grub
```

If that does the same damage to your menu.lst, then check this thread, post 44 and forward by n3Cre0( [http://ubuntuforums.org/showthread.php?t=295524&page=5](http://ubuntuforums.org/showthread.php?t=295524&page=5) ):
You should have this line:
```
 ### END DEBIAN AUTOMAGIC KERNELS LIST
```
before the windows xp option.

If update-grub is not the cause, please post back so we can investigate further.

Oh, and the archive extracts fine here on my sabayon box at least...

---

### Post by vafada on 2007-04-20
you are right. My Windows section was before 

[PHP]### END DEBIAN AUTOMAGIC KERNELS LIST[/PHP]

so update-grub was deleting it.

i was able to extract the tar file in my Linux box.. hmm weird.. 

Thanks for the help and thanks for doing SUM.... i have been using it even before feisty fawn and loving it ;)

---

### Post by Nullbyte on 2007-04-20
Would be nice with support for widescreen display :)

---

### Post by Jimmy_r on 2007-04-21
> **Nullbyte said:**
> Would be nice with support for widescreen display :)

I would implement it, if I had the grub vga codes for it.
But according to second post in this thread there seems to be problems:
[http://ubuntuforums.org/showthread.php?p=1541970](http://ubuntuforums.org/showthread.php?p=1541970)
> I've also seen questions from people wanting widescreen resolutions. I'm sorry, but it seems that vesafb doesn't support any resolution not in the table above.

---

### Post by motin on 2007-04-25
BUGREPORT:

When I choose to install grub splash images, it puts a line in menu.lst that looks like this:

splashimage=(hd0,0)/boot/grub/splashimages/NightOfUbuntu.xpm.gz

However, since my /boot folder is mounted in it's own partition, the correct path should be:

splashimage=(hd0,0)/grub/splashimages/NightOfUbuntu.xpm.gz

... leading to "Failed to read splash image" errors.

---

### Post by Jimmy_r on 2007-04-26
> **motin said:**
> BUGREPORT:

When I choose to install grub splash images, it puts a line in menu.lst that looks like this:

splashimage=(hd0,0)/boot/grub/splashimages/NightOfUbuntu.xpm.gz

However, since my /boot folder is mounted in it's own partition, the correct path should be:

splashimage=(hd0,0)/grub/splashimages/NightOfUbuntu.xpm.gz

... leading to "Failed to read splash image" errors.

motin and a-musing amazon, I will look into this.

Does anyone know of a way to programmatically find if there is a separate boot partition, and in that case find the correct hdx,y designation and path for ex. splashimages?

---

### Post by motin on 2007-04-26
> **Jimmy_r said:**
> motin and a-musing amazon, I will look into this.

Does anyone know of a way to programmatically find if there is a separate boot partition, and in that case find the correct hdx,y designation and path for ex. splashimages?

I only now quick and dirty bash tricks...

Like if:
```
cat /etc/fstab | grep ' /boot '
```
is empty - then no separate boot partition - probably... :)

---

### Post by LegoAddict on 2007-04-26
How likely is getting what comes from that big bad WARNING!!!!! thingy on your page?


I love my Ubuntu and I don't want to start over, but I want to change (or put in rather) a boot screen, and I can't find certain files (menu.lst instructions I'm following are [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up").  )



I've borked my computer several times, and I don't want to risk it.

I'm on an up to date Ubuntu 7.04 install that's fully functional.

What are the risks, and why could they occur?

---

### Post by Jimmy_r on 2007-04-27
> **LegoAddict said:**
> How likely is getting what comes from that big bad WARNING!!!!! thingy on your page?


I love my Ubuntu and I don't want to start over, but I want to change (or put in rather) a boot screen, and I can't find certain files (menu.lst instructions I'm following are [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up").  )



I've borked my computer several times, and I don't want to risk it.

I'm on an up to date Ubuntu 7.04 install that's fully functional.

What are the risks, and why could they occur?


Well, it is not too likely now, no terrible problems have appeared so far.

But, if you have hand-edited individual boot options in your menu.lst, those changes will be removed by update-grub. (See posts 44 and 152 in this thread.)

Also, if you have a separate boot partition you may meet problems as the last posts indicate.

That said, if the Ubuntu installer autocreated your partition setup and you have not made any big changes to menu.lst, using SUM should be safer than doing it by hand...
Lets say that if I was to install a grub splash or change usplash theme myself, I would rather have SUM doing it for me since my computer has better memory than me. :)

Still, no guarantees provided.

---

### Post by Jimmy_r on 2007-04-27
> **motin said:**
> I only now quick and dirty bash tricks...

Like if:
```
cat /etc/fstab | grep ' /boot '
```
is empty - then no separate boot partition - probably... :)

Thanks, the easy solutions are the best :)

So, in pseudocode I will simply do something like this(groot=grub root):

```
If /etc/fstab contains '/boot'
    splashline = groot+'/grub/splashimages/'+imagename
else
    splashline = groot+'/boot/grub/splashimages/'+imagename
```

Hmm, now I just need to solve the problem for a-musing amazon too.
I cannot depend on the groot gathered from menu.lst.
I need to extract the info from /etc/fstab somehow and convert it to hdx,y format.
In latest Ubuntu versions, /etc/fstab has UUIDs instead of readable strings but (at least for now) still keeps those as comments.
Hmm, it is hard to make the solution rubust considering those factors...

I think I will have it try to read the info from /etc/fstab, then at failure(if the comments are removed for example) fall back on the groot designation in menu.lst.

I think that is the best I can do.

---

### Post by kelvin spratt on 2007-04-27
I don't know if this helps i just downloaded the deb package 1.02.2 or 3 installed it with deb installer and it worked perfect i do not have any probs at all this was from the site mentioned on this thread then i read this thread and the added bonus is i now have a start floppy o yes one of them rather have a disc but aint woked that one out yet

---

### Post by Jimmy_r on 2007-04-27
> **kelvin spratt said:**
> I don't know if this helps i just downloaded the deb package 1.02.2 or 3 installed it with deb installer and it worked perfect i do not have any probs at all this was from the site mentioned on this thread then i read this thread and the added bonus is i now have a start floppy o yes one of them rather have a disc but aint woked that one out yet

It is nice to know when things do work too :)

About the boot floppy. I have not mentioned it, but remember that if your partition layout is changed or a new kernel is installed, the floppy should be rewritten for it to work as expected.

---

### Post by Jimmy_r on 2007-04-28
New version uploaded.
Added a warning when the " ### END DEBIAN AUTOMAGIC KERNELS LIST" line is missing.

If there is a separate boot partition, the splashimage path in menu.lst  will begin with /grub instead of /boot/grub.
Path for installation of themes is still /boot/grub/splashimages.

Please test this, I do not have a separate boot partition to test it.

One thing I did not change is the way groot is detected. Too difficult to convert /dev/hdxy /dev/sdxy to hdzy.

A-musing amazon, the best solution would be for you to change the line ```
# groot=(hd0,0)
``` in menu.lst to the proper value. I consider this bug out of my control, since I should be able to rely on the groot value in menu.lst.

---

### Post by PopeMatt on 2007-04-28
Hey, I'm sure you've gotten a lot of these, but thirty minutes of searching hasn't helped, so if you can just send me a to a link to the fix and bitch at me in DAFS style, I'd be grateful.

But anyway, I'm running a Sony Vaio Media Center desktop upon which I just installed Ubuntu 7.04 Feisty Fawn I finally got a CD drive that can boot correctly (my old ones were really f*cked up for some reason, and it was preventing me from setting up a dual boot), and I'm psyched that I can finally migrate to Linux fully.

After I set up my display, fixed some resolution issues, installed my favorite packages, and of course, configured beryl, I was happy. A few days later, once I was used to the permanent Linux workflow, I found SUM, looking for a way to change my splash screen.

Install, config, restart.

****.

Ubuntu no longer boots. Nor does the recovery console. Windows is fine.
I looked around for fixes, started up with my Ubuntu live CD, and mounted my partition, then did some stuff to menu.list and deleted all the stuff SUM installed. Now GRUB looks like it did originally, (right after installing SUM, it got weird and it was hard to know what partition I had selected and whatnot), but still no boot.

I get this error when trying to boot normally, and when I try to boot into the recovery console:

Kernel panic - not syncing: VFS: Unable to mount on root fs on unknown-block (0,0)


....Please help. I miss Ubuntu.


Thanks,
--Matt

---

### Post by Jimmy_r on 2007-04-29
> 
Kernel panic - not syncing: VFS: Unable to mount on root fs on unknown-block (0,0)
Last time I saw that message was while messing with LFS...

I am not completely sure, but I think it either could be caused by a wrong path in menu.lst or by a kernel that lacks the drivers for accessing your hard disk...
Strange, since SUM should not be able to cause neither... Unless it corrupted the default boot options line. But your recovery mode also had the problem, and SUM should not touch the alternative boot options line at all.

At first run, SUM creates a backup of the menu.lst as /boot/grub/menu.lst.backup
Try to copy it back to /boot/grub/menu.lst and see if that helps. If it does, please attach both the corrupted and good menu.lst so I can see what went wrong.

When setting up the dual boot, did you manually configure any individual boot options? They are overwritten by a system command when sum is started.

What settings did you change with SUM?

---

### Post by PopeMatt on 2007-04-29
I already reverted to the original menu.lst, which fixed the grub-looking-goofy issue, but it still won't boot. =/
Here are my current menu.lst, menu.lst.backup and menu.lst~ files.
In SUM, all I set up was a boot-loader background image.
When I set up the dual boot, I just used the guided partition to resize my Windows partition and allocate it to my Ubuntu. That was it.

Note: Forums didn't like me uploading .lst files, here are the links.
[http://www.sirmattsmith.com/menu.lst](http://www.sirmattsmith.com/menu.lst)
[http://www.sirmattsmith.com/menu.lst.backup](http://www.sirmattsmith.com/menu.lst.backup)
[http://www.sirmattsmith.com/menu.lst~](http://www.sirmattsmith.com/menu.lst~)

---

### Post by Jimmy_r on 2007-04-29
According to your menu.lst, you should have the file /boot/initrd.img-2.6.20-15-generic
Do you also have a file /boot/initrd.img-2.6.20-15-generic.bak

If you have that file, change the initrd line in your menu.lst to use that one instead.
Your default ubuntu boot option will then look like this:
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=45708c38-f5a8-43ec-9f98-40b344bfc394 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic.bak
quiet
savedefault
```

---

### Post by PopeMatt on 2007-04-29
Hey, that workified!
I have a few text errors during startup, but nothing mission critical and everything seems to be working fine. :-D Great, thanks!
Is there anything I should do to clean house, or can I go on my merry way?

Thanks so much!
--Matt

---

### Post by HyperY2K on 2007-04-30
is there a new version of SUM available?

---

### Post by Jimmy_r on 2007-04-30
> **HyperY2K said:**
> is there a new version of SUM available?

The latest version is [startupmanager_1.0.4-1_all.deb]("http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.4-1_all.deb")


PopeMatt, I am glad it worked, it was more a guess than anything else.
The first thing you should do is make a backup of that /boot/initrd.img-2.6.20-15-generic.bak

I guess it will get overwritten next time update-initramfs is run.
That will happen if you use SUM to change boot resolution.
If a package is installed it might also be run, or at a system upgrade too.

The only thing SUM could have changed that affects the initramfs is the usplash resolution.
Open /etc/usplash.conf it should look like this after an install:
```
# Usplash configuration file
xres=1024
yres=768

```

If you make sure it looks like that, SUM is free of further suspicion.

If you want to take the problem of update-initramfs now rather than later do this:

**This may make your system unable to boot again.**

After you have made a backup of initrd.img-2.6.20-15-generic.bak, run 
```
sudo update-initramfs -u
```
And then change the grub menu.lst entry initrd line back to /boot/initrd.img-2.6.20-15-generic

Reboot, and hope for the best.
If you are unable to boot again, change the initrd line to point to the initrd file you manually backed up and you should be able to boot.

---

### Post by motin on 2007-05-01
> **PopeMatt said:**
> Note: Forums didn't like me uploading .lst files, here are the links.
[http://www.sirmattsmith.com/menu.lst](http://www.sirmattsmith.com/menu.lst)
[http://www.sirmattsmith.com/menu.lst.backup](http://www.sirmattsmith.com/menu.lst.backup)
[http://www.sirmattsmith.com/menu.lst~](http://www.sirmattsmith.com/menu.lst~)

The easiest way to send stuff the forums doesn't like is to make a compressed archive of the files. Just a tip.

---

### Post by icyfeet on 2007-05-13
Hi everybody, I'm new in this forum. As I'm not native english -> excuse any mistakes.

I tried SUM the following way on dapper kubuntu.
1. installed via 'sudo python setup.py install' cause I've the wrong version of python-support
2. then I recognized that I can create a package via 'sudo checkinstall python setup.py install'
3. inatallation of the packages to get it familiar with the package-management

My problem:
While booting, the normally displayed messages are gone (not all) and some others are there:
Loading essential drivers [OK] 
Running /scripts/init-premount ??? 
Mounting root file system [OK] 
Running /scripts/local-tmp ??? 
Running /scripts/init-bottom ??? and some other strange "Running /scripts/..."-messages.

While shutdown: 
Resetting the usplash timeout ??? that's all

This behaviour remains, when i remove SUM via synaptic.

What do I have to do, to get the normally displayed messages back?

greetings icyfeet

---

### Post by Jimmy_r on 2007-05-13
Hm, I never thought of that when starting to use python-support for building the package.
If you want to install SUM again, try version 1.0.2, it is not built using python-support: [http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.2-2_all.deb](http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.2-2_all.deb)

Now for your problem, did you change any settings with SUM? Which?

Please attach a copy of your /boot/grub/menu.lst also.

---

### Post by icyfeet on 2007-05-14
Hi again.

menue.lst is at

[http://www.ubuntuusers.de/paste/10724/](http://www.ubuntuusers.de/paste/10724/)

When I first installed via 'sudo python setup.py install', there were only the few messages without the 'Running/scipts/...' left. Then I chose 'show text during boot' and the 'Running/scripts/...' messages were displayed. Same now as I've installed and uninstalled the checkinstall built package.

Don't know if it's of interest:
There is a folder with content remaining: /usr/lib/python2.4/site-packages/Startupmanager

icyfeet

---

### Post by Jimmy_r on 2007-05-14
You can remove the folder /usr/lib/python2.4/site-packages/Startupmanager if you want to, but its presence should not in any way interfere with the boot process.

I am not sure if I understand the problem correctly, but to restore the messages to the old form, you should just need to edit line 98 to change it from
```
# defoptions=splash acpi=on
```
to
```
# defoptions=quiet splash acpi=on
```

and then run ```
sudo update-grub
```

---

### Post by icyfeet on 2007-05-14
Ok, I changed the menue.lst. and made the sudo update-grub

Now I see 3 messages while booting:
loading essential drivers
mounting root file system
resseting the usplash timeout

and one message while shutdown:
resseting the usplash timeout

All the other messeges I had before I installed SUM are still gone while the progressbar (don't know, if this is the right word in english) is 'moving'.

(btw. The same behavior was, when I unmarked the 'show text during boot' in the SUM.)

---

### Post by Jimmy_r on 2007-05-15
Are you sure this is not caused by something else?
Did the problem appear after the install, without even starting sum once?
In that case it must have been caused by something else, since the install does not in any way affect the boot process. Upgrades? Other app install?

If the problem appeared after you run sum once, and only changed the 'show text during boot' option, then this is exactly what SUM has done so far to your system:

Made a  copy of /boot/grub/menu.lst as /boot/grub/menu.lst.backup at first run.
Ran update-grub(at start of app to make sure menu.lst is not missing some lines).
At press on checkbox 'show text during boot': removed the option 'quiet' from defoptions line in menu.lst.
At app shutdown: ran update-grub, since the defoptions line has been changed.

That is all it has done, and we already have changed the defoptions line back.

So, the only thing left I can think of is for you to do a
```
sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst
```

If that does not help, I am sorry but I do not think I can help you.

You may want to post in some more high-traffic part of the forums for more help.

---

### Post by icyfeet on 2007-05-15
Strange, very strange.

Anyway, thank you for your efforts.

---

### Post by Bodifar on 2007-05-19
Cool! I have been looking for this ... well, since yesterday *blush* I'm new to Ubuntu (not quite new to Linux, but still), and I found it quite annoying that I had no GUI to change my startup settings. 

Installation went like a breeze on Ubuntu 7.04 Feisty Fawn ... Downloaded it straight into the Package Installer, it went *plink* (or it did so in my head *grin*), and there it was, sitting in my Administration menu. Sweet!

Great job! (although, I imagine that you've heard this a lot these past 18 pages ;-))

[EDIT] As said before: this should be an official included package in Ubuntu, if you ask me ...

---

### Post by Jimmy_r on 2007-05-25
New version uploaded.
Some minor bugfixes.
No more freezing guis. Time-consuming tasks are done in separate threads.
Progress dialogs are shown during time-consuming tasks.

---

### Post by black07 on 2007-06-02
I think there was no German translation so I decided to create one. Maybe the author can put it into the software.

---

### Post by Jimmy_r on 2007-06-03
German translations added to version 1.0.6

---

### Post by aj.carrier on 2007-06-06
im having trouble, i did have start up manager before, then i removed it. now i realise i want it back and it installs fine, but when i click the startup manager button in system>administration nothing happens, i opened a terminal while i did this and saw nothing come up and no error messages, i cant seem to find the problem, i've already tried removing and reinstalling, but nothing happened when i tried to open it again. Any ideas? the thing im trying to change is the bootsplash, i think this is what it's called (the thing that normally says ubuntu and a progress bar underneath) i have ubuntu 7.04 feisty fawn, and as i say i have had SUM working before, but now it wont. I thought i should add, but i guess you already know, that inittab doesnt exist anymore in feisty and so all the other bootsplash and usplash changers dont work because of this. PLZ PLZ PLZ PLZ help, i've been trying to change the bootsplash to look something like an apple symbol (as im currently in the process of changing my ubuntu to look exactly like mac osx and this is the last thing i need to change) oh and finally i cant even get the normal ubuntu bootsplash usplash up anymore, its just always in verbose mode. HEEEELLLLPPPP!!!!:(:(:(

please reply asap!

---

### Post by Jimmy_r on 2007-06-07
> **aj.carrier said:**
> im having trouble, i did have start up manager before, then i removed it. now i realise i want it back and it installs fine, but when i click the startup manager button in system>administration nothing happens, i opened a terminal while i did this and saw nothing come up and no error messages, i cant seem to find the problem, i've already tried removing and reinstalling, but nothing happened when i tried to open it again. Any ideas? the thing im trying to change is the bootsplash, i think this is what it's called (the thing that normally says ubuntu and a progress bar underneath) i have ubuntu 7.04 feisty fawn, and as i say i have had SUM working before, but now it wont. I thought i should add, but i guess you already know, that inittab doesnt exist anymore in feisty and so all the other bootsplash and usplash changers dont work because of this. PLZ PLZ PLZ PLZ help, i've been trying to change the bootsplash to look something like an apple symbol (as im currently in the process of changing my ubuntu to look exactly like mac osx and this is the last thing i need to change) oh and finally i cant even get the normal ubuntu bootsplash usplash up anymore, its just always in verbose mode. HEEEELLLLPPPP!!!!:(:(:(

please reply asap!


When you open a terminal and write ```
gksu -k /usr/bin/startupmanager
```
what is the output?

---

### Post by mrcreativity on 2007-06-08
I think I messed up 2 Ubuntu installations because of startup manager.

I cant seem to boot into my desktop and laptop with feisty fawn.

Any help would really be appreciated.

Edit: I tried booting into recovery mode, that stops too.

When I try to boot from the Ubuntu Live/Installation CD, i get the following error message:

Kernel panic - not syncing: VFS: Unable to mount on root fs on unknown-block (0,0)

and my laptop just crashes. I had to remove the battery to restart my laptop.

I really need help.

---

### Post by Jimmy_r on 2007-06-08
> **mrcreativity said:**
> I think I messed up 2 Ubuntu installations because of startup manager.

I cant seem to boot into my desktop and laptop with feisty fawn.

Any help would really be appreciated.

Edit: I tried booting into recovery mode, that stops too.

When I try to boot from the Ubuntu Live/Installation CD, i get the following error message:

Kernel panic - not syncing: VFS: Unable to mount on root fs on unknown-block (0,0)

and my laptop just crashes. I had to remove the battery to restart my laptop.

I really need help.


Ok, try this:
When you are at the grub menu, select your default ubuntu boot option and press 'e'
Then, you will see some lines. One should look like this:
```
initrd		/boot/initrd.img-2.6.20-15-generic
```
select that line and press 'e' again.
add a .bak to the end of it so it looks like this instead:
```
initrd		/boot/initrd.img-2.6.20-15-generic.bak
```
Then press enter and then 'b' to boot.

If that works, we will try to fix your system more permanently from there.

By the way, did you do a fresh install of Feisty, or did you upgrade from Edgy?

Edit: What options did you change using SUM?
And did I read that right: Did you boot from the live cd and get that kernel panic? 
And you have booted from that cd before without problems?
That kernel panic could not possibly be caused by sum in that case. Either hardware error or damaged CD, would be my guess.

---

### Post by mrcreativity on 2007-06-08
Thanks for the reply m8.

The trick didn't work. I still cant boot,

The installation CD worked fine before and I have done numerous installs with that cd. And yes, I got the error msg when I tried to boot from the Live CD.

I can remember which options I had enable in SUM, although I know I didnt touch the last 2 tabs on the GUI.

 I did a fresh install of Feisty. 

And I dont think its a hardware problem because both my laptop and desktop which are running feisty refuse to boot. But I havent seen the error on the desktop yet.

---

### Post by mrcreativity on 2007-06-09
I think I fixed it. 

I remembered a copy of the menu.lst that was created after installation.

I booted the live cd, and replaced the menu.lst with the backup one.

Let's see how it boots.

Edit: It worked, I can boot into my ubuntu installation again. All is good in the world now. Thank you all.

---

### Post by jdmcg on 2007-06-11
I have a laptop and 2 hard drives that I swap out between WinXP and Ubunu Feisty. But whenever I bring up SUM (startup-manager) it changes my menu.lst  to erase the availability of booting up in XP. Would anyone know a mod or something to keep this from happening? I don't really like going into my menu.lst just after each time I use SUM.

---

### Post by Jimmy_r on 2007-06-12
> **jdmcg said:**
> I have a laptop and 2 hard drives that I swap out between WinXP and Ubunu Feisty. But whenever I bring up SUM (startup-manager) it changes my menu.lst  to erase the availability of booting up in XP. Would anyone know a mod or something to keep this from happening? I don't really like going into my menu.lst just after each time I use SUM.

SUM runs the command update-grub at start to ensure the menu.lst is healthy.

Can you please post a copy of your menu.lst, I have a feeling you do not have the line
```
 ### END DEBIAN AUTOMAGIC KERNELS LIST
```
above the windows boot option.
Also, see the first post at the page [http://ubuntuforums.org/showthread.php?t=295524&page=16](http://ubuntuforums.org/showthread.php?t=295524&page=16)

---

### Post by thelegionnaire on 2007-06-15
so i installed sum, and set it up, and before it shows my splash screen, it says i need to pick a resolution and gives me a menu, so i set it and next time i boot it does it again...help please?

---

### Post by Jimmy_r on 2007-06-17
> **thelegionnaire said:**
> so i installed sum, and set it up, and before it shows my splash screen, it says i need to pick a resolution and gives me a menu, so i set it and next time i boot it does it again...help please?

Where does it say you need to pick a resolution? Directly at boot?

In that case, there is a resolution specified that your hardware cannot show.

Boot up, open SUM and try changing between the different resolutions / color depths.
Reboot, and see if the bootloader asks the question again.
If it does, continue trying the different color depth/resolution settings in SUM.

Note that the menu shown at boot is no part of SUM, and any settings made there will not be saved.

---

### Post by Jimmy_r on 2007-06-19
SUM is moving to launchpad for bugreports, answers and translations(will be available when Launchpad admins have reviewed the .pot file).

See [https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)

---

### Post by mauricejl on 2007-06-28
Hello, here also the french translation.

---

### Post by Jimmy_r on 2007-06-28
> **mauricejl said:**
> Hello, here also the french translation.

Thank you for the translations. However, another person has already finished the french translation on launchpad.

Please see [https://launchpad.net/startup-manager/trunk/+pots/startup-manager/fr/+translate](https://launchpad.net/startup-manager/trunk/+pots/startup-manager/fr/+translate), if you are interested in helping with translations of future versions.

---

### Post by mauricejl on 2007-06-28
Your software is very good, for a graphic user like me. 
I hope it will be include in the next ubuntu version 7.10
But how to get SUM in french now?

---

### Post by Jimmy_r on 2007-06-29
> **mauricejl said:**
> Your software is very good, for a graphic user like me. 
I hope it will be include in the next ubuntu version 7.10
But how to get SUM in french now?

The latest version at [http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.8-1_all.deb](http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.8-1_all.deb) has the frensh translation.

---

### Post by betawind on 2007-09-16
Whenever I try to load SUM from a terminal I get the below:

  File "/usr/bin/startupmanager", line 29, in <module>
    main()
  File "/usr/bin/startupmanager", line 26, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 364, in __init__
    self.update_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 870, in update_widgets
    titles = self.grub.get_titles()
AttributeError: SumGui instance has no attribute 'grub'

I see the SUM window flash on my screen for half a second, then nothing.  Any thoughts?

Oh and since I see you ask for this alot, heres my menu.lst file :)

default 0
timeout 10

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=93923d4c-3f4d-4c0d-98c2-11d9a021572d ro quiet splash vga=771
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=93923d4c-3f4d-4c0d-98c2-11d9a021572d ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Windows Vista/Longhorn (loader)
root            (hd0,3)
savedefault
makeactive
chainloader     +1

---

### Post by earobinson on 2007-09-16
its on get deb!
[http://www.getdeb.net/app.php?name=Startup+Manager](http://www.getdeb.net/app.php?name=Startup+Manager)

---

### Post by betawind on 2007-09-16
Thanks earobinson!  you rock!

---

### Post by TheeMahn2003 on 2007-09-18
Jimmy, I am sorry I don't have time to read your entire thread (getting larger a good sign you are doing a good job BTW), as I hope you can imagine, my users are really liking your software integrated in UUE 1.4+.  I thought I would press some kudos your direction on behalf of the users.  Seems to me people do not take the time to give thanks when and where it is appropriate.  I am here to say thanks on behalf of the many, many (1.4 has been downloaded close to 2 million times) that have used and love your software.  Great job keep up the good work.  I did not come here to brag only to show how many people now see and use your software.  Just to give some insight (1 server of 10):

```
17.	Total data transferred 	12.123 TB
18.	Total data transferred in last 7 days 	2.616 TB
```


Thanks again,

TheeMahn

---

### Post by Jimmy_r on 2007-10-02
TheeMahn: That is great :)

Betawind: I did not quite understand your conversation with earobinson. Should I understand it as that your problem is solved?

---

### Post by AmericanYellow on 2007-10-16
My System Crashed! Really Is A Risk!:(:(

---

### Post by Jimmy_r on 2007-10-17
> **AmericanYellow said:**
> My System Crashed! Really Is A Risk!:(:(

Mind sharing what went wrong?

---

### Post by QwertyManiac on 2007-10-20
Safe to use this on Gutsy Gibbon? :)

---

### Post by jaybombalous on 2007-10-20
U try it out for us and then gives us some feedback. I would try it but I am not into fixing a computer tonight.

Will heck back to see if anyone else gets it working on gutsy.

---

### Post by Jimmy_r on 2007-10-22
I have been using(and developing) it on Gutsy for a few months now. It should be as safe as on earlier versions :)

---

### Post by Occas on 2007-10-31
I'm getting a black screen and a rebooting computer (after about a minute into booting)

Now I've gotta figure out what the program changed and how to reverse it.

*Update*

I restored the backup and works fine again, albeit still without a splash screen though.

Seems the only thing different was that it added vga=795 at the end of the main boot sequence.

I think for now I'm just gonna accept that I won't have bot or shutdown screens in x64 until its officially fixed...

Cheers!

---

### Post by Jimmy_r on 2007-11-01
Yes, that is a bug in Gutsy.

Try to edit the resolutions in /etc/usplash.conf

then run 
sudo update-initramfs -uk all

---

### Post by Occas on 2007-11-05
Thanks!

---

### Post by TheeMahn2003 on 2007-11-18
> **Jimmy_r said:**
> Yes, that is a bug in Gutsy.

Try to edit the resolutions in /etc/usplash.conf

then run 
sudo update-initramfs -uk all

Sorry it has been so long since I touched base here, I run my own [forum]("http://forumubuntusoftware.info") 5 servers to manage now crazy...   I am enjoying your new Startup Manager with grub 2 I thought I would stop by & tell you great job...  Like your new site design as well.  Once I test all the options and assure no problems I will update it on the repo.  I thought I would drop by and share some source I wrote in c that creates Usplashes:
```

/* Ubuntu Ultimate Usplash Maker
*
# Copyright (c) 2007  Ubuntusoftware Team <http://ubuntusoftware.info>
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
*/

#include <usplash-theme.h>
/* Needed for the custom drawing functions */
#include <usplash_backend.h>
extern struct usplash_pixmap pixmap_usplash_640_400, pixmap_usplash_640_480;
extern struct usplash_pixmap pixmap_usplash_800_600, pixmap_usplash_1024_768, pixmap_usplash_1280_1024;
extern struct usplash_pixmap pixmap_throbber_back_640_400;
extern struct usplash_pixmap pixmap_throbber_back_640_480;
extern struct usplash_pixmap pixmap_throbber_back_800_600;
extern struct usplash_pixmap pixmap_throbber_back_1024_768;
extern struct usplash_pixmap pixmap_throbber_back_1280_1024;
extern struct usplash_pixmap pixmap_throbber_fore_640_400;
extern struct usplash_pixmap pixmap_throbber_fore_640_480;
extern struct usplash_pixmap pixmap_throbber_fore_800_600;
extern struct usplash_pixmap pixmap_throbber_fore_1024_768;
extern struct usplash_pixmap pixmap_throbber_fore_1280_1024;
extern struct usplash_font font_helvB10;

void t_init(struct usplash_theme* theme);
void t_clear_progressbar_640_400(struct usplash_theme* theme);
void t_clear_progressbar_640_480(struct usplash_theme* theme);
void t_clear_progressbar_800_600(struct usplash_theme* theme);
void t_clear_progressbar_1024_768(struct usplash_theme* theme);
void t_clear_progressbar_1280_1024(struct usplash_theme* theme);
void t_draw_progressbar_640_400(struct usplash_theme* theme, int percentage);
void t_draw_progressbar_640_480(struct usplash_theme* theme, int percentage);
void t_draw_progressbar_800_600(struct usplash_theme* theme, int percentage);
void t_draw_progressbar_1024_768(struct usplash_theme* theme, int percentage);
void t_draw_progressbar_1280_1024(struct usplash_theme* theme, int percentage);
void t_animate_step_640_400(struct usplash_theme* theme, int pulsating);
void t_animate_step_640_480(struct usplash_theme* theme, int pulsating);
void t_animate_step_800_600(struct usplash_theme* theme, int pulsating);
void t_animate_step_1024_768(struct usplash_theme* theme, int pulsating);
void t_animate_step_1280_1024(struct usplash_theme* theme, int pulsating);


struct usplash_theme usplash_theme_640_480;
struct usplash_theme usplash_theme_800_600;
struct usplash_theme usplash_theme_1024_768;
struct usplash_theme usplash_theme_1280_1024;

struct usplash_theme usplash_theme = {
   .version = THEME_VERSION, /* ALWAYS set this to THEME_VERSION,
                                 it's a compatibility check */
    .next = &usplash_theme_640_480,
    .ratio = USPLASH_4_3,

   /* Background and font */
   .pixmap = &pixmap_usplash_640_400,
   .font   = &font_helvB10,

   /* Palette indexes */
   .background             = 0x0,
     .progressbar_background = 0x7,
     .progressbar_foreground = 0x156,
   .text_background        = 0x15,
   .text_foreground        = 0x31,
   .text_success           = 0x171,
   .text_failure           = 0x156,

   /* Progress bar position and size in pixels */
     .progressbar_x      = 212, /* 640/2-216/2 */
     .progressbar_y      = 321,
     .progressbar_width  = 216,
     .progressbar_height = 8,

   /* Text box position and size in pixels */
     .text_x      = 120,
     .text_y      = 307,
     .text_width  = 360,
     .text_height = 100,

   /* Text details */
     .line_height  = 15,
     .line_length  = 32,
     .status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar_640_400,
    .draw_progressbar = t_draw_progressbar_640_400,
    .animate_step = t_animate_step_640_400,
};

struct usplash_theme usplash_theme_640_480 = {
   .version = THEME_VERSION, /* ALWAYS set this to THEME_VERSION,
                                 it's a compatibility check */
    .next = &usplash_theme_800_600,
    .ratio = USPLASH_4_3,

   /* Background and font */
   .pixmap = &pixmap_usplash_640_480,
   .font   = &font_helvB10,

   /* Palette indexes */
   .background             = 0x0,
     .progressbar_background = 0x7,
     .progressbar_foreground = 0x156,
   .text_background        = 0x15,
   .text_foreground        = 0x31,
   .text_success           = 0x171,
   .text_failure           = 0x156,

   /* Progress bar position and size in pixels */
     .progressbar_x      = 212, /* 640/2-216/2 */
     .progressbar_y      = 291,
     .progressbar_width  = 216,
     .progressbar_height = 8,

   /* Text box position and size in pixels */
     .text_x      = 160,
     .text_y      = 312,
     .text_width  = 320,
     .text_height = 100,

   /* Text details */
     .line_height  = 15,
     .line_length  = 32,
     .status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar_640_480,
    .draw_progressbar = t_draw_progressbar_640_480,
    .animate_step = t_animate_step_640_480,
};

struct usplash_theme usplash_theme_800_600 = {
   .version = THEME_VERSION, /* ALWAYS set this to THEME_VERSION,
                                 it's a compatibility check */
    .next = &usplash_theme_1024_768,
    .ratio = USPLASH_4_3,

   /* Background and font */
   .pixmap = &pixmap_usplash_800_600,
   .font   = &font_helvB10,

   /* Palette indexes */
   .background             = 0x0,
     .progressbar_background = 0x7,
     .progressbar_foreground = 0x156,
   .text_background        = 0x15,
   .text_foreground        = 0x31,
   .text_success           = 0x171,
   .text_failure           = 0x156,

   /* Progress bar position and size in pixels */
     .progressbar_x      = 292, /* 800/2-216/2 */
     .progressbar_y      = 370,
     .progressbar_width  = 216,
     .progressbar_height = 8,

   /* Text box position and size in pixels */
     .text_x      = 225,
     .text_y      = 407,
     .text_width  = 360,
     .text_height = 100,

   /* Text details */
     .line_height  = 15,
     .line_length  = 32,
     .status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar_800_600,
    .draw_progressbar = t_draw_progressbar_800_600,
    .animate_step = t_animate_step_800_600,
};

struct usplash_theme usplash_theme_1024_768 = {
   .version = THEME_VERSION,
    .next = &usplash_theme_1280_1024,
    .ratio = USPLASH_4_3,

   /* Background and font */
   .pixmap = &pixmap_usplash_1024_768,
   .font   = &font_helvB10,

   /* Palette indexes */
   .background             = 0x0,
     .progressbar_background = 0x7,
     .progressbar_foreground = 0x156,
   .text_background        = 0x15,
   .text_foreground        = 0x31,
   .text_success           = 0x171,
   .text_failure           = 0x156,

   /* Progress bar position and size in pixels */
     .progressbar_x      = 404, /* 1024/2 - 216/2 */
     .progressbar_y      = 475,
     .progressbar_width  = 216,
     .progressbar_height = 8,

   /* Text box position and size in pixels */
     .text_x      = 322,
     .text_y      = 525,
     .text_width  = 380,
     .text_height = 100,

   /* Text details */
     .line_height  = 15,
     .line_length  = 32,
     .status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar_1024_768,
    .draw_progressbar = t_draw_progressbar_1024_768,
    .animate_step = t_animate_step_1024_768,
};

/* Added 1280 X 1024 support*/

struct usplash_theme usplash_theme_1280_1024 = {
   .version = THEME_VERSION,
    .next = NULL,
    .ratio = USPLASH_4_3,

   /* Background and font */
   .pixmap = &pixmap_usplash_1280_1024,
   .font   = &font_helvB10,

   /* Palette indexes */
   .background             = 0x0,
     .progressbar_background = 0x7,
     .progressbar_foreground = 0x156,
   .text_background        = 0x15,
   .text_foreground        = 0x252, /*was 31*/
   .text_success           = 0x171,
   .text_failure           = 0x156,

   /* Progress bar position and size in pixels */
     .progressbar_x      = 532, /* 1280/2 - 512/2 */
     .progressbar_y      = 595,
     .progressbar_width  = 525,
     .progressbar_height = 8,

   /* Text box position and size in pixels */
     .text_x      = 377,
     .text_y      = 640,
     .text_width  = 525,
     .text_height = 100,

   /* Text details */
     .line_height  = 15,
     .line_length  = 32,
     .status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar_1280_1024,
    .draw_progressbar = t_draw_progressbar_1280_1024,
    .animate_step = t_animate_step_1280_1024,
};

void t_init(struct usplash_theme *theme) {
    int x, y;
    usplash_getdimensions(&x, &y);
    theme->progressbar_x = (x - theme->pixmap->width)/2 + theme->progressbar_x;
    theme->progressbar_y = (y - theme->pixmap->height)/2 + theme->progressbar_y;
}

void t_clear_progressbar_640_400(struct usplash_theme *theme) {
    t_draw_progressbar_640_400(theme, 0);
}

void t_clear_progressbar_640_480(struct usplash_theme *theme) {
    t_draw_progressbar_640_480(theme, 0);
}

void t_clear_progressbar_800_600(struct usplash_theme *theme) {
    t_draw_progressbar_800_600(theme, 0);
}

void t_clear_progressbar_1024_768(struct usplash_theme *theme) {
    t_draw_progressbar_1024_768(theme, 0);
}

void t_clear_progressbar_1280_1024(struct usplash_theme *theme) {
    t_draw_progressbar_1280_1024(theme, 0);
}

void t_draw_progressbar_640_400(struct usplash_theme *theme, int percentage) {
    int w = (pixmap_throbber_back_640_400.width * percentage / 100);
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_640_400);
    if(percentage == 0)
        return;
    if(percentage < 0)
        usplash_put_part(theme->progressbar_x - w, theme->progressbar_y, pixmap_throbber_back_640_400.width + w,
                         pixmap_throbber_back_640_400.height, &pixmap_throbber_fore_640_400, -w, 0);
    else
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_640_400.height,
                         &pixmap_throbber_fore_640_400, 0, 0);
}

void t_draw_progressbar_640_480(struct usplash_theme *theme, int percentage) {
    int w = (pixmap_throbber_back_640_480.width * percentage / 100);
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_640_480);
    if(percentage == 0)
        return;
    if(percentage < 0)
        usplash_put_part(theme->progressbar_x - w, theme->progressbar_y, pixmap_throbber_back_640_480.width + w,
                         pixmap_throbber_back_640_480.height, &pixmap_throbber_fore_640_480, -w, 0);
    else
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_640_480.height,
                         &pixmap_throbber_fore_640_480, 0, 0);
}

void t_draw_progressbar_800_600(struct usplash_theme *theme, int percentage) {
    int w = (pixmap_throbber_back_800_600.width * percentage / 100);
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_800_600);
    if(percentage == 0)
        return;
    if(percentage < 0)
        usplash_put_part(theme->progressbar_x - w, theme->progressbar_y, pixmap_throbber_back_800_600.width + w,
                         pixmap_throbber_back_800_600.height, &pixmap_throbber_fore_800_600, -w, 0);
    else
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_800_600.height,
                         &pixmap_throbber_fore_800_600, 0, 0);
}

void t_draw_progressbar_1024_768(struct usplash_theme *theme, int percentage) {
    int w = (pixmap_throbber_back_1024_768.width * percentage / 100);
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_1024_768);
    if(percentage == 0)
        return;
    if(percentage < 0)
        usplash_put_part(theme->progressbar_x - w, theme->progressbar_y, pixmap_throbber_back_1024_768.width + w,
                         pixmap_throbber_back_1024_768.height, &pixmap_throbber_fore_1024_768, -w, 0);
    else
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_1024_768.height,
                         &pixmap_throbber_fore_1024_768, 0, 0);
}

void t_draw_progressbar_1280_1024(struct usplash_theme *theme, int percentage) {
    int w = (pixmap_throbber_back_1280_1024.width * percentage / 100);
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_1280_1024);
    if(percentage == 0)
        return;
    if(percentage < 0)
        usplash_put_part(theme->progressbar_x - w, theme->progressbar_y, pixmap_throbber_back_1280_1024.width + w,
                         pixmap_throbber_back_1280_1024.height, &pixmap_throbber_fore_1280_1024, -w, 0);
    else
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_1280_1024.height,
                         &pixmap_throbber_fore_1024_768, 0, 0);
}

void t_animate_step_640_400(struct usplash_theme* theme, int pulsating) {

    static int pulsate_step = 0;
    static int pulse_width = 56;
    static int step_width = 2;
    static int num_steps = 0;
    int x1;
    num_steps = (pixmap_throbber_fore_640_400.width - pulse_width)/2;

    if (pulsating) {
        t_draw_progressbar_640_400(theme, 0);
   
        if(pulsate_step < num_steps/2+1)
           x1 = 2 * step_width * pulsate_step;
        else
           x1 = pixmap_throbber_fore_640_400.width - pulse_width - 2 * step_width * (pulsate_step - num_steps/2+1);

        usplash_put_part(theme->progressbar_x + x1, theme->progressbar_y, pulse_width,
                         pixmap_throbber_fore_640_400.height, &pixmap_throbber_fore_640_400, x1, 0);

        pulsate_step = (pulsate_step + 1) % num_steps;
    }
}

void t_animate_step_640_480(struct usplash_theme* theme, int pulsating) {

    static int pulsate_step = 0;
    static int pulse_width = 56;
    static int step_width = 2;
    static int num_steps = 0;
    int x1;
    num_steps = (pixmap_throbber_fore_640_480.width - pulse_width)/2;

    if (pulsating) {
        t_draw_progressbar_640_480(theme, 0);
   
        if(pulsate_step < num_steps/2+1)
           x1 = 2 * step_width * pulsate_step;
        else
           x1 = pixmap_throbber_fore_640_480.width - pulse_width - 2 * step_width * (pulsate_step - num_steps/2+1);

        usplash_put_part(theme->progressbar_x + x1, theme->progressbar_y, pulse_width,
                         pixmap_throbber_fore_640_480.height, &pixmap_throbber_fore_640_480, x1, 0);

        pulsate_step = (pulsate_step + 1) % num_steps;
    }
}

void t_animate_step_800_600(struct usplash_theme* theme, int pulsating) {

    static int pulsate_step = 0;
    static int pulse_width = 56;
    static int step_width = 2;
    static int num_steps = 0;
    int x1;
    num_steps = (pixmap_throbber_fore_800_600.width - pulse_width)/2;

    if (pulsating) {
        t_draw_progressbar_800_600(theme, 0);
   
        if(pulsate_step < num_steps/2+1)
           x1 = 2 * step_width * pulsate_step;
        else
           x1 = pixmap_throbber_fore_800_600.width - pulse_width - 2 * step_width * (pulsate_step - num_steps/2+1);

        usplash_put_part(theme->progressbar_x + x1, theme->progressbar_y, pulse_width,
                         pixmap_throbber_fore_800_600.height, &pixmap_throbber_fore_800_600, x1, 0);

        pulsate_step = (pulsate_step + 1) % num_steps;
    }
}

void t_animate_step_1024_768(struct usplash_theme* theme, int pulsating) {

    static int pulsate_step = 0;
    static int pulse_width = 56;
    static int step_width = 2;
    static int num_steps = 0;
    int x1;
    num_steps = (pixmap_throbber_fore_1024_768.width - pulse_width)/2;

    if (pulsating) {
        t_draw_progressbar_1024_768(theme, 0);
   
        if(pulsate_step < num_steps/2+1)
           x1 = 2 * step_width * pulsate_step;
        else
           x1 = pixmap_throbber_fore_1024_768.width - pulse_width - 2 * step_width * (pulsate_step - num_steps/2+1);

        usplash_put_part(theme->progressbar_x + x1, theme->progressbar_y, pulse_width,
                         pixmap_throbber_fore_1024_768.height, &pixmap_throbber_fore_1024_768, x1, 0);

        pulsate_step = (pulsate_step + 1) % num_steps;
    }
}

void t_animate_step_1280_1024(struct usplash_theme* theme, int pulsating) {

    static int pulsate_step = 0;
    static int pulse_width = 56;
    static int step_width = 2;
    static int num_steps = 0;
    int x1;
    num_steps = (pixmap_throbber_fore_1280_1024.width - pulse_width)/2;

    if (pulsating) {
        t_draw_progressbar_1280_1024(theme, 0);
   
        if(pulsate_step < num_steps/2+1)
           x1 = 2 * step_width * pulsate_step;
        else
           x1 = pixmap_throbber_fore_1280_1024.width - pulse_width - 2 * step_width * (pulsate_step - num_steps/2+1);

        usplash_put_part(theme->progressbar_x + x1, theme->progressbar_y, pulse_width,
                         pixmap_throbber_fore_1280_1024.height, &pixmap_throbber_fore_1280_1024, x1, 0);

        pulsate_step = (pulsate_step + 1) % num_steps;
    }
}
```

Makefile:
```

CC=gcc
CFLAGS=-g -Wall -fPIC
LDFLAGS=
INCLUDES=

COMPILE = $(CC) $(INCLUDES) $(CFLAGS)
LINK = $(CC) $(CFLAGS) $(LDFLAGS)

INSTALL = /usr/bin/install -c
INSTALL_DATA = $(INSTALL) -m 644
INSTALL_PROGRAM = $(INSTALL) -m 755

usplash-theme-ubuntu.so: throbber_back_640_400.png.c.o throbber_back_640_480.png.c.o throbber_back_800_600.png.c.o  \
                         throbber_back_1024_768.png.c.o throbber_back_1280_1024.png.c.o \
          throbber_fore_640_400.png.c.o throbber_fore_640_480.png.c.o throbber_fore_800_600.png.c.o  \
                         throbber_fore_1024_768.png.c.o throbber_fore_1280_1024.png.c.o \
                         usplash_640_400.png.c.o usplash_640_480.png.c.o usplash_800_600.png.c.o \
               usplash_1024_768.png.c.o usplash_1280_1024.png.c.o \
          usplash-theme-ubuntu.c.o

   $(COMPILE) -shared -o $@ $^

%.png.c: %.png
   pngtousplash $< > $@

%.bdf.c: %.bdf
   bdftousplash $< > $@

%.c.o: %.c
   $(COMPILE) -o $@ -c $<

install:
   $(INSTALL) -d $(DESTDIR)/usr/lib/usplash
   $(INSTALL_PROGRAM) usplash-theme-ubuntu.so $(DESTDIR)/usr/lib/usplash/usplash-theme-ubuntu.so
clean:
   rm -f *.png.c *.bdf.c *.c.o
```

Full [source]("http://ubuntusoftware.info/themes/usplash-Ultimate-sources.tar.gz") including jpgs, original [post]("http://forumubuntusoftware.info/viewtopic.php?f=23&t=60").

Enjoy!!! & thanks for the software.

---

### Post by Jimmy_r on 2007-11-19
Yes I see you have been busy :)

Thanks, I am very happy with the website redesign. I have absolutely no skill with those things myself, a [web designer]("http://lukeen.deviantart.com/") contacted me and offered to fix it.

I see you made the progressbar use different size at different resolutions. That is good, I was playing with these things some time ago but never finished it.
This code could come in handy if I revisit some old projects, thanks.

---

### Post by icyfeet on 2008-02-11
Finally I found the solution for my problem (p. 18 ).

The file
/etc/lsb-base-logging.sh
was missing.
Maybe I deletet it by accident.

---

### Post by Jimmy_r on 2008-02-13
> **icyfeet said:**
> Finally I found the solution for my problem (p. 18 ).

The file
/etc/lsb-base-logging.sh
was missing.
Maybe I deletet it by accident.

9 months later. Wow, you dont give up easily, do you :)

---

### Post by Mark76 on 2008-02-15
Why does it pull in Firefox? :confused:

---

### Post by DJ_Peng on 2008-02-15
It pulls in Firefox? I haven't seen that happen in any of the many times I've fired up SUM.

---

### Post by Mark76 on 2008-02-15
Try uninstalling it in a terminal and tell me what happens ;)

---

### Post by Jimmy_r on 2008-02-18
> **Mark76 said:**
> Why does it pull in Firefox? :confused:

It depends on yelp for viewing documentation, and yelp depends on firefox.

I have been thinking about this recently, and the little documentation there is does not really warrant this dependency.
Maybe it would be better to keep it a pure gtk app and take the gnome dependencies away.
I might do that for the next version.

---

### Post by Mark76 on 2008-02-18
That sounds like an excellent idea :)

There should be more pure GTK apps.

---

### Post by cashmoney on 2008-08-14
hopefully your still watching this thread but 

I ran startup manager to change my splash and I get this error when I boot ubuntu. 
USB 1-2 unable to read config index 0 descriptor/all  
USB 1-2 Can't read configurations error -71

ive tried sudo dpkg-reconfigure linux-image-$(uname -r)

to no avail any ideas.

---

### Post by zollen on 2010-01-07
I have been using the Start-Up Manager, but I does not offer option for deleting any unwanted entries?? Anyone know who to do it??

---

### Post by beuzel on 2010-08-19
Hi,

I have windows xp on my computer. then i installed ubuntu 10.04 in parallel. everythings worked fine, but i wanted windows to be the default os to start in grub manager. so i installed the startup manager and set the default, but the i got a surprise after restart:

the entry "windows" in grub was deleted! starting ubuntu again an the startup manager still shows the windows entry. how can i fix this?

i have no experience in linux, please say it step by step.

thanks chris

---

