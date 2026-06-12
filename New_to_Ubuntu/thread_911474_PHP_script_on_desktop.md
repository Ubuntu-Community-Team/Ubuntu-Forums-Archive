---
title: "PHP script on desktop"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by danielcburton on 2008-09-05
I have searched the forums for an answer so I thought I would ask. I have a PHP script that gets my todo list from the database and outputs it. I want to output it on the gnome desktop. Geektool does this in Mac. Any ideas. 
Thanks for the help.

---

### Post by tahina on 2008-09-05
I don't know much about anything, but since no-one else is saying anything, I'll offer you my guesswork... 

php is not installed by default, so typing the following in a terminal window...```
sudo apt-get install php5
```...should take care of installing it (or you could find it in Synaptic Package Manager).

Then you might need to set the php-file to be executable by right-clicking on it, choosing properties and then the Permissions-tab. Check the checkbox.

To run the script, my guess is you'd type either ```
./name_of_script.php
``` or ```
php name_of_script.php
```

I imagine the output is either coded into the script or should be passed as an argument to the script... if it's the latter, maybe it's one of the above commands with a following space and path to either a folder or file, such as /home/username/Desktop or /home/username/Desktop/name_of_output_file.txt

If you find out the right command, you could probably create a launcher for it (right-click on the desktop and "Create Launcher...").

I have no idea if any of this is of any help. Please don't sue me if your computer bites your head off ;)

---

