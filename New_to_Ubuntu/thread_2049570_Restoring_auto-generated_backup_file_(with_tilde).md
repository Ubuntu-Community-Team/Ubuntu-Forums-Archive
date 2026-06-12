---
title: "Restoring auto-generated backup file (with tilde)"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by JauntyJack on 2012-08-28
I tried to edit a .hosts file, but evidently messed it up. The .hosts file is now blank, zero bytes. However, the editor seems to have created a backup. It's called .hosts(with tilde after), 289 bytes (so, not blank). 

Trouble is, I can't find a restore command, or a way to open it and re-save it as .hosts. 

This is probably simple in linux, but searching Google and the forums turns up nothing about how to do this. Can anyone point me at the right resources?

---

### Post by drmrgd on 2012-08-28
You just need to delete the wrong file and rename the file without the tilde in your file manager.  If you prefer to do it with the terminal:

```
sudo mv .hosts~ .hosts #or whatever your files are actually called
```

That will rename the .hosts~ file to .hosts, replacing the empty one in the process.

Also, it's best to make copies of important files before you mess with them just in case you don't get a backup (not all editors are configured to make one by default!).

---

### Post by JauntyJack on 2012-08-28
> **drmrgd said:**
> You just need to delete the wrong file and rename the file without the tilde in your file manager.  If you prefer to do it with the terminal:

```
sudo mv .hosts~ .hosts #or whatever your files are actually called
```That will rename the .hosts~ file to .hosts, replacing the empty one in the process.

Also, it's best to make copies of important files before you mess with them just in case you don't get a backup (not all editors are configured to make one by default!).

Thanks! That's helpful and useful. A couple of follow-up questions:

1. What's the command for making a copy of a file? (I can right-click/copy the backup file, but not right-click/paste - it's grayed out.)

2. This backup file seems in an odd format. If I try to open it, I get: "Could not display "/usr/share/vlc/lua/http/.hosts~". There is no application installed for backup file files." Are you sure it can just be renamed? Just double checking.

3. Before I use that mv command, I imagine I have to get into the right folder first, correct? Would I use this command?   cd /usr/share/vlc/lua/http/

Thanks in advance!

---

### Post by JauntyJack on 2012-08-28
> **JauntyJack said:**
> Thanks! That's helpful and useful. A couple of follow-up questions:

1. What's the command for making a copy of a file? (I can right-click/copy the backup file, but not right-click/paste - it's grayed out.)

2. This backup file seems in an odd format. If I try to open it, I get: "Could not display "/usr/share/vlc/lua/http/.hosts~". There is no application installed for backup file files." Are you sure it can just be renamed? Just double checking.

3. Before I use that mv command, I imagine I have to get into the right folder first, correct? Would I use this command?   cd /usr/share/vlc/lua/http/

Thanks in advance!

Ok, that worked! Thanks again!

---

### Post by drmrgd on 2012-08-29
> **JauntyJack said:**
> Ok, that worked! Thanks again!

Glad you got it working!  

Just as a follow up to your first question, the paste command is likely greyed out because you need admin rights to write to the folder where that is located.  If you want to use a file manager (I'm assuming Nautilus here), you need to launch it with admin rights, which is easily done from terminal:

```
gksudo nautilus
```

Alternatively, if you wish to strictly work from the terminal, you just need to use the 'cp' command with 'sudo':

```
sudo cp .hosts .hosts.bak
```

---

