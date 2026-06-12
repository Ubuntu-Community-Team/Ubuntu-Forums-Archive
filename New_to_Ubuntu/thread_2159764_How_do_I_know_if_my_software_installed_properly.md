---
title: "How do I know if my software installed properly"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by lawrencegan on 2013-07-04
Hi all,
After getting used to ubuntu, I started installing wine by using terminal, at first it seems work properly, however after I agreed a licences, it shows  "ldconfig deferred processing now taking place wine" and I had no idea how to do next,so I quite.
But I still found an application wine in my dash home,will it work properly? 

Kind Regards
Lawrence

---

### Post by newbie-user on 2013-07-04
If there were no error messages, then it will work.

---

### Post by DeathByDenim on 2013-07-04
The "ldconfig deferred processing now taking place wine" just means that the library cache is being updated. No need to worry about that. (See here: [https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/15849](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/15849) )
That happens at the end of the installation though, so that means it all should have been installed properly as newbie-user indicated.
I would suggest to just try it out:
```
wine notepad
```
That should open up the Windows text editor.

---

### Post by oldos2er on 2013-07-04
Moved to Absolute Beginners.

---

