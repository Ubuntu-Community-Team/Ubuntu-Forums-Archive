---
title: "check for program in Python"
date: 2009-10-15
forum: Programming Talk
---

### Post by Sandsound on 2009-10-15
Is there a "right" way of checking in an external program exist ?

I was thinking something like :

```

import os.path
if not os.path.exists("/usr/bin/programX"):
    error = gtk.MessageDialog (None, gtk.DIALOG_MODAL,
                        gtk.MESSAGE_ERROR,
                        gtk.BUTTONS_OK,
                        ('programX is not installed'))
    error.run()

```

But what if this is installed in another folder and added to PATH ?

---

### Post by Can+~ on 2009-10-15
If you're working with Debian distributions, then you could use apt and search if a certain package is installed. There are bindings for it (python-apt).

Or far simpler, pack your application with the dependencies, and just assume it's there.

---

### Post by Tony Flury on 2009-10-15
surely you should use "which" first and use the output of that as the path.

---

### Post by Sandsound on 2009-10-15
> **Can+~ said:**
> If you're working with Debian distributions, then you could use apt and search if a certain package is installed. There are bindings for it (python-apt).

Thanks... Python-apt looks like it's just what I need, now I just have to figure out how to use it.

> **Can+~ said:**
> Or far simpler, pack your application with the dependencies, and just assume it's there.

I haven't tried to pack my programs yet, it doesn't look as simple as it sounds, at least not to me :-) but hopefully I'll get there someday.

---

### Post by Can+~ on 2009-10-15
> **Sandsound said:**
> I haven't tried to pack my programs yet, it doesn't look as simple as it sounds, at least not to me :-) but hopefully I'll get there someday.

It's not that hard, it's about creating a config file which stores some strings (e.g "depends: libx-2.x ...")

Here's a great tutorial by IBM:
[http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)

---

### Post by diesch on 2009-10-15
It depends on how much compatibility you need:

[LIST]
[*]python-apt restricts you to Debian-based Linux distributions.
[*]"which" is a shell builtin that is not supported by all shells (but at least by bash and zsh, so it should work on most Unix-like systems using a GNU userland).
[*]searching all dirs in $PATH works on all SUSv3 compatible systems (and most other Unix-like systems, too)
[*]If there is a way of calling the program that doesn't need much time and doesn't have side effects (like calling "program --help") you can use os.system()
[/LIST]

---

### Post by Sandsound on 2009-10-15
> **Can+~ said:**
> It's not that hard, it's about creating a config file which stores some strings (e.g "depends: libx-2.x ...")

Here's a great tutorial by IBM:
[http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)

Like so many tutorials I have found in the web, it assumes some prior knowledge to a lot of things, I got as far as the bit about postinst- and prerm-scripts and then... four lines that basically tells you to just make them ? oh... and also, that they are required :-)

But you are right, I should look into making packages.

---

### Post by Sandsound on 2009-10-15
> **diesch said:**
> python-apt restricts you to Debian-based Linux distributions.

Isn't there a "deb2rpm" program ?
I know that alien can make deb-files out of rpm's, but I haven't got much experience with it.

And considering the relatively small size of my small programs (mostly just frontends to existing programs) a dependencies check would keep the code smaller (ie. more easy for me to comprehend ;-) ).

---

### Post by diesch on 2009-10-15
> **Sandsound said:**
> Isn't there a "deb2rpm" program ?
I know that alien can make deb-files out of rpm's, but I haven't got much experience with it.


That doesn't help here as apt-python is a frontend for libapt and can't access any other package manager.

> **Sandsound said:**
> 
And considering the relatively small size of my small programs (mostly just frontends to existing programs) a dependencies check would keep the code smaller (ie. more easy for me to comprehend ;-) ).

Checking $PATH is quite simple:

```

def check_program(name):
    for dir in os.environ['PATH'].split(':'):
        prog = os.path.join(dir, name)
        if os.path.exists(prog): return prog

```

That returns the path of program "name" or None if it's not found in $PATH

---

### Post by wmcbrine on 2009-10-15
I was about to post almost the same code as diesch. But you might want to use os.pathsep rather than ':', to make it more portable.

---

### Post by ghostdog74 on 2009-10-15
> **Tony Flury said:**
> surely you should use "which" first and use the output of that as the path.
not nearly foolproof. what if program's path is not in PATH.?

---

### Post by wmcbrine on 2009-10-16
> **ghostdog74 said:**
> not nearly foolproof. what if program's path is not in PATH.?Eh? How would you expect to find it if it's not in PATH? That's what PATH is *for*. It's what the shell uses, too. The only things you can run from the shell that aren't in PATH are shell built-ins, or files with a full (relative or absolute) path given.

---

### Post by ghostdog74 on 2009-10-16
> **wmcbrine said:**
> Eh? How would you expect to find it if it's not in PATH? That's what PATH is *for*. 

when installing packages from certain distributions, some of them may choose paths like /usr/local , or some others like /opt, or even some from obscure path chosen by the user who install them. If these are not in PATH, ie then you most probably won't find it using "which" or whatever tools or methods/libraries that uses the PATH environment variable. Of course, i didn't say you can't use it, i just say its not nearly foolproof. ie, one has to check other places as well in the program, AFTER checking PATH, just in case it installed elsewhere.

---

### Post by wmcbrine on 2009-10-16
There is no sane reason to check outside of PATH, unless you know specifically that what you're looking for is likely not to be there (and you know where it *is* likely to be). Programs that want to be found put themselves in the PATH, period. (At least on a Linux/Unix/POSIX system. Not so true for Windows or Mac.)

And of course /usr/local/bin and /usr/local/sbin should be in PATH.

---

### Post by Sandsound on 2009-10-16
> **diesch said:**
> That doesn't help here as apt-python is a frontend for libapt and can't access any other package manager.



Checking $PATH is quite simple:

```

def check_program(name):
    for dir in os.environ['PATH'].split(':'):
        prog = os.path.join(dir, name)
        if os.path.exists(prog): return prog

```

That returns the path of program "name" or None if it's not found in $PATH

Thanks to all for joining in, but it apears that there is no "official" rule ?

Another problem with this, is that my program uses 5 diffrent programs, and with the $PATH option I would have to do this for each program in the source.


Regarding packaging as .deb, it seams that alien check for dependencies (I might be wrong on this thou), so a .deb converted (using alien) into a .rpm would check for dependencies in a .rpm enviroment ?

---

### Post by ghostdog74 on 2009-10-16
> **wmcbrine said:**
> There is no sane reason to check outside of PATH, unless you know specifically that what you're looking for is likely not to be there (and you know where it *is* likely to be). Programs that want to be found put themselves in the PATH, period. (At least on a Linux/Unix/POSIX system. Not so true for Windows or Mac.)

And of course /usr/local/bin and /usr/local/sbin should be in PATH.
things and shi* happens. This world is not perfect. With this fact, there are possibilities that checking PATH is still not enough.

---

### Post by Arndt on 2009-10-16
> **ghostdog74 said:**
> things and shi* happens. This world is not perfect. With this fact, there are possibilities that checking PATH is still not enough.

What is actually the problem? If the program A wants to check that program B is available, it's probably because A is going to call B sooner or later, and then A knows exactly how it is going to call it - with an explicit path (hardwired or configured), or using PATH.

Or A just wants to check that B is there, as a service to the user, who is going to want to call B himself later?

---

### Post by ghostdog74 on 2009-10-16
> **Arndt said:**
> What is actually the problem? If the program A wants to check that program B is available, it's probably because A is going to call B sooner or later, and then A knows exactly how it is going to call it - with an explicit path (hardwired or configured), or using PATH.

I know one can check program paths in PATH for where the programs are found. The problem arise when a program whose path is not found in one of those paths specified in PATH, and its actually what program A wants and located somewhere else. I also know proper installation of programs will (100-x)% of them time add their paths to PATH. But i am talking about the possibility of that x% occurring. 
This is just some extra contingency measures to incorporate into the check..

---

### Post by Arndt on 2009-10-16
> **ghostdog74 said:**
> I know one can check program paths in PATH for where the programs are found. The problem arise when a program whose path is not found in one of those paths specified in PATH, and its actually what program A wants and located somewhere else. I also know proper installation of programs will (100-x)% of them time add their paths to PATH. But i am talking about the possibility of that x% occurring. 
This is just some extra contingency measures to incorporate into the check..

How do you mean they add themselves to PATH? PATH is a variable which the user sets.

---

### Post by ghostdog74 on 2009-10-16
> **Arndt said:**
> How do you mean they add themselves to PATH? PATH is a variable which the user sets.
what i mean is, with given permissions, installation programs can sometimes write to default PATH profiles etc.. eg, if i am root, and i install some program, this program can modify my profile and add its program path to my PATH variable.

---

### Post by Sandsound on 2009-10-16
> **ghostdog74 said:**
> what i mean is, with given permissions, installation programs can sometimes write to default PATH profiles etc.. eg, if i am root, and i install some program, this program can modify my profile and add its program path to my PATH variable.

I can see how this might be useful if you where to search for a program that you don't know much about (I guess that could possibly occur), but if you know what program to search for (like in my case), wouldn't you also know where that program is installed ?

imho it seams pointless to search for a program that is not in PATH.

---

### Post by diesch on 2009-10-16
> **ghostdog74 said:**
> I know one can check program paths in PATH for where the programs are found. The problem arise when a program whose path is not found in one of those paths specified in PATH, and its actually what program A wants and located somewhere else. I also know proper installation of programs will (100-x)% of them time add their paths to PATH. But i am talking about the possibility of that x% occurring. 
This is just some extra contingency measures to incorporate into the check..

If it is not in $PATH that's maybe because the users doesn't want it to be used.

There is no 100% failsafe way. But searching $PATH combined with the possibility to manually configure which program to use usually works quite well.

---

### Post by ghostdog74 on 2009-10-16
> **Sandsound said:**
> I can see how this might be useful if you where to search for a program that you don't know much about (I guess that could possibly occur), but if you know what program to search for (like in my case), wouldn't you also know where that program is installed ?

not really. I give you an example. Say you compile a source code, and during configure, you specify another installation directory due to some reason ,maybe you have an older version installed already and you don't want to mess that up somehow. however, after make and make install, that installation may not update your PATH. and then comes the part when program A needs to check where this program you installed is, as it only support higher version. Does it go to the usual PATH variable only? you can think about that. Anyway...if you know what you doing then i guess it should be no hassle. my proposal is just an extra contingency check that's all.

---

### Post by benj1 on 2009-10-16
another alternative if you just want to find a generic app is etc/alternatives

---

### Post by Sandsound on 2009-10-16
> **benj1 said:**
> another alternative if you just want to find a generic app is etc/alternatives

Sorry... but I don't get it, please elaborate

---

### Post by benj1 on 2009-10-16
> **Sandsound said:**
> Sorry... but I don't get it, please elaborate

it contains a list of links to certain default apps
so 'editor' might be linked to nano

'x-www-browser' might be linked to firefox

it depends what you want to do, if you want to open a browser then you can check x-www-browser instead of searching for a list of web browsers, it wont find a specific app tho.

---

### Post by Sandsound on 2009-10-16
> **benj1 said:**
> it contains a list of links to certain default apps
so 'editor' might be linked to nano

'x-www-browser' might be linked to firefox

it depends what you want to do, if you want to open a browser then you can check x-www-browser instead of searching for a list of web browsers, it wont find a specific app tho.

Cool 8-)

---

