---
title: "Getting an error while Ubuntu is starting"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by Oinos on 2014-03-08
I get this error every time I start the computer on loading ubuntu: 
error: mismatch in adjustment_mode.flags [expected 2, found 0]
There is also some prefix before it, but the error is displayed for a very short while and I can't remember it.
What does the error mean and how can I fix it?
I'm using ubuntu 13.10 on dell latitude.
Thanks in advance.

---

### Post by Ubi_one_2014 on 2014-03-08
did you do a complete system upgrade before?

sudo su -
apt-get update && apt-get dist-upgrade

post also, as non-root:
[COLOR=#333333][FONT=Ubuntu]cat /var/log/messages[/FONT][/COLOR]

---

### Post by ibjsb4 on 2014-03-08
A brief google search seems to indicate this is a kernel problem and most times solved with a kernel upgrade. A dist-upgrade will upgrade the kernel if there is one available.  I do it a bit different than Ubi_one.

```
sudo apt-get update

```
then

```
sudo apt-get dist-upgrade
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

[https://www.google.com/search?client=ubuntu&channel=fs&q=error%3A+mismatch+in+adjusted_mode.flags&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=error%3A+mismatch+in+adjusted_mode.flags&ie=utf-8&oe=utf-8)

---

