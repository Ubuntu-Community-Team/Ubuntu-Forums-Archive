---
title: "Send an email from python without smtplib"
date: 2016-04-15
forum: Programming Talk
---

### Post by mfvpcrec on 2016-04-15
Hello again guys :) ! I need send an email from python script but not using the smtplib library.
 I'm programming for a device that not has that library  (and the device not allows upgrade the python version)
so I need to know if there is a standalone  library that allows send mails without smtplib.

Thank you for all your help! 

Bye!

---

### Post by TheFu on 2016-04-15
SMTP is a simple protocol, so if you can connect via something like telnet to the mail server you need, then it should be possible.
The hard part comes from all the anti-spam addons to SMTP which make this harder.  For example, my email server will not allow non-encrypted connections of any type, period.

But if you control the email server and allow non-encrypted connections, a simple telnet exchange for text messages shouldn't be too hard.  You can see the required exchange by using telnet from any system and manually performing the required SMTP exchange. Lots of how-to docs on the internet with that info.

Sorry I'm not more help, but know that it is possible.

---

### Post by mfvpcrec on 2016-04-18
Thank you TheFu but I  though about the problem and I resolved the problem in another way.
Thank you!

---

### Post by TheFu on 2016-04-18
There are 500 different solutions to most problems.  I bet others would love to see what you decided. Please share.
Also, if you can mark this thread as SOLVED, that will help the community.
a) find a solution
b) NOT look to help when it has already been solved.

---

### Post by mfvpcrec on 2016-04-19
I couldn't upgrade the python version, but I could put missing files in the device. So I downloaded the python version of the
 device and I looked for smtplib and all its dependencies. After that I found files, I copy the files into the device and  it worked! 
(Really it was very annoying search for each file but it worked until now)
Bye!

---

### Post by TheFu on 2016-04-19
> **mfvpcrec said:**
> I couldn't upgrade the python version, but I could put missing files in the device. So I downloaded the python version of the
 device and I looked for smtplib and all its dependencies. After that I found files, I copy the files into the device and  it worked! 
(Really it was very annoying search for each file but it worked until now)
Bye!

So you created a self-contained python environment (which **is** a best practice for all non-OS python needs) and used that python and associated libs instead of the OS installed version.  Nice.

---

