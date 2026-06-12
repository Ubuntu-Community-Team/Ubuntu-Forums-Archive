---
title: "make[1]: antlr: command not found"
date: 2012-04-29
forum: Packaging and Compiling Programs
---

### Post by kramer65 on 2012-04-29
Hello,


I am trying to install a package called [IbPy]("https://code.google.com/p/ibpy/") on Ubuntu 12.04. In the [build instructions]("https://code.google.com/p/ibpy/wiki/BuildingIbPy") it says that I need to have "*Antlr 2.7.7 and its Python library*" installed. So I went into Synaptic and installed the following packages:
[LIST]
[*]antlr
[*]python-antlr
[*]libantlr-java
[/LIST]
Following the instructions I then got a specific revision version of java2python (revision 50) after which I enter the folder on the command line and type: *make*

Unfortunately I then get an error saying the following (I translated some words from Dutch into English, so it could be a little bit off the normal wording): 

```
kramer65@kramer65:~/src/java2python/java2python$ make
cd lib && make
make[1]: Folder '/home/kramer65/src/java2python/java2python/lib' is entered
antlr java.g
make[1]: antlr: Command not found
make[1]: *** [parser.py] Error 127
make[1]: Folder '/home/kramer65/src/java2python/java2python/lib' is left
make: *** [lib] Error 2
kramer65@kramer65:~/src/java2python/java2python$ 
```

Since it says that the antlr command is not found, I suppose there is something wrong with the installation of antlr. In Synaptic everything seems to be fine though.

Does anybody have any idea how I can solve this error? All tips are welcome!

---

### Post by strask on 2012-04-29
Looks to me like maybe the antlr command ended up in a non-standard place that's not in your path. Try ```
dpkg --listfiles antlr |more
``` to get a list of all files in the package, find the antlr command, and make sure the directory is in your PATH environment variable. Then re-try your make.

---

### Post by oldos2er on 2012-04-29
Moved to Packaging and Compiling Programs.

---

### Post by kramer65 on 2012-04-29
Alright, I am messing around with python and I feel quite comfortable navigating with the command line, but this goes to the edge of my knowledge.

> **strask said:**
> Looks to me like maybe the antlr command ended up in a non-standard place that's not in your path. Try ```
dpkg --listfiles antlr |more
``` to get a list of all files in the package,
So I copy/pasted your command and got the following list:

/.
/usr
/usr/bin
/usr/bin/runantlr
/usr/share
/usr/share/doc
/usr/share/doc/antlr
/usr/share/doc/antlr/README.Debian
/usr/share/doc/antlr/copyright
/usr/share/doc/antlr/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/runantlr.1.gz

> find the antlr command,
So I guess that /usr/bin/runantlr is what I am looking for. The contents of that file are as follows:
```
#!/bin/sh
echo Running 'java antlr.Tool $*' with /usr/share/java/antlr.jar appended to the CLASSPATH variable
export CLASSPATH
CLASSPATH=$CLASSPATH:/usr/share/java/antlr.jar
java antlr.Tool $*
```

From this I think I need the /usr/share/java

> **strask said:**
> and make sure the directory is in your PATH environment variable. Then re-try your make.
And here you lost me. I don't really know what the 'PATH environment variable' is or how I can set it.

Could you maybe help me out a little bit more here..? 8-[

---

### Post by strask on 2012-05-01
Ok, fair warning here, I don't have a clue what antlr even is or what it is supposed to do.

BUT... it looks like that runantlr script is exactly what you want to be running. For some reason make is looking for antlr instead of runantlr. One quick way to fix this is to make a symbolic link (similar sort of to a windows shortcut) called antlr that points at the runantlr program.
```
sudo ln -s /usr/bin/runantlr /usr/bin/antlr
```That way, when make tries to run 'antlr' it actually runs 'runantlr', which starts the java program and passes it whatever arguments make wanted to pass it.

Edit: The PATH variable stores a list of directories that are searched for commands you type; I was thinking the antlr command ended up in a place not listed in your PATH, but /usr/bin is pretty much always in everyone's PATH so you don't need to worry about the path stuff at this point.

Second Edit: A better way might be to edit the Makefile and see if it has a place where you can change the antlr command to runantlr. Depends on your preferences.

---

### Post by kramer65 on 2012-05-01
Hi Strask. Thanks for your response.

I had a look at the makefile of java2python (which needs to use Antlr), but that only contains the following:
```
.PHONY: all clean lib
all: lib
clean:
	rm -f *.pyo
	rm -f *.pyc
	cd lib && $(MAKE) clean
lib:
	cd lib && $(MAKE)
```

So I made the symbolic link with your line of code and ....... IT WORKED!!

Thank you so much! Next to being able to build java2python, and in turn ibpy, I also learned another thing today: building symlinks.. :)

One more question. Are the files to run a program always in /usr/bin? (I've been looking for that before)

---

### Post by strask on 2012-05-01
Congratulations! Glad that worked out for you. :)

> **kramer65 said:**
> 
One more question. Are the files to run a program always in /usr/bin? (I've been looking for that before)

/usr/bin is the main location; others are /bin, /sbin, /usr/sbin, /usr/local/bin, and /usr/local/sbin. The ones that end in sbin are more system administration commands, while the ones that end in bin (without the s) are more user-level commands.

Note that there are exceptions to the above; commands are scattered all over the place really. But the bulk of everything you will ever need are in those directories.

---

