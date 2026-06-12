---
title: "Xubuntu executing error"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Nixuser91 on 2008-10-17
Everytime I try to execute this file I run into the "No such file or directory" error.. The file is infact there so im not sure why im getting this error. Ive tried  " chmod 777 filename "   then  " ./filename "
and still get the same error..someone please tell me what is going on before i go insane. If it helps im running Xubuntu on the AMD 64bit version.   THANKS

---

### Post by Michael.Godawski on 2008-10-17
I would make sure the filename is written as Xubuntu wants it to be. So navigate in terminal to the location of the file and list all available files with the command

```
ls -a
```

Being in the right directory,execute the chmod as superuser:

```
sudo chmod 777 filename
```

What file do you want to execute?

---

### Post by Nixuser91 on 2008-10-17
Im just trying to run a simple bot :(

```
nixserv@nixserv-laptop:~/rival$ ls -a
.  ..  rivalbot  rivalbot.cfg
nixserv@nixserv-laptop:~/rival$ sudo chmod 777 rivalbot
[sudo] password for nixserv: 
nixserv@nixserv-laptop:~/rival$ ./rivalbot
bash: ./rivalbot: No such file or directory

```

---

### Post by stumbleUpon on 2008-10-17
what happens if you make a copy of the file and rename it to something else and then try to run it?

---

### Post by Nixuser91 on 2008-10-17
The same thing happens...

---

### Post by hyper_ch on 2008-10-17
```

sudo ls -al

```

---

### Post by Nixuser91 on 2008-10-17
```
nixserv@nixserv-laptop:~/rival$ sudo ls -al
[sudo] password for nixserv: 
total 32
drwxr-xr-x  2 nixserv nixserv  4096 2008-10-17 02:08 .
drwxr-xr-x 21 nixserv nixserv  4096 2008-10-17 02:15 ..
-rwxrwxrwx  1 nixserv nixserv 18833 2008-10-16 00:31 rivalbot
-rw-r--r--  1 nixserv nixserv  2610 2008-10-16 00:32 rivalbot.cfg

```

---

### Post by stumbleUpon on 2008-10-17
Can you post the contents of the those two files?

---

### Post by Nixuser91 on 2008-10-17
well the .cfg file is obviously just a config file for the rivalbot executable program.
when i try to right click and execute on the executable file I get this error

Failed to execute child process "/home/nixserv/rival/rivalbot" (No such file or directory).

Not sure if I follow your request

---

### Post by stumbleUpon on 2008-10-17
I wanted to see what the rivalbot file is supposed to do. 

Did you write the file yourself as a shell script? or did you get it from somewhere else?

Just open the file in some text editor and post the contents (if the file is not very large in size).

---

