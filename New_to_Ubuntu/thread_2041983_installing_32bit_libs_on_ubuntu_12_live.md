---
title: "installing 32bit libs on ubuntu 12 live"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by amrosama77 on 2012-08-13
I can't install 32bit libs on ubuntu 12 live

I used this code
apt-get install ia32-libs and got this result

could not open lock file /var/lib/dpkg/lock - open (13: permission denied)
unable to lock the administration directory (/var/lib/dpkg/), are you root?

Please advice,

---

### Post by marlow59 on 2012-08-13
apt-get should be run with higher privilege : 
```
 sudo apt-get ... 
```

---

### Post by amrosama77 on 2012-08-13
thank you,

I run it and got this:

.............
.............
................
Package  'ia32-libs' has no installation candidate



Please advice,

---

### Post by marlow59 on 2012-08-13
please past the output of the command 
```
 uname -p 
```

also try : 
 ```
 sudo apt-get update
sudo apt-get install ia32-libs 
```

---

### Post by amrosama77 on 2012-08-13
the output is



i686

---

### Post by marlow59 on 2012-08-13
well this is odd. Ok, try 
```
sudo apt-get install package-name:i386 
```
Hope it helps.

---

### Post by amrosama77 on 2012-08-13
I am downloading/installing some program via software center,
so I guess I should wait

thank you for helping me out

---

### Post by marlow59 on 2012-08-13
you're welcome. If your problem is solved, please mark the thread as [Solved] by clicking on the thread tools menu.

---

### Post by amrosama77 on 2012-08-13
thank you,

---

### Post by deadflowr on 2012-08-13
Your system is running 32bit ie ,i686 is 32bit architecture.
You shouldn't need 32bit libraries for your system. 
However:

[http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package]("http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package")

Hope this helps.

---

