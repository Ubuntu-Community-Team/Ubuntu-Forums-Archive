---
title: "executable"
date: 2018-06-16
forum: New to Ubuntu
---

### Post by yrobel on 2018-06-16
Hi,
I  upgraded to Xubuntu 18.04, and I have a problem with executable files  because it recognizes (application/x-sharedlib) instead of (application/x-executable). 
How can I resolve this problem?. In the link: the image corresponds to Xubuntu 16.04 (left) and Xubuntu 18.04 (right).
Thanks:D

[https://mega.nz/#!U3wlDbZR!Wjo7SNnRPgF-f1Z2xRKnHroiJgrO7phYbKfEPbvtyYY](https://mega.nz/#!U3wlDbZR!Wjo7SNnRPgF-f1Z2xRKnHroiJgrO7phYbKfEPbvtyYY)
[URL="https://mega.nz/#!BvwHRDQQ!JGzXiE7ILQG2A4VfXk6ssy8GYZIxlPyIR5uYw8rUl6s"]

[/URL]

---

### Post by again? on 2018-06-17
Try moving or renaming your **~/.config/mimeapps.list** file.

---

### Post by oldfred on 2018-06-17
Permissions?
This is lower case LL
fred@bionic-z97:~$ ll

Or not using sudo? (this particular command does not work for me) :)
       [http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by yrobel on 2018-06-17
Thanks for your reply;
I changed the name of the file you indicated but the problem persists. When compiling, it does not recognize the executable file. In Xubuntu 16.04 I recognized it as executable but in Xubutu 18.04, it recognizes it as a shared library file. By the way, the executables works correctly.
Thanks.

---

### Post by &amp;KyT$0P# on 2018-06-17
When compiling the executable in 18.04 try passing [FONT=Courier New]-no-pie[/FONT] flag to gcc/g++

---

### Post by yrobel on 2018-06-18
Thanks,
But it does not work using the "-no-pie" flags, it continues to generate shared library file. Will it be problems with gcc/g ++?

Regards

---

### Post by &amp;KyT$0P# on 2018-06-18
You could try [FONT=Courier New]-fno-PIE -no-pie[/FONT], if that doesn't work add [FONT=Courier New]-fno-PIC[/FONT] also.

If that still doesn't fix it, what program is this and how are you compiling it?

---

### Post by steeldriver on 2018-06-18
> **yrobel said:**
> Hi,
I  upgraded to Xubuntu 18.04, and I have a problem with executable files  because [COLOR=#ff0000]**it**[/COLOR] recognizes (application/x-sharedlib) instead of (application/x-executable). 
How can I resolve this problem?.
Thanks:D

[IMG]https://drive.google.com/open?id=14-bdMGXek0SCibMuWjPtcXYLAv1RMsdm[/IMG]

I don't think we know exactly what the problem is - what is "it" in this context? are you talking about double-clicking files in the file manager? or running something from the command line? or building software from source?

---

### Post by yrobel on 2018-06-18
Thanks for your reply,
I mean building software from source. Also in the /bin/ directory in Xubuntu 18.04, the executable are recognized as a shared library file.

Attached a link with an image in the original post


Thanks

---

