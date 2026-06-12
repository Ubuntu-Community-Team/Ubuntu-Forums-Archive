---
title: "[SOLVED] usb no longer working after transfer of docs"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Sbarton on 2008-08-26
Hi all! earlier inserted my usual usb stick (which i believe may be usb1) which I have used regularly. Then inserted another (usb2)stick, both recognised and mounted. I then proceeded to transfer (copy and paste)all contents from usb1 to usb2. Everything went fine, everything copied over. I then umounted both sticks. About 15 minutes later I went to use my usb printer only to find it is no longer recognised. I inserted the usb sticks to find they also are not now recognised /mounted. Both printer and usb sticks still work fine in Windows. As printer and usb1 drive have been used before in Ubuntu I am at a loss as to what happened.Could it be the second usb drive which caused it? Finally can you help me to get the usb's up and running again?
thanks and regards
PS How do I take a screen shot that includesa active scrollbar in case I need to upload a long sreenshot attachment?
Thanks

---

### Post by Titan8990 on 2008-08-26
Did you try mounting the usb sticks manually?


Do they show up using the fdisk -l command?

---

### Post by cariboo on 2008-08-26
In a Applications-->Accessories-->Terminal type:

```
lsusb
```

And post the output in your next post. That way we can see if your devices are detected.

Jim

---

### Post by Sbarton on 2008-08-26
Thanks for both replies! The details requested are attached.
regards

---

### Post by Sbarton on 2008-08-27
Solved! After trying for hours to solve the problem and as I was getting to tired, I decided to switch everything off and get some sleep.This morning I switch on and 'eureka'all usb ports are now working :).Most peculiar, but then it is a computer!:)
regards

---

