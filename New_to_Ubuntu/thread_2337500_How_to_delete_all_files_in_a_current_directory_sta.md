---
title: "How to delete all files in a current directory starting with a dot?"
date: 2016-09-19
forum: New to Ubuntu
---

### Post by Grigoriy on 2016-09-19
Hello!
                          
                          I use Ubuntu 14.04 and in a terminal I became  root with sudo su and I wanted to delete root's trash manually. It  deleted everything except for a few files that start with a dot. Like  .htaccess etc. So I went to that directory (which is "files") and I ran  this command:

```
rm -rf .*

```

It did delete those files, BUT I also got an error message that the  system couldn't delete "." and ".." What does it mean? Like if I tried  to delete the whole directory tree? Like I said, when I was running that  command I was in the lowest directory. This one to be exact:  /root/.local/share/Trash/files/ 
                          I shot down my PC and then turned it on.  Everything seems to be normal at first glance. So now I want to ask is  what went wrong and if what I did could really cause any serious damage  to the system in general? In other words, should I be worried now or  everything is OK?

---

### Post by CantankRus on 2016-09-19
In any directory if you run ...
```
ls -al
```
you will see something like...
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] ls -al**
total 908
drwxr-xr-x  78 glen glen   4096 Sep 19 11:26 .
drwxr-xr-x   3 root root   4096 Aug 24 16:32 ..

```

For an explanation see [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://stackoverflow.com/questions/23242004/what-is-double-dot-and-single-dot-in-linux")

---

### Post by howefield on 2016-09-19
> **Grigoriy said:**
> ```
rm -rf .*
```

```
rm -rf ./.*
```

would stop you trying to delete the parent folders.

---

### Post by SeijiSensei on 2016-09-19
"rm -f *" will not delete dot files.  You need to use
```
rm -f \.?*
```
That matches any file that begins with a dot followed by one or more additional characters. The backslash "escapes" the dot and tells the shell to treat it as a regular character and not one having special meaning.

If you use "rm -rf *" and then "ls -la" you'll see the dot files are still there.

---

### Post by Grigoriy on 2016-09-19
Thanks a lot for your replies!

---

### Post by bab1 on 2016-09-19
> **Grigoriy said:**
> 

... [I] couldn't delete "." and ".." What does it mean? Like if I tried  to delete the whole directory tree? Like I said, when I was running that  command I was in the lowest directory. This one to be exact:  /root/.local/share/Trash/files/ 

The single dot (.) by itself is the current working directory.  The double dot (..) is the directory just above the current working directory.

Try this at your home directory to to see what I mean. ```
cd ..
```

---

### Post by #&amp;thj^% on 2016-09-19
> **bab1 said:**
> The single dot (.) by itself is the current working directory.  The double dot (..) is the directory just above the current working directory.

Try this at your home directory to to see what I mean. ```
cd ..
```

Thanks... learn something new almost daily:o
```
cd ..
```
```
ls ..
bin   dev  home  lib64       mnt  proc  run   srv  tmp  var
boot  etc  lib   lost+found  opt  root  sbin  sys  usr

```
Thanks bab1:)

---

### Post by Habitual on 2016-09-19
> **Grigoriy said:**
> root's trash
?
Are you logging in graphically as root?

Never heard of it.

---

### Post by yetimon_64 on 2016-09-19
> **Habitual said:**
> ?
Are you logging in graphically as root?

Never heard of it.

Files can end up there ( /root/.local/share/Trash/files/) if the file browser is run as root and files are deleted with the context menu "Move to the rubbish bin" option. 

A full graphical log in is not necessary for that to happen. I used to do the file manager method of managing root files (gksudo nautilus) before I became more comfortable with the terminal and as such found some of my root files ending in that trash location for root.

---

### Post by Grigoriy on 2016-09-20
Actually, the main reason why I made that mistake, was that I wasn't aware that "." and ".." are just FILES too! 

It's much more convenient for me to use gksudo nautilus, than a terminal. That's why what I delete ends up in root's trash. And the reason why I need elevated privileges, 'cos I often delete files in /var/www/html and in Truecrypt containers.

---

### Post by SeijiSensei on 2016-09-20
> **Grigoriy said:**
> Actually, the main reason why I made that mistake, was that I wasn't aware that "." and ".." are just FILES too!
In Unix, "[everything is a file]("https://en.wikipedia.org/wiki/Everything_is_a_file")."

---

