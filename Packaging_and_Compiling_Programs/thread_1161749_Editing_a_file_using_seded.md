---
title: "Editing a file using sed/ed"
date: 2009-05-17
forum: Packaging and Compiling Programs
---

### Post by fantasyland on 2009-05-17
Hi,

I am new to shell scripting and I need to edit a few files in a script as part of an automation process. I found out that its possible using sed/ed but the examples are a bit confusing to me and I dont want to risk testing it as it might break the system.
Suppose I want to add the following to the file "  [FONT=&quot]/etc/network/interfaces[/FONT]" :

 auto eth1  
iface eth1 inet static
  
How would I do it in a script using sed/ed assuming that the file was empty initially. File can be created using "touch" or using sed/ed.

Thanks

---

### Post by squaregoldfish on 2009-05-17
If the file is empty (and you're sure about it!), you can simply use echo to put your text in the file:

```
echo "auto eth1  
iface eth1 inet static" > filename
```

If the file isn't empty, and you want to add the text to the end, you can use:

```
echo "auto eth1  
 iface eth1 inet static" >> filename
```


Steve.

---

### Post by fantasyland on 2009-05-17
Thanks a lot Steve. This seems to work for me.

---

