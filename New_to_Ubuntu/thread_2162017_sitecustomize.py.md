---
title: "sitecustomize.py"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by Sky001 on 2013-07-12
Hello everyone, 

Why is this operating system so over my head. It takes hours to do research and find a simple solution to a problem. All I want is to have a working version of python3.x and have tkinter actually be functional. 

Because everytime I think I've fixed something, I break two more. I'm not sure what I am dealing wth here. What is sitecustomize.py and how do i stop it from being so problematic? Every time I run sudo apt-get upgrade, I get the following list of problems. 
```

:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.                                                                                                                                      
                                      
                          
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python3.2-minimal (3.2.3-0ubuntu3.3) ...
**# Empty sitecustomize.py to avoid a dangling symlink**
/var/lib/dpkg/info/python3.2-minimal.postinst: 53: /var/lib/dpkg/info/python3.2-minimal.postinst: python3.2: not found
dpkg: error processing python3.2-minimal (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 python3.2-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm not sure how to empty sitecustomize.py, but this is preventing from installing the tkinter package. Any suggestions?

I also tried to do an install, sudo apt-get install python3.2-minimal but had to deal with the same problem, > Empy site costomize.py to avoid a dangling symlink. What does that even mean? Below is the full scenario
```

:~$ sudo apt-get install python3.2-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3.2-minimal is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-45 linux-headers-3.2.0-45-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python3.2-minimal (3.2.3-0ubuntu3.3) ...
**# Empty sitecustomize.py to avoid a dangling symlink**
/var/lib/dpkg/info/python3.2-minimal.postinst: 53: /var/lib/dpkg/info/python3.2-minimal.postinst: python3.2: not found
dpkg: error processing python3.2-minimal (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of python3-minimal:
 python3-minimal depends on python3.2-minimal (>= 3.2.3-0ubuntu3.3); however:
  Package python3.2-minimal is not configured yet.
dpkg: error processing python3-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3.2:
 python3.2 depends on python3.2-minimal (= 3.2.3-0ubuntu3.3); however:
  Package python3.2-minimal is not configured yet.
dpkg: error processing python3.2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                    Errors were encountered while processing:
 python3.2-minimal
 python3-minimal
 python3.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any suggestions?

Thank you, I really appreciate any help out of his situation.

---

### Post by Sky001 on 2013-07-13
I know someone out there has an answer. Please help. I'm really stuck here.
Edit: Should I just repost this in specialized support or some other more technical sub forum?

---

### Post by newb85 on 2013-07-13
What release of Ubuntu are you using?  My 13.04 system has Python 3.3 and Tkinter both installed, and I think that was by default.

Try this:
```
sudo apt-get remove python3.2-minimal
sudo rm -iv /etc/python3.2/sitecustomize.py
sudo apt-get install python3.2-minimal
```

Note: I posted the interactive verbose form of the rm command.  Read what it asks before agreeing.  The objective is to remove the sitecustomize.py symlink.

---

### Post by Sky001 on 2013-07-13
@newb85
I'm running 12.04 Precise Pangolin. Unfortunately, the sitecustomize.py is persistent. Below is what I got after running your terminal commands. 

```
:~$ sudo apt-get remove python3.2-minimal
[sudo] password for saipal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-45 linux-headers-3.2.0-45-generic-pae
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  python3.2 python3.2-minimal
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 14.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 559094 files and directories currently installed.)
Removing python3.2 ...
Removing python3.2-minimal ...
Unlinking and removing bytecode for runtime python3.2
find: `/usr/lib/python3': No such file or directory
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...

:~$ sudo rm -iv /etc/python3.2/sitecustomize.py
rm: cannot remove `/etc/python3.2/sitecustomize.py': No such file or directory

:~$ sudo apt-get install python3.2-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-45 linux-headers-3.2.0-45-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python3.2
Suggested packages:
  python3.2-doc binfmt-support
The following NEW packages will be installed:
  python3.2 python3.2-minimal
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/4,238 kB of archives.
After this operation, 14.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package python3.2-minimal.
(Reading database ... 558330 files and directories currently installed.)
Unpacking python3.2-minimal (from .../python3.2-minimal_3.2.3-0ubuntu3.3_i386.deb) ...
Selecting previously unselected package python3.2.
Unpacking python3.2 (from .../python3.2_3.2.3-0ubuntu3.3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up python3.2-minimal (3.2.3-0ubuntu3.3) ...
**# Empty sitecustomize.py to avoid a dangling symlink**
Traceback (most recent call last):
  File "/usr/lib/python3.2/py_compile.py", line 187, in <module>
    sys.exit(main())
  File "/usr/lib/python3.2/py_compile.py", line 179, in main
    compile(filename, doraise=True)
  File "/usr/lib/python3.2/py_compile.py", line 111, in compile
    with tokenize.open(file) as f:
  File "/usr/lib/python3.2/tokenize.py", line 343, in open
    buffer = builtins.open(filename, 'rb')
IOError: [Errno 2] No such file or directory: '/usr/lib/python3.2/sitecustomize.py'
dpkg: error processing python3.2-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python3.2:
 python3.2 depends on python3.2-minimal (= 3.2.3-0ubuntu3.3); however:
  Package python3.2-minimal is not configured yet.
dpkg: error processing python3.2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
           Errors were encountered while processing:
 python3.2-minimal
 python3.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by newb85 on 2013-07-14
Hmm...let's see if /etc/python3.2/sitecustomize.py is back
```
ls /etc/python3.2 | grep sitecustom
```

If it's there, then check this:
```
ls -l /usr/lib/python3.2 | grep sitecustom
```
It should show as a symlink to the file shown in the first command.

If it's not, you can fix that with 
```
cd /usr/lib/python3.2
sudo ln -s /etc/python3.2/sitecustomize.py
```

Then try reconfiguring the two python packages:
```
sudo dpkg-reconfigure python3.2-minimal
sudo dpkg-reconfigure python3.2
```

---

### Post by Sky001 on 2013-07-14
> **newb85 said:**
> Hmm...let's see if /etc/python3.2/sitecustomize.py is back
```
ls /etc/python3.2 | grep sitecustom
```
there was no output from the terminal so I proceeded to the 3rd step. 

> **newb85 said:**
> If it's not, you can fix that with
```
cd /usr/lib/python3.2
sudo ln -s /etc/python3.2/sitecustomize.py
```
This step failed because, the file was already present (even though nothing was returned after step one). Below is the output: 
```
:~$ cd /usr/lib/python3.2
:/usr/lib/python3.2$ sudo ln -s /etc/python3.2/sitecustomize.py
[sudo] password for saipal: 
ln: failed to create symbolic link `./sitecustomize.py': File exists.
```

Because the file did indeed exist. I went back and did step two. 
> **newb85 said:**
> If it's there, then check this:
```
ls -l /usr/lib/python3.2 | grep sitecustom
```
It should show as a symlink to the file shown in the first command.
```
:/usr/lib/python3.2$ ls -l /usr/lib/python3.2 | grep sitecustom
lrwxrwxrwx 1 root root     31 Apr  9 23:30 sitecustomize.py -> /etc/python3.2/sitecustomize.py
```

Lastly:
> **newb85 said:**
> Then try reconfiguring the two python packages:
```
sudo dpkg-reconfigure python3.2-minimal
sudo dpkg-reconfigure python3.2
```

Then the last step gave:
```
:/usr/lib/python3.2$ sudo dpkg-reconfigure python3.2-minimal
/usr/sbin/dpkg-reconfigure: python3.2-minimal is broken or not fully installed
:/usr/lib/python3.2$ sudo dpkg-reconfigure python3.2
/usr/sbin/dpkg-reconfigure: python3.2 is broken or not fully installed
```

Here is the whole process in one snapshot

```

:~$ ls /etc/python3.2 | grep sitecustom
:/usr/lib/python3.2$ sudo ln -s /etc/python3.2/sitecustomize.py
[sudo] password for saipal: 
ln: failed to create symbolic link `./sitecustomize.py': File exists
:/usr/lib/python3.2$ ls -l /usr/lib/python3.2 | grep sitecustom
lrwxrwxrwx 1 root root     31 Apr  9 23:30 sitecustomize.py -> /etc/python3.2/sitecustomize.py
:/usr/lib/python3.2$ sudo dpkg-reconfigure python3.2-minimal
/usr/sbin/dpkg-reconfigure: python3.2-minimal is broken or not fully installed
:/usr/lib/python3.2$ sudo dpkg-reconfigure python3.2
/usr/sbin/dpkg-reconfigure: python3.2 is broken or not fully installed
```

What do you think?

---

### Post by newb85 on 2013-07-14
The last step failed because I forgot you can't reconfigure a package that hasn't been successfully installed in the first place.  But we need to focus on things in the right order.

I was working from how my 13.04 system is set up, with python3.3, and on my system /usr/lib/python3.3/sitecustomize.py is a symlink pointing to /etc/python3.3/sitecustomize.py, which is the actual file.

[s]Apparently, on 12.04, with python 3.2, it's supposed to be the other way around, with /etc/python3.2/sitecustomize.py being a symlink to the real file, /usr/lib/python3.2/sitecustomize.py.[/s]

Nope. I was wrong.  /usr/lib/python3.2/sitecustomize.py is a symlink pointing to the missing actual file at /etc/python3.2/sitecustomize.py on your system.

Maybe this will work.
```
sudo apt-get purge python3.2-minimal python3.2
sudo apt-get install python3.2-minimal python3.2
```

---

### Post by Sky001 on 2013-07-14
You are amazing! Thank you! Thank you so much! You have saved me 20 more hours of pulling my hair out. I was starting to get worried I'd loose it all. 

It worked! The joy I feel. 

One last question. What is a good terminal command, or list of commands, to use when removing programs. You might have encountered this problem before. After using ```
sudo apt-get remove [program name]
```, the program might still be activated using the terminal. In which case, ```
whereis [program name]
``` usually shows a list of locations with such program files. I'm pretty sure, ```
sudo apt-get uninstall
``` does not work. Please let me in on any through uninstallation commands you might have. 

Thanks again.

---

### Post by newb85 on 2013-07-14
I'm glad it's working.  I'm a little ashamed that I didn't suggest that solution sooner, actually.

As to thorough uninstallation, I suggest you take a good look at the manual page for apt-get.
```
man apt-get
```

---

### Post by JKyleOKC on 2013-07-14
> **Sky001 said:**
>  Please let me in on any through uninstallation commands you might have.The most thorough is "apt-get purge whatever" which removes the program and all of its configuration files. The version you used originally -- "apt-get remove whatever" -- removes the program, but leaves the configuration files in place so that you can reinstall it without losing any customization you've done.

As newb85 said, going to the "man" page for a command will (usually) tell you all about a program, but these pages often are extremely obscure to newcomers since they frequently assume that you're already expert in everything else about the system. There's also an "info" command that attempts to be a bit more friendly to those less expert with the system, but even that is sometimes a bit difficult to comprehend...

---

### Post by Sky001 on 2013-07-14
Thanks to both of you. At this point I supposes problem this thread is concerned about has been solved. However, other questions have come to mind. 

I recall the frist time I visted the man pages: I promptly ran away from them. I thought they were a beast I couldn't deal with. But now that I've some months to play with this machine, they seem not terribly bad. Understanding and running shell scripts is obviously a very good skill to have, is [this]("http://www.linuxcommand.org/index.php") text and the exercises the best way to learn as much as I can?

Also, is there text that sheds light on the pc architecture of Linux and compares it to unix? Often times I feel so disconnected to this pc that I rely so much on. 

Thank youthis

---

### Post by JKyleOKC on 2013-07-14
I don't think there's a "best" way to learn the command line; that text seems about as good as any, but the only way to actually internalize it so that it feels natural to you is to do it over and over and over. It's much like learning to ride a bike or drive a car -- strange and confusing at first, but as you gain experience it becomes so easy that you don't have to think about it any more.

There's almost no basic difference in architecture between Linux and Unix; the apparent differences are mostly because both systems offer almost unlimited opportunities to customize them. There's more difference between Linux distributions such as Ubuntu and Red Hat than there is between basic Linux (probably best represented by Slackware!) and Unix -- and don't forget BSD when comparing systems.

I was fortunate enough to actually program on MULTICS back in the mid-70s, before PCs existed; Unix itself began as a mini-clone of the MULTICS system, just as Linux became a similar descendant of Unix. There's a common architecture among all these systems, such as the "everything is a file" philosophy and the use of "pipes" to feed data from one program to another. This made the transition into Linux very easy for me, although economic necessity forced me to work primarily in Windows from the mid-80s until a few years ago (and I still use WinXP in virtual machines to support my clients). However none of these systems resemble Windows more than superficially, and expecting any of them to behave like Windows did is probably the major cause of difficulty for people who don't have such a history...

---

### Post by Sky001 on 2013-07-15
Some good information here. I never thought Unix and Linux would be that similar. Thanks for your time. I'll definately follow up on the bits about MULTICS and the developement of both systems. I'll now mark this thread as solved.

---

### Post by JKyleOKC on 2013-07-15
A good starting point would be [http://www.multicians.org/](http://www.multicians.org/) which tells the history of MULTICS and includes personal anecdotes from many "multicians" (you might even find some from me there, although I've not been active on that site for several years). You can even find a link to the source code for the system, although it won't be very readable since it consists mostly of PL/1 (an ALGOL-like language, now obsolete) and G-E/Honeywell GCOS Assembly Language...

EDIT -- I just looked at some of the source and saw that I forgot to mention "*.ec" files although they make up a large part of the (huge) package. These were the forerunners of both Windows batch files and Linux's shell scripts, and like these consisted of a sequence of console commands to accomplish complicated jobs. It's amazing to see how little has changed in this area in almost 50 years, and how greatly things have improved due to the few changes made.

---

