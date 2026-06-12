---
title: "UNIX password: not able to enter anything in this field"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by ronaldsims on 2012-08-26
I've been trying to recover my password, as administrator, in Ubuntu 12.4 LTS using the instructions involving the GRUB boot process.  When I get to the line that says UNIX password, I am not able to enter anything.  I tried typing numbers, letters, etc.   What am I doing wrong here?

thanks for answers

---

### Post by cryptotheslow on 2012-08-26
You won't see anything displayed when you type the password - not what you are typing and not a row of asterisks - nothing at all.

That is why you are required to enter it twice, to ensure you have typed it correctly.

---

### Post by ronaldsims on 2012-08-26
Thanks for your answer.  

However: I did type a simple word, hit "enter", then typed the same word again.  I got the "maniupation error" message.  I am sure that I type that simple word correctly both times.  

Would you have any other ideas please?

---

### Post by cryptotheslow on 2012-08-26
I have a feeling in recovery mode the filesystem is mounted read only, so you are initially unable to make any changes to the system.

Once in recovery mode issue this command to remount the filesystem in read-write mode:
```
mount -o remount,rw /
```

Then proceed with your password reset procedure.

You shouldn't need to use sudo with that command as in recovery mode you are logged in as root.

---

### Post by linuxman72 on 2012-08-26
try the instructions on this site. they should work well

[http://aplawrence.com/Linux/lostlinuxpassword.html]("http://aplawrence.com/Linux/lostlinuxpassword.html")

---

