---
title: "[SOLVED] Installing/Compiling Help"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-07
Hello all. I am fairly new to compiling in Linux, so I came here. I am trying to install Xchat for use with the freenode network so I can access the Ubuntu IRC client. Here is what it says  for the INSTALLATION:

[I]# Unpack the archive:
tar -xzvf xchat-x.x.x.tar.gz
or
tar -xjvf xchat-x.x.x.tar.bz2

# Run the configure script:
cd xchat-x.x.x
./configure

# Compile the program:
make

# Become root and install the program:
su

(enter password)

make install 
[/I]

Now, the directory (xchat-2.8.4) is on the Desktop. This is what my Terminal looks like:

```
dan@dan-desktop:~$ cd xchat-2.8.4
bash: cd: xchat-2.8.4: No such file or directory
dan@dan-desktop:~$ 
```

Can anyone help me out with this? I'd love to be able to properly get access into directoryd via the Terminal. Thanks for the help.

---

### Post by quelx on 2008-05-07
xchat is part of Ubuntu, just do 

```
sudo apt-get install xchat-gnome
```

if you really want to compile the source you need to 

```
cd Desktop/xchat-2.8.4
```

From your home folder (the ~) the desktop is a sub directory (~/Desktop)

---

### Post by UnknownFear on 2008-05-07
That did the trick. Thanks a lot!

---

### Post by Joeb454 on 2008-05-07
Personally I prefer the Standard Xchat over Xchat-gnome (I know - I've used both).

You can install that by running ```
sudo aptitude install xchat
``` :) You can of course have both installed at the same time if you want to give them a try :D

---

### Post by UnknownFear on 2008-05-09
> **Joeb454 said:**
> Personally I prefer the Standard Xchat over Xchat-gnome (I know - I've used both).

I tried xchat-gnome, but didn't like the GUI, so I installed the standard xchat and I like it a lot more :).

---

