---
title: "How do I invoke a program I just installed ?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by jefisher on 2008-05-31
I'm new at Linux but got 8.04 up and running ok. Then I downloaded a program called routeplanner. After it was installed, it does not show up under Applications so how do I get it to run. I found it loaded under
/usr/share/routeplanner but I don't know what I have to do to invoke it. Can anyone give me some help on this??

Thanks

---

### Post by FuturePilot on 2008-05-31
Perhaps in a terminal (Applications&#8594;Accessories&#8594;Terminal) enter
```
routeplanner
```

---

### Post by IHATEDLINK on 2008-05-31
> **jefisher said:**
> I'm new at Linux but got 8.04 up and running ok. Then I downloaded a program called routeplanner. After it was installed, it does not show up under Applications so how do I get it to run. I found it loaded under
/usr/share/routeplanner but I don't know what I have to do to invoke it. Can anyone give me some help on this??

Thanks

Try typing in Terminal (Applications>Accessories>Terminal)
```
routeplanner
OR
route-planner
```

---

### Post by ChameleonDave on 2008-05-31
OK, I've just installed the "routeplanner" and "routeplanner-gnome" packages to see.

Once installed, click on the "installed files" tab in Synaptic, and you can see exactly what the packages have given you.  You should be especially interested in the contents of "bin" directories.

From this, I can see that you can invoke binaries such as "rplan", "rpcli", "grplan", and "gredit".

I believe that packages should always install shortcuts from intuitive names to counter-intuitive names.  I seem to be in a minority.

---

### Post by Prospero2006 on 2008-05-31
Remember, when you are using the terminal 'tab' will autocomplete anything that matches what you started typing that is in the system path.

So:

gnome-(tab)

Will give a list of all application that start with gnome-

gnome-p(tab) 
 will result in gnome-panel being autocompleted.

That might help,

---

### Post by ChameleonDave on 2008-05-31
> **Prospero2006 said:**
> 

That might help,

How could that possibly help now?

---

### Post by ad_267 on 2008-05-31
Once you sort out the command you need to run the program you can add a launcher for it in the menu by right clicking on the menu and select "Edit Menus" then add a new item in the category you want.

---

### Post by inaety on 2008-06-01
> **ChameleonDave said:**
> How could that possibly help now?

routeplanner vs. route-planner

---

### Post by ChameleonDave on 2008-06-01
> **inaety said:**
> routeplanner vs. route-planner

That was a rhetorical question.

---

### Post by jefisher on 2008-06-01
Tried it, but didn't work.
Thanks

---

### Post by jefisher on 2008-06-01
No luck. I can find the program under /usr/share/routeplanner but none of the files seem to be executable. What should the extension be for an executale file in Linux?
Thanks

---

### Post by ad_267 on 2008-06-01
Executable files usually don't have extensions.

An executable file needs to have it's permissions set to allow executing as a program but this should be done already.

> From this, I can see that you can invoke binaries such as "rplan", "rpcli", "grplan", and "gredit".

Try running these files if they are there. Type "./grplan" or "./grplan" etc from in the directory where they are located.

---

### Post by Xiong Chiamiov on 2008-06-01
As a sidenote, if you ever can invoke an app by simply its name, but don't know where it's at, you can use the whereis command, like
```

whereis gedit

```

As I think someone else said, you can view where files are installed from Synaptic.  Check all those folders to find one that has the binary.

---

### Post by ChameleonDave on 2008-06-01
> **jefisher said:**
> No luck. I can find the program under /usr/share/routeplanner but none of the files seem to be executable. What should the extension be for an executale file in Linux?
Thanks

Executables have no particular extension in Linux.    They may have something like .sh or .py if the programmer wishes to indicate what language they are written in, but most of the time they are binary files with no extension.  Linux on the whole works out what a file does by looking at the contents of the file rather than the name. If you enter the command "ls -l", you will see the full details of all the files in a given directory, with an "x" next to those which are flagged as executable (note that any file can be so flagged).  In general, executables are stored in directories named "bin".

Here is the full list of files install by the package "routeplanner".  I have marked the executables in **bold**.

```

/.
/usr
/usr/bin
**/usr/bin/rplan**
**/usr/bin/rpcli**
/usr/share
/usr/share/routeplanner
/usr/share/routeplanner/rpcity.py
/usr/share/routeplanner/rpcitylist.py
/usr/share/routeplanner/rpcli.py
/usr/share/routeplanner/rpcountry.py
/usr/share/routeplanner/rpdbase.py
/usr/share/routeplanner/rpnewt.py
/usr/share/routeplanner/rpprogress.py
/usr/share/routeplanner/rproute.py
/usr/share/routeplanner/rpunits.py
/usr/share/routeplanner/Basic-USA.rpl3.gz
/usr/share/routeplanner/NorthAmerica.rpl3.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/rplan.1.gz
/usr/share/doc
/usr/share/doc/routeplanner
/usr/share/doc/routeplanner/README
/usr/share/doc/routeplanner/TODO
/usr/share/doc/routeplanner/changelog.gz
/usr/share/doc/routeplanner/faq.html
/usr/share/doc/routeplanner/styleguide-routeplanner-na.txt
/usr/share/doc/routeplanner/copyright
/usr/share/doc/routeplanner/RoutePlanner.guide.gz
/usr/share/menu
/usr/share/menu/routeplanner
/usr/share/man/man1/rpcli.1.gz

```

Here is the same for the package "routeplanner-gnome":

```

/.
/usr
[b]/usr/bin
/usr/bin/gredit
/usr/bin/grplan[/b]
/usr/share
/usr/share/routeplanner
/usr/share/routeplanner/routeedit.glade2
/usr/share/routeplanner/routeplanner.glade2
/usr/share/routeplanner/gredit.py
/usr/share/routeplanner/rpgnome.py
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/gredit.1.gz
/usr/share/doc
/usr/share/doc/routeplanner-gnome
/usr/share/doc/routeplanner-gnome/copyright
/usr/share/doc/routeplanner-gnome/changelog.gz
/usr/share/menu
/usr/share/menu/routeplanner-gnome
/usr/share/man/man1/grplan.1.gz

```

This mean that, for example, you can type "/usr/bin/rplan" into a terminal, and the program will start.

I doubt very much that it is necessary to type the full path.  Typing "rplan" by itself will almost certainly work, because "/usr/bin/" is no doubt one of the locations that the terminal automatically looks in to find executables when you type commands.

---

