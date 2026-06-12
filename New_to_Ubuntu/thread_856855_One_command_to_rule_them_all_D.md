---
title: "One command to rule them all? :D"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Me+ on 2008-07-11
Hey

Everytime i go to install something i always have to install a different package.

Is there a single command that will download and install every package neccessary for building everything?

Thanks

---

### Post by tinny on 2008-07-11
:confused: More details please.

Is the APT install command not good enough for you?
```

sudo apt-get install <package>

```

Do you use the Synaptic package manager?

---

### Post by Dougie187 on 2008-07-11
well, im not sure how you are installing things, but you can just use
```
 sudo apt-get install *packagename*
```

That grabs all dependencies for each package you want to install.

---

### Post by DGortze380 on 2008-07-11
> **Me+ said:**
> Hey

Everytime i go to install something i always have to install a different package.

Is there a single command that will download and install every package neccessary for building everything?

Thanks

apt-get

installs any given package available in the repos along with any dependencies. (it can also install other packages available in your sources list, but i don't know about dependencies in that case.)

---

### Post by sdennie on 2008-07-11
The one command to rule them all (when building packages from source that already exist in the repos):

```

sudo apt-get build-dep name_of_the_package

```

---

### Post by Inxsible on 2008-07-11
Wizardry has still not entered the technological framework yet, unfortunately !!!

---

### Post by Me+ on 2008-07-11
lol i know about apt-get <packagename>

I mean is there any way to install every package that is out there that is required to build e.g libraries

i.e say i needed to install libssl to install a prog.

Instead of apt-get install libssl

COuld i run a command that installs everything.

I believe apt-get install build-essential is a type of shall we say combo of different libraries.

Is there like a very large combo?

---

### Post by Inxsible on 2008-07-11
The problem in your statement is that if there were such a package that installed "everything" some other user might be asking how to NOT install everything.

In any case...why would packagers and programmers want their packages to depend on something that is not required for their program or software to work?

---

### Post by crashcoredump on 2008-07-11
> **Me+ said:**
> lol i know about apt-get <packagename>

I mean is there any way to install every package that is out there that is required to build e.g libraries

i.e say i needed to install libssl to install a prog.

Instead of apt-get install libssl

COuld i run a command that installs everything.

I believe apt-get install build-essential is a type of shall we say combo of different libraries.

Is there like a very large combo?

What?
Like you want to install everything that exists??

something like apt-get install EVERYTHING????

apt-get installs a program and all required dependencies. But I am confused by your terms *"combo"* and *"everything"*

-

---

### Post by jordanmthomas on 2008-07-11
```
apt-get build-dep programname
```

EDIT: nevermind, it seems this isn't what you're looking for.

---

### Post by itsjareds on 2008-07-11
I know what he means, I was wondering the same thing.

What he means is, if there's 3 dependencies for a package he is installing, he wants to install those 3 dependencies first, and all of the dependencies for that, too. Instead of trying to install one and finding that you have to install another, then it becomes a giant confusing chain effect with 100 different packages to install. 

And it would check if you already have a dependency installed and skip it.

---

### Post by jwaiwit on 2008-07-11
Do u mean ```
sudo aptitude
``` command ?
It's will retrieving all dependencies package.

---

### Post by sdennie on 2008-07-11
If it's not the case that you are trying to build stuff from source but instead trying to install a .deb that you got from an external source, when you install it with, "dpkg -i whatever.deb", you can get the dependencies for it (after it fails) using:

```

sudo apt-get install -f

```

---

### Post by tinny on 2008-07-11
I think you are looking for [build-essential]("http://packages.ubuntu.com/hardy/build-essential")

```

sudo apt-get install build-essential

```

---

