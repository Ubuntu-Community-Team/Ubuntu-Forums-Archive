---
title: "oprofile not starting on ubuntu 7.10"
date: 2008-01-22
forum: Programming Talk
---

### Post by biberli on 2008-01-22
Does anyone know how to fix this problem when i start oprofile with 
this command ? ->

./opcontrol --init

Here is the output ->

cat: /proc/sys/dev/oprofile/cpu_type: No such file or directory
ls: /proc/sys/dev/oprofile/: No such file or directory
Unable to open cpu_type file for reading
Make sure you have done opcontrol --init
cpu_type 'unset' is not valid
you should upgrade oprofile or force the use of timer mode
Normal users are limited to either '--dump' or '--list-events'.

Thank you !

---

### Post by stroyan on 2008-01-22
You need to run opcontrol as root to be able to do init.
If I run it as a normal user I get exactly those error messages.
Use ```
sudo opcontrol --init
``` to start it.

---

