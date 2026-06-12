---
title: "internal error"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by dblackmon on 2012-08-11
Hi - I keep getting an error message that says Ubuntu has experienced an internal error and point me to a Firefox page for support, but I have  not had any luck there. I have a little experience with command line. Is there a command to debug the program?

---

### Post by 2F4U on 2012-08-11
The internal error dialogue should give you details about what happened. Can you provide these details? Some of these errors can be safely ignored. Do you experience any problems after the error happens?

---

### Post by antiartist on 2012-08-11
Go forth and check ye log files.

I'm not sure where the firefox logs are kept (I'm guessing /var/log) as run a headless server and don't actually have Firefox installed. 

Once you eventually find the log(s), locate the particular date and time that the error occurred and see if there are any messages indicating that something went horribly wrong.  If you find such things, you should post them here to give everyone a better idea of what's happening

---

### Post by nothingspecial on 2012-08-11
Prefix changed from lubuntu to ubuntu.

---

### Post by rosswmcgee on 2012-08-27
I get these often and keep wondering if it these bugs will be fixed with updates.

We use 12.04 on two computers and Debian 6.0 on another and never get them with Debian.

---

### Post by NikTh on 2012-08-27
Hi , 
**If you have no problems , and only if you have no problems : **
you can do this (to disable reports for errors) 

```
gksudo gedit /etc/default/apport
``` 
change 1 to 0(zero) so the line will be like this 
```
enabled=0
``` 
save the document and that was it. No more errors will be reported. 
**This is not the solution.** This is only a workaround for continuously reported errors that NOT affect Ubuntu's functionality.  
Thank you

---

