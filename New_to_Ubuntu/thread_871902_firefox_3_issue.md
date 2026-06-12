---
title: "firefox 3 issue"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by bmann11 on 2008-07-27
Firefox 3 has one bug that it is a pain, though not terrible.  On some sites, the drop down menus appear underneath content that they are supposed to be on top of.  Has anyone else encountered this problem and is there a way to fix it?  I'm running Hardy and FF 3.0

---

### Post by gjoellee on 2008-07-27
Yes, I have, but I have installed an addon called Adblock Pluss so i can block all items that is annoying me, and also make sure you are running Firefox3.0.1 (the problem might be fixed there, for me it did). If you still have this problem install some addons that might help you with this...

---

### Post by silkstone on 2008-07-27
Can you give a link to the sites that misbehave?

---

### Post by bmann11 on 2008-07-27
how do I update to ff 3.0.1?

---

### Post by bmann11 on 2008-07-27
espn.com for one.  The have a media player on the right of the page that manages to hide the drop downs.

---

### Post by gjoellee on 2008-07-27
I am sorry, but I do no longer know which sites that did and therefor I cant give you any links, but I will add a link to this thread if I find one :)

---

### Post by gjoellee on 2008-07-27
I don't have any problem with espn but it is maybe because I use flash 10... try do use flash 10: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
you can install Firefox 3.0.1 adding this into terminal: > sudo apt-get install firefox if you have the latest version if firefox you have 3.0.1 
please tell me if you want help with installing flash 10!

---

### Post by bmann11 on 2008-07-27
updated to ff 3.0.1 but that didn't solve the problem.  Instructions on how to install flash 10 would be appreciated.

---

### Post by gjoellee on 2008-07-27
OK....

PART 1
First we have to remove the old flash plugin, by default this i located in /home/<user>/.mozilla/plugins. So go to your home folder and click CTRL+H and go in to ".mozilla" then go in to "plugins" and delete "libflashplayer.so".

PART 2
Download Flash 10BETA here: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz)
if the link doesn't work go to this one: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and download the .tar.gz file. When downloaded extract the file and drag the extracted file into your home folder

PART 3
Enter terminal and write:> cd install_flash_player_10_linux
after that add this sentence > ./flashplayer-installer now do as the installer says untill it is installed. Rastart firefox if it was running while you installed flash 10

Alternative installation:
Follow PART1 and 2
now enter the extracted file it is by deafault called "install_flash_player_10_linux" now simply copy or cut "libflashplayer.so" from the extracted folder to the folder you entered when you deleted "libflashplayer.so"

any questions or bugs, please tell...

---

### Post by silkstone on 2008-07-27
There is another way to install Adobe Flashplayer 10 that lets you overwrite it with the version in the Ubuntu repos very easily, if you wish.

Install the Flash plugin manually by downloading the tar archive of Adobe Flash v10 beta. Simply open the tar archive, then find the file named "libflashplayer.so" and place it on your desktop. Next, execute this command in the terminal:

32-Bit Ubuntu Family Users Only:

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart Firefox and use the plugin.

That is taken from the excellent tutorial here...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

