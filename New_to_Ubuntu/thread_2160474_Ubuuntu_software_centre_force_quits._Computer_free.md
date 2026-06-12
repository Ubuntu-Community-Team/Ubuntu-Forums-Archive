---
title: "Ubuuntu software centre force quits. Computer freezes."
date: 2013-07-07
forum: New to Ubuntu
---

### Post by Lennoxheadlinux on 2013-07-07
I recently tried to install skype on a new install of Ubuntu 12.4. Now my computer freezes often and I cannot open or install anything on Ubuntu Software Center without it force closing on me. 
Here is the error message 
**An error occured. Please run package manager from right cick menu or run apt -get in a terminal to see what is wrong. The error message was: 'Unknown error: '<type 'exceptions.SystemError'>'(E:The package skype needs to be reinstalled, but I cannot find the archive for it.)'.This usually means that your installed packages have unmet dependencies**
I am not sure if these two symptoms are related. Aside from skype i have also tried to install a flash plugin. 
Please help, and keep it to simple instructions as i am a beginner. Thank you

---

### Post by Lennoxheadlinux on 2013-07-07
I have attached a photo of the desktop here. There is a red alert icon in the upper task bar. I could not get a screen shot with the error message dropped down. It reads as per post above.
There is no right click option for Ubutu software Software Centre.
Bump. Any help out there. please.

---

### Post by Lennoxheadlinux on 2013-07-09
Bump! anyone out there have any idea, please?

---

### Post by newb85 on 2013-07-09
I think the problems are related.  Let's start by getting rid of your current Skype install completely.  This should stop those pesky error messages and problems with SC.

```
sudo apt-get purge skype
sudo apt-get autoremove
```

Now, how did you go about installing it the first time?

---

