---
title: "Is chmod 777 dangerous even if you're the only person who uses your computer?"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by frogwarrior on 2013-12-26
Whenever I run into a file permission problem, I run chmod 777 because thats 100% sure to solve the problem. I make PHP webpages regularly and I regularly run chmod 777 -R /var/www/webpage. The result is I have a load of files with 777 permission scattered all over my system. I can see how giving all users read+write+execute permissions would be dangerous if there were other people using my laptop, but since its only me that uses my laptop is it still a problem? If so, why?

---

### Post by buzzingrobot on 2013-12-26
It's potentially dangerous if an application/daemon/process assumes certain files have a specific set of permissions.

And, of course, it can be risky if the user forgets.

Plus, those files are wide open to anyone who access the machine via the net or a local network.

Chmod'ing 777 can often be avoided by other means. Giving yourself access to a file does not require giving the world access to it.

---

### Post by Morbius1 on 2013-12-26
And if you are going to do this sort of thing anyway use this method instead:
```
sudo chmod -R a+rwX /path
```
The big "X" will make folders 777 and files 666 except those files that were marked as executable to begin with.

chmod'ing with an odd number in octal mode isn't smart enough to differentiate between a file and folder and makes everything executable.

---

