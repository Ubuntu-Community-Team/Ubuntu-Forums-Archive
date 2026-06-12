---
title: "Su: Authentication failure, 3 Kernels in GRUB"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Doxa on 2012-04-22
I followed this post to reset my user password:
[http://ubuntuforums.org/showthread.php?t=1957309&highlight=su%3A+Authentication+failure](http://ubuntuforums.org/showthread.php?t=1957309&highlight=su%3A+Authentication+failure)

It still does not work.  And I have three kernels in GRUB.

the last numbers are .38, .39, .40

What do I do :confused:

Lucid Linux 10.04 LTS

Thanks!

---

### Post by newbie-user on 2012-04-22
For future reference, typing in

```
sudo passwd [user]
```

in the command line will change a user's password. No need to edit the sudoers file for password changes. You only need to edit the sudoers file if you want to add a user to the sudoers list.

Regarding the three kernels, you need not worry about that. It's actually a good idea to keep at least one previous kernel just in case the current one has problems. If you want to get rid of the extra kernels, type

```
sudo apt-get remove linux-image-2.6.32-38-generic linux-image-2.6.32-39-generic -y && apt-get autoremove -y
```

This gets rid of the 38 and 39, assuming you used the generic kernels.

---

### Post by Doxa on 2012-04-22
Did what you said and it still says authentication error...
Good to know about the kernels.

Thanks!

---

### Post by newbie-user on 2012-04-22
> **Doxa said:**
> Did what you said and it still says authentication error...
Good to know about the kernels.

Thanks!

Hmm... Might be due to the change in the sudoers file. Have you enabled the root account by any chance? Or do you have another user that can still sudo?

---

### Post by Doxa on 2012-04-22
i changed the password yet again the way you said it and the third time it worked.  I don't know what that's all about, but I guess this is now solved.  Thank you. :)

---

