---
title: "putty-url for ubuntu (Clickable links in terminal emulator)"
date: 2014-10-08
forum: New to Ubuntu
---

### Post by ben5 on 2014-10-08
We use putty-url on windows so that links are clickable.  But now have some ubuntu PC's.  Is there a putty-url version for linux/ubuntu?  Or if not is there another terminal emulator for linux that allows you to click on URL's?

---

### Post by sandyd on 2014-10-09
If you are using Unity, holding down control while clicking a link in the default gnome terminal should open the link in your browser.

---

### Post by GrouchyGaijin on 2014-10-09
I have both gnome-terminal and terminator installed.  I can click links in the terminal window.  Have you tried clicking a link? (I do have to hover over the link and then right click.)

---

### Post by Impavidus on 2014-10-09
In xfce4-terminal (default terminal on Xubuntu) you can middle click on a url to open the link in your web browser. Right click &#8594; open link also works.

---

### Post by nerdtron on 2014-10-09
> **ben5 said:**
> We use putty-url on windows so that links are clickable.  But now have some ubuntu PC's.  Is there a putty-url version for linux/ubuntu?  Or if not is there another terminal emulator for linux that allows you to click on URL's?

Crtl+Left Click will follow the link from the terminal window. The default terminal in Ubuntu is much better than windows putty so try exploring it features. It even has support on tabs. If you install Terminator from the Software Center you'll even have support for split screens and even send a single command simultaneously on all terminals. Now that's what a call a bad-ass terminal :)

---

### Post by ben5 on 2014-10-19
> **nerdtron said:**
> Crtl+Left Click will follow the link from the terminal window. The default terminal in Ubuntu is much better than windows putty so try exploring it features. It even has support on tabs. If you install Terminator from the Software Center you'll even have support for split screens and even send a single command simultaneously on all terminals. Now that's what a call a bad-ass terminal :)

So these PCs are used by very low level users... 


Basically they are using putty to connect to a remote server that gives them a very basic and limited interface.


So using the default terminal app is fine with me as long as I can find a way to have an icon they can double-click that would open a terminal window and automatically ssh to a specific IP....** So that the user experience is to double-click the icon and be presented with the login prompt for the remote server.  **


Any idea what the easiest way to accomplish this would be?


Thanks!

---

### Post by nerdtron on 2014-10-19
> **ben5 said:**
> 
So using the default terminal app is fine with me as long as I can find a way to have an icon they can double-click that would open a terminal window and automatically ssh to a specific IP....** So that the user experience is to double-click the icon and be presented with the login prompt for the remote server.  **
Thanks!

First choice: (non-native way)
1. Install Wine
2. Run putty-curl.
Since putty-curl is just a simple application like putty, it should run in Wine.

Second choice: (way better)
Let's create a launcher:
1. Create a text file and save it ssh.txt. See it contents below from #/bin/bash. You'll do this once, but will just have to copy on other computers.
```
[kenneth@nerdtron ~]$ pwd
/home/kenneth
[kenneth@nerdtron ~]$ cat ssh.txt
#/bin/bash
read -p "Please enter your username: " USERNAME
read -p "Please enter your Server: " SERVER
ssh  "$USERNAME"@"$SERVER" 
```
2. Now we create a launcher (icon) on the desktop. Right Click on the desktop and select Create Launcher. See below for details.
[ATTACH=CONFIG]257365[/ATTACH]

3. You'll see the launcher created on your desktop. Double click it and you'll launch a terminal window asking for credentials.
[ATTACH=CONFIG]257364[/ATTACH]

---

### Post by ben5 on 2014-10-19
Thanks!  I should mention I am using gnome-fallback instead of unity. Perhaps that is why I have no "[COLOR=#000000]Create Launcher[/COLOR]" when I right click the desktop?

Anyway - I already tried setting up a .desktop file (is that what "create launcher" does?) with Exec= set to "bash ~/filenameToRunSsh" and it doesn't open any terminal window. 

Any ideas?

---

### Post by nerdtron on 2014-10-19
Hmmm.. Do you have this? [http://askubuntu.com/questions/64222/how-can-i-create-launchers-on-my-desktop](http://askubuntu.com/questions/64222/how-can-i-create-launchers-on-my-desktop)

Note that the Type should be "Application in Terminal" for it launch a terminal window.

---

### Post by nerdtron on 2014-10-20
> **ben5 said:**
> Thanks!  I should mention I am using gnome-fallback instead of unity. Perhaps that is why I have no "[COLOR=#000000]Create Launcher[/COLOR]" when I right click the desktop?

Anyway - I already tried setting up a .desktop file (is that what "create launcher" does?) with Exec= set to "bash ~/filenameToRunSsh" and it doesn't open any terminal window. 

Any ideas?

Here's my .desktop file:
```
[kenneth@nerdtron ~]$ cat Desktop/ssh.desktop 

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon[en_US]=gnome-panel-launcher
Name[en_US]=ssh
**Exec=bash /home/kenneth/ssh.txt**
Name=ssh
Icon=gnome-panel-launcher
```

Use absolute path on the exec. I tried to use a ~/ssh.txt and it did not work.
Also if you have the line:  #!/usr/bin/env xdg-open on the .desktop file, remove it. I don't have that line on my .desktop file

---

