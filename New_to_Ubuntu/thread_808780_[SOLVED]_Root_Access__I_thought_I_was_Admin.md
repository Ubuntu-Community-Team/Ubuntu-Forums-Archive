---
title: "[SOLVED] Root Access?  I thought I was Admin?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by CrazyCanuck on 2008-05-26
Ok, something rather interesting has happened to me.  Let me reproduce to you all the root access error I am getting.  The error is, I do not seem to have root access, and need to know how to go about doing this.

I was trying to get Grokking The GIMP from the repositories, and the following occured:

my_user_name_here:~$ apt-get install grokking-the-gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I would LOVE to learn how to achieve root access, this would allow me to get around these instances of lock-out.  :)

P.S.  In the meantime, I will try to search the forums here to learn how to achieve root access, and if I am still unable to do this on my own, will return to see your replies (I hope) :)

CC

---

### Post by dRock1286 on 2008-05-26
to use a command as root you need to use
```

sudo apt-get install grokking-the-gimp
```
it will prompt you for your password and continue on...  enjoy!

---

### Post by Maestro23 on 2008-05-26
RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=(RootSudo](https://help.ubuntu.com/community/RootSudo?highlight=(RootSudo))

---

### Post by jpeddicord on 2008-05-26
What dRock1286 said. Ubuntu uses limited permissions by default to prevent accidental (or malicious) destruction of data on your system. sudo grants root access as your user when you type in your password, then remembers it for 15 minutes so you don't have to type it in every time.

---

### Post by CrazyCanuck on 2008-05-26
Thanks everyone.  I shall do just as I have been told, and grab Grokking The GIMP from the repos.  Take care.

P.S.  Eventually, I will be answering other peoples' questions as well, I am just not able to do so now.  rawr hehe!

CC

---

### Post by CrazyCanuck on 2008-05-26
Success.  Grokking The GIMP is on its way.  Slow net this evening or very VERY busy repositories!

Thanks.

CC

---

