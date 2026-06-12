---
title: "Authorization help,"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Raven_ on 2008-08-27
Hello! 

I've been meaning to install a skin for aMSN but it doesn't seem to work. On aMSN's [Installing Plugins and Skins]("http://www.amsn-project.net/wiki/Installing_Plugins_and_Skins") guide they give you the following directions - 

"*To install a skin just download it, and extract the files for the .zip file (.zip, .tar.gz, or similar). Then copy the extracted skin folder to one of the following locations:  /usr/share/amsn/skins*." 

This was all fine and dandy since I actually managed to find the right folder. However, I can't copy/paste the folder into the right place since "*The folder 'skins' cannot be copied becasue you do not have permissions to create it in the destination.*" 

Helpful hints and tips (more like directions and guides) are more the welcome. I have had Ubuntu for a couple of days now and this is my first time using linux - I just can't seem to figure these things out.

Thank you!

---

### Post by Cheesehead on 2008-08-27
1) The amsn-compatible, already-installed application is Pidgin. Try it. It's better.


2) You, *as a user*, cannot modify or write to /usr/share/amsn/skins because it's not in your home directory (/home/YOU). That's what the error message means.

3) Copy the skins to /home/YOU/.amsn/skins which can be done as user. If you can't see the folder, press CTRL+H to show hidden folders.

*Thanks, people*

---

### Post by SuperSonic4 on 2008-08-27
It also says you can copy it to /home/<name>/.amsn/skins which can be done as user

---

### Post by halitech on 2008-08-27
to expand on what Supersonic said, when you open Nautilus, press Ctrl - H on your keyboard to show your hidden folders so you can see the .amsn folder

---

