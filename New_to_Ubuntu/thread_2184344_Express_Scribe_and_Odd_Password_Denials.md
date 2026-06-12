---
title: "Express Scribe and Odd Password Denials"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by benjamin6 on 2013-10-28
Okay, now I'm trying to install Express Scribe so that I can do some transcriptions for a company -- hopefully -- but I cannot get the program to install. I've "untarred" it and attempted to open up the "shell script" in XTerminal, but when I try to run the file by simply typing in the directory, it asks for my password and denies it!

This is odd, because the password is the same for unlocking the computer when it wakes up, and in authenticating software update. When I utilized that today, the password was accepted, so it makes no sense to me as to why it would be denied in XTerm. 

Otherwise, it seems like Express Scribe WOULD install if I could get past the password stage.

Thus, is there something I can do to see if something is wrong with the password, or should I seek some kind of alternative for installing this program?

I'm a super newb, so, just to note, I barely have a grasp of Terminal commands. I just look up specific examples online and copy them down (and BAM! They work!)

Thank you for your tolerance of my ignorance!

-Ben

---

### Post by walterorlin on 2013-10-29
Are you sure you did not mistype it? If you mistype your password it is wrong and then things will not install to make things wrong so you will get denied as they did not correctly enter your password which is good for security.

---

### Post by cariboo on 2013-10-29
You could also try:

```
sudo -1
```

this will take you to a root prompt, then cd into the directory where the script is located, and runit.

---

