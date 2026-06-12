---
title: "Problem sharing $HOME folder"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by vitorgatti on 2008-05-19
Hi,

When I share my home folder (/home/user) with Write privileges and No Anonymous Connection and I restart my PC, I get this warning:

**"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others."**

I close the window and all starts ok, BUT... why this message? What's happening?
And... where can I find a list of my Sharings? The icon Shared Folders doesn't exist anymore... why?

Thanks

---

### Post by RealPSL on 2008-05-19
You are probably getting that error message because the permissions on that ".dmrc" file are too permissive. To correct the problem click "Places  > Home Folder". In the resulting window click "View > Show Hidden Files". Locate the ".dmrc" file right click it and choose Properties. Choose Permissions, make the access permissions for group and other "None". Click close. Log out and then log in to confirm the error is gone.

---

### Post by vitorgatti on 2008-05-19
The error persists... it only goes away if I unshare my home folder.

---

### Post by RealPSL on 2008-05-19
[http://ubuntuforums.org/showthread.php?t=91455]("http://ubuntuforums.org/showthread.php?t=91455")

Is a similar thread might be worth a look.

---

### Post by jtibau on 2008-05-20
Do you really need to share your whole $HOME?
I usually share Public, and then add symlinks to folders or files I want to be viewable. For example:
```

cd $HOME/Public;
ln -s ~/Music;
ln -s ~/Pictures;

```
That, of course, may not be what you wish... I find it safer btw

---

