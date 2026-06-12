---
title: "what exactly does export PKG_CONFIG_PATH and . /ect/profile do?"
date: 2017-05-20
forum: New to Ubuntu
---

### Post by cactusfrog2 on 2017-05-20
I am  installing openCV by following this tutorial: 
[http://www.cstechera.com/2015/10/how-to-install-opencv-in-ubuntu-14-04.html](http://www.cstechera.com/2015/10/how-to-install-opencv-in-ubuntu-14-04.html)
I successfully installed it and I was able to get it to run, but I don't fully understand the part of the tutorial that involves setting up environmental variables. 
I copied and pasted the following segment of the tutorial below so you can see what I am referring to. 
> [QUOTE][FONT=&amp]**4.** Setup Environment variables. Edit "/etc/profile" in your favorite editor as follows & save before closing it,[/FONT]
```
[FONT=&amp]export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig[/FONT]
 [FONT=&amp]export LD_LIBRARY_PATH=/usr/local/lib[/FONT] [FONT=&amp]
[/FONT]
```[FONT=&amp]Type  the following command on terminal to take affect our above changes.  Again Notice the space between 'dot' & "/etc/profile"[/FONT]
```
[FONT=&amp]$ . /etc/profile[/FONT] [FONT=&amp]
[/FONT]
```[/QUOTE]

I don't fully understand what the two export commands do. I simply typed them into the terminal and pressed enter. After typing them openCV does not run until I type . /ect/profile. After typing these three commands openCV runs. 

My primitive understanding of the export commands is that it somehow tells linux where to look for pkgconfig and where to look for the new libraries. 
I have no idea what the . /ect/profile comand does.
What exactly do these commands do? What steps should I take to make it so that openCV runs without having to type these three commands every time I want  to run openCV? Should I simply edit /ect/profile with vim and add the two export commands to the top of the file?

---

### Post by Keith_Helms on 2017-05-20
> **cactusfrog2 said:**
> Should I simply edit /ect/profile with vim and add the two export commands to the top of the file?

Yes, that is what the instructions were telling you to do when they said
```
[FONT=&amp]Edit "/etc/profile" in your favorite editor as follows & save before closing it,[/FONT]
```[FONT=&amp]
I'd add the instructions to the BOTTOM of the file, not the top.

/etc/profile runs automatically every time you start the machine.   Doing a ". /etc/profile" runs it manually and is only needed when you changed something in it since your system started.[/FONT]

---

### Post by cactusfrog2 on 2017-05-22
Thanks for the help.
I added the two export lines to the bottom of the  /ect/profile file. This profile is not loaded automatically when I open a new terminal so I have to type . /ect/profile every time. I think there is a local /ect/profile somewhere that overrides the system profile file. I am not entirely sure where this is located.

---

### Post by steeldriver on 2017-05-22
The /etc/profile file (note the spelling: **not **/ect/profile) is loaded for login shells - when you open a new GUI terminal, that by default launches a non-login shell, which loads your ~/.bashrc however it should inherit exported variables from the desktop session - including those from /etc/profile

HOWEVER I don't really understand why you need to do this - AFAIK pkg-config searches /usr/local/lib/pkgconfig by default - and in any case, it's used for *compiling *programs, not for running them. Also, OpenCV is a library not a program - what exactly do you mean by "so that openCV runs"?

---

