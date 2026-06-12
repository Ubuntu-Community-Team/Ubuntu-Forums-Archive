---
title: "sharing home folder with other group users"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by awatkins1971 on 2013-04-24
Is it possible to create a folder/files for a group of users, and have it visible to all in the group including root, In the GUI screen?

---

### Post by Morbius1 on 2013-04-24
It depends on how you are going to use the shared directory.

The classic Linux way of doing this sort of thing goes something like this:

[1] Create the shared folder:
```
sudo mkdir /home/Shared
```
[2] Create the new user's group:
```
sudo groupadd newgroup
```
[3] Change ownership of the shared folder to the new group:
```
sudo chown :newgroup /home/Shared
```
[4] Add your desired users to that group:
```
sudo gpasswd -a morbius newgroup
```

Now you have some decisions to make about what you want those users to be able to do:

[a] All group users can add to and delete from the folder and can read and but not write to each others files:
```
sudo chmod 0770 /home/Shared
```
[b] Same as above but only the owner of the file can delete it:
```
sudo chmod 1770 /home/Shared
```
[c] All group users can add to and delete from the folder and can read and write to each other's files:
```
sudo chmod 2770 /home/Shared
```
[d] Same as [c] except only the owner of the file can delete it:
```
sudo chmod 3770 /home/Shared
```

A "1" in the first position of the chmod command is the "sticky bit" which prevents deletion of a file to anyone other than the owner.
A "2" in the first position of the chmod command is the "setgid bit" which forces all new or copied files to have the group of that folder.
A "3" in the first position of the chmod command is the combination of the sticky (1) & setgid (+2) bits.

*** There is one caveat to all this as far as the [COLOR=#0000cd]**setgid**[/COLOR] bit is concerned. All new files created in and any files copied to that folder will in fact inherit the group of the folder. But not files moved to that folder. Moved files retain the ownership from wherever they were moved from. One way to get past this problem is to use bindfs.

*** And in turn one caveat to bindfs is that it has no concept of a "sticky bit".

---

### Post by Warren Hill on 2013-04-24
+1 

The only bit missing is what to do about users not in the group.  You obviously don't want to let them change anything but you may want to let them read what's there 

All the examples above don't give them any access but thats easy to change if you want.  For example

> 
[a] All group users can add to and delete from the folder and can read and but not write to each others files:
```
sudo chmod 0770 /home/Shared
```


keeps everyone else out, but 

```
sudo chmod 0775 /home/Shared
```

Gives people outside the group read only access

If you want other users to have read only access just change the final 0 in the chmod to a 5.  If you don't use the commands as given

---

