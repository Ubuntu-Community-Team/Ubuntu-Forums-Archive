---
title: "adding program to applications"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by tadcan on 2008-04-27
I installed celtx unpacking in with archive manage and creating a home folder. To launch it I need to go into the folder, double click and choose run.

It came as a .tar.gz and those still confuse me. 

What I would like is it to be included in applications > office 

How can I do that?

---

### Post by tadcan on 2008-04-27
doh, wasn't paying attention, should be here

---

### Post by scragar on 2008-04-27
it's fairly easy, first move the file out of the way, don't want you acidentaly doing anything strange to it:
```
sudo mv ~/Desktop/**celtx** /opt/celtx
```
which will move it from the desktop(if that's where you've got it) to /opt which is nice and safe.
then just edit the menu by right click applications, Places or system, and pick edit menu, or via:```
gmenu-simple-editor
```
and add a custom launcher under office directing it to the program(use browse to make it easy)

---

### Post by tadcan on 2008-04-27
Its in the home folder so I did the following

```
sudo mv ~/home/celtx /opt/celtx
```

but got this

```
mv: cannot stat `/home/tadcan/home/celtx': No such file or directory
```

I think I didn't install the program properly.

---

### Post by tadcan on 2008-04-27
I don't think I installed the program properly. It will only open from inside the unpacked folder. 

I right clicked on applications and was able to add celtx to menu, but the shortcut didn't go anywhere.

---

### Post by scragar on 2008-04-27
the ~/ indicates your home directory, so if it's called celtx and it's in your home directory the command is:
```
sudo mv ~/celtx /opt/celtx
```

---

### Post by tadcan on 2008-04-27
```
tadcan@Quad:~$ sudo mv ~/celtx /opt/celtx
mv: cannot stat `/home/tadcan/celtx': No such file or directory
```

---

### Post by scragar on 2008-04-27
ok, let's try it this way:

type```
sudo mv 
```
with a space on the end, then drag the folder into the terminal(it should then put in the file path for you), and finish it off:
```
sudo mv **File-Path-Here** /opt/celtx
```

then when you want to make the launcher enter the path:
```
/opt/celtx/celtx
```

---

### Post by tadcan on 2008-04-27
This is really strange. I went back into home and the celtx folder was gone. Even though I had been writing stuff into it. I can see the celtx.tar.gz file.

I think I'd better try and installing from scratch.

AHH! I hadn't been able to use ```
tar xvzf pakage.tar.gz
``` because the file had a capital C 

So I've unpacked the file in the terminal. Which gives me the same folder in home that I had before.

According to [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

the next step is 

```
cd package
```

but I get this

```
tadcan@Quad:~$ cd package
bash: cd: package: No such file or directory
```

How do i continue the installation?

---

### Post by tadcan on 2008-04-27
Maybe this will help

```
tadcan@Quad:~$ ls
CB-35P_3_1_1_7_Release  eschalon_book_1_demo  Music              Templates
celtx                   Examples              MV-S800374-00.zip  Videos
Celtx.tar.gz            good_WG133v3-driver   ndiswrapper-1.52
Desktop                 Inf                   Pictures
Documents               mrv8335.inf           Public
```

---

### Post by tadcan on 2008-04-27
Silly me package is the defaults name in the example. 

```
tadcan@Quad:~$ cd celtx
```

Next step is configure
```
tadcan@Quad:~/celtx$ ./configure
bash: ./configure: No such file or directory
```

Any one can help?

---

### Post by scragar on 2008-04-27
you arn't compiling celtx, it comes precompiled, you just run it.
```
sudo mv ~/celtx /opt/
```
right click the menu, and the launch, using the exact command:
```
/opt/celtx/celtx
```

---

### Post by tadcan on 2008-04-27
```
tadcan@Quad:~$ sudo mv ~/celtx /opt/
mv: cannot move `/home/tadcan/celtx' to a subdirectory of itself, `/opt/celtx'
```

Thanks for explaining that.

Its late for me. Going to bed soon.

---

### Post by scragar on 2008-04-27
dunno why mv is throwing a temper tantrum, try:
```
sudo cp -v ~/celtx /opt/celtx
```
or:
```
sudo cp -v ~/celtx /opt
```

if either works then you can delete the copy in your home directory later, atleast with CP you won't acidentaly lose your copy of it though :P

---

### Post by tadcan on 2008-04-28
```
tadcan@Quad:~$ sudo cp -v ~/celtx /opt/celtx
[sudo] password for tadcan:
cp: omitting directory `/home/tadcan/celtx'
tadcan@Quad:~$ sudo cp -v ~/celtx /opt
cp: omitting directory `/home/tadcan/celtx'
```

---

### Post by tadcan on 2008-04-30
This is how I currently open celtx. I open the folder in the home directory, then right click on the page like icon and choose run. 

Is that normal in Ubuntu?

---

### Post by scragar on 2008-04-30
ok, if we can't move the folder forget that, just add a menu item for it and point it to the launcher you already have(the one your getting the display/run/terminal box for)

---

### Post by tadcan on 2008-04-30
Thanks Scragar its in my menu and launchers!

---

