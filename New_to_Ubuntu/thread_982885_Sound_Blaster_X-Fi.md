---
title: "Sound Blaster X-Fi"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by hitmanhogan on 2008-11-15
Sound Blaster X-Fi Linux 32/64-bit Driver has now been released.  The readme file has the following information:



Quick install
=============
In terminal,

1) Goto source directory

2) Execute make command as root

   make

   make install


[B]When I go to terminal I get:

michael@michael:~$ [/B]


so I try to "goto source directory" but Terminal gives me this message:

[B]michael@michael:~$ cd/desktop/driver
bash: cd/desktop/driver: No such file or directory[/B]

I guess the CD/ command does not work in terminal?


SO!!!  What do I have to do to install this driver?
Note:  The driver has been downloaded and extracted on my desktop in a directory named "Driver".  

Thanks
Mike**[B]**[/B]

---

### Post by expatCM on 2008-11-15
Ubuntu is case sensitive.  Please try here ... 
cd/desktop/Driver

---

### Post by MasterSander on 2008-11-15
Don't you mean cd ~/Desktop/driver or cd ~/Desktop/Driver

---

### Post by hitmanhogan on 2008-11-15
I figured out the problem.


In terminal, when you are changing directories you don't use /.  For example, cd/Desktop.  All you do is type cd Desktop.  

The installation went perfectly and I have sound with my Fatality sound card.  FINALLY!

Thanks for the help.

Mike

---

### Post by masa77 on 2009-01-23
> **hitmanhogan said:**
> I figured out the problem.


In terminal, when you are changing directories you don't use /.  For example, cd/Desktop.  All you do is type cd Desktop.  



Not really.. when starting with / you start from root directory and you need to enter the whole path. Without / it's relative. Example:
1. cd /home/your_homedir/Desktop or cd ~/Desktop
2. If you are already standing in your homedir, then and only then will cd Desktop work. 

Also note you need a space between cd and /

/Mattias

---

