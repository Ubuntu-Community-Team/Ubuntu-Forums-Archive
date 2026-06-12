---
title: "Google Chrome - Settings"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by Mark de J on 2014-05-28
Hello,

Google Chrome has default the option settings turned on, how can I remove that so I can open Google Chrome normal?

[ATTACH=CONFIG]253526[/ATTACH]

---

### Post by nerdtron on 2014-05-28
Sorry I can't seen to understand you situation. Can you elaborate?

Do you mean that Google Chrome is your default browser? What do you want to accomplish in "open Google Chrome normal"?

---

### Post by veddox on 2014-05-28
Remove your current Chrome icon from the launcher. Go to **/usr/share/applications**, and find the Chrome link. Copy this to your desktop. Then drag it into the launcher and try it out.

If it still does not work, do the following:
 Open the terminal (Ctrl+Alt+T), and enter:
```
cd Desktop
ls
```
In the list that comes up, you should see an entry called "chrome.desktop" (or something similar). Now use the command:
```
gedit chrome.desktop
```
Note: if necessary, replace the "chrome.desktop" with whatever your link is called.

The text editor will open. Copy its contents here, and we will hopefully be able to tell you what is wrong.

---

### Post by Mark de J on 2014-05-28
bash: cd: Desktop: Bestand of map bestaat niet

---

### Post by veddox on 2014-05-28
Try
```
cd $HOME/Desktop
```
If the desktop has a different name in the Dutch version of Ubuntu, substitute that name.
Then continue as above.

---

### Post by Mark de J on 2014-05-28
The result of LS:
askubuntu.sh
binary-code-9004-2560x1600.jpg
Dota 2.desktop
gimp-webp_0.2-1.deb
intel-linux-graphics-installer_1.0.5-0intel1_amd64.deb
Memes
Naamloos.png
Scripts
teamviewer_linux.deb
teamviewer_linux_x64.deb
TVZ-starters.pdf

---

### Post by veddox on 2014-05-28
> **veddox said:**
> Remove your current Chrome icon from the launcher. Go to **/usr/share/applications**, and find the Chrome link. Copy this to your desktop. Then drag it into the launcher and try it out.

Did you do that?

By the way, how did you install Chrome? From the Software Center or from an independent package?

---

