---
title: "uploading folder through ftp"
date: 2007-03-28
forum: Programming Talk
---

### Post by shashi123 on 2007-03-28
I have created a xampp webserver environment on my PC with ubuntu 6.06 

but when i try to upload a file in htdocs folder by  put command it does upload 

but how can i upload a folder in to htdocs 

if i try to copy and paste it in htdocs folder manualy it says permission denied 

when i try to do it with cp command it says the perticular folder is not a file

and wouldnt copy 

plz help me out with this one 


thanx in advance

---

### Post by Mr. C. on 2007-03-29
FTP does not provide recursive or directory transfers.   It can make directories, and transfer multiple files.  If you want more than this, you need a more sophisticated FTP client.  Alternatively, you can archive your files and directories into a single archive, put that archive, and then unarchive (but of course this requires access to the remote machine).

By copy/paste, do you mean in the desktop environment ?

You must have permission to copy files or folders into a directory.  The web directory is owned/group www-data; your user/group do not have permission to perform that action.  You either must change permissions on the web folder to which you are copying, add yourself to the web group, or use the command line "sudo cp ...".

It would be helpful for you to learn about Unix/Linux users, groups and permissions.  Read week 2 Notes and Homework, in the Coursework section at : [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

MrC

---

### Post by ssam on 2007-03-29
> **shashi123 said:**
> 

when i try to do it with cp command it says the perticular folder is not a file


you probably just need to add a -r flag to the copy command to tell it to recursively copy the fold (i.e. copy the contents of it)

```
cp -r afolder destination/ 
```

---

