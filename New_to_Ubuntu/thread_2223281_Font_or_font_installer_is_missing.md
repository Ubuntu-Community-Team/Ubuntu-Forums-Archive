---
title: "Font or font installer is missing?"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by steve119 on 2014-05-10
Okay, here's some specs: Sony VAIO PCG-FRV20 series/512 RAM/40GB HDD/CAT5 hardwired to Linksys WRT54G router/Lubuntu 14.04 full default install from CD obtained by website D/L. Thats the system, now me. I am a 25 year veteran of M$ products who converted from Atari when opportunity permitted. I have used Lubuntu 14.04 now for a few days, having only used Slackware 7 for a month in college 14 years ago. (Read NOOB. I still have to look up basic file commands that have no comparable M$ couterpart). I am trying to get a Netgear WNA 3100 USB Wireless NIC to work and have made assorted attempts at "package" installs with only limited success, meaning they actually did "something" other than return a "can't find" error or some such immediately after execution. The latest error appears to require reinstalling from the CD though I don't know. The text of one example follows:
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find the archive for it.

What  exactly is going on, since almost no commands needed to configure the WNA3100 (N300) USB  device are working without this error coming up?

---

### Post by Impavidus on 2014-05-10
ttf-mscorefonts-installer should be there on Trusty, in the multiverse repository. Check your software sources to see whether the multiverse repository has been enabled (should be by default). If that doesn't help, post the complete output of these commands:```
sudo apt-get update
sudo apt-get install ttf-mscorefonts-installer
```Note: If the ttf-mscorefonts-installer gets installed it will ask you to agree with the user licence. Use tab to select OK and hit enter.

Edit: Yeah, right, ignore me for the time being. It appears this was only a symptom of your real problem. I didn't fully understand your first post.

---

### Post by grahammechanical on 2014-05-10
May I make a comment? You should not need to have MS core fonts in order to get a network connection to a router. Ubuntu and its flavours such as Lubuntu have easy to use Graphical User Interface (GUI) utilities to let us do most things. It is not always necessary to do things through the command line where we need to carefully type the commands and mis-typing can lead to error messages.

May I suggest that you take a step back and review what the problems are? And we can help with each problem one at a time. And also, if you are going to use terminal commands that you make a note of the error messages.

Regards.

---

### Post by steve119 on 2014-05-11
Thanks for replying, I appreciate it. Sometimes I feel like I'm in an empty warehouse going "HELLO?!?!! Hello! hello! hello..." I think you missed something though so I'll paste it here:
"I am a 25 year veteran of M$ products who converted from Atari when  opportunity permitted. I have used Lubuntu 14.04 now for a few days,  having only **used Slackware 7 for a month in college 14 years ago**. (Read  NOOB. **I still have to look up basic file commands** that have no  comparable M$ counterpart, e.g., cd, /, md, rd, et cetera as opposed to /etc which I know is a linux directory)". 
So that being emphasized, I am afraid I don't understand what "Trusty" (although I have run across 'Trusty tar' whatever that is), "multiverse repository" (enabled or otherwise), or exactly what software sources you mean. I had help from the local public library staff in downloading the Lubuntu 14.04 to an install CD so I have NO IDEA where it actually came from, since it was THEIR idea to use IT instead of the MINT 16 I was originally considering. Presently I am using an XP machine to respond so I can't use the commands you've listed but I will post the results shortly when I switch to the other one with the Lubuntu on it. I do appreciate the replies I have received, here and elsewhere and they have helped, I think, though I may have caused the missing file problem myself, but I don't know.

---

### Post by Vladlenin5000 on 2014-05-11
Steve, whatever you're doing just stop NOW!!! Don't mess it beyond repair - if you didn't already -, take a step back and focus on your initial problem - getting your NETGEAR WNA3100 USB Wi-Fi dongle to work - and not on errors resulting from blind attempts to make it work following who knows what tutorials/suggestions.

First thing you should keep in mind is for troubleshooting non-working Wi-Fi cards/dongles knowing the real hardware - chipset - the device is based on is a must. "WNA3100" is irrelevant because often assemblers like NETGEAR change the hardware inside while keeping the model number/name. Reading some forum threads and other webpages back from 2010 it seems it's based on some Broadcom chipset but that could have changed so we need to know EXACTLY what hardware you're running. You can find it easily just by doing, in the terminal and with the dongle connected, ```
lsusb
``` This will list all your USB devices; you should find a line with something similar to ```
Bus 001 Device 015: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
``` Please post here the entire line and we can troubleshoot from there, preferably in a new thread with a proper title and in the correct forum section (network...).

Although **dealing with a Broadcom chipset under Linux usually means trouble**, there's also a chance it'll work fine after a proprietary firmware is loaded therefore the first thing to try, whenever available, is temporarily use a wired (ethernet) connection. With some luck Lubuntu will download the required firmware and the dongle will be up and running after a reboot. If not then do what I suggested in the last sentence of the previous paragraph. There are experts here that will guide you step by step, if needed.

Other comments:

 - Ignore post#2. It assumes you have a working internet connection and only answers to an unrelated issue. Post #3, on the other hand, is spot on: *You should not need to have MS core fonts in order to get a network connection to a router*.
 - "Trusty Thar" ('trusty' for short) is the codename for the Ubuntu 14.04 release (the previous release - Ubuntu 13.10 - was codenamed "Saucy Salamander"). You should always keep in mind at least the adjective ('trusty' in your case) because that's usually how the software repositories identify the release for which they are to provide software packages. 
 - Software repositories, in layman's terms, are servers providing software packages for your distro. This help page is good to start learning about it but the screenshots are a little bit outdated: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) . Look for Software & Updates in your Lubuntu.
 - Linux distros in general evolved a lot in the 14 years period since you used it last time. Nowadays most things are simpler and graphical and lots more hardware is now natively supported.

---

### Post by steve119 on 2014-05-12
I figured something important had gotten hosed, after all I had repeatedly entered commands starting with "SUDO" so I was capable of breaking something. Probably an accident on my part or someone posted some destructive code. Either way I decided the easiest thing to do was to start over and reinstall it. It was relatively new anyway so I wasn't really losing anything. The SPM actually seemed to be more functional after I reinstalled Lub14, but now I am getting the **root login request** when I tried to use it to install some USB related packages but** I don't know how to do that**. I can only login as a YOOOUSER!! (TRON ref.) Lub14 is pretty good if you want to get up and running quick, so I am happy with it generally. As for the experts, I could use some experts right now, but they need to be very gentle right now as I am still at the "Fun with D!ck and Jane" level of Linux use, hence my clear ref to being a NOOB. This is the Lub14 laptop I'm using here, hardwired as stated, and I wanted to activate the built in firewall, but I need to be root to do it, but I don't know how that is done either.

---

### Post by steve119 on 2014-05-12
The original issue being the Netgear Wireless WNA3100, the lsusb command does reproduce your information exactly as pictured but it still doesn't do anything automatically out of the box. I'll have to track down the info I read before now that I decided to hardwire the laptop to the router/modem. Maybe with the cat5 connection I 'll be able to use some of the install info I read, but I think I still need to know how to login as root in order to get it to work right. Eventually I'll get all this figured out and work it like a pro, but that's going to be a while later.

---

### Post by Vladlenin5000 on 2014-05-12
You don't login as root, that's what "sudo" is for. It temporarily elevates the previleges allowing the main user to make changes like installing new software.

Now that you have a freshly installed system you shouldn't mess it again. You're being unable to install that "USB related" whatever was probably a good thing. Any USB - including the latest USB3.0 - is natively supported.
Regarding the WiFi I strongly suggest you take some time to read the Networking & Wireless section in this forum and specifically look for instructions about the same Broadcom chipset you have. Hopefully it'll be a matter of issuing a couple of commands only followed by a reboot.  If it doesn't work you should then post a new thread in that section describing what you already did and the results. An expert will answer with a solution or a request for further troubleshooting.

---

### Post by steve119 on 2014-05-19
I should have given an update sooner but I wasn't sure how posts were tagged until later. Thank you all for your suggestions, some have in fact brought me closer to my goal and provided some needed info as well, and I appreciate it. I needed to do a hard wired update of the original installation and uncheck the cd search in order to get some needed files updated and installed properly. SO far so good, I even have two "Windows wireless drivers" shortcuts in my system tools folder which I think is a good thing and one step closer. Not sure why there are TWO shortcuts unless I did it twice, which is possible as I didn't know one of the install files was going to do that anyway. Now I need to find out what to do with the Win Installer and see if I missed anything. I might even get GIMP and OPEN OFFICE to install now. BTW, unless its out of my hands, do offer any other info or suggestions I mght need in this thread that have been overlooked, I do check back to see what may have been added. Thank you all again.

---

### Post by Vladlenin5000 on 2014-05-19
Install GIMP and LibreOffice from the Ubuntu software center. Click on "more information..." and select additional extras, if available (and needed for you, of course).

---

