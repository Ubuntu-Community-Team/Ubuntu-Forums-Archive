---
title: "ThinkorSwim application Stops at login"
date: 2016-08-19
forum: New to Ubuntu
---

### Post by vman762 on 2016-08-19
I installed Think or Swim, the application allowed me to login about twice with flawless usage.  After I installed the kernel 4.4.8 I'm able to login and thats it.... the application remains on the login screen.  I rolled back the kernel to 4.4.0 and it still doesn't work.  what is the best approach in fixing this issue?

Thanks....

---

### Post by mook765 on 2016-08-20
Here is a statement from ThinkorSwim:
> Note: For clients who  intend to run the software on Linux, Solaris or other Unix variants,  manual update of the software may be required on these systems and we  have no official support for configuring these operating systems.
So I think it could help to reinstall the application. Maybe a fresh download could be a good idea.
[https://mediaserver.thinkorswim.com/installer/install.html](https://mediaserver.thinkorswim.com/installer/install.html)
Maybe you have to uninstall the application first, but I am not sure how to do that. It seems that you can't handle that with "apt-get remove". Just deleting the files ?
You should know where you installed the application on your system, but what about configuration-files which might be stored in a different location ?
What happens when you run the installer again, does this provide an option to remove the application ?
I don't think that the problem occurred due to the kernel-upgrade.
At least, I am not the person who knows everything. I use this forum to learn about Linux, inspired by the threads I surf the web a lot, knowledge grows...
So if there is any point in this post which helps you to solve your problem, we both are winners...
Kind regards...

---

### Post by vman762 on 2016-08-20
Thanks for responding!!!....I will try each of your suggestions.  Wish me luck!

---

