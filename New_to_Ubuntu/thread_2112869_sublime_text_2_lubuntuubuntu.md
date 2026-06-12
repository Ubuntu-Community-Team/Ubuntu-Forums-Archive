---
title: "sublime text 2 lubuntu/ubuntu"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by seal308 on 2013-02-05
Hello I'm trying to install sublime text 2 for lubuntu.
My class requires me to program in java.
I was able to install java. 
Therefore I am able to compile and run in terminal and programs such as geany.
I have install sublime text 2.
In terms of installation I loosely followed this: [http://www.technoreply.com/how-to-install-sublime-text-2-on-ubuntu-12-04-unity/](http://www.technoreply.com/how-to-install-sublime-text-2-on-ubuntu-12-04-unity/)

If I type in sublime into terminal I am able to open sublime.
Now the problem is being able to compile and run my programs. 
I found this webpage that divides the process into steps:
[http://www.compilr.org/compile-and-run-java-programs/](http://www.compilr.org/compile-and-run-java-programs/)

For step1:
Steps to set PATH variable in Ubuntu
I can open into the environment file
Right now in this file it has:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
Instructions say:
"Paste jdk bin directory path in last before ” and save file;"
Is the path: usr/bin/java 
So do I just put this below the line that already exists?
Path:"/usr/bin/java"

Please help,
Thanks

---

### Post by omeomi on 2013-02-06
Java is usually located in /usr/lib/jvm/openjdk-*/bin so you should check what this directory is (depends on java version and system arch) and then you add this path to the PATH variable by adding these lines to /etc/profile
```
PATH=${PATH}:/usr/lib/jvm/openjdk-*/bin/;
export PATH
```
where you need to replace **openjdk-*** with the correct folder in your case.

---

