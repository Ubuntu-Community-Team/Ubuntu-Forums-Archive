---
title: "sudo sensors-detect"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by Johnny3 on 2014-08-04
I am using Ububtu 14.04. When I run sudo sensors-detect. It will asked if you want what it finds to be added to /etc/modules so that it will be loaded with the other kernel modules. I don't have a modules in etc. But I have a modules-load.d should I add it there or make a modules folder in etc?
Thanks Johnny333

---

### Post by Mike_Walsh on 2014-08-07
Hi, Johnny333.

I don't know what it is you're running sudo sensors-detect FOR, but my own experience of using it dictates that you say 'yes' to everything it asks you.

I was using it to install psensor. I too was a bit concerned about saying 'yes' to adding it to the other modules in etc/modules; but having chased the process through, and installed psensor afterward, i can tell you that it shouldn't hurt your system at all.

The website where I got the information about psensor from said to say 'yes' to everything, and that it would NOT upset anthing. I don't take advice blindly, but after doing a bit of research, I decided to proceed; I was fairly certain it wouldn't hurt.

It hasn't. I've installed it into both Ubuntu 14.04, AND Zorin Core OS 9 (which is based on Ubuntu anyway) and it has, so far, given 2 months of totally trouble-free operation.

The sequence is merely checking the list of motherboard components for the presence of sensors; that is why you should say 'yes' to everything, because if you don't, you may miss finding some.

Regards,

Mike.

---

### Post by coldcritter64 on 2014-08-07
> ...or make a modules **folder** in etc?

Just a quick check OP, were you looking for a directory called modules ? It is actually **a text file not a folder**, this is a mistake I also made, early on, assuming it was a folder.

To check for the file, use in terminal,
```
ls -l /etc/modules
```
If that code gives a file, to open it as READONLY for viewing,
```
gedit /etc/modules
```
To edit it manually requires root privileges,
```
gksudo gedit /etc/modules
```

---

### Post by jetman350 on 2014-10-11
coldcritter64, I did what you said here but don't know how to view all the text.
[COLOR=#000000][B][U]

[/U][/B][/COLOR]

---

### Post by coldcritter64 on 2014-10-12
@ jetman350, If you need to edit the modules file copy and paste the code below into a terminal, you will need to input your sudo password, and the file will then open in gedit.

Steps:
1. Triple clicking quickly in the code box below highlights it, then right click and select "copy".

2. Use the keyboard combination CTRL + ALT + T, a terminal opens in Ubuntu, right click in it and select "paste", then press "enter", enter your password in the popup box and click "OK".

```
gksudo gedit /etc/modules
```

The modules file is now open in a root text editor "gedit" for any alterations. Remember to save the file from the menu bar before closing. Some changes to this file may require a restart to fully take effect, or there is a command noted in the sudo sensors-detect output that can reset the changes immediately. If I recall correctly it is noted towards the end of the output. Cheers.

---

