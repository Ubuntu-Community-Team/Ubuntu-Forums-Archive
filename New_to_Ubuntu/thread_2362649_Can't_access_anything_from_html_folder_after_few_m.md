---
title: "Can't access anything from html folder after few moment on ubuntu server"
date: 2017-05-31
forum: New to Ubuntu
---

### Post by saif.precio on 2017-05-31
HI,
I was running an SSH server with ubuntu 14.04.5. And suddenly i was getting problem. The server ip respond when i access it via putty or filezila or webmin. but i can't access html folder. as html folder not responding. and after i reboot the server with putty it works again. i can access files of html folder.
Then i upgrade the server with 16.04.2 but the problem still not solved.

---

### Post by TheFu on 2017-05-31
> **saif.precio said:**
> HI,
I was running an SSH server with ubuntu 14.04.5. And suddenly i was getting problem. The server ip respond when i access it via putty or filezila or webmin. but i can't access html folder. as html folder not responding. and after i reboot the server with putty it works again. i can access files of html folder.
Then i upgrade the server with 16.04.2 but the problem still not solved.

Welcome to the forums.  I waited a day before responding hoping that someone else would understand the issue and be able to help.

I can't tell from the description what the issue is.
* hardware failing?
* file permissions?
* something else?

What do the system log files show? Whenever there is a systems issue, always, always, always check the log files first.

Perhaps if you posted some copy/pasted text of the problem directory using an **ls -l**?
"html folder" isn't descriptive enough.
I've never used webmin or filezila.  Webmin is hard to secure for people really new to Linux. It is another attack surface to be addressed.

I do understand ssh and file permissions.  These are usually completely separate, except in the ~/.ssh/ directory where permissions are absolutely critical or ssh won't work.

If the system is running a web app, the name/type would be useful information to provide as well.

---

