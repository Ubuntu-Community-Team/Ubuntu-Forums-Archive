---
title: "How to create shortcut with paramters"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by TERW_DAN on 2011-09-28
I've 'installed' eclipse on my Ubuntu 11.04 system, but it is unable to find the JRE that is installed. 
 
This is easily fixed by adding -vm and the path as paramater for the executable and this works. But is very annoying everytime I want to start eclipse to ype this. 
 
In windows you can easily make a shortcut to the executable and add the paramaters. In Ubuntu I can make a link, but it is impossible to add paramaters. 
 
Is this an impossibility, or how can I edit the target of a link?

---

### Post by pvjlieuthier on 2011-09-28
It would be better to install the JRE appropriately.
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```If it isn't enough, then go to Eclipse configurations and let it know the path you've installed java (if you did on your own). You could also reinstall eclipse after installing java.
```
sudo apt-get install --reinstall eclipse
```And of course, if want to do some programming in java, you need JDK, not JRE...

```
sudo apt-get install openjdk-7-jdk
``` or ```
sudo apt-get install sun-java6-jdk
```Good luck!

---

### Post by androssofer on 2011-09-28
> **TERW_DAN said:**
> I've 'installed' eclipse on my Ubuntu 11.04 system, but it is unable to find the JRE that is installed. 
 
This is easily fixed by adding -vm and the path as paramater for the executable and this works. But is very annoying everytime I want to start eclipse to ype this. 
 
In windows you can easily make a shortcut to the executable and add the paramaters. In Ubuntu I can make a link, but it is impossible to add paramaters. 
 
Is this an impossibility, or how can I edit the target of a link?

another option is to make a script that does it, then get the shortcut to call tht script...

---

### Post by TERW_DAN on 2011-09-29
> **pvjlieuthier said:**
> It would be better to install the JRE appropriately.

 That is not an option, I finally got the correct java working for Android, so I cannot update it.

---

### Post by TERW_DAN on 2011-09-29
> **androssofer said:**
> another option is to make a script that does it, then get the shortcut to call tht script...
 But something simple as making a shortcut isn't possible?
 
I have no clue how to make a script, I just want an easy shortcut, nothing more.

---

### Post by ninjaaron on 2011-09-29
> **TERW_DAN said:**
> But something simple as making a shortcut isn't possible?
 
I have no clue how to make a script, I just want an easy shortcut, nothing more.

A script can effectively be an 'easy shortcut.'  Just make text file (with no extention) with exactly the command you want to run, close it, and mark it as executable.

You can make it executable by right clicking it, then going to "properties,"  and in the "permissions" dialogue, you can mark it as executable by ticking a box.  You can also use this command:

```
chmod +x /path/to/file
```

... with the path to your file in place of "/path/to/file."

~~~~~~~~~~~~~~~~~~~

A script in linux is just a bunch of shell commands strung together.  Anything you find yourself repeating at the terminal  can (and should) be scripted.  If you want more logical operators, it may be helpful to specify the shell language in a header, but, for making custom shortcuts, this will be perfectly fine.  If you are a developer and you are switching to Linux, you will probably want to learn about the power of shell scripting sooner than later.

Should you want to do that, [this]("http://tldp.org/LDP/abs/html/") is an excellent resource.

---

### Post by ninjaaron on 2011-09-29
Also, I forgot about this, but you can also make custom launchers in the main menu and on the desktop.  On the desktop, you simply right click, and go to "create new launcher," and you can specify your command there.  This is essentially the same as a script, but you won't have to mark it as executable, and it only runs one command line (though you could stack a number of commands into that).  There is a program called "main menu" that allows you to edit menu items.  If you are using Unity, you may have to logout before changes appear in the dash.

I forgot about this because you said "Link," and a link is something rather different in Linux.  Links have to do with locations and data structiure, not commands.  Launchers and scripts run commands.

---

### Post by TERW_DAN on 2011-09-30
> **ninjaaron said:**
>  
I forgot about this because you said "Link," and a link is something rather different in Linux. Links have to do with locations and data structiure, not commands. Launchers and scripts run commands.
 Well, Ubuntu calls it a link, so I thought it was the correct term for it
 
I'll try making a scriptthingy, I hope it works.

---

### Post by ninjaaron on 2011-09-30
> **TERW_DAN said:**
> Well, Ubuntu calls it a link, so I thought it was the correct term for it
 
I'll try making a scriptthingy, I hope it works.

Let's try to get this clarified:

In Ubuntu, a link is techincally a "soft system link."  It can link to any file, be it a folder, an executable binary, an image, a song... it makes a link to any **location**.  What it does not do is execute a command, so you can't add tags or something to it, cause the system will try to read it as a location.  When you click "create a link" you are creating a system link to the location of the original file.

Links are excellent for directories.  You can make a link to a folder, and then you can use it in path names as if the original folder was really where the links are.  This goes for most commands except for commands executed directly on the link: If you use rm, mv, cp, etc... these commands will remove, move, or copy the link, not the original folder.  (Links can also be nice for things like sharing configuration files across operating systems in mounted partitions, but that's another matter altogether.)

Launchers are designed for executing a single command or program (with flags and everything).  They can also open locations and folders, but are not particularly well suited to this task.  They certainly don't fold themselves into the directory structure as nicely.

Shell scripts can execute as many commands as you like, can receive user input, and do caluculations.  In fact, shell scripts can also execute commands from more advance scripting languages like perl and python (and maybe java script?).  Even without these languages, you can certially write working programs using shell commands alone, though it is probably not the most efficient way to write a complex program.

The beauty of the script, however, is the real beauty of Unix:  Everything can be piped in and out of the script.  This means that that your scripts can do anything any command-line app can do.  It can take their output, manipulate it or preform calulations from it, and feed it into another program to preform another function.  Endless possiblity through elegant simplicity, that's Unix.  If you ever care to look at some of the core system files, you will find that most of them are simple shell scripts.  The the boot process and most system daemons are controlled by simple, plain text shell scripts.  This is the key to Linux's endless customizability, everything is human-readable and human-writable.

Sorry to gush.  I just get really excited about scripts.

Shell scripts, like launchers and unlike links, will not become part of your directory structure.

---

