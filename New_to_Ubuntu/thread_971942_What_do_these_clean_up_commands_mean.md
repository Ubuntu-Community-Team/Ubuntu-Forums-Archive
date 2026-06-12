---
title: "What do these clean up commands mean"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-11-05
```
sudo apt-get clean
sudo apt-get autoremove

```

like what do they do? what do they clean and whats the difference bbetween the 2.

im trying to understand the commands

---

### Post by jbrown96 on 2008-11-05
```
man apt-get
```

---

### Post by inportb on 2008-11-05
The first clears the cache of downloaded Debian packages. The second uninstalls orphaned packages.

---

### Post by Idefix82 on 2008-11-05
The first command deletes any temporary data that was downloaded when you installed packages. This includes for example the compressed packages themselves.
The second command uninstalls all packages which were installed automatically as dependencies of something and which are no longer needed because you uninstalled the dependant package.

While the first command is relatively harmless, the second can sometimes remove packages that you need. I would prefer using the orphan filter for Synaptic. This thread explains, how: [http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by Herman on 2008-11-05
Software packages are stored in /var/cache/apt/archives, in compressed files with a .deb filename  extension. 

It seems to be fashionable and trendy for people to go around recommending everyone run sudo apt-get clean to remove those .deb packages but they do no harm unless you're really cramped for hard disk space.  
For most people it's a waste of time running sudo apt-get clean, those old .deb packages will never hurt you or your system.

Use your own common sense and powers of reasoning before doing things just because a lot of people keep repeating the same idea.

It might be worthwhile for some people who have Ubuntu installed in a USB flash memory stick or a very small hard drive to run sudo apt-get clean to make some room in their file system if it's too full. 
Linux file systems like to have at least 20% unused space or they may start to become fragmented.
In that situation, running sudo apt-get auto remove would be a very good idea.

However for most people, instead of removing those packages, you might even consider making a backup of your /var/cache/apt/archives under some circumstances.
If for some reason you might want to fully back up your system to do a re-install and you don't want to waste a lot of time and use extra internet bandwidth downloading all your installed software all over again and updating it all, you can make a backup of your /var/cache/apt/archives directory.
After you re-install you can just copy all your .deb packages to your new /var/cache/apt/archives/ and re-installing all the software will be quicker.
There will be no need to re-download all your added software again.  :)

On the other hand, keeping a backup of them for long could be a waste of time and media space too, since they get out of date rather quickly.

So think before you act, and don't just blindly accept everything the trendy people say you should do without asking around first.
You are right to start a thread about it and find out, that's the best thing to do. :)

Regards, Herman :)

EDIT: I also need to mention that we can only use the same packages for another Ubuntu installation which is the same version of Ubuntu as the one they came from.
I mean if we have one Ubuntu Hardy Heron i386 installation, we can use the packages for any other Ubuntu Hardy Heron i386 operating system.
We should not try to use packages from Ubuntu Hardy Heron i386 for the amd64 version or for Intrepid Ibex or any other kind of Ubuntu, it might cause a lot of problems.

---

### Post by faraz_k86 on 2008-11-05
Thanks a lot Herman for the great tip and detailed reply



Hey inportb, glad to see you here :)

Im the_punisher from 110mb forums :)

---

