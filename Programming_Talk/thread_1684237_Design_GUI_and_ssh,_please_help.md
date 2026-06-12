---
title: "Design GUI and ssh, please help"
date: 2011-02-08
forum: Programming Talk
---

### Post by eimai malakas on 2011-02-08
hello everyone.

Im so sorry if this has been asked before, but im in the middle of a crucial matter, running out of time.

Getting to the point
A) I want to design a GUI for an old linux red-hat system on i686, which should be communicating directly with console. For example, pressing A button on GUI gives on terminal the ls command, the results of which will be showed on application.

I would use wxpython or something similar, but problem is that i cant install or modify anything on that computer. Is there a program on linux like visual basic for windows, which allows u to do that without installing anything on ur system?

B) 1 more thing. It would be pretty good if that GUI application had the possibility to be viewed and controled by other systems over ssh, mostly on windows. Im using putty to gain remote access to linux system.

 Also, i found this program [http://nixcraft.com/getting-started-tutorials/170-run-remote-x-applications-over-network-using-ssh.html]("http://nixcraft.com/getting-started-tutorials/170-run-remote-x-applications-over-network-using-ssh.html") which seems to do some of what i ask. Please do u have any better ideas?.

Thx a lot in advance for ur answers.

---

### Post by cipherboy_loc on 2011-02-08
Why can't you (on your own system) create said software, find all the libraries, include them in the directory, tarball the directory, put it on the server (I assume it is a server), extract it, and then run it.

More or less it breaks down as follows:

1) Create the software to do what ever you want (it can use wxPython, etc).
2) Find all the wxPython libraries and copy them into the source directory.
3) Tarball the source directory.
4) Upload the tarball to the server.
5) Extract the tarball.
6) Test.


Cipherboy

---

### Post by eimai malakas on 2011-02-09
> **cipherboy_loc said:**
> Why can't you (on your own system) create said software, find all the libraries, include them in the directory, tarball the directory, put it on the server (I assume it is a server), extract it, and then run it.

first of all im pretty new to this stuff, but as i said, its better to avoid copying libraries to that linux system. It is university property and dont have rights to do so.

Plus, I dont know how to select the proper libraries since im not really aware tbh. But if this is the only way i guess i can push it somehow. Is there any other idea besides this 1?

Any thoughts on plan B? the link i showed gives a tutorial on X server

---

### Post by cipherboy_loc on 2011-02-09
Why don't you do something like this (do you know if it has X already?):

```

ssh user@ip -Y gnome-terminal

```

Try replacing gnome-terminal with a list of common terminal clients:

gnome-terminal
konsole
xterm
aterm


See if any of those work. Also, what is the point of creating this piece of software?




Cipherboy

---

