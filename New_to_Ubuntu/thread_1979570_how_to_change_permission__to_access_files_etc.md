---
title: "how to change permission  to access files etc"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by auspot on 2012-05-13
I am new to ubuntu or linux think I have installed ubuntu 10.04 or its 11.04 not sure.
question is:  how to change permission so I can access all the files in terminal.  I have 
to copy and paste because I don't know the commands.  :confused:
thanks for any help
auspot

---

### Post by sidewinder46 on 2012-05-13
Changing file permessions can comprimise your system, if you dont know what you are doing. To acess files that are system the sudo command can acess them.

To actually change file permissions [chmod]("http://ss64.com/bash/chmod.html") does this.

---

### Post by NikTh on 2012-05-13
Hi , 
and here is a good tutorial about chmod -- > [http://catcode.com/teachmod/](http://catcode.com/teachmod/) 
Read it when you have time.

---

### Post by auspot on 2012-05-14
Thank you for the reply will check it out asap  ):P

Thank you
aus;pot

---

### Post by HiImTye on 2012-05-14
if you are not changing system files (which can cause horrible, horrible problems including not being able to boot) then you use chown to change ownership and chmod to alter the permissions. chown the follows simple format of:
```
chown user:group /path/to/file
```
while chmod can be used with either a mask or actually modifying the flags (including special flags, but you likely don't need to know about those). I would recommend researching chmod if you plan on using it

---

### Post by zandman on 2012-05-14
If you just want to display the contents of a file (especially text files, system logs etc) then open a terminal and type "sudo less /dir/subdir/.../filename+extension" to show that.
The comment in message #2 is something you should really take seriously.
If you have to edit a file that requires root-rights to edit it you open a terminal and type "sudo gedit /dir/subdir/.../filename+extension" to do that.
There are other ways (gksudo etc) to do it, this is how i do that and it works.

---

