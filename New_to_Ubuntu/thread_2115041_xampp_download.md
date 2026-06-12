---
title: "xampp download"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by AllenMc on 2013-02-11
I am trying to download xampp on my wubi ubuntu partition on my windows machine and after I downloaded it and am following the instructions here [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) to install it with commands in the terminal I am getting an error saying saying that it cannot open the file and there is no such file in the directory. The file is in the downloads folder, the instructions didn't tell me to move it anywhere else so I would assume that is where I am supposed to have it. Does anyone know how I can fix this?

---

### Post by papibe on 2013-02-11
Hi AllenMc.

I would recommend installing the [LAMP]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29") stack instead. It is already pre packaged for Ubuntu, and it is in the repositories, so no hassles to install it, and get it working.

Take a look at this [tutorial]("https://help.ubuntu.com/community/ApacheMySQLPHP") for details.

Let us know how it goes.
Regards.

---

### Post by stoogiebuncho on 2013-02-11
> **papibe said:**
> Hi AllenMc.

I would recommend installing the [LAMP]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29") stack instead.

+1.  This is much easier, and you'll get automatic updates.

---

### Post by AllenMc on 2013-02-12
I downloaded and installed LAMP and it was much easier and seems to have worked. But I dont have permission to save files or create folders or anything in var/www 

can either of you tell me a way to change this?

---

### Post by AllenMc on 2013-02-12
Never mind. The instructions suggested using 
$ sudo nautilus
and the 1st time I did it it didn't work but I must have typed something wrong and not noticed because I just tried again and it worked fine.

---

### Post by slickymaster on 2013-02-12
> **AllenMc said:**
> Never mind. The instructions suggested using 
$ sudo nautilus
and the 1st time I did it it didn't work but I must have typed something wrong and not noticed because I just tried again and it worked fine.

You shouldn't use **sudo** with graphical applications. Take a look at this thorough explanation of why:
[Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by AllenMc on 2013-02-12
Oh wow thanks. I would of never known that. If I just redo the same command with gksudo instead will that override the previous sudo command and I wont have any problems?

---

### Post by wlraider70 on 2013-02-12
> **papibe said:**
> hi allenmc.

I would recommend installing the [lamp]("http://en.wikipedia.org/wiki/lamp_%28software_bundle%29") stack instead. It is already pre packaged for ubuntu, and it is in the repositories, so no hassles to install it, and get it working.

Take a look at this [tutorial]("https://help.ubuntu.com/community/apachemysqlphp") for details.

Let us know how it goes.
Regards.

+1

---

### Post by slickymaster on 2013-02-12
> **AllenMc said:**
> Oh wow thanks. I would of never known that. If I just redo the same command with gksudo instead will that override the previous sudo command and I wont have any problems?

That's not point.
**sudo** doesn't load root your (i.e. the user's) environment variables for graphical applications. This means that when you launch a graphical application with **sudo** you are running it with root's permissions but using your normal user's settings and configuration files.
Depending on the program you run this can result in your normal user's configuration files becoming owned by root, which will prevent the normal user from changing program settings any more.

---

### Post by AllenMc on 2013-02-13
Oh ok so I was able to add files and folders and edit them right after I ran the command but later when I go back I might not be able to? Because they are owned by root still, so I wouldn't have writing permissions. So next time I log into Ubuntu I should redo the command but with gksudo?

---

### Post by slickymaster on 2013-02-13
Once you've done it, there's no point in re-running the command once again, using **gksudo** this time. If it were for something to happen it would have already happened and by now you probably had noticed it.

Let me quote you part of [Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo") webpage's content:

> Bottom line: most of the time when you use sudo for graphical applications, it's fine. Some of the time, though, it is not fine, and is, in fact, extremely bad.

If you made exceptions, you would have to give people a list of all the graphical applications that are okay to run as sudo and a list of all the graphical applications that must be run as gksudo or kdesudo.

Why make a list that needs to be compiled and updated, that most people won't refer to, and that is completely unnecessary? Just be consistent in suggesting good practice: gksudo and kdesudo for graphical applications. sudo for command-line applications.

---

### Post by AllenMc on 2013-02-13
Alright. I was only on Ubuntu for a few minuets after I ran the command and have been running Windows since then, I've needed some programs and files I don't have in Ubuntu. But when I go back into Ubuntu if I do run into a problem would re-running the command using gksudo fix it?

---

### Post by papibe on 2013-02-13
To repair any possible (mild) damage, just make sure you reset ownership of all your files to yourself:
```
sudo chown  -R  youruser:youruser  ~youruser
```
where 'youruser' is your actual username.

Regards.

---

### Post by slickymaster on 2013-02-14
> **papibe said:**
> To repair any possible (mild) damage, just make sure you reset ownership of all your files to yourself:
```
sudo chown  -R  youruser:youruser  ~youruser
```
where 'youruser' is your actual username.

Regards.

Exactly.

In order to verify the ownership of your files just run the command on the required file/folder to show you a long listing information about the file/directory.:
```
ls -l
```

---

