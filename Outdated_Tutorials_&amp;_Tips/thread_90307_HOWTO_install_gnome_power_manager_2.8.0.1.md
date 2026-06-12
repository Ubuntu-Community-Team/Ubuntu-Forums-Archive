---
title: "HOWTO: install gnome power manager 2.8.0.1"
date: 2005-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by lizardking on 2005-11-14
I m frustated that my laptop is not controlled well by the power manager as in windows(tm) instead.
So I found the gnome power manager in the breezy repository..Unfortunatly it is a alpha release a 0.x.y. (don't remember exactly the number). But I remember the configuration is so small: you can edit nothing.
So If you wanto to get the fresh new gnome power manager you must:
[LIST]
[*]download the new package from dapper repo [here]("http://mirrors.dk.telia.net/ubuntu/pool/universe/g/gnome-power-manager/gnome-power-manager_0.2.8.1-1ubuntu1_i386.deb")
[*]install throught terminal typing
```
sudo dpkg -i gnome-power-manager_0.2.8.1-1ubuntu1_i386.deb
```
[*]The go to System --> Settings --> POWER SETTINGS :KS 
[/LIST] 
and you have new package with advanced configuration...

enjoy by lizardking
:cool:

---

### Post by Technoviking on 2005-11-14
Good one, I'm going to see if this would be a good backport candiate.

Mike

---

### Post by bierpullen on 2005-11-17
This is great !!!
Works !!!!  :) 


------------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.


[http://www.antarctica-rbak.nl/ubuntu/index.php](http://www.antarctica-rbak.nl/ubuntu/index.php)

---

### Post by lizardking on 2005-11-17
[QUOTE=bierpullen]This is great !!!
Works !!!!  :) 


------------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.


[http://rbak.demon.nl/ubuntu/index.php](http://rbak.demon.nl/ubuntu/index.php)[/QUOTE]
i'm happy too!:KS

---

### Post by varunus on 2005-11-17
The alpha version was working for me (Toshiba Satellite A45-S150) but this new one rocks!  It doesn't have to sit there taking up space in my system tray like the old one did (though I usually leave it there anyway). Thank you very much!

---

### Post by lizardking on 2005-11-17
for me work but on my fujiutzu siemens amilo m 1425 I can view the esimated remaning time.
Some one could help me?:confused:

---

### Post by varunus on 2005-11-17
I just noticed that too...sometimes it shows time remaining for me, sometimes not.  I'm guessing its just a bug, and will be fixed later...Maybe a bug report should be filed?

---

### Post by dabear on 2005-11-17
It looks good, but it's a shame that [none of the toshiba l10 series notebooks](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=laptop++l10&titlesearch=Titles) has a working battery monitor

---

### Post by geniium on 2005-11-17
Thanks for this great info. I was looking for something like that. Great!

---

### Post by eraclito on 2005-11-17
it seem to works well, but if "system power info" tells me:

"cpu frequency has not been integrated whit hal"

what about?

eraclito

---

### Post by evs on 2005-11-17
I just did this very thing this past weekend.  Only I went all out and recompiled the .deb for Breezy, as well as all rebuilding the packages for all the upgraded dependencies from Dapper - dbus, hal, hal-device-manager, libhal, libhal-storage, libxres, and libxres-dev.  But for some reason, clicking on suspend or hibernate in Gnome-Power-Manager does absolutely nothing.  Clicking on suspend or hibernate from the log out screen works though, except I still can't resume properly (but at least it will suspend or hibernate the machine)!  The updated power manager is definitely great though.

---

### Post by quietglow on 2005-11-18
Could someone post the command which allows the applet to control frequency governing?? I know its a super user command.

I had it running with and older version of the power manager and didn't make a note of how I did it.

---

### Post by quietglow on 2005-11-18
Nevermind! Ignore me please...:-)

---

### Post by quietglow on 2005-11-18
FWIW, on my laptop (see sig) this particular Power Manager breaks my laptop's "lid close=hibernate" in acpi. Even though I set it to hibernate in the GUI, it just dims the screen. I'll look at the scripts in /etc/acpi to see what's up later.

---

### Post by Pheonix on 2005-11-20
This is now on 0.3.0 according to the web page.  Anyone know how to get it installed on Ubuntu?  Its currently a Tarball, but I've not a clue what to do with one of those! I've only just got the hand of dpkg :D

---

### Post by manicka on 2005-11-20
I've added this how-to, to the Ubuntu Document Storage Facility

---

### Post by dmonney on 2005-11-21
I tried it I got this messege

"status database area is locked by another process"

---

### Post by Rob2687 on 2005-11-21
Close synaptic or whatever other package installer dealy you have running.

---

### Post by BathroomNinja on 2005-11-22
Nice!  This will be on the wife's laptop tonight!

---

### Post by thegnark on 2005-11-23
hm... no system --> settings


am i missing something here?

---

### Post by manicka on 2005-11-23
[QUOTE=thegnark]hm... no system --> settings


am i missing something here?[/QUOTE]

Probably either 

System --> Preferences --> POWER SETTINGS

or

System --> Adminstration --> POWER SETTINGS

---

### Post by timetunnel on 2005-11-23
It's in Breezy-backports now. 
However it works worse on my IBM R52 than the version that shipped with Breezy: lid close doesn't suspend to RAM anymore, just blanks the screen and shows the login. Suspend triggered from gnome-power-manager menu doesn't work as well. Everything else works (or doesn't work) as before. :-(

Jens

---

### Post by hughsient on 2005-11-27
I'm not sure it should have been backported. g-p-m 0.3.0 will only work properly with a new HAL, something of the 0.5.4 or 0.5.5 vintage as it uses HAL for all the power management callouts, rather than the (now obsolete) PowerManager init.d daemon.
Please open bugs in gnome-bugzilla if you are having problems with g-p-m and a recent HAL, and I'll do my best to solve them.

Richard Hughes, g-p-m maintainer.

---

### Post by ashrack on 2005-12-18
Which one should I use on my laptop?
Since the original link given in the first post is no longer valid

---

### Post by evs on 2005-12-18
[QUOTE=ashrack]Which one should I use on my laptop?
Since the original link given in the first post is no longer valid[/QUOTE]

Newest version is [0.3.1]("http://mirrors.dk.telia.net/ubuntu/pool/universe/g/gnome-power-manager/gnome-power-manager_0.3.1-0ubuntu2_i386.deb")

---

### Post by nehalem on 2005-12-18
[QUOTE=evs]Newest version is [0.3.1]("http://mirrors.dk.telia.net/ubuntu/pool/universe/g/gnome-power-manager/gnome-power-manager_0.3.1-0ubuntu2_i386.deb")[/QUOTE]


This version depends on a lot of newer libraries than breezy has.  Too bad..

---

### Post by ashrack on 2005-12-19
[QUOTE=nehalem]This version depends on a lot of newer libraries than breezy has.  Too bad..[/QUOTE]
So I can't use his version, correct?

ps. Which version coud I use than?

---

### Post by ashrack on 2005-12-20
*bump*

---

### Post by manicka on 2005-12-20
The 2.8 version linked at Post 1

---

### Post by ashrack on 2005-12-20
[QUOTE=manicka]The 2.8 version linked at Post 1[/QUOTE]
The link in POST 1 is no longer valid. That's way I was asking which one.
So could some1 repair the link in POST 1 with this one:
[http://mirrors.dk.telia.net/ubuntu/pool/universe/g/gnome-power-manager/gnome-power-manager_0.2.8.1-1ubuntu1~breezy1_i386.deb](http://mirrors.dk.telia.net/ubuntu/pool/universe/g/gnome-power-manager/gnome-power-manager_0.2.8.1-1ubuntu1~breezy1_i386.deb)

---

### Post by ashrack on 2005-12-20
Installed it and works almost 100%. But the problem is if I click the right mouse button on the icon and choose suspend or hibernate it does nothing except hangs the icon for 20s. 
ps.hibernation and suspend S3 are working perfectly if I choose them from "system>log out"

---

### Post by ashrack on 2005-12-24
How to add it would auto startup:
[http://www.gnome.org/projects/gnome-power-manager/faq.html#autostart](http://www.gnome.org/projects/gnome-power-manager/faq.html#autostart)

---

### Post by btermeli on 2009-06-06
Broken link, can someone give a new link??

---

