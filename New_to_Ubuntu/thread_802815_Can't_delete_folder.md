---
title: "Can't delete folder?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-05-21
Hello, I was trying to get my Brother 420CN printer working following [this]("http://ubuntuforums.org/showthread.php?t=434731") guide. Basically, in the step Install LPR Driver, where he says to turn off the printer and then do the next two steps (sudo mkdir), I forgot to turn off my printer, and then did the next two steps. I don't know if that's why it messed up, but then I turned it off and tried the next step: sudo dpkg -i ./mfc420cnlpr-1.0.2-1.i386.deb and it said 

dpkg: error processing ./mfc420cnlpr-1.0.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./mfc420cnlpr-1.0.2-1.i386.deb


so I thought it was since I had had the printer turned on for the last 2 steps, so I tried deleting the /var/spool/lpd folder (since as I understand, sudo mkdir just creates a blank folder) so that I could just re-do the sudo mkdir /var/spool/lpd and sudo mkdir /var/spool/lpd/MFC420CN steps and see if the next one worked now, but when I tried deleting the lpd folder (by moving it to the recycle bin since I couldn't use the move to trash right-click option), it gave me this message: Cannot move to trash, do you want to delete them immediately? I click delete, but the folder is still there, and I can't delete it. Why is this?

BTW i'm just trying to get my printer working so if this isn't the problem then I don't really care about deleting the folder, I just want to get it working. Thanks.

---

### Post by Watchtow3r on 2008-05-21
bump

---

### Post by Paqman on 2008-05-21
Beacause you used "sudo mkdir" the folder will be owned by root (because of the sudo bit) Therefore only root can delete it.

You can use:
```

sudo rm -r foldername

``` 
to remove it with all it's contents. If you like using graphical tools to manipulate root-owned files you can fire up Nautilus as root by using:
```

gksu nautilus

```
Remember to shut it down after you've done everything you need root access for.

---

### Post by Watchtow3r on 2008-05-21
Thanks I used the gksu nautilus tool but next time can you warn the person about the sudo rm command first? I know that it could mess up my comp so I didn't try it, but someone else might not know. I know that -r probably isnt dangerous, but the r button is close to the f key and I was afraid that I would accidentally type the -rf command.

---

### Post by spiderbatdad on 2008-05-21
-rf only means recursively force. You would still have to specify a directory...hence the /(root)
Often called the ten letter command of death sudo rm -rf /
NEVER RUN THAT COMMAND UNLESS YOU INTEND TO WIPE OUT YOUR FILE SYSTEM.

---

### Post by aktiwers on 2008-05-21
From rm man page:
> -f, --force
              ignore nonexistent files, never prompt
I think rm -rf is only really dangerous if you run it as root on /
Then you just executed a command that deletes your entire system including all connected hard drives! 

Correct me if I am wrong, but that is how I understand the rm command.

---

### Post by Helgiks on 2008-05-21
Well the "-r" part actually is what makes it "dangerous" as it is recursive deleting (the -f is force delete, doesn't ask if the file is not writable). That is why "-rf" can be dangerous especially with "sudo" in front of it. Without the recursive, it can only delete single files.

Also if you intent to delete empty files you can also use "rmdir" to be extra safe, it won't delete the folder ***_unless_*** it's empty.

---

### Post by Paqman on 2008-05-22
> **Watchtow3r said:**
> Thanks I used the gksu nautilus tool but next time can you warn the person about the sudo rm command first? I know that it could mess up my comp so I didn't try it, but someone else might not know. I know that -r probably isnt dangerous, but the r button is close to the f key and I was afraid that I would accidentally type the -rf command.

That would still only delete the folder you told it to, which is what you wanted in the first place. "sudo rm -rf /" is only "dangerous" because it starts at the root of the system and works it's way through, deleting everything. "sudo rm -rf" is a perfectly valid and useful command as long as you're careful what you feed to it.

---

### Post by Bubba64 on 2008-05-22
> **Watchtow3r said:**
> Hello, I was trying to get my Brother 420CN printer working following [this]("http://ubuntuforums.org/showthread.php?t=434731") guide. Basically, in the step Install LPR Driver, where he says to turn off the printer and then do the next two steps (sudo mkdir), I forgot to turn off my printer, and then did the next two steps. I don't know if that's why it messed up, but then I turned it off and tried the next step: sudo dpkg -i ./mfc420cnlpr-1.0.2-1.i386.deb and it said 

dpkg: error processing ./mfc420cnlpr-1.0.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./mfc420cnlpr-1.0.2-1.i386.deb


so I thought it was since I had had the printer turned on for the last 2 steps, so I tried deleting the /var/spool/lpd folder (since as I understand, sudo mkdir just creates a blank folder) so that I could just re-do the sudo mkdir /var/spool/lpd and sudo mkdir /var/spool/lpd/MFC420CN steps and see if the next one worked now, but when I tried deleting the lpd folder (by moving it to the recycle bin since I couldn't use the move to trash right-click option), it gave me this message: Cannot move to trash, do you want to delete them immediately? I click delete, but the folder is still there, and I can't delete it. Why is this?

BTW i'm just trying to get my printer working so if this isn't the problem then I don't really care about deleting the folder, I just want to get it working. Thanks.

Highlight folder then hold down shift then hit delete on your keyboard.

---

### Post by Firedrake445 on 2009-06-15
> **Paqman said:**
> Beacause you used "sudo mkdir" the folder will be owned by root (because of the sudo bit) Therefore only root can delete it.

You can use:
```

sudo rm -r foldername

``` 
to remove it with all it's contents. If you like using graphical tools to manipulate root-owned files you can fire up Nautilus as root by using:
```

gksu nautilus

```
Remember to shut it down after you've done everything you need root access for.

A noobish question but how exactly would you shut down nautilus?

---

### Post by collinp on 2009-06-15
> **Firedrake445 said:**
> A noobish question but how exactly would you shut down nautilus?

Just closing out of it works fine.

---

