---
title: "Adding new sysfs which does not belong to any model.."
date: 2011-09-19
forum: Programming Talk
---

### Post by difuiv250385 on 2011-09-19
Hi
(sorry in the subject field its **kernel module **not** model**)
I am planning to **filter the printk logging messages** based on the **message's priority.**
For this I want to provide an **interface through shell** where the **threshold value of the message priority** can be **configured dynamically**.

So I want to **add an entry in the sysfs,** say **/sys/printk_logging_filter**, through which I can 
**edit the message priority** threshold value. As there is no particular kernel module involved with the printk (or else I would have done in the module initialization part), I am confused **where to create the sysfs file node and its attributes.**

Please let me know **which part of the kernel is the suitable place to create this file node,** and to declare the sysfs attributes.


Thanks in advance,
cbn

---

### Post by difuiv250385 on 2011-09-20
I added a file, **printk_logging_filter**  into the /proc fs at the place **/proc/sys/kernel/**  by adding an entry in the **kern_table[]** array in file **kernel/kernel/sysctl.c **this is working fine.
 
But according to the following link [http://www.mjmwired.net/kernel/Documentation/sysctl/ctl_unnumbered.txt](http://www.mjmwired.net/kernel/Documentation/sysctl/ctl_unnumbered.txt)
 
it is not recommended to add an entry into the array **kern_table[]** (Infact I dont understand what exactly the author means in the attached link).
 
But at many places in net, I found adding entry into **kern_table[]** is absolutely fine.
 
Please let me know **if any issues related to adding or editing** the entry in **kern_table[].** 
 
Also as per the original thread let me know where in kernel code to add the code to create the **sysfs file which does not belong to any kernel module**(**I know only to create the sysfs files and its interfaces during the module initilization function** :() .

---

### Post by difuiv250385 on 2011-09-21
Hi I got the idea about this issue..
and its working fine as well...:guitar:
The solution is simple, implemented the init function in kernel/kernel/sysctl.c as below
 
core_initcall(<Myinit function>)
 
int __init <Myinit function>(void)
{
<create and add the kernel object>
<create the sysfs group>
}
 
 
hope everyone knows about adding the attributes to the kobject and providing the interface to it through sysfs..;)

---

