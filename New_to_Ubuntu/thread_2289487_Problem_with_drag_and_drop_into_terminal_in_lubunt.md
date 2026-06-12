---
title: "Problem with drag and drop into terminal in lubuntu 15."
date: 2015-08-04
forum: New to Ubuntu
---

### Post by alex357 on 2015-08-04
I am trying to connect to the  Internet using open vpn service vpnbook I have read that I
 should drag and drop the ovpn file into the terminal window. 
[http://askubuntu.com/questions/508250/openvpn-gui-client-for-udp-tcp](http://askubuntu.com/questions/508250/openvpn-gui-client-for-udp-tcp)
But when I drug and drop nothing happens. Could you tell me what I should do to connect to the vpnbook. Open vpn is already installed.

---

### Post by ruzekle on 2015-08-04
You can also use right click to copy the file's location and right click your terminal window to paste.

EDIT:

You can also go into the directory you're working in. To do this use this command:

```
pwd
ls
```

This will tell you where you're working and what files and directories are available.

To go into your desired directory, just use the cd command. Hit the tab key until you're there. Use a file manager if to determine where your file is. If you downloaded it, it will probably be in the downloaded directory.

```
cd Downloads 
```

Once you're in the correct directory, first type out your command, and then write the start writing the file's name. You can also hit tab to make this faster.

---

### Post by monkeybrain20122 on 2015-08-04
I saw the thread title "drug and drop" and I feel high already. :)

---

### Post by alex357 on 2015-08-04
The file with the configuration settings is named ovpn and it is located into home/sasha. Could you tell me what I should type into the terminal to connect in accordance with the settings from this file. Sorry for the misprint,of course it's drag and drop.

---

### Post by ajgreeny on 2015-08-04
I have found the same happens in a VM of Lubuntu that I run in VirtualBox.  I do not know if it is a symptom of using pcmanfm or of lxterminal, or something completely different that causes the drag-&-drop failure, and I'm sorry but I have never investigated it either as it is simple to just right click and choose "copy location" then right click again in terminal and paste, as ruzekle said.

---

### Post by ruzekle on 2015-08-04
> **alex357 said:**
> The file with the configuration settings is named ovpn and it is located into home/sasha.

If you are user sasha, then ovpn should be located in the folder your terminal initially begins in. You can always just copy the location and paste its location into the terminal too.

---

### Post by mc4man on 2015-08-04
lxterminal doesn't support Dnd but you can copy & paste to achieve the same thing as mentioned

---

### Post by alex357 on 2015-08-05
I have gone to system tools\lxterminal and entered:  sasha@sasha-desktop:~$ sudo openvpn--config'\home\sasha\desktop\ovpn but nothing has happened. Copy and paste into the terminal doesn't work

---

### Post by howefield on 2015-08-05
> **alex357 said:**
> I have gone to system tools\lxterminal and entered:  sasha@sasha-desktop:~$ sudo openvpn--config'\home\sasha\desktop\ovpn but nothing has happened. Copy and paste into the terminal doesn't work

Remember that linux is case sensitive, so Desktop is different to desktop... and you probably need a space after openvpn--config

---

### Post by alex357 on 2015-08-05
I have entered the system tools\lx terminal . I see the following:  **sasha@sasha-desktop:~$  **. The file with the configuration settings for the open vpn connection is located at the desktop and it is named ovpn. Could you tell me what I should type into the lx terminal to connect.

---

### Post by howefield on 2015-08-05
On that information, I'd expect this to work...

```
sudo openvpn --config '\home\sasha\Desktop\opvn'
```

If not, try it without the quotes.

---

### Post by alex357 on 2015-08-07
I found three terminals in lubuntu,but copy and past works only in the the terminal from the system menu.

---

