---
title: "Building Administration Software."
date: 2008-09-03
forum: Programming Talk
---

### Post by chris062689 on 2008-09-03
I have an old laptop with a broken monitor that I'm going to be turning into a server.  I want to begin BASH scripting, as I feel this would be the best way to build administration tools?  For example, I telnet in from a Windows box, it comes up with a "dialog" frontend script, with options such as "Run shell, Shutdown Server, Reboot Server, Temperate Status, etc."
I think it would be a great idea, but is that what everyone else is using for building tools?  I want to stay with the times, because I'm looking to go into that kind of a field.

---

### Post by Cypher on 2008-09-03
You might be better served with using a more capable language to built that sort of an administration front-end. Languages like Perl and Python will yield you infinite power and expandibility. BASH is great at creating a basic system and you could use CURSES to set up a rudamentary menu system..but I consider BASH as more of a scripting tool to automate routine/mundane tasks..

It is, however, a very simple language to get your system up and experimented..you can then migrate what you learn to anything else later on..

---

### Post by mssever on 2008-09-03
If you write it in Bash, it'll become kludgey before too long. I'd recommend either Ruby or Python--both of which have much better facilities for doing whatever you want. Bash is great for typing on the command line and for simple scripts, but the larger the project grows, the harder bash becomes.

And by the way, I strongly recommend SSH over telnet.

---

### Post by chris062689 on 2008-09-03
What kind of libaries does python have that can do stuff with the CLI?  (Menus, Inputs, etc.)

---

### Post by mssever on 2008-09-03
> **chris062689 said:**
> What kind of libaries does python have that can do stuff with the CLI?  (Menus, Inputs, etc.)
Probably whatever you want. Definitely look through the standard library, than browse the other libs available in the repos. Ask the Python gurus... Especially, you'll probably want to look for an ncurses library.

I don't know the Python libs very well, since I tend to prefer Ruby. But Python has excellent library coverage.

---

### Post by stevescripts on 2008-09-03
You might also want to take a look at expect (and tcl ...)

This is not saying that there are any flies on Python, Ruby, etc

Steve

---

### Post by mssever on 2008-09-03
> **stevescripts said:**
> You might also want to take a look at expect (and tcl ...)
Didn't expect start out in Tcl? Of course, nowadays it's available for Python, too.

I can't comment on Tcl since I don't know it.

---

### Post by stevescripts on 2008-09-04
> **mssever said:**
> Didn't expect start out in Tcl? Of course, nowadays it's available for Python, too.



Expect is basically a tcl extension - I was unaware of a port for Python.

TY for the info.

Steve

---

### Post by ghostdog74 on 2008-09-04
> **chris062689 said:**
> I have an old laptop with a broken monitor that I'm going to be turning into a server.  I want to begin BASH scripting, as I feel this would be the best way to build administration tools?  For example, I telnet in from a Windows box, it comes up with a "dialog" frontend script, with options such as "Run shell, Shutdown Server, Reboot Server, Temperate Status, etc."
I think it would be a great idea, but is that what everyone else is using for building tools?  I want to stay with the times, because I'm looking to go into that kind of a field.

Reading your post, i gather you are going to administer your broken server from a Windows machine? If that's the case, just simply ssh/telnet into your server using ssh/telnet client for windows. Write your scripts and stored on your server. You do not need a GUI for that. The command line is the best way to administer your server. eg
```

#!/bin/bash


PS3='Choose a task: ' # Sets the prompt string.

select task in "Run shell" "Shutdown Server" "Reboot server" "Temperature Status" "Exit"
do
    case $task in 
        "Run shell") echo "run shell";;
        "Shutdown Server") echo "init 0";;
        "Reboot server") echo "init 6";;
        "Temperature Status") echo "insert check temperature command here" ;;
        "Exit" ) exit 0;;

    esac
done


```

---

### Post by Mickeysofine1972 on 2008-09-04
> **ghostdog74 said:**
> Reading your post, i gather you are going to administer your broken server from a Windows machine? If that's the case, just simply ssh/telnet into your server using ssh/telnet client for windows. Write your scripts and stored on your server. You do not need a GUI for that. The command line is the best way to administer your server.

+1 

... but PyGTK or wxPython are good for making GUI... just thought I would mention them

Mike

---

### Post by chris062689 on 2008-09-04
No no, it's not broken.  I havn't even made it yet.
What I was asking for was a fancy CLI-based dialog system.
(Like what BASH has, used in Debian-based installers)
Something like that for Python, so I can make fancy menus for my server administration tool!  :lolflag:

---

