---
title: "How do i auto start a program at login"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by TLD98541 on 2013-08-02
I need to auto start 2 programs at login "XBMC" and "VNC Server (User-Mode)"  The computer is a HTPC and usually has no keyboard or mouse attached only a remote control. I have been searching for the last 4 hours and can't figure it out.

Thanks for any help.

---

### Post by GwL3eNC on 2013-08-02
Hi, 

cant you do that with a script in /etc/init.d/
Create a script there and make the script executable (as sudo). Then make the script start at bootup 

sudo update-rc.d youscript.sh defaults

Hope it helps.

---

### Post by boast on 2013-08-02
You can try putting them in ~/.xinitrc

---

### Post by SweetAurora on 2013-08-02
You will need a keyboard just for the setup here, but after the setup, it won't be needed anymore
First run in a terminal, type:
```
sudo gedit /etc/rc.local
```
Then enter your password. Now, after the text document opens, move to a space below the blue text, but above the red "exit 0" text and type whatever commands you want. Make sure to only put one continuous command string per line. Now save it and close, then reboot to see if it works. :)

This script is meant to load/run commands AFTER a user session is started and is meant for user level commands only, and unlike the "Startup Applications" program, it can execute ANY command.

I personally use it to load a soundfont into memory for my sound card using asfxload.

---

### Post by TLD98541 on 2013-08-02
> **kitsuneinari78 said:**
> You will need a keyboard just for the setup here, but after the setup, it won't be needed anymore
First run in a terminal, type:
```
sudo gedit /etc/rc.local
```
Then enter your password. Now, after the text document opens, move to a space below the blue text, but above the red "exit 0" text and type whatever commands you want. Make sure to only put one continuous command string per line. Now save it and close, then reboot to see if it works. :)

This script is meant to load/run commands AFTER a user session is started and is meant for user level commands only, and unlike the "Startup Applications" program, it can execute ANY command.

I personally use it to load a soundfont into memory for my sound card using asfxload.

So do i just put the program name it that file or do i need to put a command and path like "run  /x/x/VNC Server (User-Mode)" or something?

---

### Post by SweetAurora on 2013-08-02
Treat rc.local like a terminal. Whatever commands you normally use to start VNC and XBMC in a terminal after the PC boots and logs in, you put there.

---

### Post by TLD98541 on 2013-08-02
Sorry but i have no idea what command it would take because i start them by clicking on the application menu, i've never had to run them from a terminal.

---

### Post by Frogs Hair on 2013-08-02
A  U-Studio version running XFCE allows adding start-up applications via session and start-up. The same application is in newer versions as well .
[http://xubuntugeek.blogspot.com/2011/12/add-application-to-xfcexubuntu-session.html](http://xubuntugeek.blogspot.com/2011/12/add-application-to-xfcexubuntu-session.html)

---

### Post by TLD98541 on 2013-08-03
[COLOR=#333333][FONT=UbuntuRegular]Alacarte didn't work but [/FONT][/COLOR][FONT=Ubuntu Mono]menulibre did.

Thanks for the help folks.[/FONT]

---

