---
title: "Code::Blocks for ubuntu 10.04?"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by protoss96 on 2013-09-11
Hi,

I am currently using Ubuntu 12.04 everything is ok for me but, my teachers in school agreed to install Ubuntu 10.04 on some pretty old hardware on about 15 PCs, and guess what? They are running HD videos on 256 MB RAM! :D Because I am in Engineering school for computers of course students need some good IDE and compiler. Because Ubuntu Software Center on Ubuntu 10.04 doesn't have Code::Blocks i want to ask you guys how can i install some older version of Code::Blocks(is possible) on Ubuntu 10.04 LTS? Thank you very much in advance, your will be helping alots of students in my school. :D ):P

---

### Post by leg on 2013-09-11
Isn't it available through synaptic on those machines?

---

### Post by grahammechanical on 2013-09-11
The Ubuntu 10.04 repositories have been moved. You can point the software sources to the new location and that might allow those 10.04 installations to install software. This link shows you how. You may need to enable the Universe repositories to get that application.

[URL="http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support"]http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support

[/URL]Regards.

---

### Post by protoss96 on 2013-09-11
thank you guys, i will try to re enable repositories

---

### Post by varunendra on 2013-09-12
In short, you will need to change "archive.ubuntu.com" to "old-releases.ubuntu.com" (each entry) in the **/etc/apt/sources.list** file. You can change the file in one system, then copy it in all others overwriting the existing ones.

A single command to change all entries at once -
```
sudo sed -i 's/archive.ubuntu/old-releases.ubuntu/' /etc/apt/sources.list
```
(try without sudo and "-i" to see the result on terminal without actually doing the change)

As a side note, you may try to convince them that it is much better to use Lubuntu 12.04 than an outdated version of Ubuntu. The newer Lubuntu would be less demanding than the default 'Ubuntu' 10.04.

---

