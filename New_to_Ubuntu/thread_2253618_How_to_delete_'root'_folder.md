---
title: "How to delete 'root' folder?"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by flaymond on 2014-11-21
Hey guys, I don't know how to delete a root folder in Ubuntu....here is the file location..

/home/user/Documents 

I don't know how to delete it (I deleted the root file in the folder but not the folder itself :()

---

### Post by mastablasta on 2014-11-21
in documents?

you can run Nautilus file manager with super user rights. 

open terminal and type in 

gksu nautilus

you will be prompted for your password. enter it and you will have full control. go to the folder and delete it. just be careful not to delete anything you shouldn't.

---

### Post by ajgreeny on 2014-11-21
gksu is no longer installed by default, so you may have to install that first, though it is perhaps worth mentioning that gksu and gksudo are both deprecated and not recommended by some, though they do work if installed. It is intended, I believe, that ***application*-pkexec** will be used in future Ubuntu versions when root permissions are needed for GUI applications, but at present things do not work that way, or not easily, though I have found when searching on this that using, for example ```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY thunar
``` works the same as gksu in my Xubuntu 12.04 to open the file manager as root.
Don't assume that just because it works, I am suggesting you use this, or that it is safe to do so; I am making the comment for info only.

Just be very careful, as mentioned by mastablasta, because you could do great damage if you are not careful

---

### Post by bilkay on 2014-11-21
# cd /home/user
# sudo rm -Rf Documents

---

### Post by deadflowr on 2014-11-21
I would first try changing the ownership of the folder.
```
sudo chown -R usernamehere:typicallytheusergroupnamehere path/to/folder
```
changing the username to your username, and the user'sgroupname to whatever group your user is in, typically Ubuntu create a group with the same name as the user.
The group name can also be excluded, since the only real thing you would want to change is the owner.(Unless you have other users within a group who need special access to the folder, and at this point does not seem likely...)
Example:
```
sudo chown -R bob:bob /home/bob/Documents
```
or without the group
```
sudo chown -R bob /home/bob/Documents
```
After changing the ownership, and using the recursive option, you can now delete or remove or move or copy without needing any root access.
And all files within the folder will also be owned by you.

Of course it should be noted that I would not recommend changing ownership for anything outside of your home folder, without you knowing exactly why you would be doing so. But folders and files within your own home folder should be owned by you. 

Also, is it really the Documents folder that is root-owned?

---

### Post by ajgreeny on 2014-11-21
/home/user/Documents is one of the folders that is in the /home folder of every user by default.  I think that some DEs actually make that folder again if you delete it when you login the following time.

If it has become owned by root the first question to ask is "why? What did you do to change ownership from your user to root?"

You can, however, easily change ownership back to the user who should own it, without removing it, by using command ```
sudo chown -R user:user /home/user/Documents/
```

---

### Post by flaymond on 2014-11-21
Thanks guys for your help! I figured it using this command :


```
sudo rmdir Documents/thefolder
```

and found that gksu nautilus don't work....

Alternatively, I tried this :

To install Nautilus -

```
sudo apt-get install nautilus
```


To open it -

```
sudo nautilus .
```

It will open for you a window to browse the file you want to change or delete etc.

err...Hey, I can't delete files and folder using Nautilus because Nautilus can't view the file in the trash...(I can't delete it using normal way because it still need root permission)

    I don't know the path to trash (I tried trash:///folder but not worked)
    and sudo rmdir cannot remove a folder with contains


*PS - sudo rmdir is only worked for empty folder, not a contained folder

---

### Post by yancek on 2014-11-21
The trash directory is in:  /home/user/.local/share/
The .local file is a hidden directory.  I'm curious about how you managed to get a folder named 'root' in your /home/user/Documents directory, with root permissions.
A default install should have nautilus.  If you want to delete a file click on it to highlight it then hold the Shift+Delete keys and you will be prompted to Delete.

>  sudo rmdir is only worked for empty folder, not a contained folder 		

Correct, the rmdir command will not delete a directory unless it is empty.  That is explained in the manual pages:  man rmdir in a terminal will get that.

---

### Post by deadflowr on 2014-11-21
> **yancek said:**
> The trash directory is in:  /home/user/.local/share/
The .local file is a hidden directory.  **I'm curious about how you managed to get a folder named 'root' in your /home/user/Documents directory, with root permissions.**
A default install should have nautilus.  If you want to delete a file click on it to highlight it then hold the Shift+Delete keys and you will be prompted to Delete.



Correct, the rmdir command will not delete a directory unless it is empty.  That is explained in the manual pages:  man rmdir in a terminal will get that.

I'm not sure if the folder was actually called root, or if the folder was simply root-owned. Which is easy to do if you did something with sudo.
Something like sudo mkdir, or sudo cp, and either copied a folder/file, or made a folder using sudo.
Sometimes it's unclear to users that you do not need to use sudo to make directories or copy files and folders into your own home folder.
Not that this is what happened, but it's a common occurrence in any case...

---

### Post by flaymond on 2014-11-22
I figured it..thanks...nautilus is not a default app on ubuntu (recently version, maybe 14.10)

---

### Post by deadflowr on 2014-11-22
> **InterProg said:**
> I figured it..thanks...nautilus is not a default app on ubuntu (recently version, maybe 14.10)

Yes it is.
Though the program is called Files when you search for it.
(This is Ubuntu, and not any of the other flavors, except the gnome flavors, Ubuntu Gnome;
 Kubuntu,Xubuntu,and Lubuntu have different file managers then nautilus)

---

