---
title: "How do I install Canon printer driver"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by Charlie Chick on 2013-07-06
Hello Everybody,

I have just bought a Canon iP7250 printer. I have downloaded the Linux drivers (.deb) from the Canon website onto my desktop and extracted the file onto the desktop. I understand that install.sh is the eqivalent of the Windows .exe file, but I don't know how to start the installation. Double clicking it only opens it in a text editor.

I tried installing it with CUPS drivers but it doesn't print at all, so it looks as if I need to use these pukka Canon drivers.

Can anybody help me please? I'm running 13.04.

Many thanks,

Charlie

---

### Post by jimingkui on 2013-07-06
The PPA ppa:michael-gruz/canon-stable contains official drivers of many commonly used Canon printers for Ubuntu. You can try it out at [http://handytutorial.com/install-canon-printer-driver-for-ubuntu-13-04-12-10-12-04/]("http://handytutorial.com/install-canon-printer-driver-for-ubuntu-13-04-12-10-12-04/")

Sorry, my bad!  .deb file is the eqivalent of the Windows .exe file you can double-click on the .deb package and install via popup Ubuntu Software Center. For install.sh, Press Ctrl+Alt+T to get a terminal window, run the .sh file via command, for example:

sudo bash PATH/TO/install.sh

---

### Post by Charlie Chick on 2013-07-06
Thank you very much for your help. Much appreciated. Problem solved!

---

