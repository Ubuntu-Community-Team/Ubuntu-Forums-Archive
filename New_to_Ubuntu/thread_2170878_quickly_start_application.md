---
title: "quickly start application"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-08-28
Hi all, 

I've installed JDeveloper, now to start it I should go to the ***/jdeveloper/jdev/bin*** directory and then type [B][I]./jdev 
[/I][/B]*How do I start it quickly? *****

---

### Post by tgalati4 on 2013-08-28
Add /jdeveloper/jdev/bin to your path in .bashrc file then Alt-F2 jdev.  The path is added automatically if you installed jdev to ~/bin according to .profile.

---

### Post by Marchello_Lippi on 2013-08-28
> **tgalati4 said:**
> Add /jdeveloper/jdev/bin to your path in .bashrc file then Alt-F2 jdev.  The path is added automatically if you installed jdev to ~/bin according to .profile.

Big thanks, I'll try it at home in the evening. 
Best regards.

---

### Post by meilin on 2013-08-28
You can manually create a launcher for the app that doesn't have a shortcut icon.

Install required package:

```
sudo apt-get install gnome-panel --no-install-recommends
```

Bring up Create Launcher dialog. 

[COLOR=#000000][FONT=monospace]```
sudo gnome-desktop-item-edit /usr/share/applications/ --create-new
```

Choose an icon and type in command to start the app. Add <b>gksudo</b> at beginning if need the root privilege to open it.

via: [/FONT][/COLOR][http://ubuntuhandbook.org/index.php/2013/07/create-shortcut-unity-search-results/](http://ubuntuhandbook.org/index.php/2013/07/create-shortcut-unity-search-results/)

---

### Post by Marchello_Lippi on 2013-08-28
Can I use gnome-panel and gnome-desktop-item-edit to create launcher in Unity?

---

### Post by tgalati4 on 2013-08-28
As usual, there are several ways to add your path statment:  [https://help.ubuntu.com/community/EnvironmentVariables#Persistent_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#Persistent_environment_variables)

And an example using Android software development kit:  [https://help.ubuntu.com/community/AndroidSDK#Modifying_the_PATH_Environment_Variable](https://help.ubuntu.com/community/AndroidSDK#Modifying_the_PATH_Environment_Variable)

---

