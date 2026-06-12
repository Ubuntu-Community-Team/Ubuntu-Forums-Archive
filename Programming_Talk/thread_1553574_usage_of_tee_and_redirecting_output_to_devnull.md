---
title: "usage of tee and redirecting output to /dev/null"
date: 2010-08-15
forum: Programming Talk
---

### Post by tapas_mishra on 2010-08-15
I am not clear with the usage of tee 
```

echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
```
In above 
```

 sudo tee -a /etc/apt/sources.list

```
is ok this I understand.
But I do not understand the use of 
```

 sudo tee -a /etc/apt/sources.list > /dev/null

```

why is the output redirected to /dev/null .
The above usage is on this [page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

---

### Post by geirha on 2010-08-15
tee reads from standard input and writes to standard output and one or more files. The -a option tells tee to append to the file(s) instead of truncating.

So ```
echo test | tee -a file
``` will append the line "test" to file, and also write it to stdout. It's roughly equivalent to 
```
echo test >> file
echo test

```

The reason tee is used to write to sources.list is because the file needs to be opened as the root user in order to write to it.

The following may seem like it would do the same thing
```
sudo echo line >> /etc/apt/sources.list
```
but the problem is, the file is not opened by sudo. The file is opened before sudo is even run, by the shell, which is running as your own user.

---

### Post by MadCow108 on 2010-08-15
> **tapas_mishra said:**
> 
```

 sudo tee -a /etc/apt/sources.list > /dev/null

```
why is the output redirected to /dev/null .


tee writes to stdout AND a file
in that case one probably only wants to write to the file and does not care about the stdout
so one just dumps it with > to /dev/null to ignore it
the file is nevertheless appended

---

### Post by tapas_mishra on 2010-08-15
> **geirha said:**
> 

The reason tee is used to write to sources.list is because the file needs to be opened as the root user in order to write to it.

How does tee helped here ?
> **geirha said:**
> The following may seem like it would do the same thing
```
sudo echo line >> /etc/apt/sources.list
```but the problem is, the file is not opened by sudo. The file is opened before sudo is even run, by the shell, which is running as your own user.
Here are you referring to line or /etc/apt/sources.list 
in the above command 
```
sudo echo line >> /etc/apt/sources.list
```
echo is running as super user or not ?
and when you used >> this will not open 
```
/etc/apt/sources.list
```
as root.

> **MadCow108 said:**
> tee writes to stdout AND a file
in that case one probably only wants to write to the file and does not care about the stdout
so one just dumps it with > to /dev/null to ignore it
the file is nevertheless appended
Thanks this is what I was looking for.

But the above replies from geirha gave some more insight.

---

### Post by geirha on 2010-08-15
> **tapas_mishra said:**
> How does tee helped here ?

Because with "sudo tee -a file", the file is opened by tee and not the by the shell, and since tee is running as root because of sudo, tee has write permission to it.

> **tapas_mishra said:**
> 
Here are you referring to line or /etc/apt/sources.list 
in the above command 

"/etc/apt/sources.list" is the file you want to append to. "line" just represents the string you want appended to that file.

> **tapas_mishra said:**
> 
```
sudo echo line >> /etc/apt/sources.list
```
echo is running as super user or not ?
and when you used >> this will not open 
```
/etc/apt/sources.list
```
as root.


Yes, echo is run as root, but the file is (attempted) opened for appending by the shell, running as your user.

You can wrap the whole command in a shell, and run that shell as root like so:
```
sudo bash -c 'echo line >> file'
```
In that case, file will be opened by root since the shell that opens it is running as root.

---

### Post by MadCow108 on 2010-08-15
> **tapas_mishra said:**
> How does tee helped here ?
when tee is started as superuser it will open the file as superuser and can write to it.
[/quote]

> 
Here are you referring to line or /etc/apt/sources.list 
in the above command 
```
sudo echo line >> /etc/apt/sources.list
```
echo is running as super user or not ?
and when you used >> this will not open 
```
/etc/apt/sources.list
```
as root.

no, that's why you need tee.

the operator >> does not belong to the process echo, but it is part of the shell which is a different process with possibly different permissions.
>> tells the shell to take the stdout of previous command and append it to a file.
So the shell opens the file!
When the shell does not have permissions to change that file it will fail.

---

### Post by tapas_mishra on 2010-08-15
Great.Both the answers were perfect.
Specially this one
```
sudo bash -c 'echo line >> file'
```
Got it.

Thanks.

---

