---
title: "pointer speed..."
date: 2012-08-02
forum: New to Ubuntu
---

### Post by amin021023 on 2012-08-02
Hi and Lovr

I want to speed up the pointer(touchpad) and one important detail: it cant be changed by settings....

I have a acer 5349 laptop....

thanks:popcorn:

---

### Post by NikTh on 2012-08-02
Hi , 
open a terminal(Ctrl+alt+t) and give results of  this command 
```
synclient | grep MaxSpeed
``` 

Thanks

---

### Post by amin021023 on 2012-08-02
> **NikTh said:**
> Hi , 
open a terminal(Ctrl+alt+t) and give results of  this command 
```
synclient | grep MaxSpeed
```Thanks

here it is:

```
amin@Amin-Aspire:~$ synclient | grep MaxSpeed
[SIZE=2][B]    MaxSpeed                = 1.75
    EdgeMotionMaxSpeed      = 427[/B][/SIZE]
amin@Amin-Aspire:~$ 

```

---

### Post by NikTh on 2012-08-02
Hi , 
can you incrase the speed with below command ? 
```
synclient MaxSpeed=3.0
``` 
Or 
```
synclient MinSpeed=3.0
``` 
Do you see any difference ?

After above , give again the results to see if anything change 
```
synclient | grep -e MaxSpeed -e MinSpeed
```
Thanks

---

### Post by amin021023 on 2012-08-02
> **NikTh said:**
> Hi , 
can you incrase the speed with below command ? 
```
synclient MaxSpeed=3.0
```Or 
```
synclient MinSpeed=3.0
```Do you see any difference ?

After above , give again the results to see if anything change 
```
synclient | grep -e MaxSpeed -e MinSpeed
```Thanks

yes it worked thanks....

---

### Post by NikTh on 2012-08-02
> **amin021023 said:**
> yes it worked thanks....

Glad it worked. 

You must know that is temporally. 
You can give this command each reboot , or you can  create a simple script and add to start-up applications. 

For the script take a look here --> [http://ubuntuforums.org/showthread.php?p=12143902](http://ubuntuforums.org/showthread.php?p=12143902)

Thanks

---

