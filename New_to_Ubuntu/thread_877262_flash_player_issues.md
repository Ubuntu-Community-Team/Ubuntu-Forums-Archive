---
title: "flash player issues"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Matt26 on 2008-08-01
has anyone had any difficulties with getting the new beta release of flash player 10 working in Firefox (or any other version of the flash player for that matter)?  every time i install the flash player plug-in and restart Firefox it will shut down unexpectedly- how long it takes for Firefox to shut down is always random- but it always shuts down..

i can't figure out how to get firefox to run safely with the flash player installed- can anyone help here?

thanks.

---

### Post by collinp on 2008-08-01
I had it running fine for a while, but suddenly it would crash firefox every single time it ran, so i switched back to 9.

---

### Post by dca on 2008-08-01
I only use the vers of flash that installs with the 'Ubuntu Restricted extras' meta package you get when you go into 'Add/Remove Software' at the bottom of Applications menu and select 'All available' from drop-down and type 'Ubuntu Restricted' in search bar.
 
I've always looked at attempting to run any other vers of Flash (direct from Adobe website) may lead to issues.

---

### Post by Thelasko on 2008-08-01
"Absolute Beginner Talk" isn't the place to discuss installing beta software.

---

### Post by silkstone on 2008-08-01
Taken from the following tutorial...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

-------

Installing Adobe Flash 10 beta

UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY

(Note: You can safely install the Ubuntu package (flashplugin-nonfree) over the top of this manual installation method at a later date, I've tested it several times. The method used below will install the plugin into the same directory the Ubuntu package does, with the same symlinks and can be overwritten cleanly.)

Install the Flash plugin manually by downloading the tar archive of Adobe Flash v10 beta. Simply open the tar archive, then find the file named "libflashplayer.so" and place it on your desktop. Next, execute this command in the terminal:

32-Bit Ubuntu Family Users Only:

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart Firefox and use the plugin.

------

However... some people are finding that the latest version (beta 2) causes some problems with Firefox closing unexpectedly. I am using beta 1 which I installed because I was having the same problem with Flash 9 from the repositories. Although Flash 10 beta 1 does not support transparency properly, it has never crashed or closed down on me.

I'm not sure where you can get beta 1 now, but I did see a post on these forums with a link. Try Googling!

---

### Post by Matt26 on 2008-08-06
> **silkstone said:**
> Taken from the following tutorial...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

-------

Installing Adobe Flash 10 beta

UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY

(Note: You can safely install the Ubuntu package (flashplugin-nonfree) over the top of this manual installation method at a later date, I've tested it several times. The method used below will install the plugin into the same directory the Ubuntu package does, with the same symlinks and can be overwritten cleanly.)

Install the Flash plugin manually by downloading the tar archive of Adobe Flash v10 beta. Simply open the tar archive, then find the file named "libflashplayer.so" and place it on your desktop. Next, execute this command in the terminal:

32-Bit Ubuntu Family Users Only:

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart Firefox and use the plugin.

------

However... some people are finding that the latest version (beta 2) causes some problems with Firefox closing unexpectedly. I am using beta 1 which I installed because I was having the same problem with Flash 9 from the repositories. Although Flash 10 beta 1 does not support transparency properly, it has never crashed or closed down on me.

I'm not sure where you can get beta 1 now, but I did see a post on these forums with a link. Try Googling!

thanks for the instructions, unfortunately after attempting this procedure with both the beta 1 and beta 2 release of flash player 10, firefox continues to crash.. is there anything else that i can try to get this working?  thanks.

---

