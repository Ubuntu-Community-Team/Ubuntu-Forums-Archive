---
title: "bash : .......... : No such file or directory ?"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by szohaib on 2012-07-22
Hi 
I am trying to run a python program 'hello.py' in folder 'google-python-exercises'. The  'google-python-exercises' folder  exists in 'exjobb'.

I typed the following to run the program
' ~/google-python-exercises$ python hello.py '

but it gives the following error:

exjobb@exjobb-1:~$ ~/google-python-exercises$ python hello.py
bash: /home/exjobb/google-python-exercises$: No such file or directory

can somebody guide whats the problem here?

Thanks in advance

---

### Post by codemaniac on 2012-07-22
Hello szohaib ,

Welcome to the Ubuntu Forums !!!!!


Can you please post the output of the below while standing on the ~/google-python-exercises dir .

```
ls -l hello.py
```

---

### Post by sanderj on 2012-07-22
> **szohaib said:**
> Hi 
I am trying to run a python program 'hello.py' in folder 'google-python-exercises'. The  'google-python-exercises' folder  exists in 'exjobb'.

I typed the following to run the program
' ~/google-python-exercises$ python hello.py '


That's wrong: your terminal now thinks "~/google-python-exercises$" is a command because the first string in a terminal command is interpreted as a command, and it's not.

You should run "python hello.py", but only from the directory where the file hello.py is.

You can move / change to a directory by using the "cd" command. So **if** hello.py is in ~/google-python-exercises, do:

```
cd ~/google-python-exercises
```

first. However, you say "'google-python-exercises' folder  exists in 'exjobb'", so your mileage varies.

---

### Post by szohaib on 2012-07-22
Thanks [sanderj]("http://ubuntuforums.org/member.php?u=754333")
it works now.

one more thing.. could you please tell me whats the use of ' ~ ' and ' / '   before   
 'google-python-exercises'  and of  ' $ '   after that

for example when I just wrote  ' cd google-python-exercises ' , it worked also.

but when I wrote ' cd google-python-exercises$ ' or    ' cd ~/google-python-exercises$ '  it gave the same error of 'no such file or directory'

thanks

---

### Post by szohaib on 2012-07-22
Thanks  codemaniac  for your warm welcome!

the output of  
ls -l hello.py  is ' -rwxrwxrwx 1 exjobb exjobb 970 2010-03-09 02:05 hello.py  '

could you please tell me what '  ls   -l ' does?
I don't understand what this output mean? 

thanks.

---

### Post by richpri on 2012-07-22
ls is the linux dir command [it lists the files in a directory]
ls -l asks for the long format [type "man ls" for a longer explanation].

~ is shorthand for your user home directory and / is the directory path separator. 
/ is also the name of the root of your file system.

try the following commands:

ls /
ls /home
ls /home/XXXX where you replace XXXX with you user ID. 

If you has a subdirectory called Pictures in your home directory 
then "ls ~/Pictures" would print the files there.
But so would ls /home/XXXX/Pictures if you replaced XXXX with you user ID.

---

### Post by richpri on 2012-07-22
See [http://ss64.com/bash/](http://ss64.com/bash/) for a list of all the BASH commands for Linux with some help information for each one.

---

