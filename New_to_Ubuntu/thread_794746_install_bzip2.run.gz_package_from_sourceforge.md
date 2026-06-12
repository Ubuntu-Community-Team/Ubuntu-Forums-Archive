---
title: "install bzip2.run.gz package from sourceforge?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by shelbyvision on 2008-05-14
I installed wings3d with synaptic and it won't work. Doing a little research, I found that this is normal, and I read that a someone had good results with a newer version not available through the repositories, but could be downloaded from sourceforge. The package is wings-0.99.01-linux.bzip2.run.gz. When I extracted it, it contained wings-0.99.01-linux.bzip2.run, which my file browser says is a 3.3 MB shell script. I have no idea what to do to install this. I looked in various places for instructions, but couldn't find any that a newbie such as I could understand. Can anyone help me with this?
Thank you,
Steve

---

### Post by tamoneya on 2008-05-14
go into the extracted directory and type```
./wings-0.99.01-linux.bzip2.run
```

If it complains about permissions you should use sudo to install it
```
sudo ./wings-0.99.01-linux.bzip2.run
```

---

### Post by ZabiGG on 2008-05-14
If you want to learn more about installing stuff, here's a great link:

[http://www.monkeyblog.org/ubuntu/ins...a_repositories](http://www.monkeyblog.org/ubuntu/ins...a_repositories)
How to install anything in Ubuntu

Cheers!

---

### Post by shelbyvision on 2008-05-15
tamoneya,
I tried your suggestion last night, and again this morning, with the same result, I get this message: "sudo: ./wings-0.99.01-linux.bzip2.run: command not found".
ZabiGG,
Your link turns up an error page, but I have been to that website and read the instructions, and they just don't give enough details for someone like me with no experience at writing command lines. (I've always used Windows in the past, entirely GUI)
Steve

---

### Post by Cypher on 2008-05-15
Try the following
```

file wings-0.99-01-linux.bzip2.run

```
This should return someting like "BASH Executable"

Then do
```

chmod 755 wings-0.99-01-linux.bzip2.run
./wings-0.99-01-linux.bzip2.run

```
If the execution complains about permissions, add "sudo" before running the program..

---

### Post by shelbyvision on 2008-05-15
[QUOTE=Cypher;4963985]Try the following
```

file wings-0.99-01-linux.bzip2.run

```

OK, I tried that, and this is what it returned:

wings-0.99-01-linux.bzip2.run: ERROR: cannot open `wings-0.99-01-linux.bzip2.run' (No such file or directory)

The directory that it's in is /tmp. does that make any difference?

Steve

---

### Post by Cypher on 2008-05-15
You would run the command in the location of the file..so if it's in /tmp, then do
```

cd /tmp
file wings-0.99-01-linux.bzip2.run

```
or from any location
```

file /tmp/wings-0.99-01-linux.bzip2.run

```

---

### Post by shelbyvision on 2008-05-15
[QUOTE=Cypher;4965615]You would run the command in the location of the file..so if it's in /tmp, then do
```

cd /tmp
file wings-0.99-01-linux.bzip2.run

```

That's what I did.
Steve

---

### Post by Vel0x on 2008-05-15
I had exactly the same issue with a .run file and this worked for me.

Many thanks.

---

### Post by shelbyvision on 2008-05-16
It seem very strange to me that terminal doesn't recognize the existence of that file, even though it's right there in the /tmp directory. I did some research on .run files and found this: [https://help.ubuntu.com/7.10/add-applications/C/install-file.html](https://help.ubuntu.com/7.10/add-applications/C/install-file.html)
which has a GUI approach. I went through the process described there and it worked. Well, at least it runs the file, which is supposed to install the newer version of wings, but when it's finished, nothing has happened. So, now I'm wondering if maybe the .run file is defective, and somehow terminal detected that an that's why it won't recognize its existence. ?????
Steve

---

