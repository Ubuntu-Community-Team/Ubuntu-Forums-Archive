---
title: "How do I Execute Scripts on System Startup?"
date: 2005-01-29
forum: Programming Talk
---

### Post by cwaldbieser on 2005-01-29
In other distros, there is usually a file like /etc/rc.local where you can but the scripts you want to run on system startup.  Anybody know what the mechanism for doing this in Ubuntu is?

Thanks,
Carl Waldbieser

---

### Post by az on 2005-01-29
/etc/init.d

/etc/rc2.d



the rc(runlevel).d directory contain symlinks to the actual scripts in /etc/init.d

If you want something more secure, there is a gnome startup thing. (Computer, Desktop pref, Session)

---

### Post by mendicant on 2005-01-30
Also look into update-rc.d to manage the files in /etc/init.d

---

