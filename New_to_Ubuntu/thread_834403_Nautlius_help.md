---
title: "Nautlius help"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-06-19
The following is a post that I had earlier today.  I did what it says:
> Quote:Originally Posted by drrwhistle3  
I have made a copy of a CD and to do so I copied to a folder then copied back to a new cd. I was successful however when I dragged the new folder to trash and the tried to empty the trash it won't delete. The permissions are read and execute on all the files but I can not change to read write execute. Nor will they delete. Is there a way to do it?

Open a terminal and type:


Code:
gksu nautilus

Then you will be able to delete the file in the nautilus window that pops up as it will have root privelages 
__________________
You can see right through Windows 

But then, when I type the gksu nautilus it seems to open the Nautilus window but when I select the Trash folder the screen fades and I have to "force quit" Nautilus.  Then I noticed that in termnial the following (I have to type because I am using a different computer the other is not responding at all):
> ~$ gksu nautilus
Initializing nautilus - share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nautilus:6324): WARNING **: Unable to add monitor: Operation not supported

Nautilus freezes, terminsal freezes firefox froze
I have had to reboot.  HOWEVER, this time something else happened as I was setting up this computer to type this message, it unfroze (or it seems to be fine).  Although I was able to "force quit" Nautilus before the whole thing froze so that is not open.

WHY???  Is there anything I can do to fix? I Just want to delete a folder.

---

### Post by Darkade on 2008-06-19
open a synaptic and search for
samba
install it.

I dunno if it will work but your error says that you don't have installed samba (a sharing folder library). Nautilus is trying to use it, but you don't have it

---

### Post by tjwoosta on 2008-06-19
i had problems deleting items before (the solution is to manually delete the files from your trash folder with the terminal)

first navigate to trash directory
```
cd ~/.Trash
```

then force delete the file like this
```
sudo rm -f filename
```(Only if its a file)if its a directory you need to do sudo rm -rf filename

-r means recursively (as in it will remove every file or directory within the specified directory) 
and -f means force the deletion regardless of any errors

---

### Post by drrwhistle3 on 2008-06-20
Ok, I installed samba with synaptic and tried again, the following is what terminal did before it froze the computer for an hour.  Then unfroze but Nautilus closed and did nothing.
> owner@owner-desktop:~$ gksu nautilus
Initializing nautilus-share extension

** (nautilus:6573): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSowner@owner-desktop:~$

Any ideas?

I won't try to delete the files through terminal yet.  I would like to see first if this is a bug in NAutilus or just somthing I'm doing.,

---

### Post by tjwoosta on 2008-06-20
yea thats probably a good idea, it sounds to me that you have some bigger problems than your files not deleting

---

### Post by tjwoosta on 2008-06-20
you may need to reinstall nautilus (for some odd reason)

Im not really sure on how to do that though


does anybody know how to reinstall nautilus safely?



EDIT: this should help you get things working properly
[http://ubuntuforums.org/showthread.php?t=644877]("http://ubuntuforums.org/showthread.php?t=644877")

---

### Post by Darkade on 2008-06-20
your second error really beats me, I agree that a reinstall might solve this, but it's a really weird thing the error you have.

> **tjwoosta said:**
> 
does anybody know how to reinstall nautilus safely?

It's quite safe to reinstall it "marking for reinstall" in synaptic. I've done it.

---

### Post by tjwoosta on 2008-06-21
> It's quite safe to reinstall it "marking for reinstall" in synaptic. I've done it. 

nice,
 i figured as much,i just didn't want to advise someone to do something that i wasn't sure about

---

### Post by drrwhistle3 on 2008-06-23
Reinstall did not work.  I got the same error.  Any other recommendations?  Please!!

---

### Post by vanadium on 2008-06-23
Congratulations, Absolute Beginner, you discovered a bug! Indeed I can reproduce the behaviour you see. Nautilus is actively using the processor and slowly using all memory. In the terminal where you launched nautilus, press Ctrl+z then type "pkill nautilus" to kill the proces.

You just need to avoid doing this again. Instead, you will be able to navigate to the hidden Trash folder in your home directory. Load nautilus again (gksu nautilus), now navigate to your home directory (File System - home - your_login. Then press Ctrl+h to view Hidden folders. Then continue navigation to .local/share/Trash. Delete the file both in the "Files" directory, and delete the corresponding .trashinfo file in the "info" directory.

A warning: only load a "gksudo nautilus" if you know well what you want to do. Close the nautilus windows as soon as you are done.

---

### Post by drrwhistle3 on 2008-06-23
AH, but my computer is almost completely non-responsive for the past 1/2 hr.  Curser barely moves.  Terminal is closed.  Is there a way to restart this and then proceed??  I tried Ctrl-Alt Delete but nothing.  What next?

---

### Post by Darkade on 2008-06-23
try CTRL+ALT+F1 this will take you to a text mode console. Log in and write
```

sudo halt

```

this will reboot your PC, then just follow vanadium's advice.

---

### Post by vanadium on 2008-06-23
> **drrwhistle3 said:**
> AH, but my computer is almost completely non-responsive for the past 1/2 hr.  Curser barely moves.  Terminal is closed.  Is there a way to restart this and then proceed??  I tried Ctrl-Alt Delete but nothing.  What next?

That probably happens if you waited longer: the process is increasingly taking ram and once your system begins to swap memory to disk, it becomes very unresponsive. And the extent of this also depends on the specs of your system.

---

