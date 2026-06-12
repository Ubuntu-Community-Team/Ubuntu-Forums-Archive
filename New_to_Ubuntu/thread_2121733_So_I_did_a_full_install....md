---
title: "So I did a full install..."
date: 2013-03-02
forum: New to Ubuntu
---

### Post by JihadTurtle on 2013-03-02
And it worked, which I'm kind of surprised about because computers always screw up around me. However, I'm feeling rather nostalgic today, and I'd like to get a full Windows XP theme, several of which I have found, but none of which I can install. Also, I don't have a ~/.themes folder or a Share/themes folder as far as I can see. In fact, as far as I can see I don't have ~/ or share/ folders at all. Does anyone have a full, thorough tutorial?

---

### Post by Frogs Hair on 2013-03-02
You can create the .themes folder by selecting New Folder. A folder with . will appear when Ctrl + H is used when the home folder is open. There is  also a theme folder in file system usr/share/themes if you want the themes available for all users. ```
gksudo nautilus
``` I can't help with the XP theme though.

---

### Post by JihadTurtle on 2013-03-02
> **Frogs Hair said:**
> You can create the .themes folder by selecting New Folder. A folder with . will appear when Ctrl + H is used when the home folder is open. There is  also a theme folder in file system usr/share/themes if you want the themes available for all users. ```
gksudo nautilus
``` I can't help with the XP theme though.

I've found the folder in usr/share/themes, but it says I don't have permission to extract the theme there.
Help?

---

### Post by HermanAB on 2013-03-02
Sounds like what you want is XFCE.

---

### Post by Frogs Hair on 2013-03-02
> **JihadTurtle said:**
> I've found the folder in usr/share/themes, but it says I don't have permission to extract the theme there.
Help?

You can't extract there but you can drag the new theme folder there if you use the command.

---

### Post by JihadTurtle on 2013-03-02
First, thank you. You're the best. I have it in the folder, but now it doesn't show up in the themes list. How do I enable it?

---

### Post by Frogs Hair on 2013-03-02
1. Make sure the theme is compatible with your Ubuntu version . 12.04 uses Gnome 3.4 themes and 12.10 uses 3.6.    

2. Make sure the theme is fully extracted. Some times there is more than one theme included.

3. install the Gnome Tweak Tool from the software center for making theme selections.

---

### Post by JihadTurtle on 2013-03-02
> **Frogs Hair said:**
> 1. Make sure the theme is compatible with your Ubuntu version . 12.04 uses Gnome 3.4 themes and 12.10 uses 3.6.    

2. Make sure the theme is fully extracted. Some times there is more than one theme included.

3. install the Gnome Tweak Tool from the software center for making theme selections.

I tried installing it with this code in the terminal:
```
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get install gnome-tweak-tool
```
And every time I try to open it it just doesn't open.

---

### Post by suraj5989 on 2013-03-03
> 
sudo add-apt-repository ppa:ricotz/testing

This is meant for testing and am not sure if its stable yet.
This should be available in your existing repos.

Try disabling this ppa
[http://askubuntu.com/questions/173195/how-do-i-remove-a-ppa-added-via-command-line](http://askubuntu.com/questions/173195/how-do-i-remove-a-ppa-added-via-command-line)







and then do

sudo apt-get install gnome-tweak-tool

---

### Post by Frogs Hair on 2013-03-03
You don't need a PPA , Just search Tweak Tool in the software center and select install.

---

### Post by Mikhail.Inspired on 2013-03-04
If you run "gksu nautilus" from Alt+F2 or terminal, it should open a nautilus window.
If you need to move/extract the theme to /usr/share/themes, you can navigate to /home/user/path-to-theme, copy the file, and paste it in /usr/share/themes. From there you can open Archive Manager by double clicking on it or right clicking it and selecting "Extract Here." Hope that helps.

---

### Post by Mikhail.Inspired on 2013-03-04
A good tool for switching themes that came out recently:
> sudo apt-get install ppa:freyja-dev/unity-tweak-tool-daily && sudo apt-get update && sudo apt-get install unity-tweak-tool

---

