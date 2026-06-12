---
title: "sudo: fdisk: command not found"
date: 2016-05-23
forum: New to Ubuntu
---

### Post by hach75 on 2016-05-23
Hello, 

Im trying to run this command in an external drive using ssh:

```
sudo fdisk -l
```

and i get this error:

sudo: fdisk: command not found

Help would be nice. Thank you

---

### Post by KenUBF on 2016-05-23
Hi hach,I would think it would be installed by default, but to better help, which version of Ubuntu are you using? Did you get any other error messages? I tried the exact same command in 16.04 and 14.04 and it listed all partitions so I don't see why it wouldn't work. 

Edit:  I did read that if you do not invoke sudo privileges you will get that error, but you say you ran it with elevated privileges. Are you sure you did run it as root?

---

### Post by hach75 on 2016-05-23
Hi Ken UBF, Thank you for your reply.

Im trying this command in SSH in ubunto 16.04. It works fine as long as Im not in SSH. 

What a really need to have is the list of partitions in a network drive I can only access trough SSH, therefore need to run fdisk

---

### Post by KenUBF on 2016-05-25
hach,

I've never used SSH and I'm still learning myself, so I don't think I have the experience necessary to help with your question. I haven't found anything online yet to help me answer your question, either. You may have to wait until someone else responds. I'm sorry about that.

---

### Post by sudodus on 2016-05-25
You need permissions to run sudo in the remote computer (not only your local computer). And the remote system must have fdisk installed, and as is already said, fdisk should be available in most linux systems.

If you are connecting to a server, that is owned by another person or organisation, you will probably ***not*** get permissions to run sudo.

---

