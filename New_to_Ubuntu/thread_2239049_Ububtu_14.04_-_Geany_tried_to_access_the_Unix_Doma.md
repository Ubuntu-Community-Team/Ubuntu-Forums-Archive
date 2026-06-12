---
title: "Ububtu 14.04 - Geany tried to access the Unix Domain socket..."
date: 2014-08-11
forum: New to Ubuntu
---

### Post by tuxbonewits.com on 2014-08-11
Noob here! Fair warning.

clean install 2014-08-01 on;
HP Pavillion g7 - 2269wm
AMD Quad-Core A8-4500M Accelerated Processor
17.3" diagonal HD+ BrightView LED Display
500 GB HDD
6144MB DDR3 SDRAM
WLAN: Atheros
DVD Optical Drive
20140801 - Ubuntu 14.04 Unity

Multiple problems, the biggest being this error message when clicking on Geany icon in taskbar;
Geany tried to access the Unix Domain socket of 
another instance running as another user. 
This is a fatal error and Geany will now quit.

When going to Terminal and entering;
sudo killall geany - I get the following;
geany: no processes found.

Points to ponder;
This error started 4 days ago.
I uninstalled and purged geany
and tried to get along with gedit-no win

Reinstalled geany today and it worked fine until
I had to leave the laptop
when I came back an hour later the laptop
was in suspension.
I logged back in and began getting this error again.

I do NOT understand how I'm getting the error 
IF no geany processes are found.

Your assistance in this matter will be appriciated.

How can I have no process found and still be getting this error?
How to fix?

---

### Post by tuxbonewits.com on 2014-08-11
was able to open Geany by
opening terminal
sudo geany /etc/conky/conky.conf - the last file I had open before I started getting the error

when geany openned
I closed both of the insidents of conky.conf
(The one just openned & the previously opened version)

Lesson here; close the file in geany when started from the terminal

---

### Post by oldfred on 2014-08-11
Using sudo instead of gksudo or gksu can also cause funny issues.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tuxbonewits.com on 2014-12-14
Hope this update helps someone else.

This happened again today and I now believe I know why.
I had re-named my computer. When Geany started it created 
a shortcut in it's config directory at ~/.config/geany/
I then had two of the shortcuts. One for each name my computer had.
I deleted both and when Geany started, it re-wrote it's config file and now works as expected.

Oh, and 
 	[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]  					 					 						Forums Moderator 					; thanks for the tips on sudo & UEFI !

[COLOR=darkgreen]HP Pavillion g7 - 2269wm
AMD Quad-Core A8-4500M Accelerated Processor
17.3" diagonal HD+ BrightView LED Display
Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G]
Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
500 GB HDD
DVD A DS8A9SH
6144MB DDR3 SDRAM
DVD Optical Drive
20140730-22:58 - Ubuntu 14.04.1 LTS Trusty Tahr OS[/COLOR]

---

