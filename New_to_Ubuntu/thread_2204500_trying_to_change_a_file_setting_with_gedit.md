---
title: "trying to change a file setting with gedit"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by nick58 on 2014-02-08
but it say  in permissions  i am not the owner therefore i can not change it

i am the owner so how do i change it 

thank you

---

### Post by Don_Stahl on 2014-02-08
Try opening a terminal and:

[FONT=courier new]sudo gedit[/FONT]

It will ask for your password.

You can also change file permissions (again, using sudo to gain root access).

---

### Post by stinkeye on 2014-02-08
> **Don_Stahl said:**
> Try opening a terminal and:

[FONT=courier new]sudo gedit[/FONT]

It will ask for your password.

You can also change file permissions (again, using sudo to gain root access).
Use **gksudo** for graphical applications.

> **nick58 said:**
> but it say  in permissions  i am not the owner therefore i can not change it

i am the owner so how do i change it 

thank you
What file?
Where is it located?

---

### Post by Bashing-om on 2014-02-08
nick58; Don_Stahl;

Graphical applications - gedit, nautilus or other  - require the graphical "sudo" !!! - gksudo - 
Else harm can ensue !
```

gksu gedit

```
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

take care
[INDENT][INDENT]just my little bit to help
[/INDENT][/INDENT]

---

### Post by deadflowr on 2014-02-08
Where's the file?
If it's in your home folder, then try
```
sudo chown username:groupname filenamehere
```
changing the username and groupname for whichever you have.
(typically you have a group with the same name as the user; eg bob user has a bob group.)
I don't recommend changing file permission on files outside of home.
If you simply need to edit a system file run 
```
gksu gedit path/to/filename
```
Newer versions of Ubuntu don't have gksu installed so to remedy that run
```
sudo apt-get install gksu
```
then to make sure that authentication is sudo run
```
gksu-properties
```
and make sure authentication is set for sudo and not su.

---

### Post by stinkeye on 2014-02-08
I give up on trying to help on these forums.
Seems everyones to eager to clutter each thread with repetition
and possibly unneeded or unwanted confusing/complicated info for a new user.

---

### Post by nick58 on 2014-02-08
sudo gedit thank you don 

that was perfect
well done

---

