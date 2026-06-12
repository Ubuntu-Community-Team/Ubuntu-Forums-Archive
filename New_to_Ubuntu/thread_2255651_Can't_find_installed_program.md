---
title: "Can't find installed program"
date: 2014-12-06
forum: New to Ubuntu
---

### Post by MAFinOKC on 2014-12-06
I'm brand new to (L)ubuntu; experimenting with it on an older Toshiba laptop that was *not* running Windows 8.1 well at all. in the 

First of all: I notice that when I install new software, almost invariably I get a message that some package could not be downloaded or installed. Yet the program appears to have installed correctly. I am guessing that some components are not suitable for my system and so have been omitted. Or is there another reason? 

Second: I just installed kdenlive for video editing. I got a desktop message stating that it installed correctly and it's included in list of Installed Programs in the software collection application; however, there's no icon in the start menu or on the desktop and I can't find it in the computer's folders. Where can I find some information on the Linux file structure and also where do I look for the program? Or do I remove and reinstall it? Thank you. MAFinOKC

---

### Post by Rex Bouwense on 2014-12-06
1.  Is your program listed in /usr/share/applications?
2.  Did you download the program from the repository?

---

### Post by nerdtron on 2014-12-06
> Second: I just installed kdenlive for video editing. I got a desktop  message stating that it installed correctly and it's included in list of  Installed Programs in the software collection application; however,  there's no icon in the start menu or on the desktop and I can't find it  in the computer's folders.

Not sure but I think KDE applications expect you to have a KDE menu for application entries? Anyway, to confirm it is installed correctly, you can try running it manually either:
Press Alt+F2, type kdenlive, hit Enter
or in the terminal type kdenlive, hit Enter

---

### Post by vasa1 on 2014-12-06
> **MAFinOKC said:**
> I'm brand new to (L)ubuntu; ...
First of all: I notice that when I install new software, almost invariably I get a message that some package could not be downloaded or installed. Yet the program appears to have installed correctly. I am guessing that some components are not suitable for my system and so have been omitted. Or is there another reason? 

Give us at least one example of what exactly you see. Do this by taking a screenshot of the message and uploading it here or by copying the message from the terminal and pasting it here between **code** tags.

> **MAFinOKC said:**
> Second: I just installed kdenlive for video editing. I got a desktop message stating that it installed correctly and it's included in list of Installed Programs in the software collection application; however, there's no icon in the start menu or on the desktop and I can't find it in the computer's folders. Where can I find some information on the Linux file structure and also where do I look for the program? Or do I remove and reinstall it? Thank you. MAFinOKC

Some programs may be set to be "hidden" in environments other than a particular one by means of "OnlyShowIn" in their .desktop file (or "NotShowIn"); this determines whether the menu displays the program or not. Look at /usr/share/applications/kdenlive.desktop or whatever it's called to see if that's the case.

---

### Post by bapoumba on 2014-12-07
> **MAFinOKC said:**
> I'm brand new to (L)ubuntu; experimenting with it on an older Toshiba laptop that was *not* running Windows 8.1 well at all. in the 

First of all: I notice that when I install new software, almost invariably I get a message that some package could not be downloaded or installed. Yet the program appears to have installed correctly. I am guessing that some components are not suitable for my system and so have been omitted. Or is there another reason? 

Please open a terminal and run the following. Paste the complete output here.
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
sudo apt-get update
sudo apt-get upgrade
```
The sudo part of the commands will prompt you to enter your password in the terminal window. Please do so and hit <enter>, there is no visual feedback of the password being entered, that is normal.

---

