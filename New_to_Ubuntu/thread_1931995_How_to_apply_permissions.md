---
title: "How to apply permissions"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by degarb on 2012-02-26
I have some 45,000 pictures in about 765 folders and sub folders.

I cannot share these file on network because when I click apply permissions to read/write/delete it doesn't work.  I select all and set an open permission.  I apply to enclosed files. But it only applies permission reliably to selected files.  It would take days to go into every folder and apply a permission to every file, so that the samba share works.

Got to be a tools that work recursively.

---

### Post by joetait on 2012-02-26
If you are happy to use the terminal then you can use the "chmod" command to change permissions. This website pretty much explains it (as would the man pages), except about the numbering. Basically, you can change the root, owners and groups permisions with numbers "xyz", as shown on the webpage. In this context, read = 4, write = 2 and executable = 1. So 3 = 2 + 1 would be write and execute, but not read.

If that doesn't make sense/needs further explanation let me know.

---

### Post by Lisiano on 2012-02-26
So that you won't apply execution onto your pictures (You need execution to view folders) when you do recursive chmod, here is how I would do this.
First open up a terminal (Ctrl+Alt+T) then navigate to the folder where everything starts (The folder you wish to share), say /home/degarb/Pictures or just ~/Pictures (~ means your Home directory)
```
cd ~/Pictures
```
Now let's give every file in Pictures Read rights to everyone
```
find -type f -exec chmod 664 '{}' \;
```
664 means that this file is Readable and Writeable by the Owner, Group member and is Readable by Anyone. If you want others to be able to Write, change it to 666 instead.
Now let's give Pictures and every sub-directory in it the same rights except also add Execute rights.
```
find -type d -exec chmod 775 '{}' \;
```
775 means the same as 664 except everyone can also execute, or in our case, view the folders. Again, to give write permissions, change this to 777.
Now we are done and you should be able to share the folder.

---

### Post by tristan3199us on 2012-02-26
just run in terminal [ sudo nautilus ]  that allows you to open your properties window as root so you can modify everything.. sometimes it changes the owner of the file to root so make sure when you do this that the user is you not root.. youll see what i mean when you open properties as root..

---

### Post by Lisiano on 2012-02-26
***_[SIZE="3"][COLOR="Red"]DO NOT RUN GUI APPLICATIONS USING SUDO.[/COLOR][/SIZE]_***
If you need to run GUI applications (Nautilus) as root, then use gksudo, like this
```
gksudo nautilus
```

Read here on why not. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by sudodus on 2012-02-26
> **Lisiano said:**
> So that you won't apply execution onto your pictures (You need execution to view folders) when you do recursive chmod, here is how I would do this.
First open up a terminal (Ctrl+Alt+T) then navigate to the folder where everything starts (The folder you wish to share), say /home/degarb/Pictures or just ~/Pictures (~ means your Home directory)
```
cd ~/Pictures
```
Now let's give every file in Pictures Read rights to everyone
```
find -type f -exec chmod 664 '{}' \;
```
664 means that this file is Readable and Writeable by the Owner, Group member and is Readable by Anyone. If you want others to be able to Write, change it to 666 instead.
Now let's give Pictures and every sub-directory in it the same rights except also add Execute rights.
```
find -type d -exec chmod 775 '{}' \;
```
775 means the same as 664 except everyone can also execute, or in our case, view the folders. Again, to give write permissions, change this to 777.
Now we are done and you should be able to share the folder.
Very good explanation :KS

---

### Post by enjoijesus94 on 2012-02-26
like stated above 

use 

> sudo nautilus

be careful with this tho

---

### Post by bab1 on 2012-02-27
> **Lisiano said:**
> So that you won't apply execution onto your pictures (You need execution to view folders) when you do recursive chmod, here is how I would do this.
First open up a terminal (Ctrl+Alt+T) then navigate to the folder where everything starts (The folder you wish to share), say /home/degarb/Pictures or just ~/Pictures (~ means your Home directory)
```
cd ~/Pictures
```
Now let's give every file in Pictures Read rights to everyone
```
find -type f -exec chmod 664 '{}' \;
```
664 means that this file is Readable and Writeable by the Owner, Group member and is Readable by Anyone. If you want others to be able to Write, change it to 666 instead.
Now let's give Pictures and every sub-directory in it the same rights except also add Execute rights.
```
find -type d -exec chmod 775 '{}' \;
```
775 means the same as 664 except everyone can also execute, or in our case, view the folders. Again, to give write permissions, change this to 777.
Now we are done and you should be able to share the folder.

I believe you can do the same thing in one line.  See```
sudo chmod -R u=rwXs,g=rX,o=rX $some_dir
```

This sets  everything below $some_dir to the following --all directories to 755 and all files to 644.  Hint the large X puts execute to dirs only.  ;-)

---

### Post by sudodus on 2012-02-27
> **bab1 said:**
> I believe you can do the same thing in one line.  See```
sudo chmod -R u=rwX[COLOR="Red"]s[/COLOR],g=rX,o=rX $some_dir
```

This sets  everything below $some_dir to the following --all directories to 755 and all files to 644.  Hint the large X puts execute to dirs only.  ;-)
Thanks for this very compact and efficient command :KS

But I think the red [COLOR="Red"]s[/COLOR] is a typing error, and suggest that it should be like this
```
sudo chmod -R u=rwX,g=rX,o=rX $some_dir
```

---

### Post by audiomick on 2012-02-27
+1 use 
```
gksudo nautilus
```
if you want to work in the file manager, and not just "sudo".

Just in case: all of the above applies if the stuff is on a Linux file system. If it is on a NTFS partition, it wont because non-Linux file systems don't support Linux permissions. I only mention this because I hammered away at a similar thing myself for a while before I realised that was what was going on. ;)

---

### Post by Lisiano on 2012-02-27
Interesting, the single line chmod seems way simpler. I need to read the man pages a bit more.

---

### Post by bab1 on 2012-02-27
> **sudodus said:**
> Thanks for this very compact and efficient command :KS

But I think the red [COLOR="Red"]s[/COLOR] is a typing error, and suggest that it should be like this
```
sudo chmod -R u=rwX,g=rX,o=rX $some_dir
```

The "red s" is the sguid bit.  chmod preserves a directory's set-user-ID and set-group-ID bits  unless you  explicitly  specify otherwise.  You can set or clear the bits with symbolic modes like u+s and g-s.   

I use this in a script to set the permissions.  The sguid forces the group on all subsequent files and directories to be the same as the parent directory.

I missed taking that out when I cut and pasted from my own script.  :-(

---

### Post by sudodus on 2012-02-27
> **bab1 said:**
> The "red s" is the sguid bit.  chmod preserves a directory's set-user-ID and set-group-ID bits  unless you  explicitly  specify otherwise.  You can set or clear the bits with symbolic modes like u+s and g-s.   

I use this in a script to set the permissions.  The sguid forces the group on all subsequent files and directories to be the same as the parent directory.

I missed taking that out when I cut and pasted from my own script.  :-(
I'm reading and learning :-)

---

