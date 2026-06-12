---
title: "Difference between cd Downloads/  and cd /bin  ?"
date: 2016-01-26
forum: New to Ubuntu
---

### Post by Siddharth_Syal on 2016-01-26
I was learning about Ubuntu, so I came across two commands cd Downloads/ and cd /bin. I found that if I write the command as cd bin/ , then in that case the system would show be error but if I write cd Downloads/ then the system would take me to the Downloads directory, I tried the opposite case and that too didnt work. I want to understand why the placement of ' / ' makes a huge difference ?.

---

### Post by howefield on 2016-01-26
You don't require a forward slash to go to any level down from your current point in the file system.

To go elsewhere in the file system requires the full path eg, /bin/ where you wouldn't need a forward slash to go one folder down..

[Here is a thread]("http://ubuntuforums.org/showthread.php?t=1444892") (an old one) there are plenty of others in these forums that you can search out for more information.

---

### Post by grahammechanical on 2016-01-26
When we open the terminal it opens in the user home directory. Run the ls command

```
graham@sdb7-Dev:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
```

We can change directory by using the cd command followed by the name of the directory. The forward slash is unnecessary. The command cd Downloads will do the same as cd Downloads/

To go upwards out of the home directory we need the forward slash because that indicates that the chosen directory is under the root directory. The command /bin will do the same as the two commands cd / & cd bin. Once we are in the root directory we can use the cd command without the forward slash to change directory to any directory under root.

To change directory to a directory within another directory we use the forward slash to separate the names of the two directories. Example from the root directory: cd etc/fonts.

Or we can do it all from the home directory. Example: cd /etc/fonts.

In natural language we would write: change directory to root, then change directory to etc, then change directory to fonts.

Regards.

---

### Post by Siddharth_Syal on 2016-01-26
thanks a lot ....now I understood

---

### Post by vasa1 on 2016-01-26
> **Siddharth_Syal said:**
> I was learning about Ubuntu, so I came across two commands cd Downloads/ and cd /bin. I found that if I write the command as cd bin/ , then in that case the system would show be error but if I write cd Downloads/ then the system would take me to the Downloads directory, I tried the opposite case and that too didnt work. I want to understand why the placement of ' / ' makes a huge difference ?.
The '/' without anything after it is redundant. Still, 'cd bin/' or 'cd bin' are equivalent but will work only if there's a folder called 'bin' located within the folder you're currently in. If there isn't such a 'bin' folder, you'll get an error. 

Many of us create a 'bin' folder in our home folder for user-specific scripts and stuff.

`cd /bin`, as pointed out, is shorthand for *change directory to the `bin` folder within the `root` folder* because `/` can mean two things: by itself it signifies `root`; when part of an path, it separates folder and file names).

---

