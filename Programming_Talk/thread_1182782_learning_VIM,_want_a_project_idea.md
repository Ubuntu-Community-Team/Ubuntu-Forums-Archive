---
title: "learning VIM, want a project idea"
date: 2009-06-09
forum: Programming Talk
---

### Post by Mateo on 2009-06-09
Hi, i'm interested in learning VIM and so I would like a project idea.  I'll be using either php or perl (haven't decideded yet) so it should be a console app that does... something.  Maybe automates a common task?  I don't know.  Something useful.  I love to program, but I have trouble keeping myself interested unless I'm working on a project.  Thanks for any suggestions!

---

### Post by matmatmat on 2009-06-09
some [here]("http://ubuntuforums.org/showthread.php?t=1167681") don't know if you could do them in perl, if not how about a todo list that can add entries, delete them, sort them in to priorities and so on. Or a url manager that can saves the url at the end of the program, can load the url into firefox and can create a table of urls

---

### Post by Eeqmcsq on 2009-06-09
> but I have trouble keeping myself interested unless I'm working on a project
Heh, I know that feeling. Anyway, here's one of my recent bash scripts that I wrote for myself to practice bash scripting. Perhaps you can adapt it for your project:

Write a script that prints out various hardware info, such as your CPU name, CPU speed, CPU L1/L2/L3 cache sizes, CPU virtualization support, total installed RAM, installed RAM per slot, max supported RAM by the memory controller, hard drive size, partitions, connected USB devices, etc.

The commands I used for the info are dmidecode, lshw, df, fdisk, and the file /proc/cpuinfo. You'll have to parse the output of these commands to get the values you need.

Also, don't worry if your script doesn't work on every computer. Not every computer supplies all of the information, and some computers report the information incorrectly. For example, my script reported that my old Celeron 366 did NOT have L1 cache installed, but correctly reported the L2 cache. Also, 2 of my computers did not report RAM slot information.

---

### Post by yaroto98 on 2009-06-09
You could make a little web portal. (I know apache can do it automatically for you but it'd still be fun) Have an authenticated session, and then make an auto generated list from the directory you're in, be able to move anywhere on the computer, open and play files (like mp3s), and if you're getting bored, upload files too. So long as you're carefull with your security you'll have almost complete remote access to your computer through a web interface.

---

### Post by yaroto98 on 2009-06-09
A "Hello World, my name is FooBar" script.

---

