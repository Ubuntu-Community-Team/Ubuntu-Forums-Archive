---
title: "[SOLVED] Trash Problems"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Ahunt on 2008-11-08
I am having an interesting problem with one of our Ubuntu 8.04 LTS equipped PCs.

Quite often when a large folder is moved from the user's home to trash and then the trash is opened and then "empty trash" is clicked, the file dialogue box appears as normal and then hangs up. The only solution I have found is rebooting the PC and then the trash can be cleared.

Suspecting there maybe a conflict somewhere I signed in as root using Alt-F2 "gksudo nautilus" and checked the root trash at root/.local/share/Trash/files and lo and behold the one folder that is the recurring problem is there as well! I tried deleting it while signed in as root and it won't delete, it just renames the folder to "folder2" along with all the files in it. Deleting those renames them "folder2.2" and "folder2.2.2" ad infinitum.

I have a feeling if I can figure out how to remove this from the root trash that the hang ups in the user account will no longer occur.

Does anyone know how to do this?

---

### Post by gandaran on 2008-11-08
> **Ahunt said:**
> I am having an interesting problem with one of our Ubuntu 8.04 LTS equipped PCs.

Quite often when a large folder is moved from the user's home to trash and then the trash is opened and then "empty trash" is clicked, the file dialogue box appears as normal and then hangs up. The only solution I have found is rebooting the PC and then the trash can be cleared.

Suspecting there maybe a conflict somewhere I signed in as root using Alt-F2 "gksudo nautilus" and checked the root trash at root/.local/share/Trash/files and lo and behold the one folder that is the recurring problem is there as well! I tried deleting it while signed in as root and it won't delete, it just renames the folder to "folder2" along with all the files in it. Deleting those renames them "folder2.2" and "folder2.2.2" ad infinitum.

I have a feeling if I can figure out how to remove this from the root trash that the hang ups in the user account will no longer occur.

Does anyone know how to do this?
are you deleting the trash or are you just trying to clean/empty the folder, this will just transfer the contents to another folder.
do you have the delete option in root nautilus context menu? if not you can add that or use the command line to delete **sudo rm -r ** *'path to file'*
have a look at home/'user'/.local/share/Trash/files too, no need to run root here.

---

### Post by Ahunt on 2008-11-08
Hi thanks for your advice - that makes good sense!

I am just thinking that emptying the folder will be enough. You are quite right that trying to delete the contents of the folder will cause more duplicates to be made!! I did manage to consolidate them all in a sub-folder called "single" within "files" to make them easier to delete.

The delete option does not appear in the Nautilus menu, so I thought I would try your suggestion of a command line delete and ran:

adamandruth@UbuntuPC:~$ sudo -rm -r root/.local/share/Trash/files/single
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

As you can see it didn't accept the command.

Any further ideas?

---

### Post by gandaran on 2008-11-08
> sudo -rm -r root/.local/share/Trash/files/single

copy/paste this
**sudo rm -r /root/.local/share/Trash/files/single**

---

### Post by Ahunt on 2008-11-08
My apologies! That was just my bad typing that missed the initial "/". Thank you for your patience!

That removed the folder just fine and it is now empty. Now I will just have to do some experiments and see if that prevents the dialogue hang-up in the user account when clearing the trash.

---

### Post by Ahunt on 2008-11-08
After a few tests everything seems to be working now - thanks for your help!

---

