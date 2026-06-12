---
title: "how to add system call to the kernal"
date: 2010-03-10
forum: Programming Talk
---

### Post by rejuvenate on 2010-03-10
i want to add a system call to the kernel?? plz tell me how to do it and any link which can tell about the what happening on the background of the procedure so i can understand the structure of linux kernel..i am new to ubuntu .....

---

### Post by Zugzwang on 2010-03-10
For understanding the structure of something big like the Linux kernel, you might want to check out some books. See [this thread]("http://ubuntuforums.org/showthread.php?t=1426522") for details.

---

### Post by radeon21 on 2010-03-10
Do you want to *make* a system call or *add* a system call to the kernel?

---

### Post by rejuvenate on 2010-03-12
want to add system call

---

### Post by soro on 2010-03-12
Also you can see this  [http://www.csee.umbc.edu/courses/undergraduate/CMSC421/fall02/burt/projects/howto_add_systemcall.html](http://www.csee.umbc.edu/courses/undergraduate/CMSC421/fall02/burt/projects/howto_add_systemcall.html)
and after that this one :[http://macboypro.wordpress.com/2009/05/15/adding-a-custom-system-call-to-the-linux-os/](http://macboypro.wordpress.com/2009/05/15/adding-a-custom-system-call-to-the-linux-os/)
good luck

---

### Post by nvteighen on 2010-03-12
Could you please tell us why do you intend to add a system call? What's that system call going to do? Because chances are that what you might want to implement a library or maybe a kernel module instead of creating a new system call...

---

### Post by rejuvenate on 2010-03-13
the task given to us is to add system call i got the material which tells the steps and changes required to implement that but there is no information on things going behind the operation which can help me in learning.....

---

