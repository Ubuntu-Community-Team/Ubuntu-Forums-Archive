---
title: "HOWTO: Install KBFX"
date: 2005-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-09-29
**[COLOR="Red"]THIS GUIDE DOES NOT WORK ON UBUNTU DAPPER 6.06 ![/COLOR]**


This guide is aimed at newbies (as it's easy to follow) and at everyone who want to make his/her desktop a bit more eyecandy (it will substitute your start menu). You can customise the button according to your taste.
It works in KDE ONLY (but it doesn't damage GNOME in any way, you just can't use it in GNOME)

You can have a look at a screenshot of my former desktop computer sporting a Kubuntu button:

[http://ubuntuforums.org/gallery/showimage.php?i=700&original=1&c=3]("http://ubuntuforums.org/gallery/showimage.php?i=700&original=1&c=3")

[COLOR="Red"]UPDATE: Now you can see the package in Synaptic/Kynaptic and uninstall it as any other application. Moreover a .deb will be generated and you will not have to repeat the compilation from source any more (you will use the .deb package)[/COLOR]


1) Open Synaptic/Kynaptic

Press the “Search” button

Type “kdevelop” in the search field and press enter

You will see a list of files

select “kdevelop” and “kdevelop3-dev” (click on the empty square beside these names and select “Mark for Installation”)

Press the “Search” button again

Type “build” in the search field and press enter

select “build-essential” (click on the empty square beside these names and select “Mark for Installation”)

Press the “Search” button again

Type “checkinstall” in the search field and press enter

select “checkinstall” (click on the empty square beside these names and select “Mark for Installation”)

Press the “Apply” button (then it will ask you for confirm, click Apply again)

Close Synaptic/Kynaptic

2) Download Kbfx source from the link below

[http://www.kde-look.org/content/show.php?content=24898]("http://www.kde-look.org/content/show.php?content=24898")

(get the latest release)

3) Open Terminal/Konsole and type:

cd  the_folder_in_which_you_put_the_file_you_downloaded

e.g. cd OperaDownloads  in my case 

tar -xjf kbfx-4.7.3.tar.bz2 (the name of the file you downloaded, which may vary from mine)

cd kbfx-4.7.3 (according to the name of the folder created by your file)

./configure --prefix=/usr (DON'T forget the dot “.” at the beginning of the line)
sudo make

sudo checkinstall

At a certain point it will ask you some question: press ENTER to use the default answer

Then the following sentence will appear:
[QUOTE=]Please write a description for the package.
End your description with an empty line or EOF.
>> [/QUOTE]

You can write a description if the package if you wish (otherwise leave it blank and press ENTER two times) [COLOR="Blue"](e.g. I put "Suse win deco" because I was not installing kbfx but the process is the same but the name of YOUR package will be kbfx)[/COLOR]
Press ENTER two times

Then it will ask you (this is just an example): 
[QUOTE=]This package will be built according to these values:

0 -  Maintainer: [ [email]root@localhost.loca[/email]ldomain ]
1 -  Summary: [ Suse win deco ]
2 -  Name:    [ kwin-decor-suse2-0.3 ]
3 -  Version: [ 0.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ kwin-decor-suse2-0.3 ]
9 -  Alternate source location: [  ]

Enter a number to change any of them or press ENTER to continue:[/QUOTE]

Press ENTER (unless you want to modify something)

Now you have made a .deb package of the desired program (next time you can use this to install it) (inside the folder containing the source) and you will see the program in synaptic/kynaptic too (this means you can uninstall it as any other application)

3) Ok, now you have installed the latest version of KBFX.

Now let's make it work

Right click on the panel (the main panel where you have the start menu and other icons) and select /Add to panel/Applet/kbfx

A new button will appear.

If you want to customise the button you have to download a kbfx button from [http://www.kde-look.org/]("http://www.kde-look.org/") (type kbfx in the search engine of the website)

You can drag and drop the image of the button you wish to use into the current kbfx button.

4) The size of the image usually doesn't match the size of the button, try this:

Right click on the panel (NOT ON KBFX BUTTON!) (do it on a free space)

and select /Remove from panel/Applet/kbfx

then again Right click on the panel and select /Add to panel/Applet/kbfx

Now it will match the size of the image.

5) If the result pleases you you can remove your kmenu button (you can always put it back if you wish)

Right click on the “kmenu” (the start menu) and select “Remove k menu”

6) Click on the left handler of  your kbfx button in order to move it and place it at the extreme left side of the panel (where your start menu was)

NOTE: If the kbfx button doesn't match the size (width) of the panel you will have to modify the size of your panel (quite obviously)

Enjoy your new button!

Alberto

---

### Post by Jonathan2007 on 2005-10-08
Thanks a lot for this guide.

But I ran into one problem. You said you need to do a ```
./configure –prefix=/usr
``` but that doesn't work. You need to do a ```
./configure --prefix=/usr
```. Please change that in your post.

Other than that it worked great. I had previously had the deb version of kbfx (the one that is floating around here on the forums). I couldn't figure out how to uninstall it so I just compilled and hopefully installed this one over the other one. The other one was an old version too so that is why I am upgrading.

Thanks again for the guide. :)

---

### Post by tseliot on 2005-10-08
[QUOTE=Jonathan2007]Thanks a lot for this guide.

But I ran into one problem. You said you need to do a ```
./configure &#8211;prefix=/usr
``` but that doesn't work. You need to do a ```
./configure --prefix=/usr
```. Please change that in your post.

Other than that it worked great. I had previously had the deb version of kbfx (the one that is floating around here on the forums). I couldn't figure out how to uninstall it so I just compilled and hopefully installed this one over the other one. The other one was an old version too so that is why I am upgrading.

Thanks again for the guide. :)[/QUOTE]
You're right. It was a typo but I've fixed it now. Thanks for making me notice it

---

### Post by farmer on 2005-10-11
You should also look into using .debs instead of make install.[Checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/index.php") is the tool that does it.  The backports people can tell you more about that works. I only know it's there.

---

### Post by tseliot on 2005-10-12
[QUOTE=farmer]You should also look into using .debs instead of make install.[Checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/index.php") is the tool that does it.  The backports people can tell you more about that works. I only know it's there.[/QUOTE]
Very interesting, thanks :)

---

### Post by tseliot on 2005-10-16
[QUOTE=farmer]You should also look into using .debs instead of make install.[Checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/index.php") is the tool that does it.  The backports people can tell you more about that works. I only know it's there.[/QUOTE]
I've updated my guide

---

### Post by CAE on 2005-10-20
Can someone post their .deb?

---

### Post by tseliot on 2005-10-20
[QUOTE=CAE]Can someone post their .deb?[/QUOTE]
Have you tried my method? It's very easy (although it looks long to describe). You can make your own .deb (once for all)

---

### Post by CAE on 2005-10-20
[QUOTE=tseliot]Have you tried my method? It's very easy (although it looks long to describe). You can make your own .deb (once for all)[/QUOTE]

I have, but I can't get kdevelop from the repos (it does recommend an alternative package, however). I've also mentioned keeping my install size down as small as possible due to my small disk size in a thread with you before, so I don't really want to install packages I'll probably only use once and then forget to remove. :p

Also, this isn't Gentoo, I'm quite happy with a binary distro and I don't feel the need to build everything from the source. ;)

---

### Post by CAE on 2005-10-26
Still waiting for a .deb.

---

### Post by abandoned_hussam on 2005-10-26
[QUOTE=CAE]Still waiting for a .deb.[/QUOTE]
If you want, I can mail you a breezy kbfx.deb , I rememeber making one ( a real one, not with checkinstall ). PM me your email.

---

### Post by Josef K. on 2005-10-31
[QUOTE=tseliot]./configure --prefix=/usr (DON'T forget the dot &#8220;.&#8221; at the beginning of the line)
sudo make
[/QUOTE]

got this error message
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
what does it means?! :(

---

### Post by tseliot on 2005-10-31
[QUOTE=Josef K.]got this error message
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
what does it means?! :([/QUOTE]
I don't know what the problem can be, try to install all the versions of "automake" you can see in synaptic/kynaptic.

---

### Post by jyhelle on 2005-10-31
[QUOTE=Josef K.]got this error message
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
what does it means?! :([/QUOTE]

means your system is missing some development files (not needed to run applications, but needed to compile/link them)
Just finished my installation, and as I had the same problem, here's the solution that worked for me:
on my system (fresh K5.10 installed 3 days ago) I had to install (I used Adept) the four following packages:
  xlibs-dev
  libqt3-headers
  libqt3-mt-headers
  kdelibs4-dev
also, since I use an AMD64 platform, I had to change item 7 in the checkinstall menu from "x86-64" to "amd64"
cheers,
JL

---

### Post by biovore on 2006-01-10
> 
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!


I had this error too.. after some hacking around.. I found a missing dependency for this source code buid

sudo apt-get install libxaw6-dev

fixed it here..   no clue why..
just figure I point it out..

---

### Post by limit223 on 2006-01-10
Beside
"(DON'T forget the dot “.” at the beginning of the line)" :P

"sudo make" <--- which I've never used it like this, all I know simple command: make :P

thank you for pointing me to this nice windowish theme

Cheers

---

### Post by Sokraates on 2006-01-14
Drats.

I get this error running make (or sudo make):

```
In file included from vistabar.h:19,
                              from kbfxvista.h:37,
                              from kbfxvista.cpp:1:
vistalistbox.h:11:27: error: listboxtile.xpm: No such file or directory
kbfxvista.cpp: In member function 'void kbfxvista::menuInit()':
kbfxvista.cpp:49: warning: format not a string literal and no format arguments
kbfxvista.cpp:52: warning: format not a string literal and no format arguments
kbfxvista.cpp: At global scope:
kbfxvista.cpp:203: warning: unused parameter 'height'
kbfxvista.cpp:213: warning: unused parameter 'width'
kbfxvista.cpp:256: warning: unused parameter 'o'
kbfxvista.cpp:405: warning: unused parameter 'x'
make[3]: *** [kbfxvista.lo] error 1
```

---

### Post by capitalistpiglet on 2006-01-14
> 
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!



when i try and install i get this error, i used the ./configure --prefix=/usr as the guide says.

---

### Post by tseliot on 2006-01-15
[QUOTE=capitalistpiglet]when i try and install i get this error, i used the ./configure --prefix=/usr as the guide says.[/QUOTE]
Did you install &#8220;kdevelop&#8221;?

---

### Post by tseliot on 2006-01-15
[QUOTE=Sokraates]Drats.

I get this error running make (or sudo make):

```
In file included from vistabar.h:19,
                              from kbfxvista.h:37,
                              from kbfxvista.cpp:1:
vistalistbox.h:11:27: error: listboxtile.xpm: No such file or directory
kbfxvista.cpp: In member function 'void kbfxvista::menuInit()':
kbfxvista.cpp:49: warning: format not a string literal and no format arguments
kbfxvista.cpp:52: warning: format not a string literal and no format arguments
kbfxvista.cpp: At global scope:
kbfxvista.cpp:203: warning: unused parameter 'height'
kbfxvista.cpp:213: warning: unused parameter 'width'
kbfxvista.cpp:256: warning: unused parameter 'o'
kbfxvista.cpp:405: warning: unused parameter 'x'
make[3]: *** [kbfxvista.lo] error 1
```[/QUOTE]
which file are you trying to compile?

---

### Post by Sokraates on 2006-01-15
[quote=tseliot]which file are you trying to compile?[/quote]

Huh???

I just followed your guide to the letter and this is the result when I run 

```
sudo make
```

FYI: I've added    xlibs-dev, libqt3-headers, kdelibs4-dev and libxaw6-dev. Only libqt3-mt-headers I can't install since it's not found in the repos. And yes, I've added universe, multiverse and what not.

---

### Post by tseliot on 2006-01-15
[QUOTE=Sokraates]Huh???

I just followed your guide to the letter and this is the result when I run 

```
sudo make
```

FYI: I've added    xlibs-dev, libqt3-headers, kdelibs4-dev and libxaw6-dev. Only libqt3-mt-headers I can't install since it's not found in the repos. And yes, I've added universe, multiverse and what not.[/QUOTE]
I don't use KDE in Ubuntu any more. Therefore I'm not sure I can help you.

Anyhow could you try to install other versions of "automake" (you can find them in Synaptic/Kynaptic or Adept)?

---

### Post by limit223 on 2006-01-15
Sokraates, 
I'm pretty sure that you had that error: missing listboxtile.xpm because you tried kbfxvista_beta tarball and that file is required from a previous version which should be installed. I had that problem too..and I switched to compile kbfx-0.4.8rc2.tar.bz2.

 I made a .deb file and I'll attache it here, if someone is interested to use it is welcome to download...

---

### Post by capitalistpiglet on 2006-01-15
[QUOTE=tseliot]Did you install &#8220;kdevelop&#8221;?[/QUOTE]
yes i installed kdevelop

---

### Post by Sokraates on 2006-01-17
[quote=limit223]Sokraates, 
I'm pretty sure that you had that error: missing listboxtile.xpm because you tried kbfxvista_beta tarball and that file is required from a previous version which should be installed. I had that problem too..and I switched to compile kbfx-0.4.8rc2.tar.bz2.

 I made a .deb file and I'll attache it here, if someone is interested to use it is welcome to download...[/quote]

Yep. That must be it. I'll try compiling another version sometime this week. 

@tseliot:
I've already got every automake-version available. Just in case. ;)

Should it turn out to be a problem with having to install kbfx-0.4.8rc2.tar.bz2 before trying kbfxvista_beta, you should point this out in the howto.

---

### Post by Sokraates on 2006-01-17
Compiled and installed kbfx-0.4.8rc2.tar.bz2 without problems. kbfxvista_beta_cvs.tar.bz2 still won't compile, so listbox.xpm is not included in kbfx-0.4.8rc2.tar.bz2. ;)

**Edit:** Hmmm ... maybe I did something wrong, but clicking on kbfx will just give me the normal k-menu. Any suggestions?

---

### Post by limit223 on 2006-01-17
Right-click panel-Add Applet to Panel - you'll find the kbfx in the list!

---

### Post by Sokraates on 2006-01-18
[quote=limit223]Right-click panel-Add Applet to Panel - you'll find the kbfx in the list![/quote]

I know. My problem occurrs _after_ adding kbfx (which in my case is called "kbfxvista") to the panel.

Left-clicking on the symbol will only give me another k-menu.

---

### Post by tseliot on 2006-01-18
[QUOTE=Sokraates]I know. My problem occurrs _after_ adding kbfx (which in my case is called "kbfxvista") to the panel.

Left-clicking on the symbol will only give me another k-menu.[/QUOTE]
It acts as a kmenu if you left click on it. If you right-click on it you will have its "peculiar" functions.

---

### Post by Elrond on 2006-01-19
[QUOTE=capitalistpiglet]when i try and install i get this error, i used the ./configure --prefix=/usr as the guide says.[/QUOTE]

I get the same error and I'd so much like to install kbfx. Is it possible that it doesn't work becaouse I use amd64?

---

### Post by Sokraates on 2006-01-19
Okay. Now I found out that in order to have the "new" menu you need to change the appearance of kbfx in kcontrol.

@tseliot: your how-to is very detailed so you should consider adding this piece of advice. There may be a few people who don't naturally consider configuring kbfx to be able to use the new menu.

Apart from that, is there an option to adjust the window of the menu itself (not the button)? The last icon is always halved.

---

### Post by jwfraser on 2006-01-19
I don't know what happened, but after uninstalling KBFX with synaptic, multiple files were removed, and my permissions were corrupted.  I can no longer log in with anything besides root.  Even when I log in as root, I cannot do much.  Ubuntu no longer logs anything, so I have no logs to look at, or use.  Many of the libraries are either now missing, or with incorrect permissions.

When I try logging in as something other than root, I get "Cannot cd to " followed by the home directory.

When I try su, I get a permission denied error.

Any ideas?  Or should I just give up and start over.

---

### Post by tseliot on 2006-01-20
[QUOTE=jwfraser]I don't know what happened, but after uninstalling KBFX with synaptic, multiple files were removed, and my permissions were corrupted.  I can no longer log in with anything besides root.  Even when I log in as root, I cannot do much.  Ubuntu no longer logs anything, so I have no logs to look at, or use.  Many of the libraries are either now missing, or with incorrect permissions.

When I try logging in as something other than root, I get "Cannot cd to " followed by the home directory.

When I try su, I get a permission denied error.

Any ideas?  Or should I just give up and start over.[/QUOTE]

It's weird. Anyhow you can create a new user after you access as root

---

### Post by jwfraser on 2006-01-20
No I can't, it gives me a permission denied error.  Even when I'm logged in as root.

---

### Post by tseliot on 2006-01-20
[QUOTE=jwfraser]No I can't, it gives me a permission denied error.  Even when I'm logged in as root.[/QUOTE]
try this when you are root:

apt-get install ubuntu-desktop

---

### Post by limit223 on 2006-01-21
[QUOTE=jwfraser]I don't know what happened, but after uninstalling KBFX with synaptic, multiple files were removed, and my permissions were corrupted.  I can no longer log in with anything besides root.  Even when I log in as root, I cannot do much.  Ubuntu no longer logs anything, so I have no logs to look at, or use.  Many of the libraries are either now missing, or with incorrect permissions.

When I try logging in as something other than root, I get "Cannot cd to " followed by the home directory.

When I try su, I get a permission denied error.

Any ideas?  Or should I just give up and start over.[/QUOTE]

It doesn't have anything with kbfx...
It happened something similar to me trying to recover my Dapper system, installing many files at once upgrade...and the filesystem went screwed up... But because I had my Breezy system in a different partition I managed to recover all...How? I have to tell you that this forum helped me a lot after some searches ( Greet this nice community again and again!)
What I did? 
1.go to my Breezy partion umount the Dapper partition and 
fsck.ext3 /dev/Dapperpartition 
said yes to repairs(had a lot of problems)

If you don't have another linux partition you may use Knoppix or whatever live cd.
2. mount again the partition and do chroot for Dapper.
3.reinstall the package with files affected by corruption.

You'll be surprize may be but I recover my Dapper system.

Corrupted data in linux boxes happens only in my SATA harddisk..I've read many complains about in other forums..things happen to other as well...Most of my systems are on PATA now except the one above. I went many times crazy losing my mind because of this new bleeding edge hdd tech.

PS. To be excuse some of offtopic details.

---

### Post by jwfraser on 2006-01-27
Thanks, I ended up giving up, and installing Dapper instead.  Surprisingly, I've had less problems with Dapper than I had with Breezy.

---

### Post by zeltak on 2006-01-30
Hi!

i am a complete newbee (first week!) in linux. i tried folowing the instructions but when i get to >sudo make i get this message:

make: *** No targets specified and no makefile found.  Stop.

and i cant continue from here...can anyone help?

thx alot

Zeltak

---

### Post by Sokraates on 2006-01-30
[quote=zeltak]Hi!

i am a complete newbee (first week!) in linux. i tried folowing the instructions but when i get to >sudo make i get this message:

make: *** No targets specified and no makefile found.  Stop.

and i cant continue from here...can anyone help?

thx alot

Zeltak[/quote] 
You can't continue like this. Make shure you follow the howto to the letter.
The step before "sudo make" is
```
./configure --prefix=/usr
``` executed from the directory where kbfx is extracted to. Please note, that the kbfx tarball already contains a kbfx-folder. So the path to the files will look something like [html]/home/youraccount/kbfx-version/kbfx-version[/html] 
After "./configure" run
```
sudo make
``` 
If it doesn't work, please post the output of ./configure --prefix=/usr.

---

### Post by rwabel on 2006-01-31
I've installed the deb file from this forum. I could add the applet. But when I go to kcontrol I cannot install any theme for it.

---

### Post by limit223 on 2006-01-31
They still work on this applet...not all functions are implemented though, a new released is done 4.8 (couldn't make it to work properly in KDE 3.5)

---

### Post by elgx on 2006-02-09
Hello.
I did everithing in the HowTo in my last distro, Breezy Badger, but checkinstall seem not to work properly on my system now. I changed CPU (intel celeron 2.0Gh --> amd athlon 64 3500+) and operating system (obiouvsly slightly! i only passed to Dapper Drake in beta testing).
The output at each time i do "sudo checkinstall" (with every kde package) is the following:
> elena@elena-ubuntu:~/Desktop/kbfx-0.4.8$ sudo checkinstall
Password:

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.

Copying documentation directory...
/var/tmp/DLiWFFaacIBhAYeTWaZH/installscript.sh: line 13: 24540 Segmentation fault      mkdir -p "/usr/share/doc/kbfx-0.4.8"

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

elena@elena-ubuntu:~/Desktop/kbfx-0.4.8$   
*make -f admin/Makefile.common && ./configure --prefix="/usr" && make* did not couse any error.
Does anyone know how to solve this? I'd really like to keep a repo of all that I install from source.. :(

---

### Post by tseliot on 2006-02-09
[QUOTE=elgx]Hello.
I did everithing in the HowTo in my last distro, Breezy Badger, but checkinstall seem not to work properly on my system now. I changed CPU (intel celeron 2.0Gh --> amd athlon 64 3500+) and operating system (obiouvsly slightly! i only passed to Dapper Drake in beta testing).
The output at each time i do "sudo checkinstall" (with every kde package) is the following:

*make -f admin/Makefile.common && ./configure --prefix="/usr" && make* did not couse any error.
Does anyone know how to solve this? I'd really like to keep a repo of all that I install from source.. :([/QUOTE]
I have the same problem on Dapper and I haven't found a solution yet :( .

---

### Post by Cool_dude_Prav on 2006-02-12
i get this error while trying to install...
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```
i did all the steps as the author of this HOWTO told me, but I cud not get to install the "checkinstall"

someone plz help me... 
Im on KUbuntu 5.10 using KDE 3.5

---

### Post by tseliot on 2006-02-13
[QUOTE=Cool_dude_Prav]i get this error while trying to install...
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```
i did all the steps as the author of this HOWTO told me, but I cud not get to install the "checkinstall"

someone plz help me... 
Im on KUbuntu 5.10 using KDE 3.5[/QUOTE]
Did you install kdevelop? I think it has a different name now, something like kdesdk. Anyhow if you try to install it by the command line (sudo apt-get install kdevelop) it won't be installed and apt will say that it has been replaced by that kdesdk thing. Install it and everything should work. I've tryed it in Dapper.

---

### Post by Cool_dude_Prav on 2006-02-13
hey, i just PM-ed hussam and he sent me a .deb file...

hence I cud install it without any problems...
probably because, kdesdk is already installed..

anyways its working fine ;)
thanks a ton man...

---

### Post by sirlancelot on 2006-02-23
This is the error I get ```
sudo make
Password:
cd . && aclocal-1.6
/bin/sh: aclocal-1.6: command not found
make: *** [aclocal.m4] Error 127

```After doing a tab-completion on 'aclocal' I discovered that I have 'aclocal-1.4' and not 1.6

How can I update this? I cannot find a package in the repositories to update to 1.6, or I am searching for the wrong package...

---

### Post by limit223 on 2006-02-23
I guess you are looking for the package named: **automake1.6** not aclocal-1.6* <-- are files content for this package.

Just an advice: don't install both version 1.4 and 1.6 (or lately 1.9), but just only one!

---

### Post by imbrandon on 2006-04-14
its in the dapper respo's now

enable the universe in sources.list and then .....
```

sudo apt-get update
sudo apt-get install kbfx

```

---

### Post by Patrik on 2006-04-28
When I typing in ./configure --prefix=/usr in my konsole/terminal Im getting this error:
> configure: error: cannot find sources (acinclude.m4) in . or ..

How to do? Please help me!

---

### Post by opticyclic on 2006-07-31
> **tseliot said:**
> Did you install kdevelop? I think it has a different name now, something like kdesdk. Anyhow if you try to install it by the command line (sudo apt-get install kdevelop) it won't be installed and apt will say that it has been replaced by that kdesdk thing. Install it and everything should work. I've tryed it in Dapper.

Since more people are now using Dapper you should probably change your original post.
Synaptic can say that kdevelop is installed but kdesdk-scripts wont be installed.

However, I found that I still got the **no KDE headers installed** error after installing kdesdk-scripts

What fixed it was installing the kdelibs-dev package.

---

### Post by floyd24 on 2006-09-06
Hi there,

just managed to get kbfx 0.4.9.2RC1 working under this config:

AMD Athlon64 3000+
(K)Ubuntu Dapper Drake v6.06 LTS
apt-get upgraded fully just before the build.

Here's my .deb File if it's of use to anyone. Feel free to share it wherever you like, it's not my code anyway ;-)

Cheerz, Floyd

---

### Post by Siniestro on 2007-02-22
I was able to successfully install KBFX but when I right click on my Panel and select:

Add applet to Panel...

in the new window popping up I do not see KBFX in the list of applets.

Please help :)

---

### Post by raffytaffy on 2007-03-12
ok i compiled my own and everything works. cool stuff

---

### Post by nsleiman on 2007-04-03
i changed a theme for kbfx and was surprised for losing the button! cant even re-load it. :( i tried re-installing but failed also :(

---

