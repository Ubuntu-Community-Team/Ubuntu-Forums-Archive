---
title: "HTML -&gt; Open ubuntu terminal"
date: 2009-09-11
forum: Programming Talk
---

### Post by Drenriza on 2009-09-11
im creating a webpage, where the idea is to be able to click on a ip.
and when you click on the ip on the webpage a terminal opens. with a ssh, name and ip.

ssh name@ip

But how is this done?.
Where do i start?.

Hope someone can help me.

:KSThanks on advance:KS
Cristian

---

### Post by scragar on 2009-09-11
As part of the browser security model I doubt this would be possible at all without writing a plugin and getting the users to install it.

---

### Post by Drenriza on 2009-09-11
to get users to install a plugin wodent be a problem.

---

### Post by benj1 on 2009-09-11
have a look at apt-url it seems somewhat similar to what youre trying to do, clicking on a special link starts the installer to install a given package

eg [gedit]("apt:gedit")

---

### Post by Drenriza on 2009-09-11
is that a website/command or where do u want me to look?

---

### Post by benj1 on 2009-09-11
> **Drenriza said:**
> is that a website/command or where do u want me to look?

no its just intended to show what apt-url does although it may have been better to supply something that isn't installed by default, clicking on it will just say its already installed.

anyway the point is, have a look at the source it should be possible to adapt it to launch a terminal.

---

### Post by scragar on 2009-09-11
> **benj1 said:**
> no its just intended to show what apt-url does although it may have been better to supply something that isn't installed by default, clicking on it will just say its already installed.

anyway the point is, have a look at the source it should be possible to adapt it to launch a terminal.

It's rather easy actually, you need to pass a few pref()s

This is what apt-url uses:```
pref("network.protocol-handler.app.apt","/usr/bin/apturl");
pref("network.protocol-handler.warn-external.apt",false);
pref("network.protocol-handler.app.apt+http","/usr/bin/apturl");
pref("network.protocol-handler.warn-external.apt+http",false);

```
You will need to make a few changes, changing the handler and apt label to something else.
```
pref("network.protocol-handler.app.myssh","/usr/bin/gnome-terminal -x ssh");
pref("network.protocol-handler.warn-external.myssh",false);
pref("network.protocol-handler.app.myssh+http","/usr/bin/gnome-terminal -x ssh");
pref("network.protocol-handler.warn-external.myssh+http",false);
```which would expect a link of something like:```

myssh:user@host.com
```
That's untested though.

---

### Post by tturrisi on 2009-09-12
> **Drenriza said:**
> im creating a webpage, where the idea is to be able to click on a ip.
and when you click on the ip on the webpage a terminal opens. with a ssh, name and ip.

ssh name@ip

But how is this done?.
Where do i start?.

Hope someone can help me.

:KSThanks on advance:KS
Cristian

It can be done using html forms and php.  I have a script that uses a textarea as a mysql shell and any sql commands can be executed on the server.  Note, it's insecure because it gives root access.  I use it only on a LAN server.

PHP Shell Terminal & others can be used too:
[http://sourceforge.net/projects/phpterm/](http://sourceforge.net/projects/phpterm/)
[http://sourceforge.net/projects/shcmd/](http://sourceforge.net/projects/shcmd/)

---

### Post by s.fox on 2009-09-12
Hi,

[This]("http://uk.php.net/shell_exec") may be of some use to you.  Good luck :)

-Silver Fox

---

