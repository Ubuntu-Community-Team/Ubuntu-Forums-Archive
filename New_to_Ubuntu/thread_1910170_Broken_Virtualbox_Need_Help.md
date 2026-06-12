---
title: "Broken Virtualbox Need Help"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by bennettg on 2012-01-16
My virtualbox is borked after upgrading from 11.04 to 11.10.  i searched the error messages i received and used techniques from this forum to try to fix it, but one error after another came up.  I even did the dkms uninstall and reinstall for some kind of kernal error, but that failed too.  

Uninstalling everything that said virtualbox and resinstalling did not help.  Made no difference whether i used command line, synaptic or ubuntu software center.

My question is:

Is there anyway to wipe everything and start over without having to resinstall the entire operating system.  At this point, I just need a clean slate.  virtualbox is critical for me as my kids games run only in windows.

thanks in advance
noob

---

### Post by CharlesA on 2012-01-16
purge virtualbox and reinstall it.

```
sudo apt-get purge virtualbox*
```

---

### Post by Cheesemill on 2012-01-16
More info please.

What problem are you having with VirtualBox?
What error messages are you getting?

---

### Post by bennettg on 2012-01-16
> **CharlesA said:**
> purge virtualbox and reinstall it.

```
sudo apt-get purge virtualbox*
```

thanks! worked perfectly after i ran the command and reinstalled through ubuntu software center.  

much appreciated.  have yourself a good day.

---

### Post by CharlesA on 2012-01-16
Good to know.

Don't forget to mark the thread as solved from thread tools. :)

---

