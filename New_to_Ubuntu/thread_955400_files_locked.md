---
title: "files locked"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by emilyjane on 2008-10-22
Hi, I copied some musics from a cd to my computer and now I can't delete them. They appear with the figure of a padlock over them. What is that? How can I remove it?

Thanks for any help!

---

### Post by rolnics on 2008-10-22
It sounds like you need to change the permissions of the files. Open terminal (Applications -> Accessories -> Terminal) and enter this code
```
gksudo nautilus
```
It will ask for your password enter the password you use for that user. This will open nautilus the file managers, you then can either delete them and empty your trash

If you have problems emptying it see my signature for further help.

---

### Post by Solicitous on 2008-10-22
Probably a permission problem.  Simplest way would be load Nautilus and right click on the folder you have the music file stored in and select "Properties".  

Select the "Permissions" tab and at the top it will have options for the Owner (should be your username as you copied them over). 

Change the "Folder Access" to "Create and delete files" and "File Access" to "Read and Write"

Click the "Apply permissions to enclosed files" button at the bottom (this will replicate those permissions to all files/folders in the selected folder. 

That should fix your problem.

---

### Post by AndyCooll on 2008-10-22
Agree with rolnics. They have a "lock" on them because you are not the owner of that file. And you cannot delete files you don't own.

Using "gksudo nautilus" means you are opening up a file manager session as administrator. Although in this case you simply want to delete the file, you can also use this method to re-assign permissions by right-clicking on the file and choosing properties (or is it permissions?).
If you had lots of files like this there are quicker ways using the commandline to change file permissions or delte files ...but that's for another day.

:cool:

---

### Post by Udibuntu on 2008-10-22
I had the same problem. Solved it following rolnics link.

Look here for my case - [http://ubuntuforums.org/showthread.php?t=955337](http://ubuntuforums.org/showthread.php?t=955337)

Hope this helps.

Udi

---

### Post by emilyjane on 2008-10-22
Thanks everybody, nautilus worked very well. My files are free now!

---

