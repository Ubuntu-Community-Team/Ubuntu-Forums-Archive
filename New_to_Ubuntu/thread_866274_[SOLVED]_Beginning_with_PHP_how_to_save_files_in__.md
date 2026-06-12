---
title: "[SOLVED] Beginning with PHP: how to save files in  /opt/lampp/htdocs?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by harriest on 2008-07-21
I'm going to start learning php, have installed Xampp (in Ubuntu environment). 
While trying to save files into /opt/lampp/htdocs I get message "you do not have the permissions to save the file...". Finally, I managed to save files to desired place using GNU nano in terminal. But I strongly suspect  that nano is not the best text editor for using while learning php - or is it, though? Which text editor would be recommended? I also have installed the SciTe Text Editor - but I have no idea how to save files created with it to the necessary place.
I'm sorry to say but at the very present, I do know only very little about using terminal - I'm just moving from Windows and am not familiar enough with the Linux yet.
Harri.

---

### Post by Potatoj316 on 2008-07-21
You could change the permissions of the directory to give you write permissions, in a terminal type
```
sudo chmod a+w /opt/lamp/htdocs
```
after that if it still does not work paste the output of this command
```
ls -l /opt/lamp
```

---

