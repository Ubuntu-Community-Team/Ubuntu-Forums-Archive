---
title: "I'm horrible at navigating in Terminal"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-10-24
So, ever since I have had Ubuntu I never seem to grasp the concept and knowledge of navigating in Terminal. I have a folder called 'ushare-1.1a-NeToU' in my /home/*name*/ directory. I am suppose to navigate into it and run an install (that part I know), but I have tried everything I know to try and get into it and all I can do is get into the home folder, but I'm lost at what I have to do to get into the 'ushare-1.1a-NeToU' folder. Any help? Thanks. :(

---

### Post by suprfish on 2008-10-24
Terminal:

```

$    cd {username}
$    cd ushare-[TAB]
$    ls

```

Replacing {username} with your username and [TAB] with the keystroke. Post the output, maybe (not necessary)?

---

### Post by melojo on 2008-10-24
You can also do this.

```

cd ~
cd ushare*
ls
```

cd ~           
gets you to your home directory
cd ushare*     
the star is a wild card
ls             
list the files in the directory

---

### Post by mc4man on 2008-10-24
Just open a terminal and go 
```
cd ushare-1.1a-NeToU
```
that should bring you to a ~/ushare-1.1a-NeToU$ prompt.

You could also install nautilus-open-terminal
```
sudo apt-get install nautilus-open-terminal
```

This will give you a right click 'open in terminal' option - just use on a folder you want to open a terminal prompt at.

some examples
lets say I wanted to cd to a folder in home/other - The Jimi Hendrix Experience (1967) Electric Ladyland

If I right click on it - 'open in terminal' I get this terminal prompt (correct
> doug@doug-desktop:~/other/The Jimi Hendrix Experience (1967) Electric Ladyland$

If I wanted to manually cd from an open terminal and used this (errors because of spaces and symbols in path
> doug@doug-desktop:~$ cd ~/other/The Jimi Hendrix Experience (1967) Electric Ladyland
bash: syntax error near unexpected token `('
so I add 'or " to begining and end of path like this (correct
> doug@doug-desktop:~$ cd ~/other/'The Jimi Hendrix Experience (1967) Electric Ladyland'
doug@doug-desktop:~/other/The Jimi Hendrix Experience (1967) Electric Ladyland$


If I wanted to cd to a folder on desktop (correct
> doug@doug-desktop:~$ cd ~/Desktop/NeroDigitalAudio
doug@doug-desktop:~/Desktop/NeroDigitalAudio$ 

or also correct
[QUOTE]doug@doug-desktop:~$ cd /home/doug/Desktop/NeroDigitalAudio
doug@doug-desktop:~/Desktop/NeroDigitalAudio$
[/QUOTE]
incorrect (no capital on desktop
> doug@doug-desktop:~$ cd /home/doug/desktop/NeroDigitalAudio
bash: cd: /home/doug/desktop/NeroDigitalAudio: No such file or directory

if you wanted to cd somewhere out of home dir. then just use path
> doug@doug-desktop:~$ cd /usr/share/applications
doug@doug-desktop:/usr/share/applications$

---

### Post by patrickballeux on 2008-10-24
A tool that I use a lot in a terminal is Midnight Commander.  You can view/edit/zip/tar.gz/unzip/untar.gz/move/copy/access Samba share/access SSH share/etc...

It's an all in one tool that can do a lot of things using a nice interface that can even work over a SSH/Telnet terminal for remote access.


```
sudo apt-get install mc
```

Very useful and powerful!

---

### Post by coldcoffee on 2008-10-24
I am going to have to second the nautilus-open-terminal package. You can navigate to the directory you need the terminal to be active in and right click and you will get an option to open a terminal. If you select to open the terminal, it will open in the directory where you did the right click.

Works on Desktop too. If you right click and select terminal, it will open in your Desktop directory.

I had to log out then back in after I installed it for it to begin working though. So it is very possible you will have to do the same if you choose to install the package.

---

### Post by bpowell2005 on 2008-10-24
> **ImThatNerd said:**
> So, ever since I have had Ubuntu I never seem to grasp the concept and knowledge of navigating in Terminal. I have a folder called 'ushare-1.1a-NeToU' in my /home/*name*/ directory. I am suppose to navigate into it and run an install (that part I know), but I have tried everything I know to try and get into it and all I can do is get into the home folder, but I'm lost at what I have to do to get into the 'ushare-1.1a-NeToU' folder. Any help? Thanks. :(

Why drop to the terminal at all? You should be able to go to Places > Home Folder, then find the ushare-1.1a-NeToU folder; double click it, and then double-click the install program inside that folder. Unless you need to pass arguments to the installation program, you should be able to run it from the desktop.

---

### Post by bpowell2005 on 2008-10-24
> **ImThatNerd said:**
> So, ever since I have had Ubuntu I never seem to grasp the concept and knowledge of navigating in Terminal. I have a folder called 'ushare-1.1a-NeToU' in my /home/*name*/ directory. I am suppose to navigate into it and run an install (that part I know), but I have tried everything I know to try and get into it and all I can do is get into the home folder, but I'm lost at what I have to do to get into the 'ushare-1.1a-NeToU' folder. Any help? Thanks. :(

Also,

No shame in being bad at navigating in the terminal...it's a new world to a lot of people (myself included) and it's taken me some time to find my way around in there! But Ubuntu is great for learning how to navigate around in Linux...along with the community support, I've come a long way; you will too! :)

---

### Post by cyfur01 on 2008-10-25
One of the biggest keys to nevigating the terminal is tab completion. On Ubuntu Desktop, the tab completion is actually quite amazing.

Start typing the name of a command/file/folder/etc, and hit tab. If there's only one match, it will type the rest for you. Otherwise, you can hit tab a second time and it will show you a list of commands/files/etc that match your partial string.

Also note that the terminal won't interpret spaces, $'s and other special characters at the actual characters; these are special characters used for shell scripting. If you need to use one of these, preceed it with a backslash (\) and the following character will be interpreted literally. Alternatively, you can enclose strings with singlequotes (') and everything inside them will be interpreted literally too.
For example:```

cd 'foldername with spaces'  # works
cd foldername\ with\ spaces  # also works

```

Aside from this, just knowing cd and ls are the two commands that help with navigation.

For cd, there are several things to note:
1. The tilde (~) character is an alias for your home folder. Thus "cd ~/Desktop" is equivalent to "cd /home/user/Desktop"
2. The forward-slash (/) character is the root directory. This is the highest level to can change to within the file system.
3. ".." is an alias for the parent directory of your current working directory
4. "." is an alias for your current directory. Thus, if you want to execute a script from your current directory, you have to preface it as "./script", otherwise the shell will try to find the command "script" in your PATH (folders it looks in for commands).

For ls, the -a, -l and -h flags are probably the most useful. -a causes ls to display all hidden files and etc too. -l displays a lot more information about each file. -h displays the sizes of each file in the -l list in human readable form (K for KB, M for MB, etc, rather than just bytes). You can combine these too. (ie. ls -lah)

---

### Post by benner on 2008-10-25
2 tips i found useful...

if you didn't know, you can see hidden folders with ctrl + H

install 'nautilus-gksu' and you will be able to open any file as root (administrator) from the right click menu.

---

