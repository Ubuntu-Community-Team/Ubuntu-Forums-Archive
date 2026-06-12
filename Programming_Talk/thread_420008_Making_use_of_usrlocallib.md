---
title: "Making use of /usr/local/lib"
date: 2007-04-23
forum: Programming Talk
---

### Post by WebDrake on 2007-04-23
I've tried installing from source some libraries which end up in /usr/local.  When running programs that make use of these libraries, I find that I can't access them---the system doesn't search /usr/local/lib for shared library files.

How do I make it do this?

I know that one way is to use add export LD_LIBRARY_PATH = /usr/local/lib:$LD_LIBRARY_PATH to my .bashrc_profile, but I was wondering if there's a more general way that simply tells the whole system to search /usr/local/lib as well as /usr/lib.

As a related question, what command do I use to find out what the library path currently is?

Many thanks,

     -- Joe

---

### Post by winch on 2007-04-23
Add /usr/local/lib to /etc/ld.so.conf then run ldconfig

A web serach for ld.so.conf or ldconfig should turn up plently of info.

---

### Post by hod139 on 2007-04-23
> **WebDrake said:**
> ... I was wondering if there's a more general way that simply tells the whole system to search /usr/local/lib as well as /usr/lib.
You can edit the file /etc/ld.so.conf (you might have to create the file if it does not exist) and add 
```

/usr/local/lib

```to the file.  You then have to update the cache by running
```

sudo ldconfig

```> 
As a related question, what command do I use to find out what the library path currently is?
I'm not sure how to get just the directories, but you can use ldconfig to print directories and libraries in its cache.
```

ldconfig -p

```A combination of that command and some scripting could potentially get just the dirs.  I'm not sure if there is a better command for retrieving only the dirs.

---

### Post by WebDrake on 2007-04-23
Many thanks for these great replies which solved the problem completely. :KS

---

### Post by mrowth on 2009-03-08
(Sorry about the necromancy. I've got a very much related question and thought there was no point starting an all-new thread for it.)

I'm working on a little game that consists of, among other things, a bunch of executables and a shared library (written by other people; they provide the runtime environment for what I'm doing). 

I want people to be able to plunk the contents of my tarball wherever they want, be it their home directory, or /opt, or (where I believe it would belong:) /usr/local.

But of course /usr/local/lib (where the shared library would then go) isn't "active" by default. 

Since there's a launcher shell script invovled, I could easily have the script look for the library (how? wild guesses?) and then change LD_LIBRARY_PATH accordingly before running the actual executable. That should work and would not alter people's systems.

But is that a good way to do it?

I'm a bit uncertain because /usr/local/lib is so utterly **empty**, as if one wasn't supposed to use it at all.

---

### Post by dwhitney67 on 2009-03-08
> **mrowth said:**
> ...
But of course /usr/local/lib (where the shared library would then go) isn't "active" by default. 
...
It is on some linux distros, but not all.  It is setup with Ubuntu 8.10.  Now I cannot recall if it was setup or not with 8.04.  Ditto with whether it was setup with Fedora 9.  I remember having an issue with one of these older distros, and I want to say it was with 8.04, but I'm not certain.

---

### Post by mrowth on 2009-03-08
> **dwhitney67 said:**
> It is on some linux distros, but not all.  It is setup with Ubuntu 8.10.  Now I cannot recall if it was setup or not with 8.04.  Ditto with whether it was setup with Fedora 9.  I remember having an issue with one of these older distros, and I want to say it was with 8.04, but I'm not certain.

/usr/local/lib does seem to be in use elsewhere (going by my googling anyway) - but not on 8.04, which both the original poster and I are/were using. Good to know I might not be trying to do something especially silly...

---

