---
title: "Add and Remove Programs from a Terminal"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Papenco on 2008-06-21
Hello, I would like to learn if there's a why to Add or Remove programs from a Terminal. I used the search engine in the forum but found nothing. 
THanKS For YoUR HELp

---

### Post by ad_267 on 2008-06-21
To install a package:
```
sudo apt-get install name-of-package
```

To remove:
```
sudo apt-get remove name-of-package
```

To search for package:
```
apt-cache search searchterm
```
or
```
apt-cache search --names-only searchterm
```

To show package details:
```
apt-cache show name-of-package
```

See "man apt-get" for more info

---

### Post by kwirk on 2008-06-21
to add

sudo apt-get install "package name"

to remove

sudo apt-get remove "package name"

Nowt much else to it...

---

### Post by drs305 on 2008-06-21
> **Papenco said:**
> Hello, I would like to learn if there's a why to Add or Remove programs from a Terminal. I used the search engine in the forum but found nothing. 
THanKS For YoUR HELp

The two normal commands are:
```
sudo aptitude install *appname*
```
or 
```
sudo apt-get install *appname*
```

You can read about them by typing "man aptitude" or "man apt-get" in terminal

---

### Post by Het Irv on 2008-06-21
Yeah there is, you can use Apt-Get, Aptitude, or Dpkg.

This page should help you out:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Papenco on 2008-06-21
THanks to all, but a little last question; How do I know what packages are needed for a given program?.

---

### Post by avtolle on 2008-06-21
That's why I use the aptitude command, because at one time, it handled the dependencies as well, while apt-get only installed the named program, and one had to then go get the dependencies. I believe apt-get now handles this as well, but I'm not sure.

---

### Post by drs305 on 2008-06-21
> **Papenco said:**
> THanks to all, but a little last question; How do I know what packages are needed for a given program?.

Often the package name is the same as the common name (firefox, gimp, etc). If you aren't sure, and you want to stick to a terminal, you can type "aptitude" by itself and it will open a window with options that will eventually show you the available packages. You can also type "sudo aptitude install" and a letter or letters and hit the tab key twice. Example: "sudo aptitude install gi" then tab twice will show all available packages beginning with "gi".This will reveal all the packages available with those starting letters. Usually you will be able to figure out the name from those available.

You only have to pick the overall package name; aptitude will figure out what dependencies are required and install those as well.

---

### Post by ad_267 on 2008-06-21
If you use "apt-cache show packagename" it will show the dependencies. Apt-get will automatically install dependencies.

---

### Post by Papenco on 2008-06-21
So if I type sudo aptitude install "*name-of-app*" it will automatically install the application/program and the needed packages for that program?

---

### Post by drs305 on 2008-06-21
> **Papenco said:**
> So if I type sudo aptitude install "*name-of-app*" it will automatically install the application/program and the needed packages for that program?

Yes. And you can string apps together like this:
```
sudo aptitude install startupmanager gimp firefox audacity
```

---

### Post by Papenco on 2008-06-21
THANKS to everyone for your help. But I need a little help. If I want maybe to install a program that isn't by default included in the synaptic package manager. Let's say: ndiswrapper; how shall I do?

---

### Post by Sef on 2008-06-21
> THANKS to everyone for your help. But I need a little help. If I want maybe to install a program that isn't by default included in the synaptic package manager. Let's say: ndiswrapper; how shall I do?

Depends on how it is packaged.  Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

Ndiswrapper is in the repositories.  You need to go to System > Administration > Software Sources > Click on Community-maintained Open Source software (universe) > close, then you can install it.

---

### Post by drs305 on 2008-06-21
> **Papenco said:**
> THANKS to everyone for your help. But I need a little help. If I want maybe to install a program that isn't by default included in the synaptic package manager. Let's say: ndiswrapper; how shall I do?

In this specific case, ndiswrapper IS in the repositories. You could type:
```
sudo aptitude install ndiswrapper
```
but since that isn't the complete name of the package, the error command in the terminal would tell you so but offer some suggestions. Then you could try the double tab method that would give you all the options. The one you want is:
```
sudo aptitude install ndiswrapper-utils-1.9
```

Of course, synaptic is easier ;-)

---

### Post by Papenco on 2008-06-21
Which is the difference between apt-get and aptitude?

---

### Post by Miljet on 2008-06-21
According to the man pages, aptitude is simply a test based "front-end" for apt-get.

---

### Post by nhandler on 2008-06-21
There is one very important piece of information that you need to know if you plan on installing software from the terminal. Before you install anything or perform an upgrade, you should always type "sudo apt-get update" or "sudo aptitude update" first. These will reload your /etc/apt/sources.list file. This will make sure that you are always installing the correct versions of packages on your computer. You only need to do this when installing applications through the terminal. Applications like synaptic automatically run the update command.

---

