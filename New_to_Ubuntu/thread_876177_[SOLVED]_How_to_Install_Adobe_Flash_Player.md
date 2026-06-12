---
title: "[SOLVED] How to Install Adobe Flash Player"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by ChocolateChip_Wookie on 2008-07-31
As I was 'stumbling' around, I came across a site that insists that I require further plugins in order to view it. I clicked the link but an automitic install is not allowed so I have to do a manual one. I downloaded the file (install_flash_player_9_linux) which is a tar.gz and extracted it to the /tmp file. So far so good. Inside it is a file called 'flashplayer-installer' but when I click on it, nothing happens. I opened a terminal and did the sudo apt-install command but got nothing? I cd'd to the /tmp directory and did an 'ls' and found the file but I just cannot figure out how to execute it. 

Can anyone tell me the command to execute the file and install the plugin please?

---

### Post by snowpine on 2008-07-31
Open a terminal and type

```
sudo apt-get install flashplugin-nonfree
```
and enter your password.

---

### Post by ChocolateChip_Wookie on 2008-07-31
Did that. And also from Synaptic but the site still insists that the necessary driver is not installed. Is it possible that this particular driver is too new to be included in the repository?

---

### Post by snowpine on 2008-07-31
Whoops, sorry... I misread your original post. :(
I'm afraid I don't have any other suggestions for you; that method is what worked for me. Hopefully someone more knowledgeable will be along to help you. Good luck!

ps Do you have any Firefox extensions running such as Noscript? That's the only other thing I can think of.

---

### Post by etomic13 on 2008-07-31
The current version of Flash (according to the Adobe website) is 9,0,124,0 which is also whats listed in the Ubuntu repository. So it should be installing the latest version. Does it list any dependency problems?

---

### Post by philinux on 2008-07-31
It might need java as well. Install the extras package.

sudo apt-get install ubuntu-restricted-extras

---

### Post by LittleLORDevil on 2008-07-31
I usually go to Add/Remove and search for Ubuntu Restricted Extras and install all of that and it usually works along with a lot of other proprietary formats.

---

### Post by Twitch6000 on 2008-07-31
> **ChocolateChip_Wookie said:**
> As I was 'stumbling' around, I came across a site that insists that I require further plugins in order to view it. I clicked the link but an automitic install is not allowed so I have to do a manual one. I downloaded the file (install_flash_player_9_linux) which is a tar.gz and extracted it to the /tmp file. So far so good. Inside it is a file called 'flashplayer-installer' but when I click on it, nothing happens. I opened a terminal and did the sudo apt-install command but got nothing? I cd'd to the /tmp directory and did an 'ls' and found the file but I just cannot figure out how to execute it. 

Can anyone tell me the command to execute the file and install the plugin please?

Excuse me if this sounds harsh or wrong in any manner,but were you searching for the normal things every normal person likes once in a while?If so it is probably trying to give you a windows virus and cannot succeed due to you being on a Linux machine.If I am incorrect then I would try uninstalling flash then reinstalling it.

---

### Post by jualin on 2008-07-31
Have you tried [this?]("http://www.adobe.com/products/flashplayer/productinfo/instructions/")

---

### Post by jualin on 2008-07-31
You need to navigate with the terminal to execute the installer. Once you get there then just type > ./flashplayer-installer to run it

---

### Post by aysiu on 2008-07-31
Why don't you tell us what the site is, and we can tell you whether or not it legitimately requires a Flash plugin or not?

---

### Post by ChocolateChip_Wookie on 2008-07-31
> **philinux said:**
> It might need java as well. Install the extras package.

sudo apt-get install ubuntu-restricted-extras

OK. Did that.

Still no joy. Some websites are still insisting that they require the plugin although Synaptic says it is installed. I have downloaded the package that it insists on but i just dont know how to execute it. The tar.gz is Linux version Adobe Flash 9 currently sitting in the /tmp directory

---

### Post by ChocolateChip_Wookie on 2008-07-31
Sure. Here it is. The original one was a Stumble so I've lost it, but this one is telling me the same...

[http://www.dinosaurnews.org/](http://www.dinosaurnews.org/)

---

### Post by ChocolateChip_Wookie on 2008-07-31
> **Twitch6000 said:**
> Excuse me if this sounds harsh or wrong in any manner,but were you searching for the normal things every normal person likes once in a while?If so it is probably trying to give you a windows virus and cannot succeed due to you being on a Linux machine.If I am incorrect then I would try uninstalling flash then reinstalling it.

ROFL! OMG That's the funniest thing I've heard all day.

I'm a mother of two small girls. I dont have time to search for that sort of stuff. Besides, I got the real thing this morning. Anyway, No, when I said 'Stumbling' I meant Stumbling as in Stumble. I was just randomly surfing the net but I keep comming across this Adobe Plugin problem.

No offence taken and point understood but oh my god that was funny.

---

### Post by aysiu on 2008-07-31
> **ChocolateChip_Wookie said:**
> Sure. Here it is. The original one was a Stumble so I've lost it, but this one is telling me the same...

[http://www.dinosaurnews.org/](http://www.dinosaurnews.org/)
The only Flash I see there is an embedded YouTube video, and it works for me with the *flashplugin-nonfree* package.

---

### Post by gjoellee on 2008-07-31
_delete flash (if it is there)_
-Go to your home folder and click CTRL+H and find ".mozilla"
-Now to go "plugins"
-if you find "libflashplayer.so" it may be broken or something so delete it

[U]Lets install flash 10 BETA!
[/U]-Download
**Direct Link**:[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz)
**Main Mirror**: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
-Extract the .tar.gz file and put the extracted file to your home folder
-Go to terminal Applications->Accessories->Terminal and add the commands:
```
cd install_flash_player_10_linux
```
```
./flashplayer-installer
```
-do as the installer tells you until it says you have have installed flash
-restart Firefox if it was running when you installed Flash 10BETA

---

### Post by ChocolateChip_Wookie on 2008-07-31
> **jualin said:**
> You need to navigate with the terminal to execute the installer. Once you get there then just type  to run it

OK. That fixed it. Thanks! Web sites running properly now.

---

### Post by gandaran on 2008-07-31
edit:

---

### Post by ChocolateChip_Wookie on 2008-07-31
According to the About box, this is the firefox version :

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Ubuntu/8.04 (hardy) Firefox/3.0.1 (Linux Mint)

---

### Post by jualin on 2008-07-31
Glad I helped you.

---

### Post by Twitch6000 on 2008-07-31
> **ChocolateChip_Wookie said:**
> ROFL! OMG That's the funniest thing I've heard all day.

I'm a mother of two small girls. I dont have time to search for that sort of stuff. Besides, I got the real thing this morning. Anyway, No, when I said 'Stumbling' I meant Stumbling as in Stumble. I was just randomly surfing the net but I keep comming across this Adobe Plugin problem.

No offence taken and point understood but oh my god that was funny.

Well darn now I feel dumb :(.

---

### Post by ChocolateChip_Wookie on 2008-07-31
> **Twitch6000 said:**
> Well darn now I feel dumb :(.
No go wash your mind out with soap sweetie :)

---

### Post by bondo101 on 2008-08-11
Thanks the AdobeFlash player ate my hibernation mode i hope this fixes it. i reset the hiber time but it comes up with a error code then shuts down HMMMMM !
                                           bondo101 one linux at a time

---

