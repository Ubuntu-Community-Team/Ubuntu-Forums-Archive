---
title: "Removing a theme in Bash?"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by masood3 on 2014-06-21
Hello, I am new to using Ubuntu. I've been using it for about 2 or 3 weeks now. I'm trying to understand how BASH (terminal) works? I recently installed a mac theme that I thought i would look good on my OS but I dont like the look of it. 
My question is can help me remove the 'mac theme' on Ubuntu?

I ve downloaded from this web site - [http://gnome-look.org/content/show.php/Zukimac?content=165450](http://gnome-look.org/content/show.php/Zukimac?content=165450)

The code I ran in terminal was - [B]sudo apt-get install gtk2-engines-murrine gtk2-engines-pixbuf
[/B]
I'm guessing the code to remove the them would be this **rm /home/joe/gtk2-engines-murrine gtk2-engines-pixbuf**
but it doesnt work and I can't see the 'theme' folder on my 'home' - yes i did do Crtl + H; for the hidden files

So can you help me remove **gtk2-engines-murrine gtk2-engines-pixbuf from my computer** thanks!
PS I've give points if there is any reward system here

---

### Post by tgalati4 on 2014-06-21
I would try:

```
sudo apt-get remove gtk2-engines-murrine gtk2-engines-pixbuf
```

If the theme was packaged correctly, then a fallback theme should be selected in the post-installation/removal script.  If the theme was not packaged correctly, then you make get a blank screen.

tgalati4@Mint14-Extensa ~ $ apropos theme
gtk-update-icon-cache (1) - Icon theme caching utility
gtk-update-icon-cache-3.0 (1) - Icon theme caching utility
marco-theme-viewer (1) - view marco themes
**metacity-theme-viewer (1) - view metacity themes**

---

### Post by masood3 on 2014-06-21
Thanks for the reply. I did ran the code in terminal and it did remove the theme but now there is another problem.
When I go to system setting to appearance the only theme available is 'high contrast' but I did notice that it was like that before I removed the theme in terminal. I just assumed that it was the only available option when I installed the 'mac' theme. 
So now the only theme available on my OS is 'high contrast'. I do not like this theme. I really just want the default theme now.
Is there anything i can do? Thanks!

---

### Post by deadflowr on 2014-06-21
Install unity-tweak-tool.
No matter how many themes you install, the Themes setting in Appearance will only list a few already hardcoded into it.
I have no idea why Ambiance and Radiance aren't showing up for you.

---

### Post by masood3 on 2014-06-21
I forgot to mention that. I did install that from reading other forums but on the GTX+ - High contrast is only available. The other categories like Windows, Icon, and Cursor they have multiple options just GTX+ doesn't. Is there anything i can do for this?

---

### Post by deadflowr on 2014-06-21
So for fun I ran the command with the simulate flag on a 14.04 machine and this is what it told me it would have uninstalled
```
sudo apt-get -s remove gtk2-engines-murrine gtk2-engines-pixbuf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gtk2-engines-murrine gtk2-engines-pixbuf light-themes ubuntu-artwork
  ubuntu-desktop
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Remv ubuntu-desktop [1.325]
Remv ubuntu-artwork [1:14.04+14.04.20140410-0ubuntu1]
Remv light-themes [14.04+14.04.20140410-0ubuntu1]
Remv gtk2-engines-murrine [0.98.2-0ubuntu2]
Remv gtk2-engines-pixbuf [2.24.23-0ubuntu1.1]
```
I'm going to guess that you removed both light-themes and ubuntu-artwork.

---

### Post by masood3 on 2014-06-22
Alright. So far this happen in terminal

```
:~$ sudo apt-get remove gtk2-engines-murrine gtk2-engines-pixbuf light-themes ubuntu-artwork
[sudo] password for masood: 
Sorry, try again.
[sudo] password for masood: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'gtk2-engines-murrine' is not installed, so not removed
Package 'light-themes' is not installed, so not removed
Package 'ubuntu-artwork' is not installed, so not removed
Package 'gtk2-engines-pixbuf' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gimp-data gimp-help-common gimp-help-en libamd2.3.1 libbabl-0.1-0 libblas3
  libcamd2.3.1 libccolamd2.8.0 libcholmod2.1.2 libgegl-0.2-0 libgfortran3
  libgimp2.0 liblapack3 liblcms1 libmng2 libumfpack5.6.2 python3-psutil
  xsane-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```


Is there anything else to do? I appreciate the help btw

---

### Post by deadflowr on 2014-06-22
I would simply reinstall the gtk2 packages, and go from there first.
If you want to add or subtract themes, they will be in one of two places depending on how you want to use them.
Locally, per user, you would make the .themes directory in the home folder.(if it doesn't exist)
If you want the theme to be used system-wide, then they would be in /usr/share/themes.
The difference between the two is, the user folder in home is per user. But does not require any elevated privilege.
The /usr/share/themes folder can be accessed by all users, but requires higher rights to write it.

Once the themes are in either of those two folders, then the tweak tool will see them there.
And unlike packages, you can simply delete the theme using the rm command, if you so please.

---

