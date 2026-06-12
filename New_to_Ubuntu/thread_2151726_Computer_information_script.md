---
title: "Computer information script"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by valroadie on 2013-06-05
Hello all!
Not sure where to put this thread but I figured I would put it here.

I have searched the forums and have not found what I am looking for...though I should have looked harder I suppose.

I was looking for the script that runs when you open a terminal showing the ascii ubuntu logo and your computer information like cpu ram and all that. 

Can someone post it for me? I would appreciate it!
Thank you!

---

### Post by sudodus on 2013-06-05
There are several small programs, that show information about the computer and the operating system for example

```
 sudo lshw
```
```
 sudo dmidecode
```
```
 hardinfo
```
```
cpuid
```

and about the system

```
 uname -a
```
```
 lsb_release -a
```

```
top
```
```
free
```
```
swapon -s
```
```
cat /etc/mtab
```
```
sudo parted -l
```
```
 sudo blkid
```

---

### Post by valroadie on 2013-06-05
Thank you sudodus but I was looking for a script that is auto-run when you start the terminal showing your specs and particularly the ascii ubuntu logo. 

Here is a pic of what I am talking about. 

[IMG]http://s1.postimg.org/bvshqql9b/Selection_500.png[/IMG]

---

### Post by sudodus on 2013-06-05
That was new to me :-)

It seems the name is [FONT=courier new]**archey**[/FONT] as you can see in the top line of the screenshot. So I suggest that you browse the internet for that name.

---

### Post by valroadie on 2013-06-05
Ah found it! Thank you so much sudodus. Will mark as solved!

---

### Post by sudodus on 2013-06-05
You are welcome :-)

---

### Post by Cheesemill on 2013-06-06
There's another script that does the same thing called screenfetch.
[https://github.com/KittyKatt/screenFetch](https://github.com/KittyKatt/screenFetch)

---

### Post by Petro Dawg on 2013-06-06
> **Cheesemill said:**
> There's another script that does the same thing called screenfetch.
[https://github.com/KittyKatt/screenFetch](https://github.com/KittyKatt/screenFetch)

These are interesting scripts. "screenFetch" seems to work pretty well, just needs a few tweaks to colors to get it looking really good.

[ATTACH=CONFIG]243591[/ATTACH]

It can auto-start by adding a path to the executable at the end of the .bashrc file found in the home folder.

---

