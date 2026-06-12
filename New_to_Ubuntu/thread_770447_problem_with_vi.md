---
title: "problem with vi"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Chilliman on 2008-04-27
hi.
need some help
i am trying to run ubuntu desktop on ubuntu server which acording to the server fourms will work i have loaded the software but need to add a line to rc.local but i am having a few problems editting rc.local i can open the file in VI i can insert the line "/etc/init.d/gdm start" but when i try to save and quit it tells me that it is read only and when i use :wq! command it does not save.
any ideas 

chillman..

](*,)

---

### Post by raul_ on 2008-04-27
> **Chilliman said:**
> hi.
need some help
i am trying to run ubuntu desktop on ubuntu server which acording to the server fourms will work i have loaded the software but need to add a line to rc.local but i am having a few problems editting rc.local i can open the file in VI i can insert the line "/etc/init.d/gdm start" but when i try to save and quit it tells me that it is read only and when i use :wq! command it does not save.
any ideas 

chillman..

](*,)

sudo vi <file>

:)

---

### Post by Chilliman on 2008-04-27
hi.
need some help
i am trying to run ubuntu desktop on ubuntu server which acording to the server fourms will work i have loaded the software but need to add a line to rc.local but i am having a few problems editting rc.local i can open the file in VI i can insert the line "/etc/init.d/gdm start" but when i try to save and quit it tells me that it is read only and when i use :wq! command it does not save.
any ideas 

chillman..

---

### Post by DBrocks on 2008-04-27
vi is very difficult to learn sometimes. Your best bet is a handy little text editor known as "nano" It is installed by default in Ubuntu, but I'm not sure if that's the case in Xubuntu. So, to check, just run:
```
sudo apt-get install nano
```
If you get a message: "nano is already in its newest version" or something like that, you're set. If not, let it install nano.

Now, you can use nano instead of vi:
```
nano path/to/your/file
```edit your lines, ctrl+x to exit, and type "y" to save.
Note: Make sure you are a super user when you edit protected files:
```

sudo nano path/to/your/file/you/want/to/edit
```Good Luck!
~Dan

---

### Post by raul_ on 2008-04-27
Please don't post duplicate threads

---

### Post by DBrocks on 2008-04-27
But VI is very evil. Nano is simple, fast, and easy.

---

### Post by Dr Small on 2008-04-27
That is probably one way, but that would start GDM at the end of the course, because rc.local is the last file to be loaded at boot time, from what I recall.

Using:
```
sudo update-rc.d gdm defaults
```

Would probably work better.
Also, in my opinion, Vim is easier to use than Vi. But if you find either too hard, try using nano, as it should be the easiest.

Good luck,
Dr Small

---

### Post by Dr Small on 2008-04-27
> **raul_ said:**
> Please don't post duplicate threads
+1
I feel like I already replied to this once...

---

