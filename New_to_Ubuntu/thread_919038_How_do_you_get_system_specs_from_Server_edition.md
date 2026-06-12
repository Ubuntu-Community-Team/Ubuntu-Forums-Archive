---
title: "How do you get system specs from Server edition?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by FireFreek on 2008-09-13
A while ago, maybe 3/4 of a year, some how I downloaded the server version of Ubuntu(3 times?), i guess the server did something wrong or something. Any ways, that's not the problem. I want to get the server specs on my old computer, which has the server version of Ubuntu 7.10 on it. It doesn't have any internet connection, so is there any way to get importan system information such as processor, memory, video cards, etc from the command line? I just need enough info to determine which distro would work best.

EDIT: Also, how do you get to the BIOS with Ubuntu Server. Before I installed that I was able to edit the BIOS, but now I cant.(maybe I forgot which button?)

---

### Post by ChanServ on 2008-09-13
you can but in a few differnet commands 

example:
```
uname -a
lspci -v
cat /proc/cpuinfo
cat /proc anything
top
ps aux
```

---

### Post by cdtech on 2008-09-13
This command will generate an HTML page of the installed hardware:
```
$sudo lshw -html > your-file-name.html
```

---

### Post by FireFreek on 2008-09-13
Then how would I go about reading that .html file?

---

### Post by cdtech on 2008-09-14
Copy it from the server to your desktop:
```
scp user@yourserver:~/system-info.html ~/system-info.html
```
Point your browser to it.......

---

### Post by scorp123 on 2008-09-14
> **FireFreek said:**
> Then how would I go about reading that .html file? ```
sudo apt-get install w3m
w3m /path/to/file.html 
```  ... Yes, "w3m" is a web browser. And yes, it's a text-mode program (you don't really need a GUI desktop to browse the web) ;)

---

### Post by knattlhuber on 2008-09-14
> **FireFreek said:**
> Also, how do you get to the BIOS with Ubuntu Server. Before I installed that I was able to edit the BIOS, but now I cant.(maybe I forgot which button?)

That is independent of the installed OS. I would try the following keys:
Esc, Del, F1, F2, F3, F10

---

