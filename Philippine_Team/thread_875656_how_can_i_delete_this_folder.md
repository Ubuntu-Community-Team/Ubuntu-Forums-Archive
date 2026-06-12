---
title: "how can i delete this folder?"
date: 2008-07-31
forum: Philippine Team
---

### Post by killer_d76 on 2008-07-31
i tried adding RealPlayer on my set-up by following this procedure from this link [http://amyslab.wordpress.com/2008/07/13/installing-realplayer-in-ubuntu/]("http://amyslab.wordpress.com/2008/07/13/installing-realplayer-in-ubuntu/") 

here's the procedure that i just did

```
1. Download RealPlayer

    * Go to http://www.real.com/linux and download the RealPlayer11Gold.bin file.

2. Make RealPlayer11Gold.bin file into an executable file.

    * Open a Terminal window.
    * Navigate to the directory that contains the bin file.  For example:
          o

            cd download

    * Make the bin file into an executable file.
          o

            chmod +x RealPlayer11Gold.bin

3. Run the bin file

    *

      sudo ./RealPlayer11Gold.bin

    * Accept the default values by pressing the Enter key.
    * By default, RealPlayer will be installed in /opt/real/RealPlayer

4. Setup RealPlayer

    * In the “Application” menu, select “Sounds & Video | RealPlayer 11&#8243;
    * It will display the RealPlayer Setup Assistant.  Just follow the setup instructions.

```

i created a folder that i called/named as "download" folder inside "Home Folder" and i have successfully installed it, but was not happy with it, so i what i did is that i just deleted the "download" folder from the "Home Folder" which it did, but when i tried to delete it from the Trash, it goes back in the trash folder again!, and i get this error 

[[IMG]http://img301.imageshack.us/img301/5333/screenshotrl4.th.png[/IMG]](http://img301.imageshack.us/my.php?image=screenshotrl4.png)

could you please help me remove this :(
thanks in advance!

---

### Post by brujoand on 2008-07-31
To delete something you do not have permission to delete you either have to reduce permissionlevel on that file or increase your permissions.

To decrease permissions on the fil:
sudo chmod 755 filename  (add "-r" if it's a folder, to apply to all files within)
then delete normally

To increase your permissions simply do a
sudo rm filename (add "-r" if it's a folder)

---

### Post by killer_d76 on 2008-07-31
thanks GriimmVarg.. but could you guide me on how to this.. i have the folder in the "Trash" already but i can't delete it permanently, and it doesn't want to move out of the Trash bu make a copy of itself if i try to remove it from the "Trash".

---

### Post by brujoand on 2008-07-31
open terminal (Applications --> Asseccories --> Terminal)

change directory to trash usually:

cd /home/yourusernamehere/.Trash 

Then, if the file you want to delete is name Bin and its a folder do this:

sudo rm -r Bin 

then it prompts for your password, type it in, and hit enter. You should be done.

---

### Post by killer_d76 on 2008-07-31
thanks GrimmVarg, i have already deleted it from the trash.. using sudo rm but i found out that it is located inside .local/share/Trash wherein i didn't need to type in the password.. is it ok if i deleted "files" and "info" folders inside the trash folder since it contained the folders i wish to delete?

---

### Post by brujoand on 2008-07-31
Well, I'm not 100% on this, but if my suspicions be correct, everything within the Trash folder, info and files that is, is auto-generated if they dont exist, so it probably safe to delete them.

heres a thread that explains most of this

[http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html](http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html)

---

