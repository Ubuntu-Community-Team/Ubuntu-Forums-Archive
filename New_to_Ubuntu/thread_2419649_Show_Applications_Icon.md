---
title: "Show Applications Icon"
date: 2019-05-24
forum: New to Ubuntu
---

### Post by mraamohamed on 2019-05-24
Hello and please let me introduce myself, I am Abdulah and I am NEW to Linux, this is my first install, I have been a (excuse the blasfamy) a windows user forever, and now I am tired of Big M telling me what I can and can not do.  So I moved to Ubuntu and so far so good, 

OK here is my question, on my home screen I have the bottom row of icons, and all the way on the right side of screen is my Application Launcher (9 dots icon), but I would like to have it on the left at the front, how can I move it. 

Thanks in advance for the help.

Abdulah Mohamed

---

### Post by oldrocker99 on 2019-05-24
Here's how, my friend:

[https://www.howtogeek.com/349697/how-to-move-ubuntu%E2%80%99s-launcher-bar-to-the-bottom-or-right/](https://www.howtogeek.com/349697/how-to-move-ubuntu%E2%80%99s-launcher-bar-to-the-bottom-or-right/)

A great number of problems can be solved by searching on Google. I found that URL by Googling "ubuntu move application launcher."

Not a putdown. Just a hint about where to look first. If there is no solution found with Google, by all means post your questions right here, and welcome to the forums!

---

### Post by mraamohamed on 2019-05-24
Thanks for the help OldRocker99 but to be 100% with you, I hate Big Brother Google, I rather to talk to people as Big Brother Google is always tracking all we do, and I do not like that.

---

### Post by mraamohamed on 2019-05-24
[ATTACH=CONFIG]283312[/ATTACH] 
This is what I am talking about OldRocker 99, thanks for the help

---

### Post by deadflowr on 2019-05-24
I forget if it's a setting you can set in gnome tweaks, I'm not sure,
but you can run this one time from a terminal
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-apps-at-top true
```
The setting should stick persistently.

---

### Post by mraamohamed on 2019-05-24
OK Old Rocker 99 I took advice and serached Big Brotehr Google and found this.

[https://askubuntu.com/questions/966704/how-do-i-move-the-show-applications-icon-in-ubuntu-dock](https://askubuntu.com/questions/966704/how-do-i-move-the-show-applications-icon-in-ubuntu-dock)

Worked for me, thanks for the help....maybe I can be a little less cynical next time...hehe

---

### Post by richard378 on 2019-05-24
Try this extension to control the app button: [https://extensions.gnome.org/extension/307/dash-to-dock/](https://extensions.gnome.org/extension/307/dash-to-dock/) and choose in the Gnome-Tweaks the settings for this extension under Launchers to modify the app icon.  Turn it on or off or right or left.

---

