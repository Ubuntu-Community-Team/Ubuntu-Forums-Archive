---
title: "Easy way to chane .deb build prefix?"
date: 2011-07-31
forum: Packaging and Compiling Programs
---

### Post by nerdopolis on 2011-07-31
Hi.

I am trying to make a live CD for simplifying chrooting into unbootable systems for users.

One of the abilities I want to add is the ability to import some utilities into the target system, so that they can be used as if they where installed.

The problem is is that I can't seem to work around the apps trying to search for stuff in /usr/share when they are imported. (I already have a hacky workaround for /usr/lib...) I would do a union mount on the /usr/share's, but that could confuse package managers seeing files that should not be there? 


I might need to rebuild all packages to use a different build prefix instead of /usr... Is there a way to pass an argument to debuild or dpkg-buildpackage to change the build prefix? Right now it seems I have to take a look at the contents of the source (from apt-get source) for every package and see what files are specifying /usr and figure out a way to change it for every one...

Is this possible?

Thanks.

---

### Post by nerdopolis on 2011-08-06
Bump?

Is there no way to do this?

---

### Post by nerdopolis on 2011-08-14
Is there no easy way to change the build prefix for building a .deb file?

---

### Post by nerdopolis on 2011-08-21
I guess not?

It would seem that my only other option for me would be some kind of FUSE Union File system that only gives the unioned layout for specified PID's...

And that would severly intensify the complexity of the project...

---

### Post by nerdopolis on 2011-09-05
Bump?

---

### Post by MG&amp;TL on 2011-09-07
Try a specifically programming forum, like stackoverflow or something. If nobody's answered by now, it usually means no-one can. ...sorry.

Sounds interesting, if something comes of it, tell me.

---

### Post by nerdopolis on 2011-09-07
> **MG&TL said:**
> Try a specifically programming forum, like stackoverflow or something. If nobody's answered by now, it usually means no-one can. ...sorry.

Sounds interesting, if something comes of it, tell me.

Thanks, I guess I'll give that a try.

I'll try to remember to report back in this thread if I do find something out!

---

### Post by SevenMachines on 2011-09-08
If theres a way of automatically building with different install prefix all the different types of debianized source then I've yet to hear of it or utterly forgotten it :) If someone else knows of this magic I'd be interested to hear.
 
To be honest, I'm just not sure what you're trying to achieve here? Being able to do the above would just mean installing the package to the target system in a different directory, why would that be an improvement on just installing the package to the target system 'as is'? I'm really not sure what you mean by 'importing' and 'using as if installed'. If you've got a practical example of a specific case of what you're trying to do that might help, maybe I'm being dense but its really not clear to me at all.

---

### Post by nerdopolis on 2011-09-08
> **SevenMachines said:**
> If theres a way of automatically building with different install prefix all the different types of debianized source then I've yet to hear of it or utterly forgotten it :) If someone else knows of this magic I'd be interested to hear.
 
To be honest, I'm just not sure what you're trying to achieve here? Being able to do the above would just mean installing the package to the target system in a different directory, why would that be an improvement on just installing the package to the target system 'as is'? I'm really not sure what you mean by 'importing' and 'using as if installed'. If you've got a practical example of a specific case of what you're trying to do that might help, maybe I'm being dense but its really not clear to me at all.

What I meant by "importing" and "using as installed" is by mount --bind ing the folder that I compiled to such as /usr/recoverypackages to /mnt/recoverychroot/usr/recoverypackages so that the program can be used in chroot in of offline system. For example mountmanager, a graphical fstab editor, could be imported this way, and then used easily by users whose system isn't booting due to a broken fstab.

---

### Post by SevenMachines on 2011-09-08
Ah I see. I still doubt theres a way to recompile easily all the packages you want to. mountmanager is probably an example why, --prefix=/usr is manually coded into the debian/rules file, and there can be many different ways of doing this in many different kinds of rules file. Maybe someone else knows of a way but I'd be really surprised if it was possible to automate.

[EDIT] Some apps may respond to adding new paths to the '/usr/share' search path with XDG_DATA_DIRS environment variable but I suspect not many

---

### Post by nerdopolis on 2011-09-08
> **SevenMachines said:**
> Ah I see. I still doubt theres a way to recompile easily all the packages you want to. mountmanager is probably an example why, --prefix=/usr is manually coded into the debian/rules file, and there can be many different ways of doing this in many different kinds of rules file. Maybe someone else knows of a way but I'd be really surprised if it was possible to automate.

[EDIT] Some apps may respond to adding new paths to the '/usr/share' search path with XDG_DATA_DIRS environment variable but I suspect not many

Yes... I've had really bad luck with XDG_DATA_DIRS :D

I will admit I don't know why I did not think of this earlier, and the idea came to me today, that I am now trying to replace all the references to usr to usr/mylocation with find and sed. If I do this to all packages I install...

---

