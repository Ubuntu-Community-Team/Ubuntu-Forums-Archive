---
title: "moving program to etc."
date: 2008-05-01
forum: New to Ubuntu
---

### Post by cwrann on 2008-05-01
I am running Xubuntu 7.10

I have just installed a program from a tar.gz. This is the first time I have installed software on my computer other than from add/remove or synaptic. I can successfully run the program from terminal.

I have two questions: How do I get the program file off my desktop and into etc. and how do I get a launcher under the office category in my launcher panel.

when I try to extract directly to etc. I get this message.

```
tar: celtx: Cannot mkdir: Permission denied
```

---

### Post by SunnyRabbiera on 2008-05-01
you have to use sudo, as the etc folder needs root access.
in your terminal make sure to put sudo before the command you need

---

### Post by Tatty on 2008-05-01
Firstly, why are you trying to extract it to /etc?  If the instructions do not tell you to do that then it would be best to keep it in /home for the time being.

But the reason you are having problems is because you need superuser powers to extract to /etc.  How are you trying to extract? if it is via commandline then you need to preface your command with sudo, eg:
```
sudo tar *parameters...*
```

If you are doing it graphically then to launch nautilus with superuser powers type ```
gksu thunar
```

(gksu is just like sudo, except with a few tweaks which make it handier for running graphical apps in)

---

### Post by Monicker on 2008-05-01
> **cwrann said:**
> I am running Xubuntu 7.10

I have just installed a program from a tar.gz. This is the first time I have installed software on my computer other than from add/remove or synaptic. I can successfully run the program from terminal.

I have two questions: How do I get the program file off my desktop and into etc. and how do I get a launcher under the office category in my launcher panel.

when I try to extract directly to etc. I get this message.

```
tar: celtx: Cannot mkdir: Permission denied
```

/etc is not the proper place for executables; that directory is for configuration files.

/usr/local/bin would be more suitable.

```
sudo cp programname /usr/local/bin
```

For a launcher, you can right click the top panel, select Add to Panel, and then select Custom Application Launcher.

---

### Post by cwrann on 2008-05-01
Thank you for the reply.
the program is celtx it is currently on the desktop, what command should i use to get it into etc?

---

### Post by SunnyRabbiera on 2008-05-01
well you can just extract it, open up a terminal and type in sudo thunar and manage your way to your filesystem, then go to the etc folder...

---

### Post by Tatty on 2008-05-01
command line:

```
sudo cp /home/*path/to/fil*e /etc/*path/to/where/it/should/be*
```

or grapically:

```

gksu thunar
```  Then drag n drop.


But as mentioned by monicker, it would be best in /usr/local/bin

**EDIT:** Apologies, just after reading the last post that you are using xubuntu which uses thunar instead of nautilus, have amended my posts to suit

---

### Post by cwrann on 2008-05-01
Sorry, I got the later messages after I posted my reply. I thought the program belonged in etc. because that is where I found open office and figured that they are similar programs and belonged in the same folder, I guess not.

I tried

---

### Post by cwrann on 2008-05-01
... I tried
```
sudo cp celtx /usr/local/bin
```

It did put the shell script in this folder but I cannot get the prgram to run from this folder.

---

### Post by SunnyRabbiera on 2008-05-01
dont give up, you made a basic mistake thats all.
you could try to place the app in usr/bin, and if you need to link to it you know where it is now :D

---

### Post by Tatty on 2008-05-01
[http://wiki.celtx.com/index.php?title=Install#For_Linux](http://wiki.celtx.com/index.php?title=Install#For_Linux)  here are the installation instructions for you :)

---

### Post by cwrann on 2008-05-01
Thanks everybody, I got it all figured out now.

---

