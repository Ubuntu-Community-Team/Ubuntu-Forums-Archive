---
title: "Python: Graphical sudo, no QT, no GTK"
date: 2010-06-11
forum: Programming Talk
---

### Post by juancarlospaco on 2010-06-11
Python: Graphical sudo, no QT, no GTK

**How to do a Graphical sudo ???**

without using:
[LIST]
[*]No GTK
[*]No QT
[*]No sudo *(sudo is not correct for GUI apps the documentation say)*
[/LIST]

I hope theres a solution ...

---

### Post by Bachstelze on 2010-06-11
Not possible in Python because any kind of sudo-like application must run setuid root, and this is only possible for binary executables, not scripts.

---

### Post by Zugzwang on 2010-06-11
@OP: Perhaps you might want to add what's wrong with QT and GTK in your context?

---

### Post by nvteighen on 2010-06-11
Ugh...

What's wrong with:
```

gksudo 

```

I knew in the past which was KDE's command... :P

---

### Post by juancarlospaco on 2010-06-11
> **Bachstelze said:**
> Not possible in Python

:cry::cry::cry::cry::cry::cry:

*We need something to fix these, i hope someone fix this on Python 3.x*

---

### Post by Zugzwang on 2010-06-11
> **juancarlospaco said:**
> :cry::cry::cry::cry::cry::cry:

*We need something to fix these, i hope someone fix this on Python 3.x*

This has nothing to do with Python. In most Linux distributions, the flag for running a program as root is ignored for scripts (for security reasons). Also, as there's nothing wrong with gksudo and kdesudo, so why should they change this?

---

### Post by juancarlospaco on 2010-06-11
Because NO qt NO GTK

i cant use qt/gtk
i dont want to use qt/gtk
i dont like to use qt/gtk
qt/gtk are not the only GUI tools

---

### Post by Zugzwang on 2010-06-11
Ah, wait. So you don't want to develop an application that must be run as root for full functionality (like synaptic) but rather a *replacement* for gksudo/kdesudo? Is that correct? You original post doesn't say this - to "do" a sudo could be both.

In order to "trick" this security flag thing, you could always write a small C program that does nothing but to call your python whatever-sudo tool. Then, have a look at the sources of the kdesudo or gtksudo tool to find out how these work.

---

### Post by juancarlospaco on 2010-06-11
I want to develop parts of an application that must be run as root for full functionality,
i dont want a *replacement* for gksudo/kdesudo,
i want something like os.system('xdg-open file.txt'), 
opens Kate on KDE, and Gedit on Gnome, and whatevereditor on whateverdesktop,
but, it dont exist in Python, 
im actually coding my own Graphical Sudo that dont need GTK or QT.

*Thanks anyways...* :)

---

### Post by nvteighen on 2010-06-12
> **juancarlospaco said:**
> I want to develop parts of an application that must be run as root for full functionality,
i dont want a *replacement* for gksudo/kdesudo,
i want something like os.system('xdg-open file.txt'), 
opens Kate on KDE, and Gedit on Gnome, and whatevereditor on whateverdesktop,
but, it dont exist in Python, 
im actually coding my own Graphical Sudo that dont need GTK or QT.

*Thanks anyways...* :)

The issue is... why not GTK+ nor Qt??? What will you use? Xlib? Motif? Tk? Hey, if it's because GTK+ and Qt are hard, the others won't make it easier to you either. GUI programming is always hard.

---

### Post by soltanis on 2010-06-12
Desktop environments are not standardized to the point where you could hope to write such a program, but more importantly it doesn't sound like you want sudo, you want a program that will open a file based on what program is associated with opening that kind of file.

---

### Post by rnerwein on 2010-06-12
hi
i think what soltanis tolds in his post is what you wan't to get.
do a google with "fd passing"
---> run a daemon in the background ( uid should be root )
       the daemon must check ( password .... ) if it's leagel to pass the file discriptor !!!!
       then the daemon can do:  i_rc = ioctl(i_fifo,I_SENDFD,i_file);
--> the client can: i_rc = ioctl(i_fifo,I_RECVFD,&s_fd);
in s_fd you got a fd with all the permissions the daemon run ( i used it a couple of times ). but be very carefully what
you do. ( i think it's possible to do that with "sendmsg and putmsg - more secure )
hope thats a little hint
ciao

---

### Post by lavinog on 2010-06-12
What about policykit?

---

### Post by rnerwein on 2010-06-13
> **lavinog said:**
> What about policykit?
hi laeloi
where is the problem please - i think you don't really what you are taken about :mad:
learning C !!
hasta luega - cioa

---

### Post by rnerwein on 2010-06-13
> **soltanis said:**
> Desktop environments are not standardized to the point where you could hope to write such a program, but more importantly it doesn't sound like you want sudo, you want a program that will open a file based on what program is associated with opening that kind of file.
hi
no swet i know how to use sudo ( :mad: ) for sure. 
but give other people to share the knowllege. ---> i bet you have never heard about that ( if you can use it and know what you are doing ) 99.01 % securety.
ciao

---

### Post by Zugzwang on 2010-06-13
> **juancarlospaco said:**
> i want something like os.system('xdg-open file.txt')


Ah, ok, do I get it right that you wanted some graphical sudo that does not depend on QT or GTK in the first place because you don't want Gnome users to need "kdesudo" and don't want KDE users to need "gksudo"? So you are complaining that there is no command like "xdg-open" that automatically chooses the right tool depending on the desktop environment for the purpose of sudoing, i.e. that is equivalent to "kdesudo" on KDE desktops and "gksudo" on Gnome desktops? Something that would be called "xdg-sudo" or "x-sudo"? 

@rnerwein: I don't think that the OP actually wants to edit/open a file, but rather used "xdg-open" as an example that there are cases in which some tool is chosen automatically to fit to the desktop environment.

---

### Post by juancarlospaco on 2010-06-14
> **Zugzwang said:**
> Ah, ok, do I get it right that you wanted some graphical sudo that does not depend on QT or GTK in the first place because you don't want Gnome users to need "kdesudo" and don't want KDE users to need "gksudo"? So you are complaining that there is no command like "xdg-open" that automatically chooses the right tool depending on the desktop environment for the purpose of sudoing, i.e. that is equivalent to "kdesudo" on KDE desktops and "gksudo" on Gnome desktops? Something that would be called "xdg-sudo" or "x-sudo"? 

@rnerwein: I don't think that the OP actually wants to edit/open a file, but rather used "xdg-open" as an example that there are cases in which some tool is chosen automatically to fit to the desktop environment.

My app do not install GTK on KDE, dont install QT/KDELibs on Gnome.
i dont want to edit/open a file.

xdg-sudo would be perfect!, 
and if theres no gtk and qt fallback into sudo on an xterm window,
the problem is it dont exist, lol, im coding a password widget.

Thanks anyways...

---

### Post by Zugzwang on 2010-06-14
Ok, just for fun I tried programming something you might like for your purpose. It lacks a little bit of error handling and I'm not 100% sure that all that escaping stuff is correct.

[PHP]
#!/usr/bin/python
#
# x-sudo: Automatically chooses "gksudo" or "kdesudo" depending
# on what actually exists

import os
import sys
import subprocess
import re

# Prepare actual command to execute
parameters = " ".join([re.escape(a) for a in sys.argv[1:]])

# Test which tools exist
# We can safely assume that they are not directories
kdesudo = os.path.exists('/usr/bin/kdesudo')
gtksudo = os.path.exists('/usr/bin/gksudo')

# If we have at least one of them, check which one to use.
if kdesudo or gtksudo:
    if kdesudo and gtksudo:
        # Test if gnome runs
        process = subprocess.Popen("ps -ae | grep gnome-session", shell=True, stdout=subprocess.PIPE)
        process.wait()
        if len(process.communicate()[0])>0:
            useGnome = True
        else:
            useGnome = False
    elif kdesudo and (not gtksudo):
        useGnome = False
    elif (not kdesudo) and gtksudo:
        useGnome = True

    # Run
    if useGnome:
        cmd = "gksudo "
    else:
        cmd = "kdesudo "

    # Run the actual program
    os.system(cmd+parameters)

else:
    # Oh, we don't have gtksudo or kdesudo?
    cmd = "xterm -e \"echo 'Neither \\\"gksudo\\\" nor \\\"kdesudo\\\" have been found on your machine. Thus, \\\"sudo\\\" is being used. Please leave this window open until the program has finished. Your are asked for your password below.'; sudo "+parameters+"; sleep 1\""
    os.system(cmd) 
 
[/PHP]

---

