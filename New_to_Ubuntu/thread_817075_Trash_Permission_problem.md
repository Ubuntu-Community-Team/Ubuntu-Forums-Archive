---
title: "Trash Permission problem"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by 45acp on 2008-06-03
I deleted a folder to the trash bin. Now I can't empty the trash or move the folder back to the original directory. I get a permission denied error. How do I change permissions on a folder/files already in the trash bin so I can delete them?

---

### Post by _sphinx_ on 2008-06-03
What are the current permissions and also the owner of the folder in the trash?

---

### Post by 45acp on 2008-06-03
Owner (me) can read, execute but not write. I tried to change the permission through nautilus but it would not let me. I was going to try to change them from the terminal but I can't seem to find the the trash directory from the terminal.

---

### Post by unutbu on 2008-06-03
To change ownership of all things in Trash on Hardy:
```
sudo chown -R $USER:$USER ~/.local/share/Trash/
sudo chmod -R 700 ~/.local/share/Trash/

```

To change ownership of all things in Trash on pre-Hardy Ubuntu systems:
```
sudo chown -R $USER:$USER ~/.Trash
sudo chmod -R 700 ~/.Trash

```

To delete Trash on Hardy:
```
sudo rm -rf ~/.local/share/Trash/*
```

To delete Trash on pre-Hardy Ubuntu systems:
```
sudo rm -rf ~/.Trash/*
```

---

### Post by 45acp on 2008-06-03
Thank's for the prompt replies. I'll try your suggestions.

---

### Post by Miles_Prower on 2008-10-26
@unutbu:

thanks, bro. works like a charm.

---

### Post by Paul Dietrich on 2009-02-11
I brought my favorites over from Windows IE, set them up the way I want in Firefox, then deleted them.  However, there's a file called desktop.ini that, just as the original poster asked, refuses to be deleted.  I am in Hardy.  I tried the suggested commands in the Bash terminal, and they didn't work, but it is probably my fault for being new.  Please help.

sudo chown -R $USER:$USER ~/.local/share/Trash/
sudo chmod -R 700 ~/.local/share/Trash/

I have used chown before elsewhere to change ownership, so the way I interpreted $USER:$USER was to use my username, we'll say bob, and we'll say the computer name is tom, so I entered:

bob@tom:~$ chown bob ~/.local/share/Trash/

I tried different things, including bob:tom, bob:bob, etc., but no luck.  But things get more interesting...

I noticed that the following directory is empty (0 files):

/home/bob/.local/share/Trash

But when I look in my trash, there it is, desktop.ini.  Please help.  Thanks.

---

### Post by unutbu on 2009-02-11
When you type $USER in the terminal, your username gets substituted automatically.
So it should be possible to type verbatim:

```

sudo chown -R $USER:$USER ~/.local/share/Trash/
sudo chmod -R 700 ~/.local/share/Trash/
```

to gain onership and read/write/execute permissions on your Trash directory.

The command
```

chown bob ~/.local/share/Trash/
```
makes Trash owned by bob, but to make the files inside Trash owned by bob you need the "-R" flag:

```

chown -R bob ~/.local/share/Trash/
```
-R is a mnemonic for "recursive"

Also, here is a very good guide on cleaning up trash:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by drs305 on 2009-02-11
Delayed entry - ununtbu already covered it.

> **Paul Dietrich said:**
> 
sudo chown -R $USER:$USER ~/.local/share/Trash/
sudo chmod -R 700 ~/.local/share/Trash/

I have used chown before elsewhere to change ownership, so the way I interpreted $USER:$USER was to use my username, we'll say bob, and we'll say the computer name is tom, so I entered:

bob@tom:~$ chown bob ~/.local/share/Trash/


You must use the -R switch to make the chown command work on the files and subfolders. The Trash is actually located in the *files* subfolder, so the ownership change must include subfolders:
```
sudo chown **-R**
``` bob ~/.local/share/Trash

For a tutorial on finding and deleting trash, including root's trash, take a look at the linked thread in my signature line.

---

### Post by measekite on 2009-03-18
> **unutbu said:**
> To change ownership of all things in Trash on Hardy:
```
sudo chown -R $USER:$USER ~/.local/share/Trash/
sudo chmod -R 700 ~/.local/share/Trash/

```To change ownership of all things in Trash on pre-Hardy Ubuntu systems:
```
sudo chown -R $USER:$USER ~/.Trash
sudo chmod -R 700 ~/.Trash

```To delete Trash on Hardy:
```
sudo rm -rf ~/.local/share/Trash/*
```To delete Trash on pre-Hardy Ubuntu systems:
```
sudo rm -rf ~/.Trash/*
```

There is one circumstance where this will not work.

If you have a Windows NTFS partition and accessed it in Linux and then deleted a couple of folders or files you will not be able to changes those permissions.  You also cannot delete them booting to Windows because the Trash folder resides on an ext3 partition and Windows cannot see it.

I would like to delete these from the trash also.

---

### Post by drs305 on 2009-03-18
> **measekite said:**
> There is one circumstance where this will not work.

If you have a Windows NTFS partition and accessed it in Linux and then deleted a couple of folders or files you will not be able to changes those permissions.  You also cannot delete them booting to Windows because the Trash folder resides on an ext3 partition and Windows cannot see it.

I would like to delete these from the trash also.

You can open nautilus with root privileges and navigate to the trash folder. Use SHIFT-DELETE to prevent from recycling them back to the trash bin. Caution: SHIFT-DELETE is not recoverable if you make a mistake in what you are deleting.
```
gksudo nautilus
```

If you need help locating the trash bins please refer to the guide linked in my signature line.

---

### Post by presence1960 on 2009-03-18
If you are confident of your ability to not delete files you need you can bypass Trash. In your file browser under edit go to preferences then the behavior tab. At the bottom of that tab is Trash. Tick the option that says include a Delete command that bypasses Trash. When you right click, your context menu will now have the Delete command below Move To Trash.

---

### Post by measekite on 2009-03-19
> **drs305 said:**
> You can open nautilus with root privileges and navigate to the trash folder. Use SHIFT-DELETE to prevent from recycling them back to the trash bin. Caution: SHIFT-DELETE is not recoverable if you make a mistake in what you are deleting.
```
gksudo nautilus
```If you need help locating the trash bins please refer to the guide linked in my signature line.

I did what you said.  It did not work.  This is an NTFS volume.  While permissions say owner is root, Linux cannot properly display NTFS permissions.

---

### Post by drs305 on 2009-03-19
Can you perform other operations normally on this partition? I ask to learn if you have had an unclean shutdown on the ntfs partition which may be adversely affecting disk operations.

With "gksudo nautilus" you are opening a root file browser which should be able to delete anything on your ubuntu system. Permissions should not come into play since root can normally override any set permissions.

NTFS permissions are set at mounting. If you unmount the partition and mount it again with you as the owner perhaps you will be able to work with the folder.

```

sudo umount /dev/sd[COLOR="DarkRed"]XX[/COLOR]  # change sdXX to the correct device designation
sudo mount -o uid=[COLOR="DarkRed"]1000[/COLOR] /dev/sdXX -t ntfs /media/[COLOR="DarkRed"]yourmountpoint[/COLOR] # use your uid and make sure the mount point exists

```
If it won't mount insert the "force" option (  " -o force" ) to the line.

---

