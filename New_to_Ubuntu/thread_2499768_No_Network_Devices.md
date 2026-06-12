---
title: "No Network Devices"
date: 2024-08-10
forum: New to Ubuntu
---

### Post by howsg on 2024-08-10
No Network Devices
Hi All Masters, I just installed the latest Ubuntu with some updates and was successful. 
I had done all the settings but still was not able to view all my network devices.
Please Help
Thanks & Best Regards

---

### Post by yancek on 2024-08-10
What settings have you done?
What network devices are you referring to?
Do you have an internet connection?
Try using some of the commands at the site from the link below to post information on your network and also post some specific information on what you actually did try and the specific results.  What does 'all the settings" mean and what network devices can you not see ?

[https://www.geeksforgeeks.org/how-to-list-network-interfaces-in-linux/](https://www.geeksforgeeks.org/how-to-list-network-interfaces-in-linux/)

---

### Post by howsg on 2024-08-10
> **yancek said:**
> What settings have you done?
What network devices are you referring to?
Do you have an internet connection?
Try using some of the commands at the site from the link below to post information on your network and also post some specific information on what you actually did try and the specific results.  What does 'all the settings" mean and what network devices can you not see ?

[https://www.geeksforgeeks.org/how-to-list-network-interfaces-in-linux/](https://www.geeksforgeeks.org/how-to-list-network-interfaces-in-linux/)

[COLOR=#000000][FONT=Arial]Hi Yancek, thank you for your reply.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So sorry for not remembering to mentioned I have also installed some files for my USB Hauppauge Dual Dvb-T2 Tuner that was instructed in Hauppauge webpage, “[/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]https://hauppauge.com/pages/support/support_linux.html[/FONT][/COLOR]]("https://hauppauge.com/pages/support/support_linux.html")[COLOR=#000000][FONT=Arial]”.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The commands [highlighted in Red] I have executed in Terminals are as follows,[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]First, determine the version of Ubuntu you are running[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]To do this, run this command:[/FONT][/COLOR]
[COLOR=#FF0000][FONT=Arial]dpkg -l | grep linux-image-generic-hwe[/FONT][/COLOR]

[CENTER][COLOR=#000000][FONT=Arial]If a line is displayed beginning with "ii", then you are running the HWE version of Ubuntu. You will need to know if you are running HWE this in a moment when you install the mediatree.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Download the PPA[/FONT][/COLOR][COLOR=#FF0000][FONT=Arial]sudo add-apt-repository ppa:b-rad/kernel+mediatree+hauppauge[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]After this first line, click enter when prompted to add this PPA.[/FONT][/COLOR][COLOR=#FF0000][FONT=Arial]sudo apt-get update[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Install the media tree[/FONT][/COLOR][COLOR=#000000][FONT=Arial]If you are running an HWE version of Ubuntu, use this command:[/FONT][/COLOR][COLOR=#FF0000][FONT=Arial]sudo apt-get install linux-hwe-mediatree[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If you are NOT running HWE, use this command:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo apt-get install linux-mediatree[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Firmware Install[/FONT][/COLOR][COLOR=#000000][FONT=Arial]At this point, you also need to install TV firmware if you are using one of the following TV tuners (most North American TV tuners do NOT need firmware to be loaded, so this mainly applies to European/ANZ tuners):[/FONT][/COLOR][COLOR=#000000][FONT=Arial]•[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]a Hauppauge DVB TV tuner in Europe, Australia or New Zealand (example: WinTV-soloHD, WinTV-dualHD, WinTV-quadHD, WinTV-HVR-5525, Starburst 2, etc.)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]•[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]461e or WinTV-NOVA-S2[/FONT][/COLOR][COLOR=#000000][FONT=Arial]•[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]WinTV-quadHD USB for North America[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]To download and install Hauppauge TV tuner firmware, run this command:[/FONT][/COLOR][COLOR=#FF0000][FONT=Arial]sudo apt-get install linux-firmware-hauppauge[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Close Terminal and restart your computer.[/FONT][/COLOR][/CENTER]

[COLOR=#000000][FONT=Arial]As for your questionnaires, my answers are as follows,[/FONT][/COLOR]

[LIST=1]
[*]What Settings: I mean the basic settings in setup for Ubuntu

[*]Network Devices: Hard-disk@Asus Router, a few of my Enigma2 Setup Box, Windows 10 PC
[/LIST]

[COLOR=#000000][FONT=Arial]Please Help[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Thanks & Best Regards[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by howsg on 2024-08-10
[COLOR=#000000][FONT=Arial]Almost forgot, I have also executed the following commands to install Kaffeine[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Install Kaffeine Ubuntu 22.04 LTS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt update && sudo apt upgrade[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt install kaffeine -y[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

