---
title: "Nvidea graphics driver installation"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by grbaker101 on 2014-01-09
Hello, and thanks for your valued assistance with my brief problem.
I have consulted the help pages and I think I accidently rolled back or updated my kernal so that the Linux headers no longer match the restricted module verzion.:
[h=1]Troubleshooting[/h]  
[h=2]Installation Fails[/h] If the restricted driver remains unactivated after attempting to activate it in the *Additional Drivers* dialog, you may not have the appropriate linux headers installed to compile the driver. Ensure that the linux-headers-XXX and linux-restricted-modules-XXX packages are installed, where XXX matches the version of the kernel you are using. 

My problem is that I don't know how to do this......
would somebody please walk me through the steps involved. TY

---

### Post by mikewhatever on 2014-01-10
Assuming the info you've supplied is correct, just run the following in a terminal window:
```

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`

```

---

### Post by grbaker101 on 2014-01-11
"Assuming the info you've supplied is correct, just run the following in a terminal window:"

my diagnosis was incorrect....maybe I'll describe the problem more thoroughly...
I can boot into previous versions of UBUNTU without problem....Whenever I boot into the current version, the NVIDEA Xdriver fails to load and when i go to the install additioanl drivers dialogue box, all four drivers appear but I cannot install any of them.
The error message tells me to consult the /var/log/jockey.log, which I have done, but being a noob, it doesn't make much sense to me yet.  I'm not quite sure how to reproduce the contents of the log - It's very long (as I have had the problem a long time and tried many times to fix it) - If it's just copy and paste I can do that, but if there's a command or procedure for reproducing a log file, I don't know it yet....Thanks Mike - I appreciate you taking the time to help me.

---

