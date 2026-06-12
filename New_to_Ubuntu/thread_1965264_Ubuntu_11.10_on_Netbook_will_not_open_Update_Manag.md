---
title: "Ubuntu 11.10 on Netbook will not open Update Manager"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by Marcus Zion on 2012-04-25
My computer is a HP Mini 210 1010 that I had installed Ubuntu 11.10 on after the Windows Starter 7 that came with the computer went bye bye with a master boot record error. Since I've installed Ubuntu I cannot get the update manager to open up. Solutions?

---

### Post by eriktheblu on 2012-04-25
Try in the terminal
```
sudo apt-get update
```

---

### Post by Curtis6767 on 2012-04-25
When you try to open Update Manager, do you get an error message?

---

### Post by Marcus Zion on 2012-04-25
> **Curtis6767 said:**
> When you try to open Update Manager, do you get an error message?
No it just displays the arrows around it that it's open but it won't actually open. The actual Update Manager icon doesn't show up on the menu bar but when it does it doesn't open. No error message.

---

### Post by Marcus Zion on 2012-04-25
> **eriktheblu said:**
> Try in the terminal
```
sudo apt-get update
```
It worked but any further support on getting the update manager to work without having to terminal code it every time?

---

### Post by jerome1232 on 2012-04-25
Try starting it from command line to see if there are any useful errors.

```
update-manager
```

---

### Post by eriktheblu on 2012-04-25
A lot of the errors with apt based programs can be corrected wih apt-get update. I was hoping this might correct whatever it was that prevented it from opening normally. Occassionaly it will give you error messages and further instructions on how to correct them.

---

### Post by NikTh on 2012-04-25
> **Marcus Zion said:**
> It worked but any further support on getting the update manager to work without having to terminal code it every time?

Try to reinstall it . 
```
sudo apt-get install --reinstall update-manager update-manager-core
```

[SIZE=1]If you allow me a suggestion --> [Ubuntu 12.04 LTS](http://www.ubuntu.com/) . I am almost sure that will fit  much better in your netbook . [/SIZE]

---

