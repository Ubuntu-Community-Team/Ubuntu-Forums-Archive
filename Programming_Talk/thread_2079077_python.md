---
title: "python"
date: 2012-11-01
forum: Programming Talk
---

### Post by thedardanius on 2012-11-01
ok,
in one or another way I got python runtime and libs installed. But I dont want to usepython dependancies. Now I want to remove them, but how?
And if I remove them, will it have effect on critical programs/processes?

---

### Post by Tony Flury on 2012-11-01
python is always installed by default on Ubuntu desktop deployments - not sure about servers.

Removing python will break a number of desktop features as far as i know.

---

### Post by thedardanius on 2012-11-01
ok thanks for informing!

---

### Post by spjackson on 2012-11-01
It is my understanding that Python is essential to Ubuntu. This is certainly the case for the standard desktop, i.e. the package ubuntu-desktop has a dependency on Python. I **think** it is also true for the alternative flavours (Lubuntu, Xubuntu, Kubuntu etc.). I have read reports that if you remove Python, then your system won't boot, but I haven't tried it myself. I think this may be true for Ubuntu Server (non-gui) too.

All I know for sure is that the Ubuntu standard desktop requires it. For the rest I am guessing. Let's see...

If you do
```

# WARNING THIS IS DANGEROUS
sudo apt-get remove python

```
it will list all the packages that will be removed, and you get the chance to quit.

Ah, I see that ubuntu-desktop ubuntu-minimal ubuntu-standard all depend on Python.

Since ubuntu-minimal is in that list, I am pretty confident that all flavours of Ubuntu (including Server) will be well and truly broken by removing Python.

If you want Linux without Python, then I think you need to choose another distro.

---

### Post by drmrgd on 2012-11-01
Better to run something like:

```
apt-cache showpkg python
```

That will show what dependencies and reverse dependencies the package requires and is much safer (you won't have to worry about accidentally removing the pacakge).  As others suggest, removing python will render your system useless and you'll likely have to reinstall.

---

### Post by thedardanius on 2012-11-01
ok. I dislike python, but since Ubuntu rquires it...

---

### Post by Tony Flury on 2012-11-01
Just becuase you have python installed - doesn't mean you have to use it, or come close to it.

I wont start a flame war and ask why you dislike it - just to say i was initially against python myself - but now i thik it is great - very useful tool for rapid development.

---

### Post by trent.josephsen on 2012-11-01
I dislike COBOL. Doesn't mean I boycott Citibank.

---

### Post by juancarlospaco on 2012-11-01
> **thedardanius said:**
> ok. I dislike python, but since Ubuntu rquires it...

Because you are using it wrong, 
you need to use it inside a VirtualEnv for Development purposes...

---

### Post by Tony Flury on 2012-11-01
> **juancarlospaco said:**
> Because you are using it wrong, 
you need to use it inside a VirtualEnv for Development purposes...

What ?

I can understand doing that if you are doing Kernel or maybe system application development, but I don't see the need for a Virtual Environment if you are simply doing user mode application type development, whether you are writing code in C, python, java or any other language.

and if thedardanius doesn't like python, and doesn't want to use it, then that is his choice - nothing to do with virtual environments.

---

