---
title: "Bash Script Request (someone please!! :)"
date: 2007-11-04
forum: Packaging and Compiling Programs
---

### Post by notaloafer on 2007-11-04
Right now I have a program that needs to be run at startup as a daemon process so I don't have to run it in a gnome terminal. Right now the commands to start it are:

su - jbls
(enterpasswords)
cd Desktop/JBLS
java -jar JBLS.jar

This program runs in a terminal text-only window. However I don't like running it on my gnome desktop. 

I asked someone on MSN how to create a BASH script to auto-run at startup and he said the following:

```

Eric: it runs in terminal
Eric: is it easy to daemon-tize it so it auto runs when i start up my server
Tex: hmm
Eric: and so i dont have to run it in gnome? (i usually turn gnome off when im not using it)
Tex: you *might* be able to do that with a script
Tex: does the java app display something graphical?
Eric: nope
Eric: just runs text-base in terminal
Tex: hmm... then you could just make a bash script that contains the startup commands, then put your bash script in /etc/rc.local so that it's run at boot
Tex: that'd be easiest
Eric: hm
Eric: i found /etc/rc.local and opened it
Eric: and theres nothing in it
Eric: how do i go about making a bash script?
Tex: bash scripts are easy, and they look like this:
Tex: #!/bin/bash
 cd /somedirectory
 ./somescript
Eric: ooh ok
Tex: just put the commands you usually run within that script
Tex: then make it executable:
Tex: chmod +x yourbashscript.sh
Tex: then put this in /etc/rc.local
Tex: /bin/bash /path/to/your/bashscript.sh
Eric: ah i see
Tex: good to go
Eric: thanks
Tex: well, if the java app hangs, there is a possibility that your bootup could hang :-/

```


I would do it myself but I have no idea how to make a BASH script or where to start with it... I also don't want to risk making my server un-bootable by a mis-configuration.

Thanks!
-Eric

---

### Post by notaloafer on 2007-11-04
Did i post this in the right forum?

---

### Post by Railsbuntu on 2007-11-05
First create a file inside /etc/init.d and make it executable:

> sudo touch /etc/init.d/myscript && sudo chmod 755 /etc/init.d/myscript

You can open your favorite text editor, for instance vim, so at command prompt:
```
$ sudo vim /etc/initd.d/myscript
```
Then inside your edito type in the shell commands you would usually type to perform the wanted task. See how each script starts with the same declaration **#!/bin/bash**

So inside your editor you type:
```
#!/bin/sh
 cd /somedirectory
ls -la
```

Save the file.

Then tell Ubuntu you want to add this script to the startup process:
> $ sudo update-rc.d myscript defaults

EDIT: actually when running update-rc.d, the "defaults" parameter might be inappropriate. It depends on what you script does at each run level.

---

### Post by jpkotta on 2007-11-06
If you don't need to run it as root, you should use su to run it as your user.

```
su -c "command arg1 arg2" -- username
```

---

### Post by Railsbuntu on 2007-11-06
It seems Gutsy uses**upstart**, see for more info: [http://upstart.ubuntu.com/index.html]("http://upstart.ubuntu.com/index.html")

---

### Post by notaloafer on 2007-11-16
> **Railsbuntu said:**
> First create a file inside /etc/init.d and make it executable:



You can open your favorite text editor, for instance vim, so at command prompt:
```
$ sudo vim /etc/initd.d/myscript
```
Then inside your edito type in the shell commands you would usually type to perform the wanted task. See how each script starts with the same declaration **#!/bin/bash**

So inside your editor you type:
```
#!/bin/sh
 cd /somedirectory
ls -la
```

Save the file.

Then tell Ubuntu you want to add this script to the startup process:


EDIT: actually when running update-rc.d, the "defaults" parameter might be inappropriate. It depends on what you script does at each run level.


I think I understand this... but if I mess up (which I probably will; trial & error), will my server restart still or completely hang? If it hangs is there a ubuntu-version of a safemode?

-Eric

---

### Post by notaloafer on 2007-11-16
Here's what I've come up with so far:

1) Run command 
```
sudo touch /etc/init.d/jbls && sudo chmod 755 /etc/init.d/jbls
```

2) Open it up in VIM: sudo vim /etc/init.d/jbls
3) add the following:
```
#!/bin/sh
su - jbls 
hardcode password here
cd /home/jbls/Desktop/JBLS
java -jar JBLS.jar
```

4) Test to see if it works by running 
```
sudo /etc/init.d/jbls start
```

I think I'm missing some key information here.. but the directory that the JAR file resides in is in /home/jbls/Desktop/JBLS ...

Do these steps seem right or even close?

Thanks so much for your guys' help!
-Eric

---

### Post by Martje_001 on 2007-11-16
If your script fails it doesn't hang your computer. It will only give an error message.

---

### Post by notaloafer on 2007-11-17
Okay thanks for that assurance =). My other question: How does my script look that I posted above (as far as all the steps to creating it and the actual script content)?

Thanks!
-Eric

---

### Post by Martje_001 on 2007-11-17
Looks OK to me.You don't have to type your password since your root at startup (correct me if i'm wrong).

---

### Post by ddixonr on 2008-03-21
What does the "!" do in [ #!/bin/bash ] or [#!/bin/sh ] ?

I am a complete noob in saving bash scripts, but I've managed to complete two that I needed. First one was to close a stuck Firefox:

```
#/bin/bash
killall firefox-bin
```

And the second was to quickly empty trash:

```
#/bin/bash
-rf ~/.Trash/*
```

These worked nicely for me. Saved them as .sh filenames, dragged them to the panel for accessibility and life is grand.

---

### Post by WW on 2008-03-21
The following quote is from [http://tldp.org/LDP/abs/html/sha-bang.html:](http://tldp.org/LDP/abs/html/sha-bang.html:)
> 
The sha-bang ( #!) at the head of a script tells your system that this file is a set of commands to be fed to the command interpreter indicated. The #! is actually a two-byte magic number, a special marker that designates a file type, or in this case an executable shell script (type man magic for more details on this fascinating topic). Immediately following the sha-bang is a path name. This is the path to the program that interprets the commands in the script, whether it be a shell, a programming language, or a utility. This command interpreter then executes the commands in the script, starting at the top (line following the sha-bang line), ignoring comments.

Without the !, the first line of your scripts is just a comment.

---

