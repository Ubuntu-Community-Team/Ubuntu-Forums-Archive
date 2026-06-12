---
title: "Can not install updates"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by mlvmhn on 2014-01-31
I have just installed Ubuntu 12.04 LTS, and there is 246 updates now. 

The problem is that when i click on install updates, the system is complaining about some third-party programs. 

I can uncheck some updates, but i do not know which one i shall uncheck. 

How should i proceed?

---

### Post by RadicaX on 2014-01-31
Can you show the error it is giving? You could try going to terminal and updating also.```
sudo apt-get update
```

Do you know how to take a screenshot?

---

### Post by mlvmhn on 2014-01-31
I have run the command in the Terminal, but all it did was to get some packages. 

How do i install the 246 updates using the terminal?

How do i take a screenshot?

---

### Post by rawrmonster on 2014-01-31
to install updated packages in terminal type "sudo apt-get upgrade" with out the quotes.

---

### Post by mlvmhn on 2014-01-31
I have now sucessfully installed all the available updates. But now i am facing another problem. 

I must install Flash, but i can not figure out how to do it?

I go to the Adobe Flash homepage, and there is 3 available versions to install. 

Which one do i install?

How do i proceed with installing Flash?

---

### Post by rawrmonster on 2014-01-31
"sudo apt-get install flashplugin-installer" in linux we use the package manager to install programs not websites unless there is not one in the package manager.

---

### Post by Bashing-om on 2014-01-31
mikael.hansson.967; Hi !

Though this belongs in a new thread, I will address it. -one problem to a thread -
> 
How do i proceed with installing Flash?

Terminal command:
```

sudo apt-get install flashplugin-installer

```
Until such time as you know what you are doing, it is advised to leave the 3rd party and external sources of software alone.

As your original problem has been addressed and has resolution, please mark this thread as solved;
1st post -> thread tools.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by mlvmhn on 2014-01-31
I have installed the Flash plugin using the Terminal and the above command. 
But still i get an error message from Youtube that i must upgrade my Adobe Flash Player.

I also use the latest version of Chromium

Why is not it working?

---

### Post by ajgreeny on 2014-01-31
Forget your old windows mindset of going to the website of the application you want and installing that way; you're using ubuntu now so always start by searching in the package manager that comes by default in the OS.  Not only is it so much easier than the windows way; it will also cause you fewer problems than applications that need installing in non-standard ways, or even compiling from source code.

---

### Post by mlvmhn on 2014-01-31
K, where do i find the package manager?

how will i proceed?

---

### Post by ajgreeny on 2014-01-31
> **mikael.hansson.967 said:**
> I have installed the Flash plugin using the Terminal and the above command. 
But still i get an error message from Youtube that i must upgrade my Adobe Flash Player.

I also use the latest version of Chromium

Why is not it working? 						
But did it actually install the flash plugin.  Run commands and show us the output of the second ```
sudo updatedb
locate libflashplayer.so
```

---

### Post by oldos2er on 2014-01-31
There are several different front-ends to APT (the package management system); Software Center is probably the most newbie-friendly.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by mlvmhn on 2014-01-31
Ok, now it is solved finally :P

---

### Post by RadicaX on 2014-01-31
Do not forget to mark the Thread solved! Sorry I did not get back sooner on it. A note, if the Flash is a bit too outdated on Firefox or Chromium, you can also download Chrome, it has Flash built into it.

---

