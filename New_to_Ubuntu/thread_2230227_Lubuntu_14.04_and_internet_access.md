---
title: "Lubuntu 14.04 and internet access"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by Bewildered_Bob on 2014-06-18
14.04 was recently installed but after running Software Updater and rebooting, access to the Internet was lost for a l-o-n-g time. It is difficult (for me) to understand what is happening "behind the scene" since, unlike Windows, there is no visual indicator of activity after clicking on a button for example. Is there an equivalent for "task manager" which displays active "processes" to reveal what the machine is doing ?

Also there appear to be few choices avail to understand the interface with the internet (no wireless option appears even 'tho there is an adapter; Ethernet is not configurable). Is this the logical result from using a "skinnied-down" OS ? Thanx.

Bewildered Newbie

---

### Post by LastDino on 2014-06-18
Yes, there are quite a few equivalent for task managers. Like; ''system monitor'', I personally also like to have ''glances'' but its a command line tool. I don't have Lubuntu installed so I don't know if it is preinstalled or not, but if it is not, look for it in software manager.

Actually, that problem with Wi-fi is known bug, however, you can have it fixed if computer is able to connect to internet through other means.
Read this threads first few posts
[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by squakie on 2014-06-18
ps -e  shows running processes

top will show what processes are using the most resources

with lubuntu, just select Task Manager under the System option on the menus.

Is your wireless adapter built-in or is it a USB dongle?

For built-it:

lspci | grep Network

For USB:

lsusb

Post the results back here and we can go from there.

---

### Post by bapoumba on 2014-06-18
There is a current bug that is tagged fix released (have not tried the patch yet).
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348)

nm-applet does not autostart, you need to manually include it to Preferences > Default applications for LXSession > Autostart.

---

### Post by Bewildered_Bob on 2014-06-18
Hello Baoupmba: the thumbnail included shows "manual autostarted" apps - isn't that a contradiction of terms ??

Bewildered Newbie

---

### Post by LastDino on 2014-06-18
It means you need to manually set those applications to auto start with each bootup.

---

### Post by bapoumba on 2014-06-18
> **Bewildered_Bob said:**
> Hello Baoupmba: the thumbnail included shows "manual autostarted" apps - isn't that a contradiction of terms ??

Bewildered Newbie

Thanks LastDino :)
The apparent contradiction should be solved at some point.

---

### Post by Bewildered_Bob on 2014-06-18
Hi Squakie: what am i doing wrong ??  I clicked on "RUN" and entered each cmd  (ps -e & lspci | grep network) you provided but nothing happens.

still Bewildered Newbie

---

### Post by LastDino on 2014-06-18
Copy paste those in ''terminal'' and then copy paste the output here in ''code'' tags.

---

### Post by Bewildered_Bob on 2014-06-18
Hi LastDino - i really am a "newbie" to Linux/Ubuntu/Lubuntu. Will you provide specific instructions how to manually setup at each bootup ?  Thanx.

Bewildered

---

### Post by Bewildered_Bob on 2014-06-18
Hi LastDino - apparently "run" is NOT for cmds; they seem to work when entered in LXterminal instead.  Thanx.

Bewildered

---

### Post by LastDino on 2014-06-19
Run is for running programs (similar to windows) and some very specific commands, LXerminal is your ''command-line'' where you should put commands of any sort. If you've gotten any output, please copy paste it here.

---

### Post by bapoumba on 2014-06-19
Additional note : ctrl-c or v wont work in a terminal to copy/paste (ctrl-c means "end current command process"). Please use shfit-ctrl-c or v to copy from or paste into the terminal. Middle mouse click works too.

---

### Post by squakie on 2014-06-19
Or use a mouse, highlight, righ-click and copy, then paste to the reply.  Assuming that still works in Lubuntu.

---

### Post by GrouchyGaijin on 2014-06-19
@Bob

Are you able to connect via Ethernet?
Did you get the wi-fi problem sorted out?

I have a broadcom wifi card and the usual fix I use in Ubuntu didn't work with Lubuntu.  Lubuntu couldn't find the needed nonfree package so I downloaded it manually and installed it.  Then my wi-fi worked as it should.

---

### Post by giel2 on 2014-06-20
visual wifi indicator/configurator in lubuntu: run nm-applet from commandline

If this works you can autostart this nm-applet via:
start-button --> Preferences--> Default applications for LXsession --> autostart --> type nm-applet --> +Add

took me a while to find this, but it works for me.....

Regards, 
Giel

---

### Post by Bewildered_Bob on 2014-06-20
> **bapoumba said:**
> There is a current bug that is tagged fix released (have not tried the patch yet).
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348)

nm-applet does not autostart, you need to manually include it to Preferences > Default applications for LXSession > Autostart.
====================================================================================================
The change you suggested was made to "manually autostart" nm-applet but to my untrained eye the bootup is unchanged. Am i missing something ?  Thanx.
=====================================================================================================

---

### Post by bapoumba on 2014-06-20
@Bewildered_Bob : after including nm-applet to the Autostart tab, it should pick up at next logout/log back in, and of course at next reboot. Do you mean you still not see it in the panel after booting up ?

In addition, the fixed package is in trusty-proposed should anyone want to test it.
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348/comments/56](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348/comments/56)

---

### Post by Bewildered_Bob on 2014-06-20
> **GrouchyGaijin said:**
> @Bob

Are you able to connect via Ethernet?
Did you get the wi-fi problem sorted out?

=================================================
Yes and YES - several fixes were applied so that now the WiFi network is visible. Thanx for your help
==================================================

---

