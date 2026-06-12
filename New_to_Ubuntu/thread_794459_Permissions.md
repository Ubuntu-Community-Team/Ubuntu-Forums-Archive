---
title: "Permissions"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-14
For some reason when I try to change the permissions on a file nothing happens.

What I am trying to do is allow it to read and write but when I click apply permissions nothing happens.

Any suggestions?

---

### Post by Thingymebob on 2008-05-14
You probably don't have permission to change permissions. What is it you're trying to change? Default file permissions are rarely incorrect

---

### Post by saskatchewan on 2008-05-14
It is a file that I copied from another computer and transfered using a DVD.  When I transfered it, then it showed a lock and would not accept new files to be but in the folder.

---

### Post by Oldsoldier2003 on 2008-05-14
> **saskatchewan said:**
> It is a file that I copied from another computer and transfered using a DVD.  When I transfered it, then it showed a lock and would not accept new files to be but in the folder.

```
sudo chmod 644 <filename>
``` would make it -rw-r--r-- assuming you have permissions to sudo

---

### Post by 1875 on 2008-05-14
```
gksudo nautilus
```

then browse to file and change permissions.

---

### Post by Oldsoldier2003 on 2008-05-14
> **1875 said:**
> ```
gksudo nautilus
```

then browse to file and change permissions.

as an afterthougt he doesn't make it real clear but he probably needs to chmod the folder he copied from the dvd. I suspect the op is talking about a folder with files copied from the dvd not just a file...

---

### Post by Thingymebob on 2008-05-14
get ready to use the terminal.
Before you do read the man pages for chown and chmod
```

man chown
man chmod

```
And make sure you are clear what I'm instructing you to do here

sudo will give root privileges and allow you to change the permission, clearly with this power you can also do serious damage.

```

sudo chown -R *Yourusername* *Path/to/folder/Foldername*
sudo chmod -R 644 *Path/to/folder/Foldername*

```

chown -R instructs the system to make you the owner of the folder and all files contained within

chmod -R instructs the system to change the permissions of the folder and all files contained within to user-RW group-R others-R

---

### Post by Thingymebob on 2008-05-14
> **1875 said:**
> ```
gksudo nautilus
```

then browse to file and change permissions.


Nautilus as sudo is dangerous (Particularly for new users) Be careful what you are instructing people to do and at least give an explanation/warning about the dangers

---

### Post by 1875 on 2008-05-14
> **Thingymebob said:**
> Nautilus as sudo is dangerous (Particularly for new users) Be careful what you are instructing people to do and at least give an explanation/warning about the dangers

Point taken. New guys always exhibit great care whenever you use any application as root. Also don't type any command in the console untilk you are sure it's what you want to do. That said gksudo natilus is a excellent GUI way to change permission etc, just don't go crazy with it.

---

### Post by ZabiGG on 2008-05-14
Great example of informative help, Thingy!

Thank you ;)

---

### Post by mkoehler on 2008-05-14
You can type something like this:

```
sudo chown <your_username>:<your_username> -R <folder_name> && sudo chmod 644 -R <folder_name>
```

That should solve all of your permission problems.

---

### Post by ZabiGG on 2008-05-14
> **mkoehler said:**
> You can type something like this:

```
sudo chown <your_username>:<your_username> -R <folder_name> && sudo chmod 644 -R <folder_name>
```

That should solve all of your permission problems.

Which loosely translates into "Im the boss" (sudo) "CHange OWNership" (chown) -R (make this recursive -- so basically apply it to everything inside the folder) and while you're at it, also (&&) change permissions (chmod) to 644 (each number of this series means something like Read-and-Write, or Read, or Execute)...

;)

Cheers!

---

