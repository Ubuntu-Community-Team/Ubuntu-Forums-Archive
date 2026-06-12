---
title: "HOWTO: Expocity similar to Apple task switch"
date: 2005-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by lizardking on 2005-06-17
I have found this deb package in the net to transform metacity simple task swithcer to a task switcher similar to Exposè di apple.
This is the software [EXPOCITY](http://www.pycage.de/software_expocity.html) .

I have found this debian package if some one would like to try it.
[Debian package for Expocity and download it](http://acm2.ustc.edu.cn/~roger/debian/) 

I have make backup copy on my server. You can find it under section **Expocity**
[www.iacopomasi.net/linux.php](http://www.iacopomasi.net/linux.php) 

I have installed the package by **dpkg**  beacuse apt-get doen't work.

You can use it with Alt+tab but you will loose the default switch  ](*,) 

**becaus of ubuntu have metacity 2.10 and this version is 2.6 if U want to mantein the pakage every time that U open synaptic you must set it on LOCK in Synaptic**
Click on it with right button and then Lock Package.If you want to elete unlock and remove..

This HOWTO is also present for **Warty**: [click here for Expocity howto warty](http://www.ubuntuforums.org/showthread.php?t=10991)

---

### Post by vtechstu on 2005-06-17
Wow, thats great, didn't even know linux had a similar mod for it.  I would like to try it out, but theres got to be another way to change which key(s) initiate the switch.  As i'm sure you know, in macs, you just press   F11 or something.  Any ideas anyone?

---

### Post by tread on 2005-06-17
Could you post a screenshot? I'd love to give it a go, but cannot for the next day and a half and I'm impatient and want to see a screenshot :)

All together now:
whadda we want?
screenshot!
when dwe want it?
now!

:)

---

### Post by André on 2005-06-17
Hi everybody,

if you are on KDE you can use Komposé which looks pretty good too and is in uninverse.

You can find a screenshot here: [http://kompose.berlios.de/](http://kompose.berlios.de/)

Greetings
André

---

### Post by lizardking on 2005-06-17
[QUOTE=tread]Could you post a screenshot? I'd love to give it a go, but cannot for the next day and a half and I'm impatient and want to see a screenshot :)

All together now:
whadda we want?
screenshot!
when dwe want it?
now!

:)[/QUOTE]
[SIZE=6]**Here U are** [/SIZE]   ;-) 

[[IMG]http://img278.echo.cx/img278/7493/expocity2tl.th.jpg[/IMG]](http://img278.echo.cx/my.php?image=expocity2tl.jpg)

---

### Post by lizardking on 2005-06-17
[QUOTE=André]Hi everybody,

if you are on KDE you can use Komposé which looks pretty good too and is in uninverse.

You can find a screenshot here: [http://kompose.berlios.de/](http://kompose.berlios.de/)

Greetings
André[/QUOTE]
I thnk expocity is better than Kompose but also it is a good program...

---

### Post by lizardking on 2005-06-17
[QUOTE=vtechstu]Wow, thats great, didn't even know linux had a similar mod for it.  I would like to try it out, but theres got to be another way to change which key(s) initiate the switch.  As i'm sure you know, in macs, you just press   F11 or something.  Any ideas anyone?[/QUOTE]
I don't know if it's possible.
You can try to view in gconf editor **[Gnome RegEdit better cleaner simpler that windows]** if there is a section called expocity after install to change shortcut...

---

### Post by bored2k on 2005-06-17
How is the performance using Expocity ? I have used Kompose and it is a blessed application. 
Skippy is not bad, but the performance is MAD slow. -- 

Skippy -slow!- : [[IMG]http://img32.echo.cx/img32/7580/screenshot6yw.th.png[/IMG]](http://img32.echo.cx/my.php?image=screenshot6yw.png)

Kompose :D - [[IMG]http://img52.echo.cx/img52/6136/snapshot93sz.th.png[/IMG]](http://img52.echo.cx/my.php?image=snapshot93sz.png)

---

### Post by André on 2005-06-17
Hi lizardking,

i didn't try expocity but could you tell why it is better than komposé?

I am pretty satisfied with komposé and just would like to know.

Greetings
André

---

### Post by bored2k on 2005-06-17
[QUOTE=André]Hi lizardking,

i didn't try expocity but could you tell why it is better than komposé?

I am pretty satisfied with komposé and just would like to know.

Greetings
André[/QUOTE]
 I am no one to answer, but I would think Kompose is better. It is newer (Expocity is almost two years old) and runs perfect with metacity. To get expocity you would have to downgrade and use external DEBIAN native packages. Plus, Kompose's performance could be hardly outdone.

---

### Post by rimmer on 2005-06-17
[QUOTE=vtechstu]Wow, thats great, didn't even know linux had a similar mod for it.  I would like to try it out, but theres got to be another way to change which key(s) initiate the switch.  As i'm sure you know, in macs, you just press   F11 or something.  Any ideas anyone?[/QUOTE]
 To cure the hassel of alt-tab. You can change it in the Config Editor -- > apps --> metacity --> globalkey_bindings. The "switch_windows" was linked to alt-tab all I had to do was change that to what I wanted and that was it for me, now it runs with Scroll_Lock. It's a nice program however after I installed the rendering of my windows slowed down dramaticly, will kompose run in Gnome?

---

### Post by tread on 2005-06-17
Hmm .. I installed expocity .. compiled it from source .. and then nautilus wouldn't start .. got hung up about 2 icons into the startup progress bar. Lucky I installed it in /usr/local .. it was easy to uninstall. But any ideas on what went wrong? I am on breezy .. maybe thats the problem .. what with all the x changes even skippy has stopped working.

---

### Post by Wolki on 2005-06-17
[QUOTE=rimmer]will kompose run in Gnome?[/QUOTE]

I just tried it, it works. It's a little buggy though, it likes to display a little of the panels on some workspaces, closing windows in kompose will leave traces and other minor grapic errors. Nothing big though, it seems to be quite usable and useful. Doesn't even take a lot of cpu, but I had to disable xcompmgr's fading because that combination was really slow. Until a gnome version works well enough, kompose is fine.

here's a screenshot.

---

### Post by cybrid on 2005-06-20
Any ideas of how to tweak expocity for better performance, in my machine it runs pretty slow, and I think I have a good machine:

-PIV 3.06Ghz Hyperthreading
-512x2 DDR 400 in double channel
-ATI Radeon 9600XT 128Mb
-Maxtor 160Gb SATA
-LG 18'' TFT

I'm running Ubuntu Hoary.

Thanks in advance.

---

### Post by GameGod on 2005-06-22
Wow, Kompose is awesome!
Just got it through synaptic and it kicks ass, it's exactly what I wanted!

I used a Mac at work, and I got hooked on having the bottom right corner of my screen set as a hot-corner to launch expose... Kompose does that for me now in Linux, I'm extremely happy! :)

Thank you!

---

### Post by bored2k on 2005-06-22
[QUOTE=GameGod]Wow, Kompose is awesome!
Just got it through synaptic and it kicks ass, it's exactly what I wanted!

I used a Mac at work, and I got hooked on having the bottom right corner of my screen set as a hot-corner to launch expose... Kompose does that for me now in Linux, I'm extremely happy! :)

Thank you![/QUOTE]
 Are you guys using Kompose with GNOME ? :? How is that working out ? (performance, etc). I have only dared to try it out with KDE. (I know someone posted on that but I didn't quite understand)

---

### Post by cdk on 2005-06-22
yes has anyone tried it out on gnome.  i dont really want to install all the kde libs if i dont have too.  

cheers,

---

### Post by André on 2005-06-22
Mmmhhh...

i tried komposé on Gnome the other day.

It worked but not as good as in KDE. If i remember right it doesn't show the background (maybe you have to set it via the KDE control center??) and sometimes has some graphic errors.

But it works and maybe you can ask the programmer if it is possible to have a better gnome integration.

Greetings
André

---

### Post by Tyr_7BE on 2005-06-26
I'm using it on Gnome.  I don't know how to tell it to set the background.  It's just grey.  It's very unsexy.  However, it's functional whereas skippy was not.  And until there's an expose clone that gives me decent performance and 3d effects, I'll be sitting with kompose.

---

### Post by André on 2005-06-26
Hi Tyr_7BE,

i don't excactl know how komposé works and i cannot try it right now because i have no gnome installed (and don't want to install too many unnecessary libraries just for testing purposes).

My idea would be the following: Maybe komposé gets the wallpaper from the kde configuration. Than it would be enough to install the KDE control center (avaible as kcontrol via synaptic) and set the wallpaper for the KDE applications there (call kcontrol via command line -> Look&Feel -> Wallpaper [or something like... using a german system here]).

Maybe this works but comes without any warranty.

Greetings
André

---

### Post by brim4brim on 2005-07-11
This program a) does not work and b) stopped my nautillus browser application launcher icon from working.  If anyone knows how to get it to work please post up.

If anyone else has problems with their Nautillus icon simply remove it and create it again and it'll work.

---

### Post by Mr Frosti on 2005-07-26
I installed Kompose, and happily report that it is working fine. It is very functional, and very fast. 

I checked the KDE control center and changed the background, however this does not affect Kompose. I still have a grey background. This isn't really an eyesore, since I have a gray Gnome theme anyways. 

I recommend this to anyone who is curious.

---

### Post by szdavid on 2005-07-27
Hello,

it is quite nice but is it possible to use only the keybord to switch between different windows (like the previous version) ?
Right now, I am only able to see the windows and, after that, i have to use the mouse ; not very usefull...

Thx

---

### Post by angrykeyboarder on 2005-10-13
[quote=lizardking]I have found this deb package in the net to transform metacity simple task swithcer to a task switcher similar to Exposè di apple.
This is the software [EXPOCITY]("http://www.pycage.de/software_expocity.html") .

I have found this debian package if some one would like to try it.
[Debian package for Expocity and download it]("http://acm2.ustc.edu.cn/%7Eroger/debian/") 

I have make backup copy on my server. You can find it under section **Expocity**
[www.iacopomasi.net/linux.php]("http://www.iacopomasi.net/linux.php") 

I have installed the package by **dpkg**  beacuse apt-get doen't work.

You can use it with Alt+tab but you will loose the default switch  ](*,) 

**becaus of ubuntu have metacity 2.10 and this version is 2.6 if U want to mantein the pakage every time that U open synaptic you must set it on LOCK in Synaptic**
Click on it with right button and then Lock Package.If you want to elete unlock and remove..

This HOWTO is also present for **Warty**: [click here for Expocity howto warty]("http://www.ubuntuforums.org/showthread.php?t=10991")[/quote]

It appears that both download links are dead.

---

### Post by Alex^77 on 2006-03-06
I have tried Expocity and I have some problems with  Breezy, because Metacity Crash when i push Alt + Tab.

So, I have decided to UNINSTALL Expocity and now.. I have loose all ShortCut! So?? What can I do??

---

