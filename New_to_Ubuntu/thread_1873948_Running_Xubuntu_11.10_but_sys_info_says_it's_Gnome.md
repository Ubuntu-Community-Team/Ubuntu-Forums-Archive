---
title: "Running Xubuntu 11.10 but sys info says it's Gnome 2.32.1!"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by rojaasensei on 2011-11-02
I have xubuntu 11.10, but if I run sysinfo it says my os is Gnome 2.32.1 under ubuntu 11.10

Is this normal?  If not then I worry about the next Xubuntu upgrade.  How can I correct this. 

Your help would be much appreciated.

---

### Post by gsmanners on 2011-11-02
The sysinfo package is a Gnome program, so of course it assumes you're running Gnome. Nothing strange about that.

If you feel like this is a serious error, you can [report it]("https://launchpad.net/ubuntu/+source/sysinfo/+filebug"). I highly doubt it matters, though.

```
cat /etc/lightdm/lightdm.conf | grep user-session
```

The above terminal command shows you what you're *really* running (assuming you're using a default installation).

---

### Post by rojaasensei on 2011-11-02
Thank you for your response.  The terminal response to the command you suggested returned "ubuntu."

---

### Post by gsmanners on 2011-11-02
By way of comparison, here's what mine says:

```
$ cat /etc/lightdm/lightdm.conf | grep user-session
user-session=xubuntu
```

---

