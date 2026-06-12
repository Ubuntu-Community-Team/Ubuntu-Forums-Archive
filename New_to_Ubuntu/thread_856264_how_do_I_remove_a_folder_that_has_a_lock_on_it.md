---
title: "how do I remove a folder that has a lock on it?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by alien8predator on 2008-07-11
How do I remove a folder with a lock on it, if I have uninstalled the program making use of that folder?

---

### Post by MasterXandrex on 2008-07-11
Define lock. If you're getting permission denied that's probably file permissions, not a locked file.

Give the output when you try.


Xan

---

### Post by appi2012 on 2008-07-11
what folder do you want to remove? Most folders that have locks on them aren't meant to be removed. But if you know that its removable, then press Alt+F2, and type:```
gksudo nautilus
``` This runs nautilus (the file manager) with higher privileges. from there you can navigate to the folder and delete it.

---

### Post by Inxsible on 2008-07-11
> **appi2012 said:**
> what folder do you want to remove? Most folders that have locks on them aren't meant to be removed. But if you know that its removable, then press Alt+F2, and type:```
gksudo nautilus
``` This runs nautilus (the file manager) with higher privileges. from there you can navigate to the folder and delete it.That is not a very good idea. You could accidentally delete some other folders wreaking havoc on your system.

Everyday, I see threads about someon accidentally deleting the panel or some other folder and such...so "accidents do happen

if you have root access it won't even ask you for a password and you wouldn't even realize it unless whatever you deleted stops working.

You should always, read ALWAYS, use the CLI and the sudo command to remove something from outside your home directory.

---

### Post by alien8predator on 2008-07-11
thanks. that worked :) I'm new to ubuntu/linux. Is there a way to get to know all these commands? without having to memerize every single one? cuz what Ive been doing up to know is just copy paste for the most part, it d be easier if I knew how to work my way in linux with the commands?

---

### Post by Inxsible on 2008-07-11
> **alien8predator said:**
> thanks. that worked :) I'm new to ubuntu/linux. Is there a way to get to know all these commands? without having to memerize every single one? cuz what Ive been doing up to know is just copy paste for the most part, it d be easier if I knew how to work my way in linux with the commands?for the very basic linux commands that will work with all distros

[www.linuxcommand.org](www.linuxcommand.org)

Distro specific commands are a different matter though and depends on the distro you are using.

---

### Post by rraj.be on 2008-07-11
If you dont want to memorize any syntax of any command you can use this command to know what you should enter with your command

man-->which gives the manual help for the command you have entered.
```

example 

man gparted
```

it will open a manual for gparted.

Mostly every command to invoke a application will be its name like gparted to gparted 

firefox for Firefox

nautils for nautils etc.

So you don't want to memorize any thing.

By time and experience you will gather many more.

---

### Post by alien8predator on 2008-07-11
I have another question off topic now. I had my sound working before. and I uninstalled something from the synaptic package manager. But it was working after I uninstalled it. I left for 10 min and now my sound is not working. is there a way to fix that?

---

### Post by Inxsible on 2008-07-11
> **alien8predator said:**
> I have another question off topic now. I had my sound working before. and I uninstalled something from the synaptic package manager. But it was working after I uninstalled it. I left for 10 min and now my sound is not working. is there a way to fix that?
Did you reboot or log out within those 10 mins. Unlike Windows when you un-install something in Linux..the packages stay around - if they are currently being used. On the next logout or restart..it cleans it up. so you may have un-installed some packages related to sound. You also don't mention what you un-installed.

Try running ```
alsamixer
```from a terminal and max out the volumes

---

### Post by MasterXandrex on 2008-07-11
> **alien8predator said:**
> thanks. that worked :) I'm new to ubuntu/linux. Is there a way to get to know all these commands? without having to memerize every single one? cuz what Ive been doing up to know is just copy paste for the most part, it d be easier if I knew how to work my way in linux with the commands?

There is a command called apropos that will help you guess at commands.

Try 
```

apropos move

```

As you continue to work with them you will learn them.


Xan

---

### Post by alien8predator on 2008-07-11
> **Inxsible said:**
> Did you reboot or log out within those 10 mins. Unlike Windows when you un-install something in Linux..the packages stay around - if they are currently being used. On the next logout or restart..it cleans it up. so you may have un-installed some packages related to sound. You also don't mention what you un-installed.

Try running ```
alsamixer
```from a terminal and max out the volumes

I can't remember what it was I thought it was part of vmware server which I had installed.

---

### Post by Inxsible on 2008-07-11
> **alien8predator said:**
> I can't remember what it was I thought it was part of vmware server which I had installed.You always wanna be careful of what you are removing and such. In any case, try out alsamixer and see if that works. if not, try rebooting or logging out.

---

### Post by alien8predator on 2008-07-11
I tried both of those, but didnt work. isnt there a way to run something. like you can restore or fix your sound drivers?? I know linux is different from windows, but I would supposed there would be something similar to that?

---

### Post by jpeddicord on 2008-07-11
> **Inxsible said:**
> That is not a very good idea. You could accidentally delete some other folders wreaking havoc on your system.

Everyday, I see threads about someon accidentally deleting the panel or some other folder and such...so "accidents do happen

if you have root access it won't even ask you for a password and you wouldn't even realize it unless whatever you deleted stops working.

You should always, read ALWAYS, use the CLI and the sudo command to remove something from outside your home directory.

I have to disagree. What if, when trying to remove a rooted folder in your home directory, you accidentally bumped the Enter key too early and removed all of /home? I know sudo prompts for a password, but not if used within the last 15 minutes. In cases like that it is actually much safer to remove using the GUI. Nautilus, by default, also stores Trash for root, so if a file was removed accidentally, it can simply be retrieved from /root/.local/share/Trash.

---

### Post by alien8predator on 2008-07-11
root trash was empty

---

### Post by Inxsible on 2008-07-11
> **jacobmp92 said:**
> I have to disagree. What if, when trying to remove a rooted folder in your home directory, you accidentally bumped the Enter key too early and removed all of /home? I know sudo prompts for a password, but not if used within the last 15 minutes. In cases like that it is actually much safer to remove using the GUI. Nautilus, by default, also stores Trash for root, so if a file was removed accidentally, it can simply be retrieved from /root/.local/share/Trash.
Even if you lost your /home - your operating system will still work - provided you weree smart enough and created a separate partition for it. You will probably lose all settings for the apps but that would be easier than a re-install.

Also it will not delete the entire home unless of course you gave the -rf flags to the remove command because the directories would not be empty and so the rm command would not delete it just like that.

CLI can be extremely powerful, if you know how to use it.

In either case - there is no fail-over mechanism for layer 8 problems ;)

---

### Post by alien8predator on 2008-07-11
that worked. thanks. should have thought of it myself, but thought there might be a different way too. From mistakes you learn :)

---

### Post by alien8predator on 2008-07-11
Ubuntu is working normal again :) but back to the locks on folders. What are the locks for on folders I created myself? for example I had these folders which I had burned on cd, which I then copied to my home, once copied they had a lock on them. how do you turn off the locks for self created folders?

---

### Post by Inxsible on 2008-07-11
> **alien8predator said:**
> Ubuntu is working normal again :) but back to the locks on folders. What are the locks for on folders I created myself? for example I had these folders which I had burned on cd, which I then copied to my home, once copied they had a lock on them. how do you turn off the locks for self created folders?When they have locks on them...can you access them or modify them?

if not, it only means that you dont have permissions on them. You probably copied them when you had root access...and therefor those folders are owned by root and not by the user (YOU)

You can use the chown command to change permissions if you are sure you want to have ownership of those folders.

---

### Post by alien8predator on 2008-07-11
I made those folders when I was logged in as user. I could try deleting them, and copying them back from my cd again?

---

### Post by Inxsible on 2008-07-11
> **alien8predator said:**
> I made those folders when I was logged in as user. I could try deleting them, and copying them back from my cd again?Or you could simply do ```
chown -R *your-username*:*your-username* /path/to/folder
```

---

### Post by asifagaria on 2010-03-29
good it work

---

