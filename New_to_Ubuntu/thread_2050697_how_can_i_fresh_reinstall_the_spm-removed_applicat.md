---
title: "how can i fresh reinstall the spm-removed applications avoiding old settings!"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-08-31
why is it so that every time i completely remove an application through SPM and reinstall it with the expectation that it would be installed fresh again but the same old setting and problems persist at all! this is troublesome in ubuntu so far i have realized! the completely fresh installation; is it not possible in ubuntu???

---

### Post by mattpatey on 2012-08-31
Program settings are usually stored in your home folder in a directory starting with a ".". You can see them by using ls -a (or CTRL-H in nautilus). For example firefox stores all user settings in ~/.mozilla/

I don't know what program you are talking about, but deleting/moving the settings files is all you probably need to do. Uninstalling / reinstalling the program will just remove and then re-add the same packages resulting in no net change in most cases.

---

### Post by tojonukokhadush on 2012-08-31
okay i have a screenshot here!

so i cannot every time locate where these damn ;-) setting files are stored!! like for example i cannot find here for rhythmbox nor for particular openoffice calc! so when these were re-installed they would be carrying the same flaws again! like in my case in rhythmbox pause button was not being pressed; i needed to close the whole application as a whole. and in case of openoffice calc it get hang everytime i try to export the sheet as pdf!!

now i want to fresh reinstall them! how can i find the setting files for them!

and also where can i get info about-     .* files that we get to see in home folders! like i need to know to handle them safely!!

---

### Post by robtygart on 2012-08-31
What program are you trying to fix? 

If you want to remove it you can use the "purge" command

```
sudo apt-get install purge "program name"
```

from: "apt-get" manual entry

> purge
           purge is identical to remove except that packages are removed and purged (any configuration files are deleted
           too).


for more info type ```
man apt-get
```

---

### Post by BDNiner on 2012-08-31
The ./*folders* are hidden folders. You need to turn on the option to "view hidden files"

---

### Post by tojonukokhadush on 2012-08-31
m trying to reinstall rhythmbox and openoffice calc! but i do not want the problem that existed with them earlier to return!  and the complete removal i.e purge even did not help!

no i can't find where the setting files for these apps are located! and i have shown all ".filename"  folders in my home in the screenshot in above post! 

somebody please help!

---

### Post by mattpatey on 2012-08-31
On my system, rhythmbox seems to keep its settings in ~/.local/share/rhythmbox and libreoffice in ~/.config/libreoffice

---

### Post by Linux_junkie on 2012-08-31
On the screen image you posted, there should be a folder called .openoffice.org this is where the config files are stored for all Open Office apps including Calc.  Highlight this folder and delete it.

The rhythmbox  folder I believe is in either .config folder or .local folder locate it and delete it.

---

### Post by tojonukokhadush on 2012-08-31
okay thankyou! guess .xml file in rhythmbox is the one i am searching. but for openoffice its complicated i guess! it keeps on going inside ;-) anyway thanks for your help!

---

