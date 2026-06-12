---
title: "How could  &quot;cd /linux/src&quot;"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by shewenhao on 2008-05-15
I am using a IBM T43 and I try to install the disk protection by following this link "http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43" no need to read them all:) I just have a little problem that in the middle of this installation process, this instruction tries to let me doing this:

$ sudo su
# cd /linux/src
# apt-get install linux-source
# cd linux-source-2.6.20
# patch -p1 -l < /home/silvan/993-001.bin

but when i type the cd /linux/src

there is notification : no such file or folder

before this step, I did everything under the home/myusername but suddently, this require to use CD order to enter the /linux/src folder. 

Who can tell me what is wrong ?


Thank you so much!!!!

---

### Post by shewenhao on 2008-05-15
I just noticed a line right above the commands lines, I pasted here in the yellow color. Hope this help you to know what is wrong.


[COLOR="Yellow"]Get the kernel sources and patch them:[/COLOR]

$ sudo su
# cd /linux/src
# apt-get install linux-source
# cd linux-source-2.6.20
# patch -p1 -l < /home/silvan/993-001.bin 

Thanks again!!!!

---

### Post by gerben1 on 2008-05-15
You need to install the kernel source code first, what you are going to do if you follow along the guid is, patching the kernel source code and then rebuilding the kernel from that patched source code. This is a pretty serious thing so make sure to follow the instruction closely. 

So just install the kernel-source package (part of that package will be the directory /linux/src) and then just go on following the guide.

---

