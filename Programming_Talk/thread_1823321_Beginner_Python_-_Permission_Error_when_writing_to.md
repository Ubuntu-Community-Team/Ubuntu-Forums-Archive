---
title: "Beginner Python - Permission Error when writing to text file"
date: 2011-08-11
forum: Programming Talk
---

### Post by heatherr126 on 2011-08-11
Hi,

So, I'm stuck on a permission error on when attempting to open text files to be able to write to them.  I have some experience with programming, but this is my first time ever using ubuntu (11.04).  

I've been working through the exercises in "Learning Python the Hard Way" and am stuck on exercise 16 because of this error.

This works fine:

```
from sys import argv
script, filename = argv
txt = open(filename)

```

But, this gives me the error  
    IOError: [Errno 13] Permission denied: 'sample.txt' 

```
from sys import argv
script, filename = argv
txt = open(filename, 'w')

```

I've been using the terminal, and called the program as such:
```

python ex15.py sample.txt 
```

I'm not sure if there is some setting I need to change to allow writing/editing of the text files?

I tried to search the forums and google the error, but everything seems to be a more complicated problem than what I am having.

Thanks in advance!

---

### Post by papibe on 2011-08-11
Try this before running it (it adds read permissions to the file):
```
$ chmod a+r sample.tx
```
Regards.

---

### Post by cgroza on 2011-08-11
Could you tell us were the sample.txt file is located? If it is in the home directory you should not have any permission problems with it.

---

### Post by Alan D on 2011-08-12
By default your file will be written to the directory containing your py file. If the code file is outside of /home, you will have write permissions to deal with. 

At first glance, this seems most likely.

---

### Post by dazman19 on 2011-08-12
find the folder you are writing to. and use command ls -l on it.

if the file you are writing do already exists, if you open with open(filename, 'w') you are going to overwrite it. if this is not what you want use append. 

if the user you are running the python program as is not the owner of the folder. then you most likely wont have write access. (if its outside your home directory).

use
chown usertogiveowhershipto:usertogiveowhershipto filename
and if that still fails you should give RWX to the owner.
chmod -R 755 foldername (recursively give RWXR-XR-X to that folder. 

You will probably need to be root or a sudoer to run these depending on where they are located.

---

### Post by heatherr126 on 2011-08-12
Both the sample.txt and ex15.py file are in the same folder:

```

heather@heather-Inspiron-8600:~/pythonthehardway/ex15$ ls
ex15.py  sample.txt
heather@heather-Inspiron-8600:~/pythonthehardway/ex15$ ls -l
total 8
-rw-r--r-- 1 root root 273 2011-08-11 16:45 ex15.py
-rw-r--r-- 1 root root  98 2011-08-11 15:30 sample.txt
heather@heather-Inspiron-8600:~/pythonthehardway/ex15$ 

```

I thought that the ~ means that I am in my home directory, and was really confused about the error.

---

### Post by aeiah on 2011-08-12
> **heatherr126 said:**
> 

```


-rw-r--r-- 1 root root 273 2011-08-11 16:45 ex15.py
-rw-r--r-- 1 root root  98 2011-08-11 15:30 sample.txt
heather@heather-Inspiron-8600:~/pythonthehardway/ex15$ 

```


you are in your home directory (~/), but as you can see, the files are owned by root. have you been running your python command with sudo?

---

### Post by aeiah on 2011-08-12
to take ownership of the whole pythonthehardway directory, open a terminal and do
```

sudo chown -R heather:heather pythonthehardway/

```

this will recursively change the ownership of the directory and its contents to user: heather group: heather

---

### Post by heatherr126 on 2011-08-12
aeiah - I have not been running my commands with sudo, however when I try your suggestion I get the following: 

```
 

heather@heather-Inspiron-8600:~$ sudo chown -R heather: heather pythonthehardway/
[sudo] password for heather: 
chown: cannot access `heather': No such file or directory

```

Looking at the Wikipedia page for chown, I thought I might be typing in the directory incorrectly, so I did the following:

```


heather@heather-Inspiron-8600:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
heather@heather-Inspiron-8600:/$ cd home
heather@heather-Inspiron-8600:/home$ ls
heather
heather@heather-Inspiron-8600:/home$ cd heather
heather@heather-Inspiron-8600:~$ ls
Desktop    Downloads  examples.desktop  Pictures  pythonthehardway  Ubuntu One
Documents  Dropbox    Music             Public    Templates         Videos
heather@heather-Inspiron-8600:~$ sudo chown -R heather: heather pythonthehardway/
chown: cannot access `heather': No such file or directory
heather@heather-Inspiron-8600:~$ 

```

Do I need to modify
```

$ sudo chown -R heather: heather pythonthehardway/

```
?

I tried the following with the same error:
```

~$ sudo chown -R heather: heather/pythonthehardway/
chown: cannot access `heather/pythonthehardway/': No such file or directory

```

---

### Post by papibe on 2011-08-12
There has to be no space between the your username and the colons:
```
$ sudo chown -R heather:heather pythonthehardway/
                       [COLOR="Red"]**[SIZE="4"]^[/SIZE]**[/COLOR]

```
Regards.

---

### Post by heatherr126 on 2011-08-12
It worked!

Thank you all so much!

:KS

---

