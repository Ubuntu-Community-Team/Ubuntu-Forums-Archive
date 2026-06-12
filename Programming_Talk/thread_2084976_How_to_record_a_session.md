---
title: "How to record a session?"
date: 2012-11-17
forum: Programming Talk
---

### Post by Mohan1289 on 2012-11-17
Hi guys..

how can we record a session i.e completed upto now..

i mean 

```

#!/bin/bash
echo "The Kernal Version is"
uname -a
echo "The Distribution Version is"
lsb_release -a
echo "The Partition Sizes are "
cat /proc/partitions


```

after completion of these operations it has to echo what it has done
is that possible?

---

### Post by Lars Noodén on 2012-11-17
You can use [script](http://manpages.ubuntu.com/manpages/precise/en/man1/script.1.html) to record what you do in the shell.  Is that what you were looking for?

---

### Post by Mohan1289 on 2012-11-17
> **Lars Noodén said:**
> You can use [script]("http://manpages.ubuntu.com/manpages/precise/en/man1/script.1.html") to record what you do in the shell.  Is that what you were looking for?

I see but how can use that script again??

suppose i started recording all using

```

script test.log

```

when does it stop and how can i see what that contains.. i tried myself but it's displaying empty file

---

### Post by Lars Noodén on 2012-11-17
[script](http://manpages.ubuntu.com/manpages/precise/en/man1/script.1.html) stops when you press ctrl-D.

The default filename for the saved session is 'typescript' and it will be put in the local directory.  If you want a different name, you can specify it when you start script.

```

script /home/mohan1289/test.log
```

You can even append to an existing session file, using the -a option.  It's all there in the manual page for 'script'.

You can see what the file contains the same way you would for any other text file.  You can use your favorite text editor like 'vi' or a pager like 'less'

```

less /home/mohan1289/test.log

```

---

### Post by Mohan1289 on 2012-11-22
> **Lars Noodén said:**
> [script]("http://manpages.ubuntu.com/manpages/precise/en/man1/script.1.html") stops when you press ctrl-D.

The default filename for the saved session is 'typescript' and it will be put in the local directory.  If you want a different name, you can specify it when you start script.

```

script /home/mohan1289/test.log
```You can even append to an existing session file, using the -a option.  It's all there in the manual page for 'script'.

You can see what the file contains the same way you would for any other text file.  You can use your favorite text editor like 'vi' or a pager like 'less'

```

less /home/mohan1289/test.log

```


This is not working how can i rectify this?? If i 1st started to record the session using script command it's not executing the commands after script here is the script i wrote but no avail..

```


#!/bin/bash
script testscript
echo "The Kernal Version is"
uname -a
echo "The Distribution Version is"
lsb_release -a
echo "The Partition Sizes are "
cat /proc/partitions
exit
less testscript


```

---

### Post by Lars Noodén on 2012-11-22
I've tried a few ways but it looks like you have to have script call your shell script.  Try using the -c option with script.

---

### Post by Mohan1289 on 2012-11-22
> **Lars Noodén said:**
> I've tried a few ways but it looks like you have to have script call your shell script.  Try using the -c option with script.

yes it worked... Thank you

but why doesn't it worked before?? what's wrong?

and the script itself is not exiting even if i entered exit command in shell script why so?
i will post my code and the Output it gave me..

```

#!/bin/bash
script -c testscript
echo "The Kernal Version is"
uname -a
echo "The Distribution Version is"
lsb_release -a
echo "The Partition Sizes are "
cat /proc/partitions
exit
echo " So far what the script does is"
less testscript
exit
```The OUTPUT is
```

krishna@ubuntu:~/Desktop/Samples$ sh envcheck.sh 
Script started, file is typescript
bash: testscript: command not found
Script done, file is typescript
The Kernal Version is
Linux ubuntu 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux
The Distribution Version is
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
The Partition Sizes are 
major minor  #blocks  name

   7        0   30457856 loop0
   8        0  312571224 sda
   8        1   51407968 sda1
   8        2          1 sda2
   8        5  130584321 sda5
   8        6  130576288 sda6
   8       16    3956736 sdb


```
It is not working right it's closing immediately after starting.. what should i do??
it has to display again

---

### Post by Mohan1289 on 2012-11-23
Won't anyone help me??

---

### Post by Zugzwang on 2012-11-23
> **Mohan1289 said:**
> Won't anyone help me??

You did read the output that you got, right? The message in the third line should contain the necessary hint.

---

### Post by Mohan1289 on 2012-11-24
> **Zugzwang said:**
> You did read the output that you got, right? The message in the third line should contain the necessary hint.

No i don't get it... what i understood it recieved file name as command not as a file name

i tried that as normal command like

```

script testfile

```

but if entered the command as above the shell script is not running it just runs 1st command in shell script i.e script since i want to record what i have done and then Blank until i close the session again by pressing ctrl+D then only remaining commands in the script are executing.. i can't able to find a way out of this...

is there any other way to record a session in terminal instead of script command?

---

