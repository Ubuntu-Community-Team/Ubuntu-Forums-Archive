---
title: "update manager not working"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by chestycuogth on 2012-03-22
ok, i have searched for similar topics and failed to find any - if this question has already been answered then could you please direct me to previous thread thank you.

anyway MY QUESTION.
when the update manager starts then i am only given the option of a partial upgrade - but the update stalls on the 'preparing to upgrade' part. i checked the terminal and this is what it said:
Setting up sandboxgamemaker (2.6.1+dfsg-7) ...
Cleaned old data
--2012-03-22 16:52:59-- [http://sandboxgamemaker.com/sandbox/...tiplatform.zip](http://sandboxgamemaker.com/sandbox/...tiplatform.zip)
Resolving sandboxgamemaker.com... 69.163.252.177
Connecting to sandboxgamemaker.com|69.163.252.177|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.sandboxgamemaker.com/sand...tiplatform.zip](http://www.sandboxgamemaker.com/sand...tiplatform.zip) [following]
--2012-03-22 16:52:59-- [http://www.sandboxgamemaker.com/sand...tiplatform.zip](http://www.sandboxgamemaker.com/sand...tiplatform.zip)
Resolving [www.sandboxgamemaker.com](www.sandboxgamemaker.com)... 69.163.252.177
Reusing existing connection to sandboxgamemaker.com:80.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

The file is already fully retrieved; nothing to do.

replace PlatinumArtsSandbox2.6.1/bin/jpeg.dll? [y]es, [n]o, [A]ll, [N]one, [r]ename:

what exactly do i have to do to just get the update to continue?
i really need help because i cannot find any help on this anywere.

thank you for your time.

---

### Post by Bucky Ball on 2012-03-22
Welcome.

It is control+shift+c to copy from the terminal (or mark out the section you want to copy and press the scroll wheel on the mouse where you want to copy it). ;)

---

### Post by chestycuogth on 2012-03-22
thanks for showing me how to copy and paste - i updated the post

---

### Post by Bucky Ball on 2012-03-22
Hit 'Y' to replace PlatinumArtsSandbox2.6.1/bin/jpeg.dll?

---

### Post by chestycuogth on 2012-03-22
i have tried hitting y and Y and [y] and [Y] and it doesnt seem to work

---

### Post by tbhatia4 on 2012-03-22
Try updating update manager core
```
sudo apt-get install update-manager-core
```

---

### Post by Bucky Ball on 2012-03-22
Have you tried:

```
sudo apt-get upgrade
```? What message does it throw when you try updating via the Update Manager? Incidentally, what release are you using? Sorry if you said and I missed it ...

---

### Post by chestycuogth on 2012-03-26
Package operation failed

The installation or removal of a software package failed.
this is what it says now.
it lets me start the operation now but i get this message when the operation completes.
btw. the version is the latest.
11.10 i think.

---

### Post by Bucky Ball on 2012-03-26
Please go to 'System Monitor' and check for sure. ;)

---

