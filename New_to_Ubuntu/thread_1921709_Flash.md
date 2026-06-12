---
title: "Flash :/"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by Joemech7 on 2012-02-07
Hello, im having a problem with flash. i cant click in the settings box...which is weird. im running ubuntu 11.10

also, im very new to ubuntu, obviously since im posting in this forum.

also, ive tried this fix, [http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

but when i type in the commands and such nothing comes up, and im very confused. thanks.

---

### Post by ikt on 2012-02-07
I'm the same, I can't click on the settings box either.

If anyone has the answer would be good to know.

---

### Post by peebly on 2012-02-07
I removed the version which came installed with ubuntu and downloaded the one from adobe website. It installs the native control panel like the one in windows.

The control panel works way better then the online version at macromedia.

At adobe I clicked other versions, linux 64bit, and ubuntu (apt). Then just follow instructions.

---

### Post by Joemech7 on 2012-02-07
how would i go about that actually?

---

### Post by peebly on 2012-02-07
[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Select linux 64bit or 32bit, in the next box select ubuntu (apt). A install box will pop up.

Just click the install buttons and it installs it for you.

Remember to remove the preinstall version first.

---

### Post by Joemech7 on 2012-02-07
just to be safe, can you run me through how to uninstall the preinstall version?
i dont know ubuntu very well yett :/

---

### Post by peebly on 2012-02-07
Put this in the terminal.

sudo apt-get remove flashplugin-nonfree

---

### Post by Joemech7 on 2012-02-07
it says it cannot be removed :/

---

### Post by peebly on 2012-02-07
Do you have flash player installed ?

You could use the ubuntu software centre, start it up and type flash in the search and selected it from the list. On the right there will be a remove button.

---

### Post by Joemech7 on 2012-02-07
and then re download from the adobe site and i should be fine right?

---

### Post by Joemech7 on 2012-02-07
i went to the adobe site you gave me, and after i removed flash from the software center, i downloaded the file. it asks me to run it in the software center and sends me to the same flash page i installed it from before...

help?

---

### Post by peebly on 2012-02-07
yep

Download, installer will pop up. Think there are about 2 things to click, istall/add. It says something is not found but then adds it for you.

Control panel will be put in dash board applications.

takes about 15 secends.

---

### Post by romain.astie on 2012-02-07
had same issues, and reinstalling flash worked fine, how about you?

If installing the way peebly pointed out doesn't work, you can try this: [http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

I know it says  for Ubuntu 8.04, but it works anyways. You need to google around to the flash_player_10_linux file, but you'll find it...

---

### Post by Joemech7 on 2012-02-07
its still not working. i still cant click inside the settings box to turn on my webcam, or change the data alloted for the sites i visit. and i found the control panel for flash, but it wont save any of my settings. i dont get why this doesnt work...

---

### Post by romain.astie on 2012-02-07
What browser are you using?

---

### Post by Joemech7 on 2012-02-07
stock firefox

---

