---
title: "shell script file execute error"
date: 2009-07-13
forum: Programming Talk
---

### Post by rahul_shilps on 2009-07-13
I am using Ubuntu 8.04.. Its having "bash" shell.

I learn t that if i create a shell script file i can combine the commands and fire that commands in one go by including that file in my.sh file

----------------------------
my.sh
----------------------------
#!/bin/sh
# show.bash: Sample shell script
echo "Today's date: `date'"
echo "This month's calendar:"
cal `date "+%m 20%y"`
echo "My shell: $SHELL"
----------------------------

Now when i execute this file as:
$my.sh

error O/P:
it produces following error:
**************************
bash: show.sh: command not found
**********************************

why so ? I have checked my /bin directory there is no "sh" file there is only shortcut of "sh" file. 

but there is file like "bash".

what am i suppose to do now. I got in trouble

Please help me.

---

### Post by monraaf on 2009-07-13
I'm not sure if I'm understanding you here but I think your problem is that the script you are trying to execute is not in your path. Try this:

```

$./my.sh

```

---

### Post by rahul_shilps on 2009-07-13
> **monraaf said:**
> I'm not sure if I'm understanding you here but I think your problem is that the script you are trying to execute is not in your path. Try this:

```

$./my.sh

```

hi,

How to make sure that my.sh is in path?


I fired command as you said its showing error like:

$./my.sh
bash: $./my.sh: No such file or directory

my path is as follows:

 echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

i make sure my file is there what may be the problem

Instead if you give my a simple and best example i can follow it and try to do it.

Thank you.

Rahul

---

### Post by Keith Hedger on 2009-07-13
Are you in the same directory as the script my.sh when you tried ./my.sh also once you have written your script you must make it executable by for instance```
chmod 755 /path/to/your/script/
```

---

### Post by soltanis on 2009-07-13
You said your script was called my.sh, but your bash error names "show.sh". That file isn't listed in your commands. Maybe you're just confusing the names of your script.

You don't need to put scripts into your path every time you write one; keep them in your home directory (it keeps your directories from getting cluttered), and execute them with the

```

./script.sh

```

Syntax mentioned earlier. Also make sure your script has mode 755 set (that's rwxr-xr-x). Your #! line is completely correct, and there is nothing wrong with your shell.

If all else fails, try running

```

sh ./script.sh

```

---

### Post by rahul_shilps on 2009-07-16
> **soltanis said:**
> You said your script was called my.sh, but your bash error names "show.sh". That file isn't listed in your commands. Maybe you're just confusing the names of your script.
 
You don't need to put scripts into your path every time you write one; keep them in your home directory (it keeps your directories from getting cluttered), and execute them with the
 
```

./script.sh

```
 
Syntax mentioned earlier. Also make sure your script has mode 755 set (that's rwxr-xr-x). Your #! line is completely correct, and there is nothing wrong with your shell.
 
If all else fails, try running
 
```

sh ./script.sh

```
 
o sorry that is a mistake.
 
1) I ahve created my.sh in /home/documents
 
2) now i open terminal and will go to /home/documents path
 
3) i fired command my.sh
Then it produce that error
 
What should be done?
 
answer:
         either i should fire
 
         ./my.sh
 
         OR
         i put that shell file in Home directory and fire
 
         ./my.sh
 
What i am supposed to do?

---

### Post by Martin Witte on 2009-07-16
> **rahul_shilps said:**
> o sorry that is a mistake.
 
1) I ahve created my.sh in /home/documents
 
2) now i open terminal and will go to /home/documents path
 
3) i fired command my.sh
Then it produce that error
 
What should be done?
 
answer:
         either i should fire
 
         ./my.sh
 
         OR
         i put that shell file in Home directory and fire
 
         ./my.sh
 
What i am supposed to do?
You can do three things
1) Got to the directory the script is and run it from there with ./
```
martin@sony:~$ cd Documents/
martin@sony:~/Documents$ pwd
/home/martin/Documents
martin@sony:~/Documents$ ls -l
total 4
-rwxr-xr-x 1 martin martin 146 2009-07-16 19:20 my.sh
martin@sony:~/Documents$ ./my.sh
Today's date: Thu Jul 16 19:22:11 CEST 2009
This months calendar:
     July 2009      
Su Mo Tu We Th Fr Sa
          1  2  3  4
 5  6  7  8  9 10 11
12 13 14 15 16 17 18
19 20 21 22 23 24 25
26 27 28 29 30 31   
                    
My shell: /bin/bash
martin@sony:~/Documents$ 
```

2) Run it from any place with the full path name in front of it
```
martin@sony:~$ cd /tmp
martin@sony:/tmp$ pwd
/tmp
martin@sony:/tmp$ /home/martin/Documents/my.sh 
Today's date: Thu Jul 16 19:23:35 CEST 2009
This months calendar:
     July 2009      
Su Mo Tu We Th Fr Sa
          1  2  3  4
 5  6  7  8  9 10 11
12 13 14 15 16 17 18
19 20 21 22 23 24 25
26 27 28 29 30 31   
                    
My shell: /bin/bash
martin@sony:/tmp$ 
```

3) Put the directory the script is in your PATH environment variable```

martin@sony:/tmp$ export PATH=$PATH:/home/martin/Documents
martin@sony:/tmp$ my.sh
Today's date: Thu Jul 16 19:24:59 CEST 2009
This months calendar:
     July 2009      
Su Mo Tu We Th Fr Sa
          1  2  3  4
 5  6  7  8  9 10 11
12 13 14 15 16 17 18
19 20 21 22 23 24 25
26 27 28 29 30 31   
                    
My shell: /bin/bash

```
Assuming you run bash you can set this in file .bashrc in your home directory, see [this link, paragraph 3.1.2.4 for more information on this subject]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html")

---

