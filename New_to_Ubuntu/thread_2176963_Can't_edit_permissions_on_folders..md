---
title: "Can't edit permissions on folders."
date: 2013-09-26
forum: New to Ubuntu
---

### Post by julia3 on 2013-09-26
I go to computer and for example try to edit permissions on var. It says:
You are not the owner so you can not change these permissions. 
I am the owner. So why can't I change the permissions. 
Please help me. 
Thanks,
Julia

---

### Post by deadflowr on 2013-09-26
What is the output of

```
ls -al foldername
```
replace foldername with the folder's name.

You will see two names listed, the first is the owner, and the second is the group.
If yourname is listed then it could be an attribute problem.
Look at the output for the attributes
```
lsattr foldername
```

---

### Post by julia3 on 2013-09-26
Thank you for your reply. 
It says can not accesss. No file name or direcotry.

---

### Post by khelben1979 on 2013-09-26
You can always try and increase your permissions for your regular user by using system tools. Other than that, what is it that you're trying to do?

---

### Post by julia3 on 2013-09-26
What I'm trying to do is edit my wordpress folder. So I can solve a wordpress problem I'm having. And it would be nice to be able to edit those folders. 
--- 
What do you mean increase the permissions?

---

### Post by deadflowr on 2013-09-26
> **julia3 said:**
> Thank you for your reply. 
It says can not accesss. No file name or direcotry.

Try it with the full path
Example
```
ls -al /var/mydumbfolder
```

---

### Post by julia3 on 2013-09-26
drwxrwxr-x  2 julia www-data    4096 Sep 25 22:39 .
drwxr-xr-x 14 root  root        4096 Sep 22 18:15 ..
-rw-rw-r--  1 julia julia         58 Sep 25 22:09 index.html
-rw-rw-r--  1 julia julia         47 Sep 25 21:44 index.html~
-rw-r--r--  1 root  root     4029511 Sep 11 13:13 latest.tar.gz
lrwxrwxrwx  1 julia www-data      21 Sep 20 20:57 phpmyadmin -> /usr/share/phpmyadmin
lrwxrwxrwx  1 root  root          20 Sep 25 22:39 wordpress -> /usr/share/wordpress
That is my output.

---

### Post by khelben1979 on 2013-09-26
```
man chown
```

Using that command you can change ownership of any file or folder on your system. Should do what you want from this.

---

### Post by ibjsb4 on 2013-09-26
> **julia3 said:**
> What I'm trying to do is edit my wordpress folder. So I can solve a wordpress problem I'm having. And it would be nice to be able to edit those folders.

You don't need to change permissions to edit a file.  Just start Nautilus as a superuser.

```
gksudo nautilus
```

---

### Post by ajgreeny on 2013-09-26
Or more safely just use the command ```
gksudo gedit filename 
``` to edit the file, but use the full pathway for the file, eg. /var/WordPress/foldername etc etc.

---

### Post by nothingspecial on 2013-09-26
> **khelben1979 said:**
> ```
man chown
```

Using that command you can change ownership of any file or folder on your system. Should do what you want from this.

Make sure you know exactly what you are doing before using chown

---

### Post by julia3 on 2013-09-27
Thanks for the reply you guys. However when I do..
gksudo nautilus, and gksudo gedit filename.
Of course I type in my file name. 
It says. 
(gksudo:31020): Gtk-WARNING **: cannot open display:

---

### Post by ibjsb4 on 2013-09-27
And it opens anyhow, right.  Its only a warning, if it was an error then it would be cause for concern.

---

### Post by julia3 on 2013-09-27
[COLOR=#000000][INDENT]And it opens anyhow, right. Its only a warning, if it was an error then it would be cause for concern.
-- 
It does not open though. [/INDENT]
[/COLOR]

---

### Post by ibjsb4 on 2013-09-28
Very odd that neither one will open.  Are you running a custom theme?

---

### Post by julia3 on 2013-09-28
[COLOR=#000000][INDENT]What do you mean running a custom theme? [/INDENT]
[/COLOR]

---

### Post by iGyan on 2013-09-29
Try to change the permission using sudo in terminal like

sudo chmod 777 -R folder/

or you may try it by log in with root user. to login with root user 

sudo su root

after that you will have all the permissions.

- [iGyan]("http://iGyan.org")

---

### Post by ibjsb4 on 2013-09-29
> **julia3 said:**
> What do you mean running a custom theme?

Thats the way your desktop gets displayed.  Its located in System Settings>Appearence.

I think you did not change this, since it takes some doing.

---

### Post by julia3 on 2013-09-29
Can somebody please help me. 
				 				 					 						 	[**[COLOR=#000000]iGyan[/COLOR]**]("http://ubuntuforums.org/member.php?u=1865674") that does not work.

---

### Post by 3rdalbum on 2013-09-29
> **julia3 said:**
> Can somebody please help me.

Are you running a desktop, or just a terminal?

If you're just running a terminal-only system, you can run the same commands that you do normally, but whenever you modify anything outside your home directory you need to use that command with "sudo". For instance, instead of:

```
cp file.txt /var/file.txt
```

you would do:

```
sudo cp file.txt /var/file.txt
```

You don't own anything outside your home directory, but 'root' does. If you are modifying anything owned by root, you need to use "sudo" to temporarily become 'root'. If you want to run a full GUI program as root, you need to use "gksudo" instead of "sudo":

```
gksudo nautilus
```

```
gksudo gedit
```

If you're running a desktop, make sure that you are putting terminal commands into the terminal on your desktop (Control-Alt-T can bring one up). **Don't** press Control-Alt-F1 to use a terminal, that sort of terminal is only for emergencies. If you are using a terminal on your desktop, the "gksudo nautilus" command will work.

---

