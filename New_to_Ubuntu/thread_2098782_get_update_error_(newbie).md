---
title: "get update error (newbie)"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by codyyy67 on 2012-12-27
so i am somewhat new to ubuntu and i am running precise.
i am unable to install anything so i am try to run apt-get update and it looks like it starts to work then it gets to the bottom and says "Reading package lists" and gets to 99% then stops and says,
"Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened."
so now i cant figure out what to do :/
please help it would be greatly appreciated.

---

### Post by LuisGMarine on 2012-12-27
First make sure that no applications like Ubuntu Software Center/Update manager are open and running.

Then launch a terminal window, CTRL + ALT + TAB, and type:

```
sudo apt-get update
```

Post back with any errors.

If all goes well you should also update the system with:

```
sudo apt-get upgrade
```

---

### Post by codyyy67 on 2012-12-27
see thats what i was doing but when it says "reading package lists" it stops at 99 then says,
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

also i have a red circle with a white line at the top right of my screen

---

### Post by Pjotr123 on 2012-12-27
Start with a fresh list:
```
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

---

### Post by codyyy67 on 2012-12-27
whenever i do anything that has to read package lists its say that error
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

---

### Post by LuisGMarine on 2012-12-27
> **codyyy67 said:**
> whenever i do anything that has to read package lists its say that error
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

Did you try what Pjotr123 said?

---

### Post by codyyy67 on 2012-12-27
yeah i tried that but it didnt change anything

---

### Post by codyyy67 on 2012-12-27
i just want to be able to install stuff again lol

---

### Post by LuisGMarine on 2012-12-27
Try the fix suggested by RedSingularity in the following link.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/829185]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/829185")

Let us know if it works.

---

