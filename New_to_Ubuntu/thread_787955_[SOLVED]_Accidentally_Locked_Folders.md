---
title: "[SOLVED] Accidentally Locked Folders"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-09
Is there a way to unlock folders in the /etc directory? I did this command:

```
sudo chown <username> /etc
```

And now all the directorys and files in that folder has a lock on it. Any help? Also, I am trying to change the permissions of one folder in the /etc directory, but it says I am not the owner. I want to delete that one folder. Any help?

---

### Post by brigux on 2008-05-09
su <username>
chown root /etc

---

### Post by UnknownFear on 2008-05-09
I dont think it worked.

```
dan@dan-desktop:~$ su dan
Password: 
dan@dan-desktop:~$ chown root /etc
chown: changing ownership of `/etc': Operation not permitted
dan@dan-desktop:~$
```

I still have locks on my folders.

---

### Post by MonkeyRail on 2008-05-09
I had a similar problem with music files in my home directory.
I managed to sort it be right clicking on the folder, then Properties, clicked on the Permissions tab and changed it that way.

I could change multiple folders at the same time by using ctrl-a then going right clicking on the folders.

---

### Post by Monicker on 2008-05-09
> **UnknownFear said:**
> I dont think it worked.

```
dan@dan-desktop:~$ su dan
Password: 
dan@dan-desktop:~$ chown root /etc
chown: changing ownership of `/etc': Operation not permitted
dan@dan-desktop:~$
```

I still have locks on my folders.

```
sudo chown root /etc
```

---

### Post by mlentink on 2008-05-09
afaik....

```
su
```  means "switch user"
```
sudo
``` means "as super user do...."
Different things...
```
su
``` without an argument will switch you to root. But in Ubuntu, root is diabled by default, so it will have null result. 
You could do ```
sudo su
```by the way, which would effectively make you root for the current terminal session or until you exit

Again, I'm no expert, but this is my understanding

---

### Post by UnknownFear on 2008-05-09
> **Monicker said:**
> ```
sudo chown root /etc
```

That worked!! I now don't have any locks on the folders!! Now, I tried deleting the folder (vmware) but it said i dont have the permission to delete it :S I went into the folder properties and on the Permissions tab, everything is greyed out and it says i am not the owner. Some help? All I want to do is delete the vmware folder so I can reinstall vmware-server again.

---

### Post by tacutu on 2008-05-09
sudo rm -rf /etc/vmware

But, really big WARNING: do not play with file permissions in system folders (like /etc). You can badly damage your system.

---

### Post by UnknownFear on 2008-05-09
> **tacutu said:**
> sudo rm -rf /etc/vmware

But, really big WARNING: do not play with file permissions in system folders (like /etc). You can badly damage your system.

Believe me, I won't I just wanted to increase the GRUB timeout to 30 sec. That was all I needed.

---

### Post by wootah on 2008-05-09
You could always check the permissions of the folder at terminal with:
```
ls -lsad folder_name
```

---

### Post by terry_gardener on 2008-05-09
to increase the grub timeout the best program to use if you dont want to edit config files manually is startup-manager it is in the repros. 

you can also change the default os easily

---

### Post by tacutu on 2008-05-09
to increase the grub timeout, just do:

```
sudo gedit /boot/grub/menu.lst
```

no need to mess w/ permissions!

And I thought you wanted to delete /etc/vmware, not mess with grub?

---

### Post by svenofix on 2008-05-10
I seem to be having a problem similar to the one mentioned in the previous
posts. Yesterday I got all my backed up music that I had burned to CD's (I
used Windows and burnt the music as data not as an audio CD) back into 
ubuntu (not using any media player, just click n drag n drop). However, I
noticed after I had done that, that all the music folders were locked, nor
can I play any of them as far as I know. Now I would like to delete those
folders and try again, but find I can't as I get these error messages:

```

[FONT="Courier New"]
Cannot move file to trash, do you want to delete immediately?
   The file "'folder/audio'" cannot be moved to trash

     >  Show more information
       Unable to trash file: Permission Denied

Cancel     Skip All    Skip    Delete All    Delete
[/FONT]

```

That's my first error message, I click delete all and get:

```

[FONT="Courier New"]
  Error while deleting.
There was an error deleting desktop.ini

    >  Show more details
      Error removing file: Permission Denied

Cancel    Skip All    Skip

[/FONT]

```

Any help anyone?

---

### Post by MikeConklin on 2011-09-30
1) open terminal
2) type gksudo nautilus
3) navigate to the folder that is locked ( the lock icon does not show in nautilus )
4) right click on that folder 
5) open permissions tab
6) change permission to your name
7) the folder is now unlocked

---

