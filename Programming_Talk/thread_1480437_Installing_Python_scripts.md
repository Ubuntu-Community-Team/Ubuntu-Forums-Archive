---
title: "Installing Python scripts"
date: 2010-05-11
forum: Programming Talk
---

### Post by kalasoka on 2010-05-11
Hi Everyone,

I have a small application written using Python. I've a "setup.py" script to install this application and related files. However, I'm confused where should these files get installed. 

Would "/usr/local/myapp" be a good idea? Or is there any kinda standard location in Linux where one should install them? 

The point to note is that this is not a single executable file. But a bunch of scripts together with other related data and configuration files - and they should exist in the same directory. 

Thanks in advance for all your help!

~ Barun

---

### Post by derrick81787 on 2010-05-11
> **kalasoka said:**
> Hi Everyone,

I have a small application written using Python. I've a "setup.py" script to install this application and related files. However, I'm confused where should these files get installed. 

Would "/usr/local/myapp" be a good idea? Or is there any kinda standard location in Linux where one should install them? 

The point to note is that this is not a single executable file. But a bunch of scripts together with other related data and configuration files - and they should exist in the same directory. 

Thanks in advance for all your help!

~ Barun

I had a similar setup for one of my Python programs I had written.  I put all of my files into /etc/myapp/ and then put a simple executable Bash script into /usr/local/bin that I used to cd into the directory and launch the program.  /usr/local/bin is the standard location to put custom applications, but only binaries go in there.

If you do this and put your files in /etc/myapp/ and the name of your main executable is myexec, the bash script (here called myscript) would look like this:

```
#!/usr/bin/env bash
cd /etc/myapp
./myexec
exit
```

Then, as long as it's marked executable with *chmod +x myscript*, you can launch your program from the command line by simply typing *myscript*.

- Derrick

---

### Post by kalasoka on 2010-05-11
Hi Derrick,

This seems to be a good idea!

---

### Post by wmcbrine on 2010-05-11
Please don't put programs under /etc.

[http://www.dslreports.com/forum/r24165131-Where-to-palce-my-app-and-files](http://www.dslreports.com/forum/r24165131-Where-to-palce-my-app-and-files)

---

### Post by kalasoka on 2010-05-12
Thanks for pointing this out!

I think I should go for installing in the $HOME dir itself. It's a rather small application, and theoretically multiple users could have different configurations. That way, I can put all my files altogether.

---

### Post by wmcbrine on 2010-05-12
Ugh. No. You can have a global installation with per-user configuration, and you should. Applications that do this normally keep their config data in a "hidden" file in $HOME (i.e., a file whose name starts with a "."). They may also keep global config (only!) in /etc.

I really urge you to take a closer look at what existing apps do before you proceed. And don't worry about keeping all your files together, because -- generally speaking -- Linux just doesn't work that way.

---

