---
title: "Symbolic vs Absolute"
date: 2024-09-04
forum: New to Ubuntu
---

### Post by jmkmx on 2024-09-04
Hello forum,

I am currently learning how to use the chmod command, now my question would be, when using the Symbolic Mode is there a way to set permissions separately like you do with the Absolute mode?

e.g.
```
sudo chmod 777 filename
```
With this I am granting rights individually to all; user, group and others but I don't know how to do the same with the Symbolic mode, lets just say I want to give rwx rights to the group but at the same time I want to revoke all rights for others.

I know I can do the following but I'm not sure if I would need to run the command a second time to achieve what I am trying to do.
```
chmod go +wrx filename 
```

---

### Post by Dennis N on 2024-09-04
You can do it all in one command```
:
chmod g+rwx,o-rwx filename
```
You can also use = to set permissions:
```
chmod g=rw,o=r filename
```
with = any permission not specified is removed if present. So g loses x, and o loses w and x

---

### Post by jmkmx on 2024-09-05
Awesome, I appreciate the extra tip right at the bottom... Thank you very much my friend!

---

### Post by ActionParsnip on 2024-09-05
Please mark as solved if the issue is sorted, or add more detail and we can assist more

---

### Post by jmkmx on 2024-09-05
Sorry, I had no idea this was a thing, it is done now, I have another post, let me go mark it as resolved as well...

---

### Post by jmkmx on 2024-09-06
I have one more question regarding the same subject...

When removing the SUID or GUID in symbolic mode I would do the following:
```
sudo chmod ug-s filename
```

But when I try to do the same while using the absolute mode, only the SUID gets removed for some reason while GUID stays in place.

e.g.
```
sudo chmod 0755 filename
```

What would be the proper command to remove the GPUI or both of them at the same time in the absolute mode?

---

### Post by Dennis N on 2024-09-06
> What would be the proper command to remove the GPUI or both of them at the same time in the absolute mode? 

Here's an example, setting and unsetting:

```
Original file:

[dmn@Tyana testing]$ ls -l
total 0
-rw-r--r-- 1 dmn dmn 0 Sep  6 13:45 myfile.txt

Set SUID and GUID:
[dmn@Tyana testing]$ chmod 6644 myfile.txt
[dmn@Tyana testing]$ ls -l
total 0
-rwSr-Sr-- 1 dmn dmn 0 Sep  6 13:45 myfile.txt

reverse it:
[dmn@Tyana testing]$ chmod 644 myfile.txt
[dmn@Tyana testing]$ ls -l
total 0
-rw-r--r-- 1 dmn dmn 0 Sep  6 13:45 myfile.txt

as it originally was.
```

---

### Post by jmkmx on 2024-09-10
Ah I see, you don't really need to specify, just set the original values, interesting, once again thank you very much!

---

### Post by Dennis N on 2024-09-10
> **jmkmx said:**
> Ah I see, you don't really need to specify, just set the original values, interesting, once again thank you very much!
You got it. This is an advantage of the 'absolute' (numerical) notation. No adding or subtracting involved.

---

