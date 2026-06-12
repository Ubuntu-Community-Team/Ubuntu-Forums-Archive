---
title: "Can I make new files in a folder inherit a certain permission set?"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by wlraider70 on 2013-10-04
Basically: I have a folder "folder1" I often save files "file1" into in. However the default permissions of the file are not the same as the folder.
I want to make the files default to the permissions of the folder.




More info: Some files get added to "folder1" by a script. I have no idea how to alter a script though I'm guessing its setting the permissions. 


THANKS

---

### Post by oldfred on 2013-10-04
I have seen this as a recommendation. But never run this on a system partition or folder. Especially with the -R as that is recursive and all lower level folders get changed. If accidentally run at root, you end up having to reinstall as resetting all the system permissions is just about impossible. So make sure you have changed to your folder.

 sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

---

### Post by steeldriver on 2013-10-04
You probably don't want files to inherit the exact permissions of the folder - folders (directories) have the execute permission bit set (in order to be openable).

If you are creating the files using a script, then probably the easiest way to get the permissions that you want is to set the umask value within your script. The umask expresses the complement of the permissions you want to have - the default umask is 0002 which removes write permissions from 'other' (equivalent to octal value 664 for plain files):
```

$ umask -p
umask 0002
$ 
$ touch testfile1 && ls -l testfile1
-rw-rw-r-- 1 steeldriver steeldriver 0 Oct  4 10:45 testfile1

```

To remove write permissions from 'group' as well as 'other' you can set umask = 0022

```

$ umask 0022
$ touch testfile2 && ls -l testfile2
-rw-r--r-- 1 steeldriver steeldriver 0 Oct  4 10:46 testfile2

```

Hope this helps - if you really *do* want to base the file permissions on those of the parent directory for some reason, you could use 'stat' to get the octal permissions of the parent and base the new umask on that.

---

### Post by grahammechanical on 2013-10-04
You can do this using the File Manager. Right click the folder and select permissions and there will be a clickable panel called Change Permissions for Enclosed files. At least this is so on 13.10. You can set the permissions of files to Read-Only or Read and Write. And the permissions of folders in the folder to None, List files only, Access files and Create and delete files.

You will need to run File Manager with administrator privileges. So, run

```
sudo gksudo nautilus
```

in 13.04 onwards we need to install gksu in order to do that.

```
sudo apt-get install gksu
```

Regards.

---

