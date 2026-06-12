---
title: "HOW TO INSTALL OPERA 8.5 in Ubuntu 5.10"
date: 2005-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by pminetti on 2005-10-18
Well the credit not belongs to me, but I make little changes to make this works

It's the same to make works Skype! from there it's this code

code:
mkdir opera.tmp
mv opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb.orig

dpkg-deb &#8211;-extract opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb.orig opera.tmp
dpkg-deb --control opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb.orig opera.tmp/DEBIAN

vi opera.tmp/DEBIAN/control

Change to:
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)

dpkg &#8211;build opera.tmp
mv opera.tmp.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb

that's all

---

### Post by kperkins on 2005-10-18
Or just download the deb for breezy from the opera site to your home folder, open up a terminal and type in sudo dpkg -i opera.XXXXXXXXxxx.deb  enter your password and let 'er rip.
It really is just that simple. (or at least it was for me.)

---

### Post by sabre on 2005-10-19
I just download the etch one. And it works well on my breezy box!

---

### Post by mpettitt on 2005-10-19
Seems very complicated... Why not just download the Breezy one from the Opera.com page, and install with a simple dpkg? It works! Don't need to complicate matters!

---

### Post by pminetti on 2005-10-19
Ok if you want more easy add this lines to synaptic

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
or
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

but steel have the same problem with libqt3
for me the only way was download a static version or do what I write first

---

### Post by lupo on 2005-10-19
[QUOTE=mpettitt]Seems very complicated... Why not just download the Breezy one from the Opera.com page, and install with a simple dpkg? It works! Don't need to complicate matters![/QUOTE]
I've done that, but when I try to run Opera it crashes with an "Segmentation fault"... any ideas? 
The older version 8.04 worked well.

---

### Post by mpettitt on 2005-10-19
[QUOTE=pminetti]Ok if you want more easy add this lines to synaptic

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
or
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

[/QUOTE]

These are the pure Debian repositories, not the one that Ubuntu needs. You'd want 


deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

for the Ubuntu version.

---

### Post by virgule on 2005-10-19
Let me point out that Ubuntu .debs are not available for PowerPC CPUs (only x86?). Fortunatly, Other/Static DEB is working just fine I found.

---

### Post by sanguinemoon on 2005-10-19
[QUOTE=pminetti]Ok if you want more easy add this lines to synaptic

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
or
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

but steel have the same problem with libqt3
for me the only way was download a static version or do what I write first[/QUOTE]

Same problems I had. I'm using Gnome right now, but there are seemingly unresolvable dependecy issues stemming from having Konqueror and a few other KDE apps. I think it /would/ work if I got rid of all KDE stuff :/

---

### Post by Nomearod on 2005-10-20
To install Opera:


> $ sudo aptitude install libqt3c102-mt

Then, download Opera from [this]("http://www.opera.com/") site. ( It has a package for Ubuntu ).

After:

> sudo dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb

( if the name of the package is diferente, you must put that name instead of this,

Then:

Open the Menu Editor ( applications -> System ( something like this ) and put this:( in the Internet part )

 Name: Opera
Command: /usr/bin/opera
Icon: /usr/share/opera/images/opera.xpm
Category: Internet

[Source]("http://www.guia-ubuntu.org/breezy/doku.php?id=aplicaciones:internet")

I installed Opera a few hours ago, and it worked. ;)

---

### Post by kittcankitt on 2005-10-21
[QUOTE=lupo]I've done that, but when I try to run Opera it crashes with an "Segmentation fault"... any ideas? 
The older version 8.04 worked well.[/QUOTE]

I posted a similar question about the segmentation fault but I haven't figured out the problem yet...anyone else have the same problem/solution?
:confused:

---

### Post by Nomearod on 2005-10-21
[QUOTE=kittcankitt]I posted a similar question about the segmentation fault but I haven't figured out the problem yet...anyone else have the same problem/solution?
:confused:[/QUOTE]

Did you installed libqt3c102-mt ?

I don't know if this is important, but maybe could help...

> sudo aptitude install libqt3c102-mt

---

### Post by Xian on 2005-10-22
You need to install the [libqt3c102-mt]("http://archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.3-7ubuntu3_i386.deb") package. 
This is not possible if you are using a KDE desktop or applications.

Also install the Breezy [lesstif2](http://archive.ubuntu.com/ubuntu/pool/universe/l/lesstif1-1/lesstif2_0.93.94-11.4ubuntu3_i386.deb) package.

You can still use KDE and Opera by installing the [Opera-static_8.50]("ftp://opera.nsc.no/pub/nsc.no/mirrors/operasoftware/linux//850/final/en/i386/static/opera-static_8.50-20050916.1-qt_en_i386.deb") version.

---

### Post by moerl on 2005-10-23
Here's what I get:

ismar@ISMARubuntu:~$ sudo dpkg -i /home/ismar/Downloads/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
(Reading database ... 58864 files and directories currently installed.)
Preparing to replace opera 8.50-20050916.6 (using .../opera_8.50-20050916.6-shared-qt_en_etch_i386.deb) ...
Unpacking replacement opera ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera"

I just installed the linux-686 kernel. Is that a problem? The next logical step was to look for the missing packages in Synaptic, so I did.

I found "xlibs", the other one I couldn't find using Synaptic. Here's the comment for xlibs:

"X Window System client library transitional package
This package smooths upgrades from Ubuntu 5.04 ('Hoary') to Ubuntu 5.10
('Breezy') by ensuring the smooth removal of all XKB configuration files that
were formerly in the 'xlibs' package.  If you are running Breezy already, you
may safely remove this package."

Notice the last sentence... I'm rather confused now.

EDIT:
Forgot to say.. when I start Synaptic now, it alerts me that I have one broken package on the system... and that's Opera.

---

### Post by moerl on 2005-10-23
K.. I checked update manager and oddly, XLIBS was in there. I updated and after that, installed Opera using the same method without any problems! Now I'm just wondering.. how the hell do I start Opera?

I'll go try to find that out.

---

### Post by darrenrxm on 2005-10-24
I can not get opera to install either. Im going to try the static version and see if that works.

---

### Post by moerl on 2005-10-24
The static version is the one that's supposed to work.. however, I don't even know what the static version is, how it differs from the "normal" one and/or where to get it.

If that doesn't work for you, here's a sure fire way to get it to install and work: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

It's a beautiful app to have regardless of the Opera installation problem, but this will correctly install Opera for you!

---

### Post by darrenrxm on 2005-10-25
Opera is now working for me. Thankyou everyone for your advice. Now all I have to do is get the plugins to work.

---

### Post by missmoondog on 2005-11-05
Open the Menu Editor ( applications -> System ( something like this ) and put this in the Internet part )

Name: Opera
Command: /usr/bin/opera
Icon: /usr/share/opera/images/opera.xpm
Category: Internet

i'm not grasping how to do this part of the Opera installation.

HELP!!

Edit:
Don't know what I did, but I now have the darn Opera icon in applications/internet just like it's supposed to be!! Now my Ubuntu is complete. Opera flat out rulez whether on Linux or Windows!! Can't live without it!!

---

### Post by missmoondog on 2005-11-05
[QUOTE=Nomearod]To install Opera:




Then, download Opera from [this]("http://www.opera.com/") site. ( It has a package for Ubuntu ).

After:



( if the name of the package is diferente, you must put that name instead of this,

Then:

Open the Menu Editor ( applications -> System ( something like this ) and put this:( in the Internet part )

 Name: Opera
Command: /usr/bin/opera
Icon: /usr/share/opera/images/opera.xpm
Category: Internet

[Source]("http://www.guia-ubuntu.org/breezy/doku.php?id=aplicaciones:internet")

I installed Opera a few hours ago, and it worked. ;)[/QUOTE]



Ah, finally!! Between this post and another post on this forum, I now have Opera installed and the icon where it belongs!! Can't live without my Opera. Easily the best/fastest/securest browser there is!!

Thank you!!

---

### Post by missmoondog on 2005-11-10
like i said in previous post, don't know what i did to get opera installed on 1 machine, but can't for the life of me get it installed correctly on my other 2. been working on these 2 machines since i  posted about my success on the first machine.

---

### Post by kevcart3 on 2005-11-10
^^ It's your loss....

But if you would have asked nicely, someone could have told you that you can simply use smeg (menu editor) to add an entry to the Applications menu for Opera.

---

### Post by missmoondog on 2005-11-10
i'm going to retract what i said above. i can't let this thing kick my butt. ;)
i have to admit, i like this ubuntu.

i tried what you suggested just before i posted that though. this is what i get from that.

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package smeg

can't find that anywhere in synaptic or update manager either.

---

### Post by cowlip on 2005-11-11
Hi I'm not sure, what happens with sudo apt-cache search smeg ?

What about right clicking "applications" on the menu bar (or the gnome icon) and choosing Edit Menus?

---

### Post by Zunflappie on 2005-11-23
[QUOTE=Nomearod, page 1, 10st post]To install Opera:

Then, download Opera from [this]("http://www.opera.com/") site. ( It has a package for Ubuntu ).

After:

( if the name of the package is diferente, you must put that name instead of this,

Then:

Open the Menu Editor ( applications -> System ( something like this ) and put this:( in the Internet part )

 Name: Opera
Command: /usr/bin/opera
Icon: /usr/share/opera/images/opera.xpm
Category: Internet

[Source]("http://www.guia-ubuntu.org/breezy/doku.php?id=aplicaciones:internet")

I installed Opera a few hours ago, and it worked. ;)[/QUOTE]

I have downloaded **opera_8.51-20051114.6-shared-qt_en_etch_i386.deb** from [www.opera.com](www.opera.com)
I have done (in console) *sudo aptitude install libqt3c102-mt*
I have done [i]sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
[/i]
Then, I get a error in the console:
[i]
eddy@eddy:~$ sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
dpkg: fout bij afhandelen van opera_8.51-20051114.6-shared-qt_en_etch_i386.deb (--install):
 kon archief niet benaderen: Onbekend bestand of map
Fouten gevonden tijdens behandelen van:
 opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
eddy@eddy:~$
[/i]

Oke.. thats Dutch. It says that it cant reach the archive > " file is unknown.
There are errors while handling opera_8.51-xxxxx.i386.deb" 

What now?
Waiting on Opera.com releases a good package?
I have tried do this same with version 8.01.

As OS i use Ubuntu 5.10 Breezy Badger

---

### Post by kperkins on 2005-11-23
[QUOTE=Zunflappie]I have downloaded **opera_8.51-20051114.6-shared-qt_en_etch_i386.deb** from [www.opera.com](www.opera.com)
I have done (in console) *sudo aptitude install libqt3c102-mt*
I have done [i]sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
[/i]
Then, I get a error in the console:
[i]
eddy@eddy:~$ sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
dpkg: fout bij afhandelen van opera_8.51-20051114.6-shared-qt_en_etch_i386.deb (--install):
 kon archief niet benaderen: Onbekend bestand of map
Fouten gevonden tijdens behandelen van:
 opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
eddy@eddy:~$
[/i]

Oke.. thats Dutch. It says that it cant reach the archive > " file is unknown.
There are errors while handling opera_8.51-xxxxx.i386.deb" 

What now?
Waiting on Opera.com releases a good package?
I have tried do this same with version 8.01.

As OS i use Ubuntu 5.10 Breezy Badger[/QUOTE]
According to the error message you are in your home folder--is that where you downloaded the opera .deb to?  Usually if dpkg (or any other program) can't find a file, then it's not in the path specified (and since you didn't specify anything except the file name, then dpkg is assuming that it's in the folder that you are in).

---

### Post by Zunflappie on 2005-11-24
Sounds good.
I am starting the console from my desktop.
And there is the deb-file.

But i will try it from my home-folder!

**EDIT**
I tried it.
And it works... for 50%.
The file is found now (THANKS!!!!)

But the next problem is walking in.
I wont post the code > its dutch.

But now the console says that Opera is depending on **xlib6g (>= 3.3.6) | xlibs**. But packet **xlib6g** en **xlibs** are not installed.
I started the Synaptic-packet-manager. Searched for those packets. But cant find anything like that.
So, how to continue?

**EDIT 2 **
Installed xlibs as packet.
Opera reinstalled... and now NO ERRORS!
I may say Hoera!
Next... where can i start Opera?

**EDIT 3! **
I have readed the complete topic and found the solution (page 1).
Opera WORKS!!!!!
Now, just setting up the program to get loss of Firefox (Opera is, in my opion, better).

Thanks all!!!!

---

### Post by kperkins on 2005-11-24
hoorah!

---

### Post by madjinx on 2005-11-24
just to let you guys know, alot of trouble i had with Opera 8.5 was solved with Opera 9 beta.

---

### Post by o_bEnFiQuIsTa on 2005-11-25
Edited: Forget this post

---

### Post by jockjunior on 2005-12-03
libqt3c102-mt
tried to install opera 8.51 but when I tried to install the library I got error saying no candidate??  for it 

what do I do next?

thanks

Jock

---

### Post by Unicast on 2005-12-08
I installed Opera 8.51 in Breezy using the apt-get instructions in the [Ubuntu Wiki](https://wiki.ubuntu.com/OperaBrowser?highlight=%28opera%29#head-d3fc157abca89472846ed502ebbc26de36d616d1)

---

### Post by greywolf73 on 2005-12-10
[QUOTE=kittcankitt]I posted a similar question about the segmentation fault but I haven't figured out the problem yet...anyone else have the same problem/solution?
:confused:[/QUOTE]

Here is the solution to your problem:
[https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera]("https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera")

Scroll down and go to section titled Opera Segmentation Fault and Java crash with static version problem.  Don't worry that it is saying static version it works!:)

---

### Post by telemetric_au on 2006-03-10
[QUOTE=pminetti]Well the credit not belongs to me, but I make little changes to make this works

It's the same to make works Skype! from there it's this code

code:
mkdir opera.tmp
mv opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb.orig

dpkg-deb &#8211;-extract opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb.orig opera.tmp
dpkg-deb --control opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb.orig opera.tmp/DEBIAN

vi opera.tmp/DEBIAN/control

Change to:
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)

dpkg &#8211;build opera.tmp
mv opera.tmp.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb

that's all[/QUOTE]

used this guide exactly for:

opera_8.52-20060201.3-shared-qt_en_powerpc.deb

except instead of using "vi" to edit the dependencies file i use "gedit" :)

successfull upgraded my static version which i had been using due to not being able to install shared version:

"Package libqt3-mt is not installed."

but still getting:

[I]Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/netscape/plugins-libc6/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/netscape/plugins-libc6[/I]

On startup... maybe leftovers from the static version shich looked crappy and has adds !! well hushmail is working great now anyway...

and the small plugin prob ive seen mentioned on other forums while looking for fixs for my larger issue, so i guess ill go back through the history and dig it up :)

PS

am using IBM jave 1.4xxx SDK succesfully (better than 1.5 and blackdown)

and am getting to like oprea over firefox as is not as violent...

Goodluck

---

### Post by telemetric_au on 2006-03-10
[QUOTE=telemetric_au]used this guide exactly for:

opera_8.52-20060201.3-shared-qt_en_powerpc.deb

except instead of using "vi" to edit the dependencies file i use "gedit" :)

successfull upgraded my static version which i had been using due to not being able to install shared version:

"Package libqt3-mt is not installed."

but still getting:

[I]Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/netscape/plugins-libc6/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/netscape/plugins-libc6[/I]

On startup... maybe leftovers from the static version shich looked crappy and has adds !! well hushmail is working great now anyway...

and the small plugin prob ive seen mentioned on other forums while looking for fixs for my larger issue, so i guess ill go back through the history and dig it up :)

PS

am using IBM jave 1.4xxx SDK succesfully (better than 1.5 and blackdown)

and am getting to like oprea over firefox as is not as violent...

Goodluck[/QUOTE]



well got this:

Could not start plug-in executable 'operamotifwrapper'.

bit sorted very easily,

just grabbed the libmotif3 package from the debian repositories, installed it and no more issues  :-D

---

### Post by JuhazOne on 2006-06-04
If I understood the first message correctly, you should append " | libqt3" to libqt3c102-mt in opera.tmp/DEBIAN/control .

I wrote a small script to automate this. Obviously, you should save this to a file that's called something like fix-opera.sh, chmod u+x it and run it with an original opera .deb as an argument.

The regex is meant to take into account that there may or may not be something in parenthesis after the string libqt3c102-mt. Also, regex allows to you other character than / as the separator and I often use s#pattern#replacement#flags.

```
#!/bin/sh

if [[ $1 == '' ]]; then
        echo "I want to have an opera package as an argument. :(."
        exit
fi

mkdir opera-fixed \
&& dpkg-deb --extract $1 opera-fixed \
&& dpkg-deb --control $1 opera-fixed/DEBIAN \
&& sed -r -i 's#libqt3c102-mt([^,]*),#libqt3c102-mt\1 | libqt3-mt,#' opera-fixed/DEBIAN/control \
&& dpkg --build opera-fixed \
&& rm -rf opera-fixed/ \
&& echo "I'm done, now try dpkg --install opera-fixed.deb :)"
```

---

