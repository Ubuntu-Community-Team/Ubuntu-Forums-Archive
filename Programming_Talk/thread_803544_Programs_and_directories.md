---
title: "Programs and directories"
date: 2008-05-22
forum: Programming Talk
---

### Post by mike_g on 2008-05-22
I have a java program that I want to be available to all users on a machine. I also have some data files associated with it that I want to be only directly viewable/editable by root, but still be able to be used and edited within the program regardless of what user is running it. 

I have a few questions here:

1 - What directory do I put my .jar file in (is it usr/bin)?
2 - Can I put the data files in a directory so that the program can still use relative addressing? If so where and wht naming conventions should be used.
3 - How do I go about setting the access privileges for the data folder? I'm guessing roughly something like: 
```
chmod a+x-rw datadir
chmod root +rw datadir
```
But I'm not sure.

Thanks.

---

### Post by mrMango on 2008-05-22
For more information about the "proper" way to install files and things, refer to the FHS, which is the standard upon unix filesystems are (mostly) based. [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

In a nutshell, world-executable program files would go in /usr/bin, and program data would go in /usr/share/<programname>

Chmod does not do user-based permissions like you are trying to implement. That's called an ACL, and it does require explicit filesystem support, which as far as I know isn't standard.

Root has implicit permissions on things, that is, it can do stuff whether you allowed it to happen or not. This code below will make a directory, and allow everyone to cd into that directory. However, no one will be allowed to read or write anything in that directory; indeed, they won't even be able to list the files in the directory.
```
chmod a+x-rw dir
```

However, since you want your users to be able to use files within the directory when they're running a program, the above isn't too useful unless you have setuid set on the program, which is a little insecure. To use any data within the datadir you would still need to allow read permission to normal users unless they have a method of gaining root privs:
```
chmod a+rx-w dir
```

Of course, this is all assuming you don't set the sticky bit on the directory, which means that files deposited into the directory retain ownership of the depositor. This would allow you to have read access on each user's files, and still not list anyone else's files... but that's starting to get a bit on the crazy-advanced side of things. At least, I think. [http://www.uwsg.iu.edu/usail/tasks/fileper/fileper.html](http://www.uwsg.iu.edu/usail/tasks/fileper/fileper.html)

---

### Post by NormR2 on 2008-05-22
I haven't tried any of these and I'm a newbie to Ubuntu.

Since jar files are data to the java program, would they only need to be marked as readable, not executable? I had a problem executing  jar files in GNOME from a script/launcher when they were marked executable. The script worked when I removed the x from the jar file.

Where/how is mike-g executing his java programs(jar files)? From scripts or a launcher in a GUI or from the commandline?

Does editting a data file mean writing it back after the changes?
Would this imply a separate thread with owner privileges to do the writing?

Could giving read permissions to a group vs all be used to control who can read/execute a jar file?

Thanks,
Norm

---

### Post by mike_g on 2008-05-23
Thanks for the replies. I want to start the prog from a bash script on startup. I think I'll just leave the files in a directory in the users userspace and run it from there; its pretty crude but it should work for now. Might get back to this later.

---

### Post by jamesstansell on 2008-05-31
Some of the resources at [http://jpackage.org/](http://jpackage.org/) may provide you with some ideas.  Also the Debian policy for Java [http://www.debian.org/doc/packaging-manuals/java-policy/](http://www.debian.org/doc/packaging-manuals/java-policy/) may interest you.

---

### Post by mike_g on 2008-06-02
cheers dude.

---

### Post by skullmunky on 2008-06-03
for location, /usr/bin for the program and /usr/share for the data is good.  another option is /opt for a directory containing the program and data directory both.  if the program is always just run from .bashrc then that's fine; if you want to have it in your path you could symlink it into /usr/bin.

that seems kind of unusual to have data files that can only be accessed by a user when using your program but not otherwise ... that's probably pretty complicated to do, so is it absolutely necessary?

---

