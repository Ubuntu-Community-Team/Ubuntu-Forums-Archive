---
title: "How to find installed app ?"
date: 2018-08-16
forum: New to Ubuntu
---

### Post by sususudio on 2018-08-16
I have successfully installed an app. Is there a way I can search to see where it is located? It doesn't have a GUI client, can I create a shortcut to it and place it on the favorites section?
Thank you.

---

### Post by The Cog on 2018-08-16
If you know the name of the program, you can update the file location database and then ask it:
```
sudo updatedb
locate <program-name>
```

---

### Post by sususudio on 2018-08-16
Great, I found a bunch of references to it and its location. Is there a way to tell which of them is the actual app? I mean does it have an equivalent .exe from DOS? Once found, can I create a shortcut to it in my favorites?

---

### Post by Dennis N on 2018-08-16
If you used a package manager to install it, the program in likely in one of several standard locations in your file system and can be run from the Activities Overview - just enter the program name in the search box. Click on the icon which represents the program in the results below the box to start it. An icon will then appear in the dock on the left when it is running; right click on it and select "Add to Favorites".

---

### Post by sususudio on 2018-08-16
I installed it from the terminal, and it only runs from there. I thought If I'd have located, I could great a shortcut to it.

---

### Post by Dennis N on 2018-08-16
> **arkas2 said:**
> I installed it from the terminal, and it only runs from there. I thought If I'd have located, I could great a shortcut to it.

If it starts from the terminal prompt, then look at the directories in the output of the command below. The executable file of the program is in one of them.

```
dmn@Roxanne:~$ echo $PATH
/home/dmn/bin:/home/dmn/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

```

(Be sure to use the output from YOUR computer not mine)

---

### Post by oldos2er on 2018-08-16
> **arkas2 said:**
>  Is there a way to tell which of them is the actual app? 

```
dpkg -L <package name>
``` look for a file in /usr/bin

---

### Post by sususudio on 2018-08-17
Ok, thanks everyone I found it. Is there a way I can create a shortcut to it and place that in my favorites so I can just double click to run it?

---

### Post by oldos2er on 2018-08-17
Try [https://askubuntu.com/questions/887943/create-a-desktop-shortcut-for-a-terminal-comand](https://askubuntu.com/questions/887943/create-a-desktop-shortcut-for-a-terminal-comand)

---

