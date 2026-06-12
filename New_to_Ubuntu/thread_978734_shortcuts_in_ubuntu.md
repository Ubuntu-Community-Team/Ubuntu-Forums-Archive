---
title: "shortcuts in ubuntu?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Chapter&amp;Moon on 2008-11-11
I used to put shortcuts on my desktop in Windows so I could single click all over the world efficiently. How do I do that in ubuntu?

---

### Post by abeisgreat on 2008-11-11
> **Chapter&Moon said:**
> I used to put shortcuts on my desktop in Windows so I could single click all over the world efficiently. How do I do that in ubuntu?

On your desktop 

Rightclick > Add Launcher

Then if the program is install just enter the name in the command box and done :D

---

### Post by mcduck on 2008-11-11
For program launchers just frag & drop them from the Applications-menu to your desktop. For links to fils/directories just drag them to desktop with middle mouse button and select "create link" (or whatever the actual option is) from the popup menu.

---

### Post by stans on 2008-11-12
How do I get a command such as ./startmvs to work ? It works great from Terminal - so I'd like to start the terminal application then issue the .startmvs command from the launcher.

---

### Post by bcd87 on 2008-11-12
Can't you use "Create Launcher" like abeisgreat said and then just put in the path to startmvs?

---

### Post by stans on 2008-11-12
That is why I am here asking - it doesn't work from launcher but DOES work from terminal. So I need to start terminal and from it issue the ./startmvs command - via launcher.

---

### Post by directcharitycontribution on 2008-11-12
is it <application in terminal>?

---

### Post by stans on 2008-11-12
If I understand your question - it is started via terminal. I open terminal then issue ./startmvs

This is the script that executes:

#!/bin/bash
PATH /home/stan/mvs38j/hercules:${PATH}
clear
echo "Do not IPL until you have started all the clients"
echo "needed to successfully start MVS:"
echo "  a)  A standard telnet client to this host on port 3270"
echo "  b)  Two tn3270 clients to this host on port 3270 as consoles"
echo "  c)  Additional tn3270 clients as TSO terminals"
echo "  "
echo "  press the ENTER key to continue hercules startup"
read dummy
hercules -f ./conf/turnkey_mvs.conf

---

### Post by theozzlives on 2008-11-12
> **Chapter&Moon said:**
> I used to put shortcuts on my desktop in Windows so I could single click all over the world efficiently. How do I do that in ubuntu?

in Linux they're called launchers, anyhoo right click on the launcher and select add launcher to desktop, you can also add them to the panel. I created  a new panel and  put it on the left of my desktop  and  put my fequently used progs there.

---

### Post by bcd87 on 2008-11-12
> **stans said:**
> If I understand your question - it is started via terminal. I open terminal then issue ./startmvs

This is the script that executes:

#!/bin/bash
PATH /home/stan/mvs38j/hercules:${PATH}
clear
echo "Do not IPL until you have started all the clients"
echo "needed to successfully start MVS:"
echo "  a)  A standard telnet client to this host on port 3270"
echo "  b)  Two tn3270 clients to this host on port 3270 as consoles"
echo "  c)  Additional tn3270 clients as TSO terminals"
echo "  "
echo "  press the ENTER key to continue hercules startup"
read dummy
hercules -f ./conf/turnkey_mvs.conf

What about making a link to the file?
Go to the directory where startvms is located in terminal, then type:
ln startvms ~/Desktop/startvms

Then just open the startvms file on your desktop.

---

### Post by stans on 2008-11-12
Do you mean add that line as the first line in the script ?

---

### Post by bcd87 on 2008-11-12
Nah, leave the script alone. Just put that command in terminal. It'll make a hard link file on your desktop called startvms that links to wherever your startvms file is located.
I think you should be able to start it from your desktop then :)

---

### Post by stans on 2008-11-12
I tried it and the script actually took off. I only want to execute it from the launcher.

Oh well... out of time for the morning.

BTW - thanks for your reply.

---

### Post by Flimm on 2008-11-12
Right-click on the destkop, do create launcher, type in the command section:
```
/home/user/startmvs
```
Replace user with your username.

This should work, because your script is in your home directory. When you open a terminal, your current directory is your home directory (type pwd to see your current directory). A dot stands for your current directory, that's why you had to type
./startmvs
for it to work.

---

### Post by stans on 2008-11-12
Thanks... but I did try that. I tried several variations. This evening I will continue experimenting.

---

