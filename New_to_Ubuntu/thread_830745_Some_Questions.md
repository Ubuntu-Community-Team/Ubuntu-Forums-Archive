---
title: "Some Questions"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by jotnarta on 2008-06-16
Hi

First of all, I would like to thank you very much guys for your answers, I am a newbie for Ubuntu and linux, so you will see some trivial or simple questions for you, but not for me:popcorn:.

I have some simple questions:
First: How can i know the version of Ubuntu?
Second: How can I know the architecture?
Thrid: From where can I get a document that explains the terminal commands and its usage, like (sudo, apt-install, etc).

Thank you in advance
Jotnarta

---

### Post by _sphinx_ on 2008-06-16
For the version. Type
```

gnome-system-monitor

```
open the first tab and you fill find the specifications like about your cpu and versoin.
For terminal usage, just type man in front of command in the terminal, like for example,
```

man sudo

```

---

### Post by nothingspecial on 2008-06-16
This ought to give you a good start -

[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

---

### Post by kpkeerthi on 2008-06-16
**GUI:**
    System > About Ubuntu

**Command Line:**
    cat /etc/issue
    cat /etc/lsb-release

[https://help.ubuntu.com](https://help.ubuntu.com)

---

### Post by rraj.be on 2008-06-16
System->preferences-->About Devices

Just get here to get well introduced easily to Ubuntu

[[COLOR="Blue"]http://ubuntuguide.org/wiki/Ubuntu:Hardy[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

---

### Post by RomeReactor on 2008-06-16
Hi to find the version press the blue 'Help' button on the top panel adn press 'New to Ubuntu?'; or, open a terminal (Applications->Accessories->Terminal) and write or paste:
```
cat /etc/issue
```
or
```
cat /etc/lsb-release
```

To find which architecture you're running:
```
uname -m
```
If the output is **i386** or **i686**, it's 32 bits; if it's **x86_64**, then it's 64 bits.

---

### Post by jotnarta on 2008-06-16
Thank you buddy, I see that it's like pressing Ctrl+Alt+Del in Windows, what is the equivalent of this command in linux? (i.e. Is their any shortcut for this command like Ctrl+Alt+Del)?

---

### Post by _sphinx_ on 2008-06-16
OK so you what some shortcut for system-monitor ??

---

### Post by jotnarta on 2008-06-16
Thank you very much, it's valuable information, I have another simple question:

What is bach, tracsapplet, and sh?

---

### Post by RomeReactor on 2008-06-16
> **jotnarta said:**
> I see that it's like pressing Ctrl+Alt+Del in Windows, what is the equivalent of this command in linux? (i.e. Is their any shortcut for this command like Ctrl+Alt+Del)?

The gnome-system-monitor (System->Administration-> System Monitor) shows you which processes are running, how much memory is being used, and lets you end (or kill) processes.

EDIT: If you want to kill processes, you can make a button: Right-click on the top panel, select 'Add to panel...', double click on 'Custom Application Launcher' and fill it out like this:

Type: Application
Name:Xkill
Command:*xkill*
Comment: (leave empty if you wish)

Please note that killing applications isn't recommended.

---

### Post by hyper_ch on 2008-06-16
(1) ask different questions in seperated threads --> you can then mark the according therad solved when it's solved

(2) use a descriptive topic title that reflects the content of the thread/problem/question. Don't use a generic title like "noob here" or "help needed"

---

