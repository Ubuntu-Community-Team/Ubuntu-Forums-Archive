---
title: "List of applications"
date: 2019-04-04
forum: New to Ubuntu
---

### Post by vysero on 2019-04-04
Is there a way to view all the applications and programs that are on my Ubuntu machine? For instance, if I didn't already know how to open a terminal then its feasible that I would be able to use Ubuntu without every using a terminal right? This made me wonder, how many other useful applications are on my system that I will never know about?

---

### Post by oldfred on 2019-04-04
Not sure how to do it in apt, but you can install aptitude (more software) and run this:
       Top level only - no depends (not for reinstall)
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

---

### Post by yetimon_64 on 2019-04-04
> **vysero said:**
> Is there a way to view all the applications and programs that are on my Ubuntu machine? For instance, if I didn't already know how to open a terminal then its feasible that I would be able to use Ubuntu without every using a terminal right? ...

For GUI only I like Synaptic Package Manager and especially with the quick filter installed , like...

[ATTACH=CONFIG]282948[/ATTACH]
 
Synaptic is probably my favourite, non cli, tool in ubuntu-mate.
It may not be installed by default in standard ubuntu installs though ... but a simple terminal command can fix that :wink: ...

```
sudo apt install synaptic apt-xapian-index
```

There is still also a "software center" program for graphical interfaces, not sure exactly what it is called nowadays with the newer ubuntu releases. 

Cheers, yeti. :-)

---

### Post by again? on 2019-04-04
The applications overlay shows installed graphical applications including the terminal.
Ubuntu Software will also show installed graphical applications.
Which is really all the casual user needs.

However,if you wish to delve deeper you can see all installed packages (including a a huge list of libraries and dependencies)
with synaptic as shown by yetimon_64.
or via terminal...
```
apt list --installed
```

You can also use the terminal to show available commands...
```
compgen -c
```

Add the "whatis" command for a one line description taken from the command's manual page if it exists, and sort alphabetically.
```
whatis $(compgen -c) | sort
```

Send the output to a file for easier reading/searching(saves file in your home directory)...
```
whatis $(compgen -c) | sort > commands.txt
```

Most commands will have a manual page that you can view in terminal or at least a --help option.
eg
```
man whatis
whatis --help
```

Ubuntu also has an [online manual pages.]("http://manpages.ubuntu.com/")

---

### Post by Impavidus on 2019-04-05
In a sense, every executable file is a program. When you can call a program an application I can't say. Most of them are in /usr/bin. You'll find over 2000 programs there.

---

### Post by TheFu on 2019-05-16
> **vysero said:**
> Is there a way to view all the applications and programs that are on my Ubuntu machine? For instance, if I didn't already know how to open a terminal then its feasible that I would be able to use Ubuntu without every using a terminal right? This made me wonder, how many other useful applications are on my system that I will never know about?

Having a list of the manually installed packages is extremely helpful for backup purposes.
```
$ apt-mark showmanual | tee pkgs_manual.lst 
```

Have a list of automatically installed packages is useful for some other reasons, though I've never needed it.
```
$ apt-mark showauto
```

These are relatively tiny text outputs that can be redirected into a file. Backup the file and you have effectively made a way to perform a fresh Ubuntu install, then run 2 more commands and have all the applications from the prior install, installed into the new system. If the file with the manually installed packages is name "pkgs_manual.lst" as shown above, these commands will reinstall them on a fresh system.```

$ sudo apt-mark manual $(cat pkgs_manual.lst)
$ sudo apt-get -u dselect-upgrade
```
Of course, you can also few the file to see which programs were installed.

If you are interested in learning more about each program, almost all have "manpages". These are installed under /usr/share/man/ ... organized into different sections by the type of command.  The manpage for "man" explains the sections and how to access, search, read, each of them.  Run $ **man man** to access it.  Every major Unix-like OS has manpages installed, unless you specifically ask not to have them or the OS is stripped down to use minimal storage.

As said by Impavidus above, most end-user programs are in /usr/bin/, but administrative programs go into /sbin/ and /usr/sbin/.  These are for programs installed through the package manager.  For manually installed programs outside the package manager, those are most often placed into /usr/local/bin/ or /usr/local/sbin/ (for admin tools).  Programs can be manually installed almost anywhere, including by end-users into their own HOME directories.

You can use this command to search the entire file system for programs with executable permissions.  Just because a file has those permissions, doesn't mean it is a program.  People are often lazy about permissions, especially if they have non-Linux file systems like NTFS or vFAT.  Anyway, the command is:
```
$ find / -type f -executable -print
```
You'd be amazed at the number of scripts and programs for which you and I have little use that are installed.

---

### Post by leunam12 on 2019-05-18
```
sudo dpkg --get-selections
```

---

### Post by oldrocker99 on 2019-05-20
Synaptic, which every Ubuntu user should install, has a tab showing all installed programs.

And, by all means, add the Quick Filter as explained above.

---

### Post by TheFu on 2019-05-20
> **leunam12 said:**
> ```
sudo dpkg --get-selections
```

Getting the automatically installed packages leads to having cruft on a new install.  That's why I showed how to get the list of manually installed packages. These are the ones someone specifically said "install X" using the package manage.  Dependencies will be handled in the normal way.

Does synaptic have a way to export the list of manually installed packages?  Does it have a way to get that list imported on a fresh install?  I don't know the answer. Tried to figure it out and couldn't in about 5 minutes of looking. Perhaps I'm just dumb.

A GUI package manager tool is difficult to use on a server 2000 miles away.

---

