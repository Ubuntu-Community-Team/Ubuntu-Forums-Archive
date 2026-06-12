---
title: "Help understanding environment and shell variables"
date: 2020-07-29
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-07-29
Hi everyone,

So environment and shell variables are confusing me a bit.

Where are the configuration files that require editing to persistently set variables?

I have found my $PATH in '/etc/environment' to which I added '~/bin' as when I ran 'PATH=$PATH:~/bin' in the terminal the change was not persistent. However that is the *only *variable listed within the file, in fact it's the only thing in there.

/etc/profile is full of a load of human readable jargon (maybe a script) but being a Linux layman I have no idea what that's all about.

I guess my questions are...


[LIST=1]
[*]Where are the config files that store environment variables?
[*]Why do a lot of guides tell the reader to use 'export' to set environment / shell variables, as I understand the variables set in this way are not persistent and will only be inherited by the child processes of the terminal that the 'export' command is run in?
[*]What is the difference between exporting a variable, and simply running 'VARIABLE=value'
[*]Is the GUI technically a login shell? (in Ubuntu 20.04)
[/LIST]

Thanks!

---

### Post by TheFu on 2020-07-29
There are system config files, default skeleton configs that get copied whenever a new userid is created, and there are config files inside each userid's HOME.  In general, it is considered bad form (i.e. dangerous) to modify the system defaults.

Environment variables can be set in any shell script anywhere on the system.  But only child processes inherit those settings.
Most users would set environment variables in their personal ~/.bashrc file, assuming bash is their shell. Each different shell has a specific way to accomplish this. csh, sh, ksh, bash, tsch, fish, pash, and the 50 other shells available can all have specific ways to do it AND they can have different files that get checked automatically just after login happens. 

A userid's shell is set in the password entry for that userid.  A user can change their shell to any that the admin has approved using the chsh tool. For an admin to allow other shells is a little more complicated.

A GUI is NOT a shell.

To learn more about Unix startup, find any beginning Unix book.  Linux mostly follows the same processes.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is the no hassle, free download, ebook for how Linux does stuff.  See chptr 11.

---

### Post by Impavidus on 2020-07-29
1: They can be all over the place. /etc/environment, /etc/profile, ~/.profile, ~/.bashrc. Many are set by processes. For example, the terminal sets an environment variable (TERM) to tell the shell in what kind of terminal it runs, so the shell knows whether it can use colours. A process started by the shell, running in the same terminal window, inherits that variable and can also see if it can use colours.

2: They are indeed not persistent from one session to the next. To make them persistent, you have to define the environment variable in a file that gets sourced automatically. **export** means export to child processes.

3: Without export, you simply set a shell variable. It only has meaning to the shell and is not inherited by child processes. With export, it's an environment variable, which is inherited by child processes, including child processes that are not a shell.

---

### Post by ActionParsnip on 2020-07-29
You can define your own user variables in ~/.bashrc if you like. I use a few to make navigation easier. Things like:
```

$ export PICS=$HOME/Pictures
$ echo $PICS
/home/foo/Pictures

```
You can then run:
```

cd $PICS

```
and jump into that folder. I personally use it for Freeradius
```

export RADHOME=/etc/freeradius/3.0

```


I can even use it in commands
```

cat ~/proxy.conf | sudo tee $RADHOME/proxy.conf > /dev/null

```

Super readable :p

---

### Post by jcdenton1995 on 2020-07-30
> **ActionParsnip said:**
> You can define your own user variables in ~/.bashrc if you like. I use a few to make navigation easier.

I see, I thought ~/.bashrc was just for shell variables, is this for environment variables too?

---

### Post by jcdenton1995 on 2020-07-30
> **Impavidus said:**
> 1: They can be all over the place. /etc/environment, /etc/profile, ~/.profile, ~/.bashrc. Many are set by processes. For example, the terminal sets an environment variable (TERM) to tell the shell in what kind of terminal it runs, so the shell knows whether it can use colours. A process started by the shell, running in the same terminal window, inherits that variable and can also see if it can use colours.

Thank you, I think this has actually highlighted a misunderstanding I have had for a while. I always thought "terminal" and "shell" were the same thing as people often refer to a shell as a "terminal emulator" and I thought the use of the word terminal was just an abbreviated version of "terminal emulator"

However after some more reading it seems that the terminal is some sort of archaic throwback to when Unix-like systems were distributed and they are kind of like an emulation of a physical terminal of old, but just on your own machine, although maybe I've got that all wrong?

---

### Post by jcdenton1995 on 2020-07-30
> **TheFu said:**
> Most users would set environment variables in their personal ~/.bashrc file, assuming bash is their shell.

A GUI is NOT a shell.

I think my confusion comes from a lack of understanding of the Linux architecture, for example I don't understand how a GUI and desktop environment relates to the shell

For example I previously thought that ~/.bashrc was only for shell variables, although now as you have said I realise it can be for environment variables too, but how does this relate to programs initiated from the desktop environment? as to me the shell is just what pops up when I press 'ctrl + alt + T'.

 is it the case that the DE is simply like an overlay for your shell and when you open / run things from within the graphical environment it simply passes the relevant commands to a shell in the background?

---

### Post by Impavidus on 2020-07-30
> **jcdenton1995 said:**
> Thank you, I think this has actually highlighted a misunderstanding I have had for a while. I always thought "terminal" and "shell" were the same thing as people often refer to a shell as a "terminal emulator" and I thought the use of the word terminal was just an abbreviated version of "terminal emulator"

However after some more reading it seems that the terminal is some sort of archaic throwback to when Unix-like systems were distributed and they are kind of like an emulation of a physical terminal of old, but just on your own machine, although maybe I've got that all wrong?

The word "terminal" is loosely used for terminal emulator all the time, but there's indeed a clear difference with shell, even though that word too is often used interchangeably. This is because terminal windows are usually used to run a shell and shells usually run in a terminal. The terminal is the thing that accepts keyboard input, paste operations and things like that and passes them on to the shell (or any other text interface process running in the terminal) as a sequence of characters (and some control codes), and also accepts output from the shell in the form of sequences of characters, renders that text in some nice font (using embedded control codes to switch to bold face, colours etc.) and displays it. The shell doesn't know anything about rendering or copying and pasting, but does all the other stuff than input/output. Most of the time I use xfce4-terminal as my terminal application, but I can also use xterm or one of many others, and use bash as my shell, but I can use csh or one of many others too.

---

### Post by TheFu on 2020-07-30
A shell is any interactive CLI program to interface with the OS, manage files, launch programs, and monitor processes. You can change the current shell to be anything you want, just by running the other program.

A "login shell" is set in the passwd entry, usually in the /etc/passwd file on small systems, but in LDAP on corporate systems.  
```
$ getent passwd
```
is the command to see the passwd file for any Unix system, though if the admin didn't setup LDAP, then the /etc/passwd file is it. Anyways, each userid has a login shell specified.  If you want to know more, get that link I provided above and work through the book 1 chpt / week.  That way you won't have too many knowledge gaps.  Around 6 months in, things should start "clicking" together so a deeper understand begins to happen.

Anyway, the allowed login shells is controlled by the admin. There are restrictions, which are controlled by a config file, /etc/shells.

Forget about DEs.  Those as so far removed from anything related to logins as to be useless.  The GUI is controlled by the Window Manager, WM, and display server (X11 or Wayland). DEs run on top of the WM and perhaps a "Compositor".  There is no requirement for a DE to be used. There is no requirement for a Compositor to be used.  You can have a fast, pretty, GUI with just a WM that supports transparent windows and menus, if that is your desire.

It is worth learning what happens when you "login" to a Unix system. There are step-by-step guides that try to explain.  Just know that starting a WM is around step 8.  That's my guess. I haven't checked recently.

Terminal ...  Impavidus nailed it.
CLI and shell are more interchangeable.

I use a uxterm as my preferred terminal. My preference for less bloat. All the included default terminals use 5-10x more RAM for what I consider useless features. To each their own.

---

### Post by ActionParsnip on 2020-07-30
> You can have a fast, pretty, GUI with just a WM that supports transparent windows and menus, if that is your desire.

Yep, OpenBox or FluxBox as stand alone WM is fantastic. Super light

---

