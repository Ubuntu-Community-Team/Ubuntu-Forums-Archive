---
title: "Can't update my Ubuntu MATE"
date: 2024-11-02
forum: New to Ubuntu
---

### Post by giannicarbone on 2024-11-02
Hello. I'm a begginer Ubuntu MATE user and I can't seem to update my Ubuntu system. Can anyone help me out? 

Thanks. :)

---

### Post by grahammechanical on 2024-11-02
No. Not until you tell us about your computer and the problem you are having. Talk to us. All I can think of at this stage is: Open Software Updater or whatever utility the Mate desktop has. Or, run in a terminal

```
sudo apt update
```

and post the printout within quote tags and do the same with

```
sudo apt upgrade
```

Regards

---

### Post by yancek on 2024-11-02
You neglected to post a significant bit of information, namely which release version of Ubuntu you are using.  The command below will give that information so post it here.  It is much more difficult to upgrade older non-LTS releases which is why this information is useful.

```
 cat /etc/os-release
  
```

---

### Post by Norm24 on 2024-11-02
System>Administration>Software Updater

or what @grahammechanical suggested.

A little more info as already suggested would be helpful if you're having some type of issue and updating isn't working.

---

### Post by ActionParsnip on 2024-11-04
The apt output will help greatly. The CLI way is more verbose than the GUI apps and gives good information if there are issues

---

