---
title: "[SOLVED] Trying to install a program in root -help"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by browny254 on 2008-11-25
Hi, there is a program I am trying to install in the /opt directory. The program comes as a perl script that when run should download the necessary files and install them automatically, but when I run it I get the following error```
mkdir "/opt/prog/system" failed: Permission denied (13)

```

I have changed the ownership of both the perl script and /opt by using chmod 777, but I'm still getting the same error?

Is there anything user or group related I need to change to be able to do this?

Cheers.

---

### Post by taurus on 2008-11-25
How about you create with sudo command.

```
sudo mkdir /opt/prog/system
```

---

### Post by browny254 on 2008-11-25
That would probably work, but the program contains 100's of folders, that is just the first so I cant really manually make them all.

---

### Post by aysiu on 2008-11-25
How about running the script using *sudo*?

---

### Post by browny254 on 2008-11-25
ok tried that and got this error right away.



```
Error: You are logged in as root or are a member of the root group.  This leads to all sorts of trouble.
```

---

### Post by taurus on 2008-11-25
Do you allow to use sudo?  Are you the first/original user that you created during the installing process?

What's the output of this command from a terminal?

```
id
```

---

### Post by halitech on 2008-11-25
what exactly are you trying to run/install? almost sounds to me like the program knows it shouldn't be run as root (sudo in our case).

---

### Post by browny254 on 2008-11-25
yeah im the only user on this computer,

[CODE]$ id
uid=1000(andrew) gid=1000(andrew) groups=4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),119(admin),120(sambashare),1000(andrew)
[\CODE]

---

### Post by browny254 on 2008-11-25
the program is some image processing software found here [http://www.aips.nrao.edu/install.shtml](http://www.aips.nrao.edu/install.shtml)

---

### Post by taurus on 2008-11-25
Assuming you are in the directory where those files are, what happens if you run it like this?

```
sudo ./install.pl
```

---

### Post by browny254 on 2008-11-25
this is the full output I get when I run that...

andrew@Laptop:/opt/aips$ sudo ./install.pl -n       ( <-the -n is to say continue previous install )
AipsWiz: Error: You are logged in as root or are a member of the
AipsWiz: Error: root group.  This leads to all sorts of trouble.

AipsWiz: Error: Quitting now - log in as a normal user and run
AipsWiz: Error: install.pl from that account.

---

### Post by halitech on 2008-11-25
ummmmmm okay, good luck with this. I'm not sure but is this some kind of backup software?

---

### Post by browny254 on 2008-11-25
No, its a program to process astronomy data.

Im sure that the error is related to group or user permissions, its just i dont really know enough about linux to work out what to change or even how or where... 

thanks anyway.

---

### Post by halitech on 2008-11-25
ok, maybe instead of trying to install to /opt, install it in your /home folder and see what happens

---

### Post by browny254 on 2008-11-25
Yeah it works in /home...well at least I think it is, its downloading but I only have a 256k connection here so it will take a while till I know if it worked. 

Still Id like to be able know how to get it installed in /opt, because I will be installing it on more computers in the future that will have more than one user accessing it.

---

### Post by rhcm123 on 2008-11-25
> **browny254 said:**
> this is the full output I get when I run that...

andrew@Laptop:/opt/aips$ sudo ./install.pl -n       ( <-the -n is to say continue previous install )
AipsWiz: Error: You are logged in as root or are a member of the
AipsWiz: Error: root group.  This leads to all sorts of trouble.

AipsWiz: Error: Quitting now - log in as a normal user and run
AipsWiz: Error: install.pl from that account.

try running it without the sudo command

---

### Post by halitech on 2008-11-25
not sure what to tell you, seems the instructions are generic *nix so maybe its something with the way Ubuntu uses sudo to do things and you need a true root login *shrugs* maybe try contacting the software developers and see if they can help.

---

### Post by browny254 on 2008-11-25
> **rhcm123 said:**
> try running it without the sudo command

then i get my original error...

```
mkdir "/opt/prog/system" failed: Permission denied (13)
```

---

### Post by browny254 on 2008-11-25
> **halitech said:**
> not sure what to tell you, seems the instructions are generic *nix so maybe its something with the way Ubuntu uses sudo to do things and you need a true root login *shrugs* maybe try contacting the software developers and see if they can help.

No, it definatley works fine in ubuntu (well kubuntu at least). I had it installed before but I did a clean install for 8.10 and lost it. I installed it so long ago though that I have no idea how I did it, I saved the output from the terminal window, but the install procedure is more than 1000 lines long which is all the terminal was dipalying and I have only now just realised that I didnt end up saving anything useful.

I know I had this exact same problem first time and it took me a long time to get it and it was related to permissions some how, just thought someone would know exactly what my problem is so I dont have to spend a couple of days tinkering.

---

### Post by halitech on 2008-11-25
ok, then *maybe* this will work but then again maybe not.

you do have the /opt/???? folder created correct? if you do, open a root nautilus (gksu nautilus) and see if you can go to the folder, right click-properties and change the ownership on that folder that way. then see if it will let you install.

---

### Post by browny254 on 2008-11-25
ahh yes, thats just rung a bell, I did chmod 777 to /opt, but I dont think that changes all subdirectories which I think I did last time. Is there some way to easily do this do you know?

---

### Post by halitech on 2008-11-25
to do it for all sub-directories, do 
```
sudo chmod -R 777 /opt/????
```

the -R is for recursive so it will change all folders inside it

---

### Post by browny254 on 2008-11-25
YES! that did it...I knew it was something stupid like that. Cheers Halitech, you got me there a lot quicker than if i was working through it myself :D

---

### Post by halitech on 2008-11-25
thats what we are all here for, to help and be helped :) remember to mark the thread solved in case anyone else comes looking.

---

