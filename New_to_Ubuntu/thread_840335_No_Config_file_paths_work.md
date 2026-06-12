---
title: "No Config file paths work"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by climb.colorado on 2008-06-25
****

I am curious to know, why is it that when I try to locate my configuration files for a specific program, I always get the error - "no directory found"?  Is there a way around this?  Is there somewhere I can bring up a list of ALL my configuration file paths?  Please help!  Thanks!

---

### Post by ET! on 2008-06-25
are you asking the kernel config file???

---

### Post by cpetercarter on 2008-06-25
Config files are normally in the /etc directory.

---

### Post by chrisccoulson on 2008-06-25
Please tell us which configuration files you are having issues with

---

### Post by climb.colorado on 2008-06-25
I'm having problems with any and all config files - sys.conf, Apache2.conf, Server.conf.  The problem really is when I install something new and want to check out how it is configured, nothing ever works.  For example:

sudo /etc/apache2/apache2.conf - no directory found

yet this is what eveyone is telling me to input.

---

### Post by chrisccoulson on 2008-06-25
> **climb.colorado said:**
> I'm having problems with any and all config files - sys.conf, Apache2.conf, Server.conf.  The problem really is when I install something new and want to check out how it is configured, nothing ever works.  For example:

sudo /etc/apache2/apache2.conf - no directory found

yet this is what eveyone is telling me to input.
Try:
```
sudo nano /etc/apache2/apache2.conf
```
...to open the file in the nano text editor

---

### Post by avtolle on 2008-06-25
Or, just to read it ```
cat /etc/apache2/apach2.conf
```

---

### Post by climb.colorado on 2008-06-25
> **avtolle said:**
> Or, just to read it ```
cat /etc/apache2/apach2.conf
```
It says "no such file or directory"

---

### Post by avtolle on 2008-06-25
"cat" is short for concatenate. The simple form of the command as I gave you just "concatenates" the contents of the file and using the standard output routine, "prints" it to the terminal so you may read the file. See```
man cat
```for more information.

---

### Post by cpetercarter on 2008-06-25
@climb.colorado
The command in the terminal needs:

1  "sudo" - so that you can work with root privileges. You can't open most config files without such priveliges.

2  "nano" or "gedit" or the name of another text editor (installed on your computer, obviously)

3  the path from root to the file you want to open

And you need to get the spelling right, since computers are totally dumb at guessing what you meant to type. There is a small typo ("apach2" instead of "apache2") in the command you tried earlier.


The terminal will ask for your password (ie your normal log-in password). Type it in and hit Enter.

PS If you are using gedit, you should use gksudo rather than sudo.

---

### Post by avtolle on 2008-06-25
Sorry about the typo there; just flat missed it before posting. :-(

---

