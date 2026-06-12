---
title: "Getting an inf file from my netgear driver exe"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by laurencemulchrone on 2008-04-24
Hey guys.

i have read so many posts about getting inf files from exe's but i just cannot seem to do it....
i have unzip installed as well as cabextract installed.
the file is called wg111t_2_0_setup.exe and it is saved on my desktop

could anyone help me, how can i get the inf, im afraid i am still not good with the terminal, i am even unsure how to navigate to a file!

appreciate it!****

---

### Post by rbc on 2008-04-24
Have a look at this:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

And also #20 on this site:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

---

### Post by zolookas on 2008-04-24
Open terminal and type "sudo su" (witout quotes) and enter your password.
Then try doing like here (pasting commands to terminal): [http://forums.debian.net/viewtopic.php?p=68058#63628](http://forums.debian.net/viewtopic.php?p=68058#63628)

---

### Post by spiderbatdad on 2008-04-24
If the file is on your desktop, first navigate to the desktop. Desktop is case sensitive.```
cd Desktop
``` You can use the tab key to auto complete for you. In the case of Desktop, you would need to type cd De then the tab key, as Documents is also a folder in the Home directory...so you would get a system beep just having cd D.

Once on the desktop run cabextract on the .exe. Again tab key will auto complete files names for you when you are in the correct directory.

Use sudo -i or sudo -s for root access, not sudo su.

---

