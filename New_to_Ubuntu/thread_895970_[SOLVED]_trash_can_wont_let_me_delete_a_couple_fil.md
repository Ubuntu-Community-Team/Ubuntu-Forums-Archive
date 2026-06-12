---
title: "[SOLVED] trash can wont let me delete a couple files!?!"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by icecloud on 2008-08-20
ok so i followed the how to on installing World of Warcraft which told me to copy the cd's onto my desktop in a WOW_INSTALL folder well when i put the folder in the trashcan after installing the program in wine it wont delete some directx files. is there a way to force delete them?

---

### Post by linuxguymarshall on 2008-08-20
Use these commands

```
cd trash:///
```


then 

```
rm filename
```

or 

```
rm -r filename
```

or you could just reboot

---

### Post by icecloud on 2008-08-20
i've rebooted my machine and shut it down more than once...still no go..its weird. i dont want to have to format and reinstall ubunto just to erase a file...0.o

---

### Post by icecloud on 2008-08-20
and just fyi when i use the rm WOW_INSTALL command it says cannot remove "filename" no such file or directory
any ideas?

---

### Post by aktiwers on 2008-08-20
Try this:

READ THIS BEFORE YOU DO IT

I am currently not on Ubuntu so if someone can confirm that cd trash:/// goes to trash, please follow my advice below. 
But please wait until someone confirms it, or you could wipe your system clean :(

Go to your trash
```
cd trash:///
```Delete with root rights
```
sudo rm -rf *
```WARNING: Always be careful with the rm -rf command !!!!!! One step wrong and you could wipe out everything!!

---

### Post by tomzzv3 on 2008-08-20
$ sudo rm -rf ~/.local/share/Trash

---

### Post by tomzzv3 on 2008-08-20
this code above will delete all in trash with one shot

---

### Post by cybrsaylr on 2008-08-21
> **tomzzv3 said:**
> $ sudo rm -rf ~/.local/share/Trash

Thanks.
I was having the same problem and the above got rid of an empty folder that would not delete out of Trash for me.

---

