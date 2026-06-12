---
title: "Terminal when open will not accept commands"
date: 2020-12-29
forum: New to Ubuntu
---

### Post by tajreed2 on 2020-12-29
Terminal opens, but when I attempt to  type for examle Sudo...... Nothing happens. I can't type anything. Using 20.10.
Any thoughts?

---

### Post by wildmanne39 on 2020-12-29
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by Impavidus on 2020-12-30
When you open the terminal, do you see a prompt? It should normally look like user@host:dir$, with a username, hostname and current working directory. Something like john@orion:~$.

BTW, I never type Sudo (except just now). Occasionally I type sudo, one of my less used commands. The command line (like almost everything in Linux) is case-sensitive. And when sudo asks for your password, you won't see anything typed. That's normal, just type the password and hit enter.

---

### Post by TheFu on 2020-12-30
```
$ sudo
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user] [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-T timeout]
            [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-T timeout]
            [-u user] file ...
```
is what a userid in the sudo group should see.  Let's see what a user not in the sudo group sees:
```
foo@regulus:~$ id
uid=1001(foo) gid=1001(foo) groups=1001(foo)

$ sudo 
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user] [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-T timeout]
            [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-T timeout]
            [-u user] file ...
```

Same thing. Interesting. For some reason I would have thought that sudo wouldn't work for non-sudo group members.
```
$ ll /usr/bin/sudo
-rwsr-xr-x 1 root root 166056 Jul 14 20:17 /usr/bin/sudo*
```
I would have expected:
```
$ ll /usr/bin/sudo
-rwsr-x**---** 1 root **sudo** 166056 Jul 14 20:17 /usr/bin/sudo*
```

---

### Post by tajreed2 on 2020-12-30
No prompt, All I get is James@james XPS 13 9360 -
The dash is barely visible and is a light blue.

---

### Post by TheFu on 2020-12-30
Delete your ~/.bashrc and ~/.profile files. .... or move them somewhere else.
Something is screwed in the new shell process. Those 2 files are part of the defaults.
Or you could change the shell for your userid to some other valid shell, but that's really not for a beginner.

---

### Post by Impavidus on 2020-12-31
> **tajreed2 said:**
> No prompt, All I get is James@james XPS 13 9360 -
The dash is barely visible and is a light blue.

To me that sounds like a prompt. The dash would actually be a tilde. But it could be that your .bashrc or .profile or some file sourced from these was messed up. The shell may be in a deadlock, preventing it from accepting input, or echoing of input may be turned off, so you can still type, but don't see anything happen (like when typing a password).

The defaults for .bashrc and .profile can be found in /etc/skel/.

---

### Post by TheFu on 2020-12-31
Er ... what is your hostname?  hostnames should be lowercase, no funny characters, no spaces.  There are many reasons.

---

### Post by tajreed2 on 2021-01-01
I reinstalled 20.10 and the terminal worked. But later on it failed again. I still get the same response as shown above.
I've been with Ubuntu since 2006 and this has me stumped. 
Now what?

---

### Post by tea for one on 2021-01-01
> **tajreed2 said:**
> No prompt, All I get is James@james XPS 13 9360 -
The dash is barely visible and is a light blue.

During the installation process, there is a warning about the computer name:-

[COLOR="#0000FF"]Computer name must not start or end with a hyphen[/COLOR]

How did you circumnavigate this when re-installing?

Here is a suggestion:-

Settings > About > Device name > Try and rename device without spaces and without a trailing hyphen

Reboot and/or log out/log in.

Any luck?

---

### Post by ActionParsnip on 2021-01-01
Does xterm work OK?
Sudo only works for users defined in visudo. The sticky bit is set so the command runs as root but the configuration controls who can run what

---

### Post by tea for one on 2021-01-01
Try **Alt F2** which opens the dialogue box **Run a Command**?

---

### Post by TheFu on 2021-01-01
> **tajreed2 said:**
> I reinstalled 20.10 and the terminal worked. But later on it failed again. I still get the same response as shown above.
I've been with Ubuntu since 2006 and this has me stumped. 
Now what?

Maybe answer the questions asked and provide proof for the answer? We can't read your mind.

---

### Post by tajreed2 on 2021-01-01
No luck. I shall reinstall and modify computer name-take out hyphon.

---

### Post by tajreed2 on 2021-01-01
I just ckecked on my PC with 20.04 and the terminal works with the same name/device configuration. name-device with hyphons.

---

### Post by tea for one on 2021-01-01
Hyphens in the middle are OK but not at the beginning or end i.e.

**eric@eric-gardenshed** will be fine.

---

### Post by tea for one on 2021-01-01
> **tajreed2 said:**
> I just ckecked on my PC with 20.04 and the terminal works with the same name/device configuration. name-device with hyphons.

Is this a separate PC?

---

### Post by tajreed2 on 2021-01-01
O.K, I reinstalled and set up the computor name as u suggested. The terminal worked. But after I opened Settings to do some work with new installation, I went back to  terminal and low and behold it was broken. This has happened a couple of times. Reinstall, terminal works, later it fails, I think, after opening other apps.

---

### Post by TheFu on 2021-01-01
Any permissions changed on the ~/.bashrc or ~/.profile files?

---

### Post by tajreed2 on 2021-01-01
Don't know what to look for.

---

### Post by tea for one on 2021-01-02
> **tajreed2 said:**
> O.K, I reinstalled and set up the computor name as u suggested. The terminal worked. But after [COLOR="#FF0000"]I opened Settings to do some work with new installation[/COLOR], I went back to  terminal and low and behold it was broken. This has happened a couple of times. Reinstall, terminal works, later it fails, I think, after opening other apps.

What did you change in settings? Please be precise.

---

### Post by Impavidus on 2021-01-02
> **tajreed2 said:**
> Terminal opens, but when I attempt to  type for examle Sudo...... Nothing happens. I can't type anything. Using 20.10.
Any thoughts?

> **tajreed2 said:**
> No prompt, All I get is James@james XPS 13 9360 -
The dash is barely visible and is a light blue.

> **tajreed2 said:**
> But after I opened Settings to do some work with new installation, I went back to  terminal and low and behold it was broken.
That's all we have right now, and not nearly enough to solve this. You have a fresh install, then do some unspecified things and then you can no longer type in the terminal. You say you've got no prompt, but the thing you get looks very much like a prompt. The fact that the "dash" is blue (and the things before not, I assume) suggests that it's in fact a tilde, giving your current working directory. Using a default .bashrc, the current working directory is shown in blue. But even then, I would expect some dashes (and not spaces) in de hostname if you left that at the default, a colon after the hostname and a dollar sign at the end of the prompt. Maybe the characters on your screen are so small you can't properly see them? Try increasing font size in the terminal.

Maybe it helps if you tell us what things you do before the terminal breaks and show us what exactly you get in the terminal instead of this description. Show us what happened to your .bashrc and .profile files. Does it fix the problem if you restore the original .bashrc or .profile, as found in /etc/skel?

---

### Post by ajgreeny on 2021-01-02
> **tajreed2 said:**
> O.K, I reinstalled and set up the computor name as u suggested. The terminal worked. But after I opened Settings to do some work with new installation, I went back to  terminal and low and behold it was broken. This has happened a couple of times. Reinstall, terminal works, later it fails, I think, after opening other apps.
What changes did you make in Settings?

Perhaps what you did there will be the cause of this terminal error.

---

### Post by tajreed2 on 2021-01-02
Settings/accessability-enable large text, high contrast and cursor to medium.

---

### Post by tea for one on 2021-01-02
> **tajreed2 said:**
> Settings/accessability-enable large text, high contrast and cursor to medium.

I changed the settings one by one in Ubuntu 20.10 and found that [COLOR="#0000CD"]High Contrast[/COLOR] is the culprit.

Neither the terminal nor ALT F2 would accept input after changing to High Contrast.

If you toggle off High Contrast, log out and log in, terminal input will be accepted.

You could file a bug report on Launchpad but it is never obvious which package contains the bug (terminal or High Contrast theme).

Also, the fix will probably not be rapid.

This problem does **not** present itself in Ubuntu 20.04 therefore you may wish to consider installing 20.04?

---

### Post by tajreed2 on 2021-01-02
Wow, your right, I disabled high contrast and terminal fixed. 
I'm impressed, great work.
Thanks a bunch. I'll probably stick with 20.1 and wait for a fix in 21.04. If I need ther terminal, I'll just turn off high contrst.

---

### Post by TheFu on 2021-01-02
There are 20 different terminal programs. You can pick anyone to use.  

I've been using xterms for 25+ yrs. Habit. The generally use 10x less RAM than all the fancy terminals with a menu-bar.  But if you like menus, there is lxterm, lxterminal and most flavors have their own that you can install.  An xterm should already be on your system.  Try uxterm or rxvt/rxvt-unicode if you need unicode support. rxvt is a nice compromise between features, like extended ASCII (think text-line-drawing) and RAM use.  Something like:
```
$ rxvt -sb -bg  black -fg yellow &
```
But I miss the xterm menus (mouse button+hold / <cntl>+ mouse buttons / etc ) that rxvt doesn't have by default.

Clearly, make an alias for whatever terminal settings you like.  Font control is part of the available options.

---

### Post by ActionParsnip on 2021-01-03
Could install guake. You can then hide and show the terminal using a shortcut key (like the tilde console in Quake / Counterstrike and similar)

---

### Post by TheFu on 2021-01-04
Or use the "rollup" feature that Window managers should provide, assuming "iconify" (middle mouse button anywhere in the title bar of any window) isn't appreciated.

---

