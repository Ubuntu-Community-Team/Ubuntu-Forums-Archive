---
title: "run a script when shutdown computer"
date: 2006-05-31
forum: Programming Talk
---

### Post by Pilsner on 2006-05-31
Hello all!!

Hope I am in right forum and so.

Well. I have created a small script I can run sometimes to free some space from computer.

I have created a file "rensa.bin"
```
rm -rf /home/erik/.thumbnails/normal/*
rm -rf /home/erik/.thumbnails/fail/gnome-thumbnail-factory/*
rm -rf /home/erik/.Trash/*
rm -rf /home/erik/.mozilla/firefox/pl7hilo9.default/Cache/*
```

I have made it executable on the desktop. It runs a command "sh rensa.bin"
I can use this script and it erase the contents in these directories.
This is not so important but I think its fun to make something automatic.

I wonder how do I integrate this script when computer shutdown?
So I dont need to run from desktop...

---

### Post by Klaidas on 2006-05-31
On shutdown: don't really know, sorry
My advise would be to setup cron to execute that script let's say, every 2 hours.
[https://wiki.ubuntu.com/CronHowto](https://wiki.ubuntu.com/CronHowto)

---

### Post by Zed on 2006-05-31
In the UNIX world, such shell scripts normally begin with a "shebang" line:

```

#!/bin/sh

```

and the filename gets the suffix '.sh'. Then you can just mark it executable:

```

chmod +x rensa.sh

```

and you can just run it as is (if it exists somewhere in your command path) without having to say 'sh rensa.sh'.

To have it run at shutdown, this should do it:

```

sudo cp rensa.sh /etc/init.d
sudo ln -s /etc/init.d/rensa.sh /etc/rc0.d/K10rensa.sh
sudo ln -s /etc/init.d/rensa.sh /etc/rc6.d/K10rensa.sh

```

For some background as to why this works:

[An introduction to run-levels](http://www.debian-administration.org/articles/212)

---

### Post by Pilsner on 2006-06-01
It works! Thank you.

---

### Post by linuxnovice on 2008-08-21
Is it necessary to put the script in int.d for running it on shutdown?

---

### Post by xouns on 2008-08-21
Can't you put in a script to reboot or shutdown the computer? like sudo reboot/ sudo shutdown?

---

### Post by linuxnovice on 2008-08-21
umm..i am not sure i understand what you mean..?

---

### Post by mssever on 2008-08-21
> **linuxnovice said:**
> Is it necessary to put the script in int.d for running it on shutdown?
The script has to be in /etc/rc{0,6}.d to run on shutdown and reboot. Convention is for the script itself to live in /etc/init.d and for there to be symlinks to it from the proper rc*.d directories. You should follow the convention unless you have a very good reason for doing otherwise.

In Ubuntu, there's another method available: Upstart. Upstart is event-based, and theoretically more flexible. I've never messed with it, though, so I couldn't tell you how to use it.

---

### Post by Zugzwang on 2008-08-21
> **linuxnovice said:**
> umm..i am not sure i understand what you mean..?

He/She means that you just copy your commands to a script, append the command to shutdown the computer and in the future use this script to shotdown the computer instead of the usual GNOME System->Quit menu command or whatever.

For adding your script to the boot sequence, look at [http://ubuntuforums.org/showthread.php?t=669165&highlight=bootup]("http://ubuntuforums.org/showthread.php?t=669165&highlight=bootup")
this post by me - It tells you how to install a custom script to the bootup&shutdown sequence. It also tells you how to revert these changes. Note that your script will then be run at bootup&shutdown. However, you can check what is the case. So your code should look like:
[PHP]
#!/bin/bash

if [ "$1" = "stop" ]
then 
  ....
fi
[/PHP]

---

### Post by MarkieB on 2008-08-21
no longer participating in ubuntuforums.org

---

### Post by roccivic on 2008-08-21
What's wrong with running the script on startup? It's essentially the same thing, isn't it? And it's way easier to implement, just go to System -> Preferences -> Sessions
Then in the "Startup Programs" add your script as a new program to run.

Rouslan

---

### Post by jinksys on 2008-08-21
> **roccivic said:**
> What's wrong with running the script on startup? It's essentially the same thing, isn't it? And it's way easier to implement, just go to System -> Preferences -> Sessions
Then in the "Startup Programs" add your script as a new program to run.

Rouslan

Because then his tracks would still be on the system after he shuts down and someone else logs in.

---

### Post by Jacdeb6009 on 2008-08-30
This is very useful, but there is something strange that happens on my machine...

If I issue:

rm -rf /home/gandalf/.thumbnails/fail/gimp-2.2/*

The command executes and the directory is emptied of files, however, if I issue the command :

rm -rf /home/gandalf/.thumbnails/large/*

The following error is returned and nothing happens :

bash: /bin/rm: Argument list too long

Clearly the rest of the process describer in the thread (i.e making the script executable and linking it to the shutdown or re-boot process) also does nothing.

Anybody have any idea what the problem is??

Please help because this is a most useful little script and also a nice example of how to include things in the shut down process of the machine.

---

### Post by Jacdeb6009 on 2008-08-30
Aaaahhhh! Problem is there are too many files in the folder.  So clearly rm can only accept a limited number of files as part of the "argument"

Question then is what is the limitation on this...??

Anyone have any ideas

---

### Post by Reiger on 2008-08-30
> **xouns said:**
> Can't you put in a script to reboot or shutdown the computer? like sudo reboot/ sudo shutdown?

Yes. For a generic command (which jumps to various levels of services, 6 being the default session; 0 being power off...)

```

sudo init <value>

```

Alternatively:
Power off after shutdown:
```

sudo shutdown -h -P now

```

Reboot:
```

sudo shutdown -r

```

EDIT: For more information regarding the shutdown command type: ```
shutdown --help
```

---

### Post by lswb on 2008-08-30
/etc/init.d is not an appropriate place for a script that runs on the home directory of a user. Add the #!/bin/bash line at the start of the script, and chmod +x it like an earlier poster suggested. Then add a line to call the script to the file .bash_logout, which is a script that is run whenever the login shell exits. Or you could add the commands directly to the .bash_logout file.

Also, you can just remove the entire .thumbnails directory tree. It will be recreated as needed by gnome.

---

### Post by Jacdeb6009 on 2008-08-30
> **lswb said:**
> /etc/init.d is not an appropriate place for a script that runs on the home directory of a user. Add the #!/bin/bash line at the start of the script, and chmod +x it like an earlier poster suggested. Then add a line to call the script to the file .bash_logout,...

Please excuse my ignorance, but why is it not appropriate to place a script like this in /init.d

I think I sort of understand, but a proper explanation would be helpful.

Thanks!

---

### Post by lswb on 2008-08-30
The init.d scripts are run with root permission levels. The scripts themselves are owned and executable by root. Their purpose is starting and stopping system services at boot and shutdown, not running user-level scripts or processes. The init.d scripts are run whenever the systems starts or stops (or runlevel changes), even if a particular user (meaning _you_ in this case) has not logged in.

Your script only references user-owned files and needs no elevated priveledge levels. Suppose you were not an adminstrator on your system (no sudo privledges), you would not even be able to modify and install your script in the init.d directory. Or suppose a user on a multi-user system, _did_ have the ability to install and run scripts in init.d. A malicious user could use that to view and manipulate private information in other users home directories. 

As a general rule of security, don't use root-level scripts or commands to do what can be accomplished at the user level.

---

### Post by Jacdeb6009 on 2008-08-30
Thanks! That explains it nicely!!

---

### Post by mssever on 2008-08-31
> **Jacdeb6009 said:**
> Aaaahhhh! Problem is there are too many files in the folder.  So clearly rm can only accept a limited number of files as part of the "argument"

Question then is what is the limitation on this...??

Anyone have any ideas
Actually, the limit is the maximum length of a command in bash. I don't know what that limit is. There are several ways to work around such limits. One is to use a for loop: ```
for i in ~/.thumbnails/*;do
    rm "$i"
done
```This code works, but it's quite inefficient. It's better to exploit the find command. Unfortunately, I'm to lazy to remember how to use it. It's easier for me to write up a for loop then to read the manual for find.

---

### Post by ghostdog74 on 2008-08-31
> **mssever said:**
>  I don't know what that limit is.

its in limits.h
```
 # grep ARG_MAX /usr/include/linux/limits.h
#define ARG_MAX       131072    /* # bytes of args + environ for exec() */

```

> 
 There are several ways to work around such limits. One is to use a for loop: ```
for i in ~/.thumbnails/*;do
    rm "$i"
done
```This code works, but it's quite inefficient. It's better to exploit the find command. Unfortunately, I'm to lazy to remember how to use it. It's easier for me to write up a for loop then to read the manual for find.

find with xargs.

---

### Post by lswb on 2008-08-31
Using find or looping through the directory is really not necessary in this case. Instead of removing files, the .thumbnails directory or any of its subdirectories can be removed i.e. 

rm -r .thumbnails

without affecting anything. The thumbnailer process will create a new directory when needed.

---

### Post by SaintDanBert on 2011-01-05
> **Jacdeb6009 said:**
> Aaaahhhh! Problem is there are too many files in the folder. ... So clearly rm can only accept a limited number of files as part of the "argument"

Question then is what is the limitation on this...??

Anyone have any ideas

[highlight]RE: "too many arguments"[/highlight]

When you type the command
```

prompt$ rm -v /path/*

```

Your shell, probably **bash**, replaces the path+star (or splat or ...) wildcard with "/path/name1 /path/name2 .../path/nameN" for everything that matches the wildcard. The "too many arguments" error is a complaint from the shell and not from the rm command.

I scanned **man bash** and did not find a stated limit. From programming, I know that the command line is *an array of pointers to arrays of NUL-terminated character strings* -- specifically *char * argv[]* (sorry for the technobabble). So I'm certain there is a compiled in limit somewhere.

[highlight]RE: remove large number of files[/highlight]

When I need to remove a large number of files I use one of the following:
[list=1]
[*] remove the entire folder and make a fresh but empty folder of the same name.
```

prompt$ ls /some/folder/*
... too many files to count ...
prompt$ rm -f /some/folder
prompt$ mkdir /some/folder
.... start adding files into /some/folder/*

```
This only works if you don't want anything that is already there.
If /some/folder contains other folders, use **rm -rf** to remove them as well. I leave recreation of the sub-folders to the reader.
[*] remove files with a complex file name pattern
```

prompt$ find /some/folder -name "pattern" -type f -exec rm --interactive --verbose "{}" \;

```

The **find** command handles the search and pattern matching and limits the actions to plain files not folders or others.

For each matching file, "-exec ..." runs the stated command.

In this case, we "remove" files, asking for end-user confirmation (--interactive) and announcing what we did (--verbose).
[*] If the file collection is large and varied in content, I'll create a tar archive.
```

[color=green]
prompt$  # tar will see the file-type "tgz" to enable gzip compression
prompt$  # other compression tools are in the man-page[/color]
prompt$  tar --create --file blackhole.tgz --remove-files --verbose  list-of-files

```
(I leave creation of a suitable list-of-files for tar to the reader.)

Here everything gets copied into the archive and then removed from wherever it lived by tar itself leaving only the archive copy.
[/list]

Bonne Chance,
~~~ 0;-Dan

---

### Post by seydou on 2011-02-22
> **mssever said:**
> Actually, the limit is the maximum length of a command in bash. I don't know what that limit is. There are several ways to work around such limits. One is to use a for loop: ```
for i in ~/.thumbnails/*;do
    rm "$i"
done
```This code works, but it's quite inefficient. It's better to exploit the find command. Unfortunately, I'm to lazy to remember how to use it. It's easier for me to write up a for loop then to read the manual for find.

That is what this forum is for, to substitute reading of manuals :P. It is rather easy and straightforward, using the magic of "-exec":

```

find ~/.thumbnails/ -type f -exec rm -f {} \;

```

Note, that find must be followed by the path we want to search and the meaning what follows is:

"-type f" :  we look only for object type file, d would be for directory, have a look to man page for more.

"-exec rm -f {} \;" : all which falls between -exec and final ";" gets executed, when the the file is hit. {} sunstitutes the filename, and since ";" has a special meaning for bash, it has to be escaped \; so it gets processed by find rather than by shell.

Do not be scared of find, it is a lot more than just a search tool.

---

