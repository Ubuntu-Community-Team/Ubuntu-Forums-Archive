---
title: "HOWTO: Make QT apps look more Gnome'ish"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-15
Originally written by [**FLeiXiuS**]("http://ubuntuforums.org/member.php?u=26")

Edited and rewritten By **arnieboy**

**Polymer QT Theme**

1.) You will need to install **qt3-qtconfig** in order to change the styles. 
```
sudo apt-get install qt3-qtconfig
```
2.) Now it's time to install the theme. download and install the following package:
```
wget http://www.informatik.tu-cottbus.de/~mkrause/debian/polymer/polymer_0.3.2-1_i386.deb
sudo dpkg -i polymer_0.3.2-1_i386.deb
```
3.) Lastly install msttcorefonts. (These are not required but it makes the style look SMOOTH!)
```
sudo apt-get install msttcorefonts
```
4.) Now that the files are installed lets get to the config!
```
qtconfig
```
5.) Lets change the font before hand to make it look even sweeter in the end. I decided to use Sans Serif 10pt. Make the following changes...
```
-Default Font-
Family: Sans Serif
Style: Normal
Point Size: 10

```

6.) Now click on the **Library Paths** tab. In the input-box at the bottom enter "**/usr/plugins**" (minus quotes) and then click **add**.

7.) Now in the **Appearance** tab, select **Polymer** as your **GUI** style.


8.) Go to **File**>**Save**. Exit the program and your almost done!


Another great benefit of this theme is that it has TRANSPARENCY!!
```
polymer-config
```
Down around the bottom you'll see "**KDE Style Settings**", change the "**Transparency Engine**" to "**Software Tint**" and then **close** the application. You will be prompted to **save**, click **yes** of course.

For other KDE applications, you'll need **kcontrol**.

1.) Install kcontrol
```
sudo apt-get install kcontrol
```
2.) Configuring the new theme.
```
kcontrol
```
3.) Click **Appearance and Themes**--->**Style** and select the "**Polymer**" theme. 
4.) Click **Appearance and Themes**-->**Fonts**-->**Adjust all fonts** and check the "**font**" box and change to** Sans Serif** and the "**size**" box to change the **size** to **10**
Apply and exit

Credits:
1) **Kassetra**
2) **GilGalad**

---

### Post by LaSSarD on 2005-10-15
Tested and approved :)

---

### Post by flibblesan on 2005-10-16
Excellent, works. But the howto needs to be cleaned up. You have duplicated steps and I can see that a novice could get to the first 5 steps wondering why the theme isn't showing up. Can you please give it a full clean up and remove anything that isn't required? :)

---

### Post by matthias_k on 2005-10-16
> Before / After Screenshots Below!
Where? ^^

---

### Post by arnieboy on 2005-10-16
[QUOTE=matthias_k]Where? ^^[/QUOTE]
no screenshots.. sorry. but this thing works (I have tested it myself). Its someone else's howto and I am just transferring it to the breezy forum cuz thats my job.

---

### Post by hanzj on 2005-10-18
[QUOTE=flibblesan]The howto needs to be cleaned up. You have duplicated steps and I can see that a novice could get to the first 5 steps wondering why the theme isn't showing up. Can you please give it a full clean up and remove anything that isn't required? :)[/QUOTE]

arnie, I read your reply to flibblesan, and I think a editing would be very helpful. I really don't think it should be left the way it is. It's confusing. It's hard to know that/what you're quoting, and thus hard to know where your howto starts and ends. I'm going back and forth between your post here and flexius's post, and I'm still trying to figure it out.

Reading for another time, I'm not sure of the reason why steps 1-5 were repeated.

I was wondering why you wanted to keep flexius's words. Perhaps you feel that you don't want to take undue credit, or perhaps you don't want to rip him off. And this would be very noble of you. Well, you could cite his article at the beginning, saying "This howto is based on [Flexius's howto for hoary]("http://ubuntuforums.org/showthread.php?t=56630")." You could give mention that this is someone else's post, but you don't have to leave things the way they are. If you really want to keep flexius's words, you could at least format the design to make it easy to see what's going on. 


yours...

---

### Post by traherom on 2005-10-18
Because he just copied the whole darned thing... he's trying to move things over which work in Breezy, not rewrite everything. Quit yelling at the man for making this easy for you to find.

---

### Post by arnieboy on 2005-10-18
[QUOTE=hanzj]arnie, I read your reply to flibblesan, and I think a editing would be very helpful. I really don't think it should be left the way it is. It's confusing. It's hard to know that/what you're quoting, and thus hard to know where your howto starts and ends. I'm going back and forth between your post here and flexius's post, and I'm still trying to figure it out.

Reading for another time, I'm not sure of the reason why steps 1-5 were repeated.

I was wondering why you wanted to keep flexius's words. Perhaps you feel that you don't want to take undue credit, or perhaps you don't want to rip him off. And this would be very noble of you. Well, you could cite his article at the beginning, saying "This howto is based on [Flexius's howto for hoary]("http://ubuntuforums.org/showthread.php?t=56630")." You could give mention that this is someone else's post, but you don't have to leave things the way they are. If you really want to keep flexius's words, you could at least format the design to make it easy to see what's going on. 


yours...[/QUOTE]
I am just doing my job here.. typically I dont like editing howto's of other people... but the kids are screaming too loud on this thread.. so I will rewrite the first post when I get time.

---

### Post by arnieboy on 2005-10-18
does the Howto look any neater now?

---

### Post by hanzj on 2005-10-18
[QUOTE=arnieboy]does the Howto look any neater now?[/QUOTE]
Arnie, it looks great! On behalf of all the ubuntu Gnome kids, thank you.

---

### Post by magic_T on 2005-10-22
Yep, this really makes Skype look good! Nice work!

---

### Post by pelago on 2005-10-24
This is great. (I used used [https://wiki.ubuntu.com/QtGnome](https://wiki.ubuntu.com/QtGnome) which is similar but also includes instructions to get the XLinSans font).

Anyone know whether there's a colour scheme for KDE to match the default Ubuntu brown theme?

---

### Post by flower on 2005-10-25
GREAT thanks !!!

I can't belive it ... I tought my skype will be ugly forever ...

thanks :) smells like geek spirit :)

---

### Post by abmcr on 2005-10-28
[QUOTE=pelago]I used used [https://wiki.ubuntu.com/QtGnome](https://wiki.ubuntu.com/QtGnome) which is similar but also includes instructions to get the XLinSans font.[/QUOTE]
But what is the line to add on the sources.list files? 

sarge (stable)->hoary:
etch (testing) / sid (unstable)->breezy:
:confused: 
Thank you

---

### Post by Wyld on 2005-10-28
So, any chance this (what I am assuming here is non-arch dependant issue) can become non-arch dependant?  I'm running AMD64 here, and can't install the i386 file.

---

### Post by bmk789 on 2005-10-30
Maybe I'm missing something, I followed the directions but it didn't apply to skype.  How do I get it to apply to skype?

---

### Post by ubnoobie on 2005-10-31
[QUOTE=arnieboy]does the Howto look any neater now?[/QUOTE]
it should warn folks of the 7 depends for kcontrol, though.

---

### Post by djpeanut on 2005-11-01
There's one change I would make based on my following of the HOWTO.  After adding "usr/plugins" in qtconfig, I had to choose File > Save before Polymer would show up in the drop-down menu.

Otherwise, great! Thanks!

---

### Post by donar73 on 2005-11-01
Great HowTo, thx alot! :) 
Amarok looks fantastic now!

[[IMG]http://img498.imageshack.us/img498/3420/bildschirmfoto13yj.th.png[/IMG]](http://img498.imageshack.us/my.php?image=bildschirmfoto13yj.png)

---

### Post by Sionide on 2005-11-01
That is brilliant. Props to all those involved. Thanks alot!!

---

### Post by byoon on 2005-11-02
Every time I try to run kcontrol, my system locks up.

I can still move the mouse around, but I cannot change window focus, I cannot do anything with the keyboard (not ctl-alt-bckspc or anything else), the clock doesn't even increment.

I am running the regular desktop with no kubuntu packages installed except the ones for kcontrol and qt-config.  The qt-config modifications work fine.

Anybody have any ideas?

---

### Post by arnieboy on 2005-11-02
[QUOTE=byoon]Every time I try to run kcontrol, my system locks up.

I can still move the mouse around, but I cannot change window focus, I cannot do anything with the keyboard (not ctl-alt-bckspc or anything else), the clock doesn't even increment.

I am running the regular desktop with no kubuntu packages installed except the ones for kcontrol and qt-config.  The qt-config modifications work fine.

Anybody have any ideas?[/QUOTE]
try doing the following:
```
rm -rf $HOME/.kde
```
and try starting kcontrol again.

---

### Post by byoon on 2005-11-02
I tried this already.  I deleted .kde & .qt and tried to restart but it still hangs.

I even tried to run using "sudo kcontrol" and it still hangs.

Any other ideas?


[QUOTE=arnieboy]try doing the following:
```
rm -rf $HOME/.kde
```
and try starting kcontrol again.[/QUOTE]

---

### Post by veloct on 2005-11-02
[QUOTE=arnieboy]Written by [**FLeiXiuS**]("http://ubuntuforums.org/member.php?u=26")

Edited By **arnieboy**

**Polymer QT Theme**
This sorta looks exactly like gnomes clearlooks.
1.) You will need to install **qt3-qtconfig** in order to change the styles. 
```
sudo apt-get install qt3-qtconfig
```
2.) Now it's time to install the theme. download the install the following package:
```
wget http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb
sudo dpkg -i polymer-0.3.2_0.3.2-1_i386.deb
```
3.) Lastly install msttcorefonts. (These are not required but it makes the style look SMOOTH!)
```
sudo apt-get install msttcorefonts
```
4.) Now that the files are installed lets get to the config!
```
qtconfig
```
5.) Lets change the font before hand to make it look even sweeter in the end. I decided to use Sans Serif 10pt. Make the following changes...
```
-Default Font-
Family: Sans Serif
Style: Normal
Point Size: 10

```

6.) Now click on the **Library Paths** tab. In the input-box at the bottom enter "**/usr/plugins**" (minus quotes) and then click **add**.

7.) Now in the **Appearance** tab, select **Polymer** as your **GUI** style.


8.) Go to **File**>**Save**. Exit the program and your almost done!


Another great benefit of this theme is that it has TRANSPARENCY!!
```
polymer-config
```
Down around the bottom you'll see "**KDE Style Settings**", change the "**Transparency Engine**" to "**Software Tint**" and then **close** the application. You will be prompted to **save**, click **yes** of course.

For other KDE applications, you'll need **kcontrol**.

1.) Install kcontrol
```
sudo apt-get install kcontrol
```
2.) Configuring the new theme.
```
kcontrol
```
3.) Click **Appearance and Themes**--->**Style** and select the "**Polymer**" theme. 
4.) Click **Appearance and Themes**-->**Fonts**-->**Adjust all fonts** and check the "**font**" box and change to** Sans Serif** and the size box to change the **size** to **10**
Apply and exit

Credits:
1) **Kassetra**
2) **GilGalad**[/QUOTE]

Worked flawlesly.  Thanks for the effort on the rewrite.

---

### Post by lonetree on 2005-11-10
I still have problem doing this

---

### Post by ThomThom on 2005-11-12
Nice howto. I was horrified of how Skype looked like. In Windows and OSX it looks very nice.

However, I had to restart qtconfig between point 6 and 7 to get the polymer theme to appear.

Is there any way to enable font smoothing as well? (I couldn't see any settings)

And what was this kcontrol? Did I just install KDE there?

---

### Post by ThomThom on 2005-11-12
Ignore the question about anti-aliasing. The kcontrol font section fixed that.

---

### Post by arnieboy on 2005-11-12
[QUOTE=ThomThom]Nice howto. I was horrified of how Skype looked like. In Windows and OSX it looks very nice.

However, I had to restart qtconfig between point 6 and 7 to get the polymer theme to appear.

Is there any way to enable font smoothing as well? (I couldn't see any settings)

And what was this kcontrol? Did I just install KDE there?[/QUOTE]
kcontrol is the control panel for kde. it contains almost all settings for the kde desktop. yes, when u install kcontrol, u install lots of kde libs and packages.

---

### Post by lonetree on 2005-11-14
Has anyone got polymer work on 5.04? I managed to install qtconfig and fonts did change to the type i want, but the polymer option in Appearance did not show up. When I did a polymer-config, it throws an error:

 #polymer-config
polymer-config: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory


Btw, has anyone has got Skype successfully installed on 5.10 via apt-get? If yes, can someone guide me on this? Or what is the repository for this. Thanks a lot.

regards,

---

### Post by arnieboy on 2005-11-14
[QUOTE=lonetree]Has anyone got polymer work on 5.04? I managed to install qtconfig and fonts did change to the type i want, but the polymer option in Appearance did not show up. When I did a polymer-config, it throws an error:

 #polymer-config
polymer-config: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory


Btw, has anyone has got Skype successfully installed on 5.10 via apt-get? If yes, can someone guide me on this? Or what is the repository for this. Thanks a lot.

regards,[/QUOTE]
for using this howto on 5.04 refer to the following:
[http://ubuntuforums.org/showthread.php?t=56630&highlight=HOWTO%3A+Make+QT+apps](http://ubuntuforums.org/showthread.php?t=56630&highlight=HOWTO%3A+Make+QT+apps)
for installing skype on 5.10 use [automatix]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by lonetree on 2005-11-14
[QUOTE=arnieboy]for using this howto on 5.04 refer to the following:
[http://ubuntuforums.org/showthread.php?t=56630&highlight=HOWTO%3A+Make+QT+apps](http://ubuntuforums.org/showthread.php?t=56630&highlight=HOWTO%3A+Make+QT+apps)
for installing skype on 5.10 use [automatix]("http://ubuntuforums.org/showthread.php?t=66563")[/QUOTE]


Thanks a zillion :-)

---

### Post by Rob2687 on 2005-11-19
I had to use sudo kcontrol and sudo qtconfig to get the settings to save and to get Polymer to show up.

---

### Post by tanari on 2005-12-18
Why do you use polymer? Try **[Klearlook]("http://www.kde-look.org/content/show.php?content=31717")** theme!

Check my screenshot:

---

### Post by JoshHendo on 2006-01-17
Ok. Below is what my skype looked like before (no, that isn't my skype, though it is what it looked like):
[IMG]http://neojp.aquitperu.com/personal/data/phoo/2005_10_25/skype1.png[/IMG]

Below is what my skype looks like now (yes, and this time it is my skype :P) :)
[IMG]http://uploadgo.com/files/skype.png[/IMG]

Thanks allot :D

---

### Post by ember on 2006-01-17
[QUOTE=tanari]Why do you use polymer? Try **[Klearlook]("http://www.kde-look.org/content/show.php?content=31717")** theme!

Check my screenshot:[/QUOTE]

Ah, great to know - that's exactly what I was looking for.

---

### Post by el_Salmon on 2006-01-19
**arnieboy**, qt-config must be reboot then you add "polymer" library path. Moreover, you should write a Klearlooks in the HOWTO.

By the way, thank you very much. My desktop is cool now !

---

### Post by george_apan on 2006-01-24
Here is a KDE icon theme with the default ubuntu icons:
[http://kde-look.org/content/show.php?content=27788&vote=good&tan=42362229&PHPSESSID=1a0306d035baedbc80d11b109f3fb682](http://kde-look.org/content/show.php?content=27788&vote=good&tan=42362229&PHPSESSID=1a0306d035baedbc80d11b109f3fb682)

Run kcontrol, go to Index/Appearance and Themes/Icons and push the "Install new theme" button. Select the .tar.bz2 file you downloaded and you've got gnome icons in KDE apps.

And here you can find a KDE color scheme that matches the ubuntu default:
[http://kde-look.org/content/show.php?content=29333&vote=good&tan=96842971&PHPSESSID=1a0306d035baedbc80d11b109f3fb682](http://kde-look.org/content/show.php?content=29333&vote=good&tan=96842971&PHPSESSID=1a0306d035baedbc80d11b109f3fb682)

Again, run kcontrol, go to Index/Apperance and Themes/Colors and push the "Import scheme" button. Select the .kcsrc file you downloaded and you've got a matching color scheme in all KDE apps.

I just love the way my K3b looks right now... Thanks for the howto arnieboy! :)

---

### Post by ashrack on 2006-01-26
a guide called from heaven themself ;)

---

### Post by stalefries on 2006-01-26
By the way everyone, Skype has official repositories: [http://forum.skype.com/viewtopic.php?t=29679]("http://forum.skype.com/viewtopic.php?t=29679")

Add that line the guy has to your /etc/apt/sources.list and you will get the official Skype .deb's. W00t!

---

### Post by stalefries on 2006-02-03
Anyone got directions on how to get Klearlook? I can't find a .deb anywhere. I'll try compiling from source, and doing a checkinstall.

---

### Post by stalefries on 2006-02-03
[quote=stalefries]Anyone got directions on how to get Klearlook? I can't find a .deb anywhere. I'll try compiling from source, and doing a checkinstall.[/quote]

Uh-oh. I think it wants KDE installed. I don't have the time or the hard drive space to do that.

---

### Post by tlaloczint on 2006-02-09
I cant make it to install what I am doing wrong ?


tlaloczint@aztlan:~$  wget [http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb](http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb)
--18:55:54--  [http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb](http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb)           => `polymer-0.3.2_0.3.2-1_i386.deb.1'
Resolving fleixius.com... 82.165.128.85
Connecting to fleixius.com|82.165.128.85|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 483           --.--K/s

18:55:54 (30.71 MB/s) - `polymer-0.3.2_0.3.2-1_i386.deb.1' saved [483]

tlaloczint@aztlan:~$ sudo dpkg -i polymer-0.3.2_0.3.2-1_i386.deb dpkg-deb: `polymer-0.3.2_0.3.2-1_i386.deb' is not a debian format archive
dpkg: error processing polymer-0.3.2_0.3.2-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 polymer-0.3.2_0.3.2-1_i386.deb
tlaloczint@aztlan:~$

---

### Post by Chris Tucker on 2006-02-10
you arent doing anything wrong.. i just tried to redo this after looseing the polymer deb file. 
Length: unspecified [text/html] caught my attention, i used a web browser, and a server setting is redirecting EVERYTHING on that page to a list of .. digg quotes?
anyway, not to arnieboy! update your link please!
i cant find the theme file anywhere on the net thus far (but that was only 1 google search ;P)

---

### Post by mp3guy on 2006-02-10
Works great, skype looks perfect now. That link in the HOWTO is broken, but you can download polymer here; [http://www.kde-look.org/content/download.php?content=21748&id=1](http://www.kde-look.org/content/download.php?content=21748&id=1) and build from source.

---

### Post by sup on 2006-02-12
the package can be downloaed from here [http://static.int.pl/~mig21/dev/releases/polymer/]("http://static.int.pl/~mig21/dev/releases/polymer/") - it is a cource code, but ./configure make checkinstall went flawlessly and really quickly (it was compiled in lesser time than it takes for rhythmbox to configure:-D)

---

### Post by arnieboy on 2006-02-12
can anyone verify if the following package works or not? if it does, i will update the first post.
```
wget http://www.informatik.tu-cottbus.de/~mkrause/debian/polymer/polymer_0.3.2-1_i386.deb
sudo dpkg -i polymer_0.3.2-1_i386.deb
```

please follow the rest of the instructions as is on the first post.

---

### Post by gtdj on 2006-02-13
[QUOTE=tlaloczint]I cant make it to install what I am doing wrong ?


tlaloczint@aztlan:~$  wget [http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb](http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb)
--18:55:54--  [http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb](http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb)           => `polymer-0.3.2_0.3.2-1_i386.deb.1'
Resolving fleixius.com... 82.165.128.85
Connecting to fleixius.com|82.165.128.85|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 483           --.--K/s

18:55:54 (30.71 MB/s) - `polymer-0.3.2_0.3.2-1_i386.deb.1' saved [483]

tlaloczint@aztlan:~$ sudo dpkg -i polymer-0.3.2_0.3.2-1_i386.deb dpkg-deb: `polymer-0.3.2_0.3.2-1_i386.deb' is not a debian format archive
dpkg: error processing polymer-0.3.2_0.3.2-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 polymer-0.3.2_0.3.2-1_i386.deb
tlaloczint@aztlan:~$[/QUOTE]

try
```

wget http://www.informatik.tu-cottbus.de/~mkrause/debian/polymer/polymer_0.3.2-1_i386.deb
sudo dpkg -i polymer_0.3.2-1_i386.deb

```

---

### Post by tlaloczint on 2006-02-13
Code:

wget [http://www.informatik.tu-cottbus.de/~mkrause/debian/polymer/polymer_0.3.2-1_i386.deb](http://www.informatik.tu-cottbus.de/~mkrause/debian/polymer/polymer_0.3.2-1_i386.deb) sudo dpkg -i polymer_0.3.2-1_i386.deb




yep! that worked without a glich. 

thanks

---

### Post by ghanthar on 2006-02-14
This is great thanks!!

---

### Post by Leppiz on 2006-02-22
[QUOTE=Wyld]So, any chance this (what I am assuming here is non-arch dependant issue) can become non-arch dependant?  I'm running AMD64 here, and can't install the i386 file.[/QUOTE]

I managed to install the theme for AMD64 using following procedure:
1. install qtconfig as said on the original post
2. get the source from [http://www.informatik.tu-cottbus.de/~mkrause/debian/polymer/polymer_0.3.2.orig.tar.gz](http://www.informatik.tu-cottbus.de/~mkrause/debian/polymer/polymer_0.3.2.orig.tar.gz)
3. get the depedencies needed for building it
4. build and install the package:
```
./configure
make
make install
```
5. install the i386 over the built one(I don't know why this is needed):
```
sudo dpkg -i --force-architecture polymer_0.3.2-1_i386.deb
```

6. continue from the first post's step 3.

---

### Post by roniez on 2006-02-25
awww SWEET! skype and amrok looks teh sexy now.

---

### Post by dunnerz on 2006-02-28
Brilliant

worked fine (the first page) for me

Skype looks good now

As does Quanta


Cheers! \\:D/

---

### Post by wvelez on 2006-02-28
Great job!!!  Excellent instructions.

:-)

---

### Post by oopsz on 2006-03-12
AMD64 users.. I've compiled a native AMD64 polymer deb here:
[http://www.plur.ca/ubuntu/](http://www.plur.ca/ubuntu/)

(If you're using skype in a chroot, you're going to want to install the i386 version in your chroot, as well)

---

### Post by escape on 2006-03-14
Fantastic. Lyx-qt looks accpetable now with the rest of my gnome theming.

---

### Post by blackrim on 2006-03-18
just wanted to say that it looks great with xubuntu (xfce4) too. thanks

---

### Post by sailor420 on 2006-03-19
Should this work in Dapper?

---

### Post by Chris Tucker on 2006-04-05
i still wish they would release an up-to-date version of skype for linux... even without video would be nice to have the new features

---

### Post by hyperair on 2007-05-20
*grumbles* I prefer Gnome and all, but couldn't they have some kinda QT engine to make the apps follow the Gnome themes? I'm currently playing around with KDE, and I found that Gnome apps look pretty much at home in that desktop environment. Wish it were the same the other way round.

---

