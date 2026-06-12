---
title: "Unable to move files to trash after upgrade."
date: 2008-05-03
forum: New to Ubuntu
---

### Post by gofes on 2008-05-03
Hello since upgrading to 8.04 I can no longer move files to trash.

Instead I get the error

```
Unable to create wastebasket dir /home/ben/.local/share/Trash: Permission denied
```

And I can then permanently delete the file.

Looking around this forum I notice that trash has now moved to
~/.local/share/Trash

but I can not seem to navigate to here in the terminal:

```
ben@time:~/.local/share$ cd Trash
bash: cd: Trash: No such file or directory
```

Any suggestions?

---

### Post by frup on 2008-05-03
First I am going to say make sure your update completed properly

sudo apt-get update
sudo apt-get dist-upgrade

just in case something go missed out.

I would then maybe open Nautilus as root

gksudo nautilus 

This could be risky, I don't know if this could have negative implications but it might give nautilus the permissions to create the Trash dir itself.

If things still don't work navigate to ~/.local/share/ and try

mkdir Trash

I say mkdir last because I am not sure what permissions etc it might need to be and the fact that the new way in which trash is handled also relies on a trash:// area (like files) that might not get made properly by simply creating the Trash dir.

my Trash dir, seen using ls -al is 

drwx------ 4 username username 4096 2008-04-29 23:42 Trash

presumably if you made it you would need to chmod and chown and chgroup it to make it match your own username and group with single rwx permissions.

---

### Post by gofes on 2008-05-03
Looks like the upgrade worked.

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I used nautilus as root to create the folder, and it seems to be working

ls -al the Trash folder gives

```
drwxrwxrwx 4 root ben  4096 2008-05-03 13:59 .
drwxr-xr-x 6 root root 4096 2008-05-03 13:58 ..
drwx------ 3 ben  ben  4096 2008-05-03 13:59 files
drwx------ 2 ben  ben  4096 2008-05-03 13:59 info
```

So root and myself seem to have permission. Anyone know if this looks correct?

Thanks

---

### Post by Bodsda on 2008-05-03
just to be perfectly sure make a document and delete it then check the Trash folder again. but apart from that everything looks fine

---

### Post by gofes on 2008-05-03
Yep deleted files seem to be moving to trash.

Cheers everyone.

---

### Post by spimby on 2008-06-25
I also have just experienced this problem after upgrading. I performed the update steps with the same result, but it didn't fix it.  I used gksudo nautilus to create a Trash directory in  ~/.local/share/ 

I modified the permissions on the trash directory and I now have:

drwx------ 2 username username 4096 2008-06-24 23:31 .
drwxr-x--- 5 root    root    4096 2008-06-24 23:31 ..

Still, when I drag things into the trash I get:

"The file "blah blah blah" cannot be moved to the trash. 
Unable to create trash dir /home/username/.local/share/Trash: Permission denied"

Um. I'm lost..help? 	:confused:

---

### Post by vikkyhacks on 2011-09-25
Me too having the same problem , I remastered my ubuntu and everything works fine except this Permission denied problem


I tried 
sudo chmod -x * 


but it did not work ...... I think if we just have lower the privileges for it to work properly but don know how ... Any ubuntu geeks with any idea  ????

---

### Post by 3rdalbum on 2011-09-25
```
sudo rm ~/.local/share/Trash
mkdir ~/.local/share/Trash
```

Creating the trash folder as root will cause this problem. It shouldn't be created as root, because it's inside your home directory. Deleting the root-owned Trash directory and creating a user-owned one should do the trick.

---

