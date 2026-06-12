---
title: "Permission denied"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by bengar on 2008-04-21
When I drag and drop a file from a cd the extracted file take this form, with a lock upside the icon.

[IMG]http://i30.tinypic.com/2z7n6ma.png[/IMG]

The problem is, that It doesn't can be send to the trash bin and the following message appear
 > Unable to trash file: Permission denied

What do I need to do to resolved this now and on the future.

---

### Post by Rocket2DMn on 2008-04-21
If you are deleting it, you can chown the folder recursively, then delete it
```
sudo chown -R yourusername:yourusername ~/Desktop/*foldername*
```
Use TAB to autofill the folder name, otherwise remember the \ escape character for spaces (or wrap the whole path in quotes).
That is the safest way to do it, but you can also use rm -rf combined with sudo, but you must be very careful with that command since it is dangerous if used incorrectly.

The reason the folder is locked is because you don't own it, it is probably owned by root.

---

### Post by russo.mic on 2008-04-21
> **bengar said:**
> When I drag and drop a file from a cd the extracted file take this form, with a lock upside the icon.

[IMG]http://i30.tinypic.com/2z7n6ma.png[/IMG]

The problem is, that It doesn't can be send to the trash bin and the following message appear
 

What do I need to do to resolved this now and on the future.

So,  The lock just means that it's been copied over as a file you don't have permissions to delete.  to solve this, 

1.  right click on the file, hit properties, and go the permissions tab, and enable the proper permissions, which may or may not work depending on what there set at now, or

2. what will def. work is for you to open up a terminal, and type 
sudo rm -r ~/Desktop/[name of directory].

RM is for remove, -r is for recursive (all files and subfolders within this folder), and sudo for execute as superuser.  it'll prompt you for your password.  the ~ is to denote your home directory, then /Desktop is the folder in which your desktop lives.

Good Luck!

Russo

---

### Post by skrribble on 2008-04-21
if you need to delete something that you supposedly don't have permission to, and you know that it won't affect the system, in the terminal type:
```
sudo nautilus
```
and from that window browse to the file and delete it.  that command gives you root permissions to the files.

---

### Post by bengar on 2008-04-21
> **russo.mic said:**
> So,  The lock just means that it's been copied over as a file you don't have permissions to delete.  to solve this, 

1.  right click on the file, hit properties, and go the permissions tab, and enable the proper permissions, which may or may not work depending on what there set at now, or

2. what will def. work is for you to open up a terminal, and type 
sudo rm -r ~/Desktop/[name of directory].

RM is for remove, -r is for recursive (all files and subfolders within this folder), and sudo for execute as superuser.  it'll prompt you for your password.  the ~ is to denote your home directory, then /Desktop is the folder in which your desktop lives.

Good Luck!

Russo

**Rocket **
I tried that but I don't know why is not working, this is what I got.
> bengar@bengar-desktop:~$ sudo chown -R bengar:bengar ~/Desktop/Libros Angeles Y Demonios - Dan Brown - Spanish - Audiobook 
chown: cannot access `/home/bengar/Desktop/Libros': No such file or directory
chown: cannot access `Angeles': No such file or directory
chown: cannot access `Y': No such file or directory
chown: cannot access `Demonios': No such file or directory
chown: cannot access `-': No such file or directory
chown: cannot access `Dan': No such file or directory
chown: cannot access `Brown': No such file or directory
chown: cannot access `-': No such file or directory
chown: cannot access `Spanish': No such file or directory
chown: cannot access `-': No such file or directory
chown: cannot access `Audiobook': No such file or directory


**Russo **
I tried this, I don't know if the path is correct:
> ~$ sudo rm -r ~/home/bengar/Desktop/Libros Angeles Y Demonios - Dan Brown - Spanish - Audiobook 
rm: cannot remove `/home/bengar/home/bengar/Desktop/Libros': No such file or directory
rm: cannot remove `Angeles': No such file or directory
rm: cannot remove `Y': No such file or directory
rm: cannot remove `Demonios': No such file or directory
rm: cannot remove `-': No such file or directory
rm: cannot remove `Dan': No such file or directory
rm: cannot remove `Brown': No such file or directory
rm: cannot remove `-': No such file or directory
rm: cannot remove `Spanish': No such file or directory
rm: cannot remove `-': No such file or directory
rm: cannot remove `Audiobook': No such file or directory


**skrribble**

I tried your method and it works, but when i browse I don't see the audio book folder showing a clear desktop.


Thanks guy for be patience, I f is possible to explain me what i did wrong will be appreciated.

bengar

---

### Post by Rocket2DMn on 2008-04-21
That is why I said to use the \ escape character or wrap it in quotes.  The command should be
```
sudo chown -R bengar:bengar "~/Desktop/Libros Angeles Y Demonios - Dan Brown - Spanish - Audiobook"
```
or
```
sudo chown -R bengar:bengar ~/Desktop/Libros\ Angeles\ Y\ Demonios\ -\ Dan\ Brown\ -\ Spanish\ -\ Audiobook
```

Same would apply for using the sudo rm -r command (but be careful to use it correctly)

---

### Post by bengar on 2008-04-22
> **Rocket2DMn said:**
> That is why I said to use the \ escape character or wrap it in quotes.  The command should be
```
sudo chown -R bengar:bengar "~/Desktop/Libros Angeles Y Demonios - Dan Brown - Spanish - Audiobook"
```
or
```
sudo chown -R bengar:bengar ~/Desktop/Libros\ Angeles\ Y\ Demonios\ -\ Dan\ Brown\ -\ Spanish\ -\ Audiobook
```

Same would apply for using the sudo rm -r command (but be careful to use it correctly)


Thank you Rocket2DMn
I applied both command and these are the result, is like the folder does not be there.

> bengar@bengar-desktop:~$ sudo chown -R bengar:bengar "~/Desktop/Libros Angeles Y Demonios - Dan Brown - Spanish - Audiobook"
chown: cannot access `~/Desktop/Libros Angeles Y Demonios - Dan Brown - Spanish - Audiobook': No such file or directory



> bengar@bengar-desktop:~$ sudo chown -R bengar:bengar ~/Desktop/Libros\ Angeles\ Y\ Demonios\ -\ Dan\ Brown\ -\ Spanish\ -\ Audiobook
chown: cannot access `/home/bengar/Desktop/Libros Angeles Y Demonios - Dan Brown - Spanish - Audiobook': No such file or directory

---

### Post by Rocket2DMn on 2008-04-22
Have you tried using
```
sudo nautilus
```
as skrribble suggested?  For security's sake, it should actually be
```
gksudo nautilus
```
Then navigate to /home/bengar/Desktop and delete the folder from there.

Did you try using TAB in terminal to autofill the name?
```
cd ~/Desktop
sudo chown -R bengar:bengar Lib[press TAB now]
```

---

### Post by bengar on 2008-04-22
Okay guys, thank you very much for your help I did it, yeaaah.
This was what I did.
1 Select Place, then home
2 Select to the left Items desktop
3 The file was there with the lock
4 I select it with a right click, as Russo said, I select delete, the lock's icon go away.
5 Return to the main desktop, right click on the icon, select trash and that's all folks.


bengar

---

### Post by bengar on 2008-04-22
How can Mark this Thread as [SOLVED] the Thread tools doesn't show me to mark it.

---

### Post by Rocket2DMn on 2008-04-22
> **bengar said:**
> How can Mark this Thread as [SOLVED] the Thread tools doesn't show me to mark it.

Hrrm, they just did a major forum upgrade and it seems things have changed, I can't figure out how to mark a thread as [SOLVED] either!

---

### Post by austicorn on 2010-08-27
:ks> **skrribble said:**
> if you need to delete something that you supposedly don't have permission to, and you know that it won't affect the system, in the terminal type:
```
sudo nautilus
```and from that window browse to the file and delete it.  That command gives you root permissions to the files.

---

### Post by austicorn on 2010-08-27
> **austicorn said:**
> :ks thanks, a lot.

---

