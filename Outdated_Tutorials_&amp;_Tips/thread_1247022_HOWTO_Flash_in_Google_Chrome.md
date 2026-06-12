---
title: "HOWTO: Flash in Google Chrome"
date: 2009-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by MadnessRed on 2009-08-22
This simple script will add the flash plugin to Chrome.

Please make sure that google chrome is updated as only the newer versions support plugins.

_Simple script for default configuration:_
[INDENT]This assumes that flash is installed in /usr/lib/adobe-flashplugin/ and google chrome in /opt/google/chrome/
1) Install flash:
If you haven't already done so, then download and install flash from the adobe website.
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

2) Run the script:
```
cd /opt/google/chrome/; sudo mkdir plugins; cd plugins; sudo ln -s /usr/lib/adobe-flashplugin/libflashplayer.so
```

3) Edit the launchers:
Click on System > Prefernces > Main Menu
Then select Internet > Google Chrome
Select edit and change the launcher to
```
/opt/google/chrome/google-chrome --enable-plugins %U
```
If you have any other launchers on the panel or desktop, right click on them and select properties and then do the same.[/INDENT]

_Not so simple way: via gui_
[INDENT]You need to find the flash plugin folder, if you can't find the /usr/lib/flash-plugin/ then you may also find it in the firfox/plugins folder. Now you need to make a folder in your chrome directory called plugins. Either copy into or make a link to "libflashplayer.so" in that folder.

After this do step 2 of the simple method.[/INDENT]

I did this and youtube works for me, haven't tested anything else yet.

---

### Post by Sam_S on 2009-11-18
For me running Ubuntu 9.10 on a Toshiba satellite laptop, I still received errors with the flash plugin and Chrome would sometimes lock up.

I just came across a posting for the chromium browser that solved my problem with a slight adjustment for chrome.  The following is what worked for me:
[LIST]
[*]sudo mkdir /opt/google/chrome/plugins
[*]sudo ln -s /usr/lib/firefox/plugins/flashplugin-alternative.so /opt/google/chrome/plugins/libflashplayer.so
[/LIST]

---

### Post by Vihosa on 2009-12-09
I have this problem, when I download and open the .deb file, it says:"Error: Wrong architecture 'i386'" What should I do?

---

### Post by YosefKaro on 2009-12-11
This works great.  Thank you so much :D

-Yos

---

### Post by aysiu on 2009-12-11
> **MadnessRed said:**
> This simple script will add the flash plugin to Chrome. I don't get why this tutorial is necessary. I just installed the Ubuntu .deb from the Adobe website and double-clicked it. That Flash plugin worked for Chrome, Opera, and Firefox. I didn't have to do anything else special to get it to work in Chrome.

> **Vihosa said:**
> I have this problem, when I download and open the .deb file, it says:"Error: Wrong architecture 'i386'" What should I do? It's probably the wrong architecture. Can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and paste the output back here? ```
uname -m
```

---

### Post by burtonbarber on 2009-12-12
Thanks!!!! I didn't have sound with YouTube, now I do.:D

---

### Post by mehkidoo on 2010-05-10
Aysiu - I have the same problem as Vihosa - Chrome isn't installing and is giving ab i386. When I pasted the text into the Terminal, I get this output:

x86_64


I'm a complete newbie, so I have no idea what this means. :P

---

