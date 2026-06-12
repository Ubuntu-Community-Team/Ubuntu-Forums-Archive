---
title: "ubuntu 11.10 first steps, using grep"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by antobbo on 2011-11-20
Hi ya, I have installed ubuntu 11.10 yesterday on my machine and everything seems to have gone ok
Today I was looking at the basics, so things like using grep.
I open the terminal and run:
```
grep -r broadbean
``` (that's because I read somewhere [http://www.techradar.com/news/software/operating-systems/grep-command-in-linux-explained-699455](http://www.techradar.com/news/software/operating-systems/grep-command-in-linux-explained-699455) that this will look for anything containint broadbean in my folders)  but the terminal freezes, and doesn't return anything. The prompt disappear and if I now type any command, say ls it doesn't return anything. Is that because when I run grep I have to do sth else?
thanks

---

### Post by ikt on 2011-11-20
Welcome to Ubuntu :)

Best way to see a commands options are using the man pages, just put 'man' in front of a command and it will tell you everything.

man grep

grep -r broadbean /home

From the website you linked:

> grep -r Jenkins /home/faye

Basically you were just missing the directory you wanted to search.

---

### Post by antobbo on 2011-11-20
hiya,
thanks for that. I tried your suggestion but I get a bunch of info which doesn't seem to be useful at all, see screenshot, but most importantly I loose the promp,t in that whatever I type after what you can see on the screenshot it doesn't do anything, so I have to restart the terminal

I have also tried ```
grep man
``` but same result, I loose the prompt in the terminal and I have to close it and open it again. Do I need to install sth to use grep then, not sure why it is doing that

thanks

---

### Post by oldos2er on 2011-11-20
If you need to use the prompt while grep works in the background, run ```
grep -r broadbean /home/user &
```
Or your can kill the grep process with Ctrl-c.

---

### Post by antobbo on 2011-11-20
hi there, thanks for that, I didn't know that I could use "&" with grep.
I have given it a go and yes, now I get my prompt back thanks, but I still don't quite understand the command above, it returns an awful lot of things, pretty much what you have seen in the screenshot I attached before. So say that in my Documents folder I have some other folders that contain some files and some of these files contain the string "photography". Now I want to search the files in there to see which one contains "photography". I am currently in home/usr so I run
```

grep -r photography /Documents/2011_11_18 &


```
where 2011_11_18 is a folder that contains some files which contains the string photography. But what I get from that is this:
```

[7] 15954
antobbo@antobbo-NC10-ubuntu:~$ grep: /Documents/2011_11_18: No such file or directory

```
how's that? Apologies in advance if I have made some stupid mistake

---

### Post by rockstarrem on 2011-11-20
If you are trying to find photography within the Documents directory of your home folder, You'll need to alter that command slightly:

```

grep -r photography ~/Documents/2011_11_18 &

```

See how I put the tilda in front of "/Documents"? The tilda (~) represents your home directory of the current user, the slash (/) represents the root of your filesystem. You probably don't have a directory called "Documents" under your root.

---

### Post by Miljet on 2011-11-20
If you are in your home directory, you can accomplish the same thing like this
```
grep -r photography ./Documents/2011_11_18 &
```
The period in front of /Documents tell Linux to start searching in the current directory. This is an important point to remember; Linux does not automatically search the current directory unless the current directory happens to be in your path. Otherwise you have to somehow point it to the current directory.

---

### Post by JayKay3OOO on 2011-11-20
This complication stems from the users non-understanding of the basic file structure used in Linux.

/ - this is like 'start' or the beginning or 'root'

/home - user folder

/home/JayKay3OOO - JayKay3OOO home folder

/home/JayKay3OOO/Documents - JayKay3000 documents folder

Have a play around by doing / in the terminal followed by ls to see the directories and cd to change directory.

It's pretty simple once you get the hang of it.

Use ~/Documents to go around your home folder without having to type the /home etc.

---

### Post by antobbo on 2011-11-21
ah I see, now I understand!! Yes I will play around with the file system then to get to know it a bit better. I might ask more questions about grep though in the near future.
Thanks for your help

---

