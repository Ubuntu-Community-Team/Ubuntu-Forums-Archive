---
title: "Unable to update my login password"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by keheikev on 2012-07-14
kevin@kevin-desktop:~$ sudo passwd
[sudo] password for kevin:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
kevin@kevin-desktop:~$
However I don't seem to be updating the correct password!
Could it be the keychain manager in Ubuntu 10.04 is interfering with changing the login password.?
Kevin

---

### Post by Kopkins on 2012-07-14
What happens when you use the GUI to change your password?

---

### Post by NikTh on 2012-07-14
Hi , 
try ```
sudo passwd username
```
username = your username 
Thanks

---

### Post by Kopkins on 2012-07-14
> **NikTh said:**
> Hi , 
try ```
sudo passwd username
```username = your username 
Thanks

I should have noticed that. ```
sudo passwd
``` changes the root password.

The way NikTh suggested is how to change passwords for any other user. 

Kopkins

---

### Post by keheikev on 2012-07-14
Thanks so much I knew there was a step I was missing.
Kevin

---

### Post by Krytarik on 2012-07-15
> **Kopkins said:**
> The way NikTh suggested is how to change passwords for any other user.
> **NikTh said:**
> ```
sudo passwd username
```
 Actually, just running ...
```
passwd
```... , without "sudo", would be enough in this case.

Regards.

---

### Post by NikTh on 2012-07-16
> **Krytarik said:**
> Actually, just running ...
```
passwd
```... , without "sudo", would be enough in this case.

Regards.

Yes it is ! :-)

---

