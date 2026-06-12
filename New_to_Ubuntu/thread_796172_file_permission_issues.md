---
title: "file permission issues"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2008-05-16
I have an issue with 8.04 regarding file permissions. If i copy a folder from a cd to my /home directory the file appears as read only with a little lock symbol above the icon...Why would files that i copy to my /home directory from a cd not have read/write permissions? 
Also, some files in my Trash/Garbage Bin i cannot delete. It says i do not have permission to delete files from my own Trash :( What is going on??

---

### Post by UnWarierMage224 on 2008-05-16
those files in the trash were created by root, and so have root's permissions. 
You, not being root, can't delete those files. 

Easy fix, however. 

fire up a terminal and type 

```

gksudo nautilus

```

This will give you the file browser with root permissions. Then navigate to your trash folder in your user/.local/share/Trash and delete the files (hit Ctrl+H to show hidden folders) 

As for the CD thing, I'm not sure about that one.... Maybe they got copied down as root? (speculation) 

Hope this helps, 

-'Mage

---

### Post by ibutho on 2008-05-16
Could be that most discs come with read only permissions. You should be able to add the write flag using chmod or nautilus. As for your trash can, what are the permissions and ownership of the files in there. Run "ls -l ~/.local/share/Trash/files" and post back the output.

---

### Post by e1ektrob0y on 2008-05-16
> **UnWarierMage224 said:**
> 
navigate to your trash folder in your user/.local/share/Trash and delete the files 



-'Mage

that directory doesn't exist i can find usr/local/share but no /Trash or /.local. Are you sure thats right?

---

### Post by e1ektrob0y on 2008-05-16
```
ls -l ~/.local/share/Trash/files
total 8
drwxr-xr-x 3 ben ben 4096 2008-04-30 23:05 internode-applet-1.5
drwxr-xr-x 4 ben ben 4096 2008-05-11 00:15 windowsxp

```

---

### Post by ibutho on 2008-05-16
Seems like the files are owned by the user "ben". If you are logged in as ben try
```
cd ~/.local/share/Trash/files
rm -rf internode-applet-1.5 windowsxp

```
Can you delete the files? If that does not work try running the second command as 
```
sudo rm -rf internode-applet-1.5 windowsxp
```
If you are ben and can't delete those files, it could be an indication of a problem with your user account.

Note: be careful when using "rm -rf" because any mistake can result in permanent loss of data.

---

### Post by e1ektrob0y on 2008-05-16
Thanks, that worked fine. What i wonder is why i lost my read/write permissions over those files when they were obviously owned by me to begin with. Could have something to do with why when i copy something across from a cd to my /home directory, it comes with read only permissions, even though it is owned by me :(

---

