---
title: "accessing files with spaces in the name"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-03-18
output
ray@ray-GC660AA-ABA-SR5123WM:~$ cd /home/ray/Documents/house
ray@ray-GC660AA-ABA-SR5123WM:~/Documents/house$ ls -l
total 32
-rw-rw-r-- 1 ray ray 17893 Feb 20 11:20 for house.odt
-rw-rw-r-- 1 ray ray 11407 Jan  6 07:14 house equilty.odt
 okay then i run this to open the the first with libreoffice
ray@ray-GC660AA-ABA-SR5123WM:~/Documents/house$ libreoffice "for house.odt" this works fine. file is displayed with libre .
note that both .odt files have a space in their name. what wild card would i use not to have to type out the whole path
eg. if i replace "for house.odt" with "for*.odt" i get the error message that file doesnt exist. doing something stupid

tks

---

### Post by sudodus on 2013-03-18
You can use 'TAB completion' and type TAB (the tabulator key often above Caps Lock)
 ```
libreoffice for***TAB***
```
and bash will fill it to
```
 libreoffice for\ house.odt
```

So another way to manage spaces or other special characters in bash is the backslash character '\' in front of each special character, and this is done automatically by 'tab completion'

---

### Post by rburkartjo on 2013-03-19
sud tks but i first had to find out how to install tab complete in xubuntu as it is not installed by default. found this

August 1st, 2011 #13 edwinorc  
First Cup of Ubuntu

Join Date
Aug 2011
Beans
5
 Re: Installed xfce, now no Tab-complete in Terminal apps?
I accidentally discovered a fix for this while trying to solve a different problem.

edit
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml

find the line 

<property name="&lt;Super&gt;Tab" type="string" value="switch_window_key"/>

and change it to 

<property name="&lt;Super&gt;Tab" type="empty"/>

reboot or whatever and then tab will work properly!



again after i did the above it works like a charm

---

### Post by sudodus on 2013-03-19
I'm glad you fixed it :-)  but no tab-completion in Xubuntu? Which version are you running?

*Edit*: I just tried in Xubuntu 12.04.2 LTS, and it works in the default terminal window, 'Xfce Terminal Emulator'. But it does not work in the **alt + F2** 'Run Program' window. Was that what you meant?

---

### Post by rburkartjo on 2013-03-19
yup

---

