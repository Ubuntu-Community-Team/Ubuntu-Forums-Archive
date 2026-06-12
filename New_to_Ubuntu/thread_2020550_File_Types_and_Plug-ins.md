---
title: "File Types and Plug-ins"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by joepop on 2012-07-08
Hi, I'm new to Ubuntu Linux so here are some pretty elementary questions:
 
What are the executable file types in Linux? And how do you execute them?
Even more general: What are the main file types, e.g.: In windows an HTML file is [COLOR=darkorange].**htm**[COLOR=black]**; **a code library is .[/COLOR][/COLOR][COLOR=darkorange]**dll**[/COLOR]?
 
Also, how are **shortcuts** (pointers to executable files) represented, Ubuntu doesn't seem to have desktop icons like windows does (except in the navigator)?
 
Windows has basicly two executable files: [COLOR=darkorange]**.exe **[/COLOR][COLOR=black](starts a program),[/COLOR] and [COLOR=darkorange]**.bat **[/COLOR][COLOR=black](runs a list of DOS commands)[/COLOR]; each can be started up by double clicking on it, or pressing return after it on the command line. What are the Ubuntu Linux equivalents, and how do you start them?
 
Also, I can't get the Flash Player plug-in working in FireFox. I added the plug-in FlashAid 
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
to FireFox and ran it, but Flash player apps still don't work. Any suggestions?
 
I have Ubuntu 11.10 running on a Dell Inspiron 8000
 
Thanks for any help in these matters!

---

### Post by MG&amp;TL on 2012-07-09
> What are the executable file types in Linux? And how do you execute them?Linux usually uses ELF binaries. To execute, you give your shell the path to it, or let it search the directories in the environment variable $PATH for you. Or you could just double-click in a file browser.

For example:

```
/usr/bin/firefox
```executes firefox, but so would:

```
firefox
```as /usr/bin/ is included in $PATH.

> Even more general: What are the main file types, e.g.: In windows an HTML file is .htm; a code library is .dll?
Linux doesn't rely on file extensions to differentiate files. You could call any file anything you like, and it would still work the same way. However, some programs might get a little confused and would have to be told exactly what to do, so people recommend using standard file extensions. The exception to this appears to be shared object files (DLLs for Linux, if you will), which have the extension .so
 
> Also, how are shortcuts (pointers to executable files) represented, Ubuntu doesn't seem to have desktop icons like windows does (except in the navigator)?Two types of shortcuts:

-A symbolic link. This is just a small file which points to the actual file (be it executable or regular file). 

-A desktop entry file (usually has extension .desktop) which is a more complicated form of shortcut used to launch applications, files etc with defined icons, flags etc.


> Windows has basicly two executable files: .exe (starts a program), and .bat (runs a list of DOS commands); each can be started up by double clicking on it, or pressing return after it on the command line. What are the Ubuntu Linux equivalents, and how do you start them?
Linux doesn't have a set executable format. You can set any file to be executable. And it will theoretically execute, although if you try and execute a word document, <deity> only knows what will happen, although probably an error.

**Common** formats you see are:

-ELF binary files.
-Shell scripts, plaintext files, usually .sh files.
-.pl, .py, etc. Other script files, python and Perl respectively

You execute them in the same way you would in windows.
 
> Also, I can't get the Flash Player plug-in working in FireFox. I added the plug-in FlashAid 
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
to FireFox and ran it, but Flash player apps still don't work. Any suggestions?No idea, but have you installed the *ubuntu-restricted-extras* package?

---

### Post by mastablasta on 2012-07-09
shell scripts are kind of .bat files. 
 
ubuntu also uses installer files .deb which are kind of .exe files in windows. red hat based distros use .rpm instead of .deb
 
also if you want more look & feel of desktop that is close to windows try KDE (found in Kubuntu) where "shortcuts" are made just like in windows and most stuff has look & feel of windows (t.e. GUI configuraiton, control panel etc.)

---

### Post by joepop on 2012-07-09
Thanks MG&TL and Mastablasta for your help!
 
MG&TL: I have never heard of the [COLOR=darkorange]"ubuntu-restricted-extras package"[/COLOR]
[COLOR=black]What does it do, and[/COLOR] [COLOR=black]how do I install it?[/COLOR]
 
Thanks again!

---

### Post by MG&amp;TL on 2012-07-09
> **joepop said:**
> Thanks MG&TL and Mastablasta for your help!
 
MG&TL: I have never heard of the [COLOR=darkorange]"ubuntu-restricted-extras package"[/COLOR]
[COLOR=black]What does it do, and[/COLOR] [COLOR=black]how do I install it?[/COLOR]
 
Thanks again!

Not a problem. :)

You can install the restricted-extras package from the software centre, or:

```
sudo apt-get install ubuntu-restricted-extras
```It works for me every time, but some people are different. If you still have problems, there's various other things we can try.

I understand we can't ship the package by default for legal reasons.

---

