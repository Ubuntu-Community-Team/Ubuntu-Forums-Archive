---
title: "What should the default permissions for your home folder be?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Roasted on 2008-11-11
Without thinking I ran sudo chmod 777 on my home directory. Now I get a message every time I boot up.

```
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
```

So, I thought, oh! okay! chmod 644 to my home directory!

Nah, doesn't work. I lose my background and everything else. So I chmod'd back to 777 and everything is back, but I'd like it to be how it was before.

What should my home directory's permissions be?

---

### Post by ghost_ryder35 on 2008-11-11
i'd change it to 770
you should be able to read write and execute, and any body that belongs to your group should be as well.  all others should not be able to see anything in your folder (my personal opinion)

---

### Post by mr.v. on 2008-11-11
> **Roasted said:**
> What should my home directory's permissions be?

2 things. First you can create a new user and see what it's permissions are on files just to be sure there isn't a special file permission that is required by ubuntu for something.

second, the last octal shouldn't be 7. You usually don't want other users being able to see your files let alone write and execute them. Your first one should definitely be 7 (you should be able to read/write/execute from the directory). The group (mid octal) is a bit more up in the air depending on if you want the group being able to see the home directory. If you're the only user on your computer with no guest account this is almost a non-issue and 777 is fine.

---

### Post by tahitiwibble on 2008-11-11
This should do it for you. [http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

---

### Post by Roasted on 2008-11-11
Someone in the Ubuntu chat thought the default was 750, which... my train of thought with following your explaination kind of makes sense for 750. 

But, I have a question. I granted 750 to my home directory. Then I logged onto another user on my computer. I have 4 users on this computer, but only I use it. Reasoning is, for Samba to work, I need to have the Samba users added as local users to my computer... so I have my two brothers + mom added as users even though they don't touch the computer.

I logged into their accounts and noticed a few things. In their accounts, I can't even open my home directory. Yet they can open each other's directories. So how is mine different? I right clicked on their directories and compared the permissions tab to my permissions tab. Everything was identical.

I can't see where I can see the number permissions assigned... like I can see "access, read write, etc." but I can't see "750, 777" or whatever. So I don't know the EXACT permissions they have offhand.

But nonetheless, I'm confused as to why the directories now differ with me using 750 on my own home directory.

EDIT - I just found out the default home directory permissions are 755. I logged onto the other accounts and sure enough 755 seems right. Now the system reacts on all accounts the way they should. Good stuff!

---

### Post by mr.v. on 2008-11-12
> **Roasted said:**
> 
I can't see where I can see the number permissions assigned... like I can see "access, read write, etc." but I can't see "750, 777" or whatever. So I don't know the EXACT permissions they have offhand.

But nonetheless, I'm confused as to why the directories now differ with me using 750 on my own home directory.

EDIT - I just found out the default home directory permissions are 755. I logged onto the other accounts and sure enough 755 seems right. Now the system reacts on all accounts the way they should. Good stuff!

The numbered permissions are the octal setting. When you do an
```
 ls -l 
```
you see the permissions read write execute
The octals are 3 octal bits per file that are a translation of what the read/write permissions are for a file.

For instance. A file with a 755 means the file is rwxr-xr-x 7 is the number for full permission, 4 is for read, 1 is for execute and 2 is for write. You add those up to get the permissions. read and write is 4 + 1 = 5  read write execute is 4 + 2 + 1 = 7. You can read all about them if you google "chmod octal"

---

### Post by tuxulin on 2008-11-12
the /home folder and all user account folders within it have a default permission of 755

---

### Post by Paqman on 2008-11-12
Yep, 755 for the home folder, except for .dmrc, which needs to be 644.

So:
```

chmod -R 755 /home/username
chmod 644 /home/username/.dmrc

```
Should sort out all your problems.

---

