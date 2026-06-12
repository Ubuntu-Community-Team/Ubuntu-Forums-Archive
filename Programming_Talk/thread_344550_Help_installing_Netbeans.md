---
title: "Help installing Netbeans"
date: 2007-01-23
forum: Programming Talk
---

### Post by nick.inspiron6400 on 2007-01-23
Hi,

I have been interested in Java for some time now, i have been reading on which IDE and i have found that netbeans is very good.

1: How do I install it? I am very new to Linux and i cant find it in the add or remove.

Thanks,

Nick,

P.S

I will have more questions once i can have it installed!:D

---

### Post by renzokuken on 2007-01-23
have you searched in Synaptic?

---

### Post by Mirrorball on 2007-01-23
I don't think it's in Synaptic. Have you installed Java already? If you haven't, there is a recent thread that has instructions on how to install the most recent version. Then go to Netbean's site, download the Linux packages, unpack it, then run an install script. Here:
[http://www.netbeans.info/downloads/index.php](http://www.netbeans.info/downloads/index.php)

---

### Post by lukew on 2007-01-23
> **Mirrorball said:**
> I don't think it's in Synaptic. Have you installed Java already? If you haven't, there is a recent thread that has instructions on how to install the most recent version. Then go to Netbean's site, download the Linux packages, unpack it, then run an install script. Here:
[http://www.netbeans.info/downloads/index.php](http://www.netbeans.info/downloads/index.php)

I vouch for that... no problems from installing the bin file. Using Dapper BTW.

Luke

---

### Post by laxmanb on 2007-01-23
Yeah... the .bin file will even place shortcuts on your desktop and Applications menu...

---

### Post by nick.inspiron6400 on 2007-01-23
Okay, I will try that!

I will get back to you all later!

Thanks,

Nick,

---

### Post by nick.inspiron6400 on 2007-01-23
It says "Could not open the file /home/nick/Desktop/netbeans-5_5-linux.bin. gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

What does this mean?

Thanks i am really stuck!

Nick,

---

### Post by rekahsoft on 2007-01-23
> **nick.inspiron6400 said:**
> It says "Could not open the file /home/nick/Desktop/netbeans-5_5-linux.bin. gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

What does this mean?

Thanks i am really stuck!

Nick,

You have to make it executable. To do do this open your terminal and put the following in:```
chmod +x /home/nick/Desktop/netbeans-5_5-linux.bin
```

---

### Post by nick.inspiron6400 on 2007-01-23
Thanks!

I did that and it worked! Thanks for everyone's help anyway!

Nick,

---

