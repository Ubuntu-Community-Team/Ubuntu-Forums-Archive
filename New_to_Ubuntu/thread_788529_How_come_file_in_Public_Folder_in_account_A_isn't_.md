---
title: "How come file in Public Folder in account A isn't visible in account B?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by hanzj on 2008-05-09
I'm trying to move stuff from one user account to another. I put one file "foo" into the Public folder. I then went to the other account and checked its Public folder, but it was empty.

---

### Post by Joeb454 on 2008-05-09
Can you open a terminal and run ```
cd Public
ls -l
``` and post the output.

Also the output of just ```
ls -l
``` without the first command :)

Not that is a lowercase 'L' not a number 1 ;)

---

### Post by hanzj on 2008-05-09
:~/Public$ ls -l
total 0


----------
drwx------  4 sarah sarah 4096 2008-05-08 22:57 audio
drwxr-xr-x  2 sarah sarah 4096 2008-05-09 15:18 Desktop
drwx------ 19 sarah sarah 4096 2008-05-08 22:55 documents
-rw-------  1 sarah sarah   23 2008-05-09 15:09 jpilot.log
drwx------ 13 sarah sarah 4096 2008-05-08 22:56 pictures
drwxr-xr-x  2 sarah sarah 4096 2008-05-05 12:30 Public
drwxr-xr-x  2 sarah sarah 4096 2008-05-05 12:30 Templates

---

### Post by Joeb454 on 2008-05-09
Hmm, odd looks like the permissions of your Public folder are correct :confused:

---

### Post by hanzj on 2008-05-09
I don't need to install Samba, do i?

---

### Post by Joeb454 on 2008-05-09
Sorry I've just realised that you check the OTHER public folder.

It should be noted that each account has it's **own** public folder :) This is why you can't see the files ;)

---

### Post by hanzj on 2008-05-09
Huh? What's the use of the Public Folder? Isn't it so that any user can see it?

---

### Post by Iowan on 2008-05-09
You could build a "Public" folder elsewhere... but "~" is the users home folder (which generally isn't accessible to anyone else).

But... even if the "Public" directory IS accessible by anyone, you would still need to reference the right one.  As mentioned "~" is a shortcut tho the users home directory.  In reality the directory is more like /home/user1/public.  Check with the **pwd** command to verify that "~/home" is a different path depending on whether you're logged in as user1 or user2.

---

