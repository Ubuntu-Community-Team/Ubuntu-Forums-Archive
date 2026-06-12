---
title: "Terminal help"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by willyo on 2008-09-11
Hi this is my first post and hopefully last n00b post lol

ive got an eee 901 with 8.04.1 with the eee kernal and the wireless webcam everyting works fine but ive just tried to read a sd card and i have to be a super user to read it 

ive searched the forums and found solutions to the problem regarding becoming a superuser but to fix the problem i am being told to write things in a command line or terminal 

how do i get to the terminal or command line ?

so for this suupper stupid question :P 

many thanks will

---

### Post by t0p on 2008-09-11
**Applications > Accessories > Terminal**

and welcome to ubuntu!! :)

---

### Post by OffAxis on 2008-09-11
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by Bölvaður on 2008-09-11
Whow that is amazing that you are able to go into super user mode without the terminal.

I am not sure how your setup is so I'll just give you few ways.

1. (main gnome way)
Find Applications in the panel at top of your screen. Click it and then find Accessories. Under there you find Terminal.

Applications -> Accessories -> Terminal

2. (Run application: Terminal)
You can also run the program that is called gnome-terminal. It is the same program as above, but this time we dont use shortcuts but just type what program to execute.

Alt+F2

Type:  gnome-terminal

3. (not standard ubuntu)
Right click on the desktop. There should either be a list to make files and copy... rename... ect.. or there will be a list that will include folders like Games, Internet, Accessories.

Find Accessories and click terminal


there you go mate

---

### Post by nothingspecial on 2008-09-11
Then type 
```

sudo
```

before the command you wish to run.

You will be asked for your password, type it, you won`t see it but it`ll work.

---

### Post by Vivaldi Gloria on 2008-09-11
[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

---

### Post by SkonesMickLoud on 2008-09-11
Be careful with sudo.  If you don't know what you're doing you can break stuff.

Out of curiosity, which thread is it that's telling you that you have to be super user to read an SD card?

---

### Post by willyo on 2008-09-11
ok im into terminal thanks guys i spent ages looking through the menues and there it was 

:P

actually cant find that post on super user anymore seems not to search the whole phrase anymore oh well :P

i have a sd card i cant read because it says unable to mount volume 

ive downloaded sudo but  the install instructions seem to give no information on how to install it any tips? 

thanks again

---

### Post by ds[de] on 2008-09-11
You shouldn't have to install sudo, it's already a part of a fresh ubuntu install.

For example, when you execute a command that requires superuser priviledges (let's say /etc/init.d/gdm restart), you'd have to prefix the command with sudo. When asked for a password, enter your user password (don't worry if typing doesn't give you an echo on the screen).

So in our little example you'd write
```
**sudo** /etc/init.d/gdm restart
```

so that the command above is being executed with superuser privs.
Imagine sudo as a substitution for: login as root, execute command, logoff as root (except the root user isn't enabled by default on ubuntu systems).

Hope I could clear things up for you (and also that I understood the problem correctly).


Regards,
ds[de]

---

