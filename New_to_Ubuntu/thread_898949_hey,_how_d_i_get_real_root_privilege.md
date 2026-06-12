---
title: "hey, how d i get *real* root privilege?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by pablolie on 2008-08-23
i need to make changes to a file in the etc folder.

ubuntu won't let me.

i installed it. my user is an administrator. i do not have permission to the etc folder, even though i changed my user to be root group?

all i need to do is add a file, and i can't. frustrating!

---

### Post by damis648 on 2008-08-23
You must ACTUALLY be root\run the program as root. In a terminal, type
```
gksudo nautilus
```
and enter. This is why Ubuntu is so secure, normal accounts are unprivileged in many ways. Only root can do administrative tasks, so a virus as a normal user couldn't do much damage. As opposed to Windows, whereas anything an be modified by any program. That is how viruses get in. Good luck!

Make sure you know what you are doing!

---

### Post by zamadatix on 2008-08-23
same thing i need access to a folder and did thatand certantly dont want to go through terminal every time thoough i think thats the only way.

---

### Post by Diabolis on 2008-08-23
From the command line use the mv command with root privileges(sudo).

Lets say that you have a file here: /home/username/myfile and that you want to move it to the /etc folder. You would have to execute this command:
```
sudo mv /home/username/myfile /etc
```

---

### Post by Rocket2DMn on 2008-08-23
We don't teach people how to truly use the root login since this ia a major security problem.  See here for a more detailed explanation of our policy - [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
Use sudo and graphical sudo!

---

### Post by Diabolis on 2008-08-23
> **zamadatix said:**
> same thing i need access to a folder and did thatand certantly dont want to go through terminal every time thoough i think thats the only way.

As mentioned above, you can open a nautilus window with root permissions too. I don't recommend doing this as its easier to commit a mistake and cause serious damage to your system. The command line is a lot safer, plus it makes you look like a hacker ;).

---

### Post by pablolie on 2008-08-23
thanks a lot - that did the trick and made it easy.

i utterly appreciate ununtu's security and strict rights policy, and think this is a very workable compromise, once you know it. it is the first time i have needed it in 6 months of ubuntu use, which is a testament to its everyday usability for the vast majority of tasks.

---

### Post by zamadatix on 2008-08-23
im not ot worried abotu lloking like a hacker in my room ;) but is there any way to just login from the login screen as root? (could i type username as rot and my pass for the pass?)

---

### Post by Shippou on 2008-08-23
Speaking of root permissions, Mint Elyssa is different: after installation and the first time you log in, it asks you two questions. The first question is... guess what?

See the picture uploaded below.

---

### Post by Diabolis on 2008-08-23
Again, it is not recommended to use su. You don't really need to use it.

---

### Post by damis648 on 2008-08-23
> **zamadatix said:**
> im not ot worried abotu lloking like a hacker in my room ;) but is there any way to just login from the login screen as root? (could i type username as rot and my pass for the pass?)

As good forum advisors, we cannot provide such information... it is too dangerous.

---

### Post by damis648 on 2008-08-23
> **Shippou said:**
> Speaking of root permissions, Mint Elyssa is different: after installation and the first time you log in, it asks you two questions. The first question is... guess what?

See the picture uploaded below.

Ubuntu, though, sets a randomly generated password for root.

---

### Post by dje on 2008-08-23
just thought id post a link to [this]("http://ubuntuforums.org/showthread.php?t=765414"), the forum policy on "login as root" tutorials ;)

dje

---

### Post by zamadatix on 2008-08-23
...so obviously there is a way... anyone who is not admin know?

---

### Post by Rocket2DMn on 2008-08-23
I am closing this thread because it is asking how to do something that we don't allow, and people are ACTUALLY telling despite the forum policy which I ALREADY mentioned - [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

