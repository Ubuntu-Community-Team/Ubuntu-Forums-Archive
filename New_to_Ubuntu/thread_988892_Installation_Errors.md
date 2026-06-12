---
title: "Installation Errors"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Drezard on 2008-11-21
Getting installation errors like this:

> 
Setting up libapache2-mod-php5 (5.2.4-2ubuntu5) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_AU.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory


when installing things. Whats going on?

Daniel

---

### Post by iaculallad on 2008-11-21
You could try:

```
gksudo gedit /etc/default/locale
```

Delete the content(s) and add:

```
LANG=en_US.UTF-8
```

Saved and close the file and issue the command:

```
locale -a
```

---

### Post by x0x on 2008-11-26
i am still getting this problem...

---

