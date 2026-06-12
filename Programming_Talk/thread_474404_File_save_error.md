---
title: "File save error"
date: 2007-06-15
forum: Programming Talk
---

### Post by tagu on 2007-06-15
HI all, I'm programming with php, I installed apache server,mysql and php. I can see the "It works" page from localhost. But whe I try to save or edit I get ;

Could not write file:

"/var/www/apache2-default/index.html"

Waiting from u to response, thanks...

---

### Post by meatpan on 2007-06-15
Probably a silly question, but have you verified that you have write permissions on the specified file?

There are several ways to see if you have write permissions.  I recommend running the command 'ls -l'
 in the directory /var/www/apache2-default.  

Output of the command might look like:

```

total 24
-rw-r--r-- 1 root root 2205 2005-12-14 08:25 index.html

```

In this case, the file is only writable by the root user.   One possible workaround is to save your index.html file in your home directory, and then run 'sudo cp index.html /var/www/apache2-default' to copy (and essentially overwrite) then file as root.

---

### Post by zoobave on 2007-06-15
Use "chmod" command to give the write permission.

---

### Post by tagu on 2007-06-15
I have fix the my silly problem with sudo chmod 777 /var/www/apache2-default command

Thanks all ;)

---

### Post by newagelink on 2008-07-09
> **zoobave said:**
> Use "chmod" command to give the write permission.[COLOR="Indigo"]The chmod manual is too complicated; I don't know if these read/write permissions are only for me, or if they apply to online viewers, once a file is hosted on a web server. Shouldn't I already be able to write this file? (See attached image.) Aren't I a member of the "others", who have permission to read and write?[/COLOR]

---

### Post by mssever on 2008-07-09
> **newagelink said:**
> [COLOR=Indigo]The chmod manual is too complicated; I don't know if these read/write permissions are only for me, or if they apply to online viewers, once a file is hosted on a web server. Shouldn't I already be able to write this file? (See attached image.) Aren't I a member of the "others", who have permission to read and write?[/COLOR]
Yes, you're presumably a member of "others" and have read/write permission. But such permissions as in your screenshot (777 permissions) are dangerous, because if someone exploits a vulnerability in your server, they can change the file, too. There are few reasons to use 777 permissions. The solution by tagu above is bad advice for the reason I just mentioned.

A better solution is to make yourself the owner of everything in the webroot, then set permissions to 644 for files and 755 for directories. If multiple people need write access, add a group for that purpose, add the people who need write access to the group, chgrp the files to that group, and chmod g+w the files.

The web server should NOT have write access to any files in the web root. There might be situations where your app wants to edit some files, but think twice and three times before granting write access. My brother had his site destroyed because of the server having write access and a script kiddie who thought it would be fun to overwrite other people's files.

---

### Post by newagelink on 2008-07-09
[COLOR="Indigo"]In the terminal I ran ```
sudo nautilus
``` and navigated to "/media/sda1/Documents and Settings/Owner/My Documents/My Webs/dan/". I tried editing the folder's permissions (i.e. dan/pages), but it will not let me change them. Owner is 'root', cannot change to 'daniel'. Group is 'root', cannot change to 'daniel'. Folder access for Others is set to 'Create and delete files', it won't let me change it to "Access files" (although I don't know what the difference is between that and 'List files only'.

Must I use chmod? Why can't I edit them from nautilus as root?

To clarify, I don't know much of anything about what goes on at my web server. I basically edit the files at "/media/sda1/Documents and Settings/Owner/My Documents/My Webs/dan" from my linux partition at "/home/daniel", then upload them.[/COLOR]

---

### Post by mssever on 2008-07-09
> **newagelink said:**
> [COLOR=Indigo]In the terminal I ran ```
sudo nautilus
``` and navigated to "/media/sda1/Documents and Settings/Owner/My Documents/My Webs/dan/". I tried editing the folder's permissions (i.e. dan/pages), but it will not let me change them. Owner is 'root', cannot change to 'daniel'. Group is 'root', cannot change to 'daniel'. Folder access for Others is set to 'Create and delete files', it won't let me change it to "Access files" (although I don't know what the difference is between that and 'List files only'.

Must I use chmod? Why can't I edit them from nautilus as root?

To clarify, I don't know much of anything about what goes on at my web server. I basically edit the files at "/media/sda1/Documents and Settings/Owner/My Documents/My Webs/dan" from my linux partition at "/home/daniel", then upload them.[/COLOR]
I'm no nautilus expert. Maybe you can do it from nautilus, maybe you can't. It should be possible, but that doesn't necessarily mean anything. IMHO, it's just easier to do that kind of thing from the terminal. Because the shell is a programming language in its own right, once you learn your way around you can automate stuff easily, without even leaving the shell.

---

