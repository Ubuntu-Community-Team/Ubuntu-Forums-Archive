---
title: "Really strange proble with gksudo"
date: 2010-06-22
forum: Programming Talk
---

### Post by hakermania on 2010-06-22
User alex is currently logged in.
```
gksudo echo Hello > /home/alex/welcome.txt
``` >>> This asks for passwd and then works perfectly
```
gksudo echo Hello-pc > /etc/hostname
``` >>> This asks for passwd and then sais /etc/hostname permission denied.
What's wrong with it?

---

### Post by sisco311 on 2010-06-22
[uhelp]community/RootSudo[/uhelp]

*Redirecting the output of commands run with sudo requires a different approach. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. *

```
echo **whatever** | sudo tee /path/to/file
```

---

### Post by potat on 2010-06-22
welcome.txt is in your home folder and you have write permissions to it. /etc/hostname is owned by root and you don't have write permissions. The reason is that the sudo works for echo but not for the file redirect ">". Try using
```

sudo su
echo Hello-pc > /etc/hostname
exit

```

EDIT: sisco311's method makes more sense. The reason is that the shell plans out the file redirect before running sudo to gain root permissions. tee does the same thing (it also spits the text out to the terminal) but will run after sudo with proper permissions.

---

### Post by hakermania on 2010-06-22
Thank you all of your replies. [sisco311]("http://ubuntuforums.org/member.php?u=244665") is completely right. His method works perfectly with sudo, but, because I am developing a program in C++ and I want system() to call gksudo (and not sudo), is there any way this to work for gksudo as well? Becauz it doesn't work.. The file after gksudo is empty...

---

### Post by hakermania on 2010-07-15
:( ?

---

### Post by geirha on 2010-07-15
If your program needs to be able to write to files as root, run the program as root.

---

### Post by sisco311 on 2010-07-15
```
gksu "bash -c 'echo line > path/to/file'"
```
or use pkexec:
```
echo line | pkexec tee path/to/file
```

---

### Post by hakermania on 2010-07-15
> **geirha said:**
> If your program needs to be able to write to files as root, run the program as root.
The program in a moment needs to open up nautilus, something that is not permitted when run as root..:)
sisco311 thx for your replies...
Cheers!

---

