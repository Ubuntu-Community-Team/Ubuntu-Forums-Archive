---
title: "how the kernel intimates about hibernate??"
date: 2011-03-24
forum: Programming Talk
---

### Post by vishy.palepu on 2011-03-24
Hi,
I am software developer. 
I have a requirment where I have to store some data before the system goes to hibernate. 
How the kernel intimates to the application when it goes to hibernate. 
Is there any event or a signal that kernel posts to all applications???
I need to write an application in user level.
Please help me out

---

### Post by Zugzwang on 2011-03-24
As a starter to your search for solutions, consider checking if you can achieve your goal via using the DBUS protocol: [http://www.linuxjournal.com/article/10455?quicktabs_1=1](http://www.linuxjournal.com/article/10455?quicktabs_1=1)

---

### Post by kostkon on 2011-03-24
Yes, a language agnostic solution would be to use the DBus interface of [*UPower*]("http://upower.freedesktop.org/") (or if you want, use the *libupower-glib-dev lib* if you are coding in C/C++) and listen for the *sleeping* signal
> This signal is sent when the session is about to be suspended or hibernated. Session and system programs have one second to do anything required before the sleep action is taken (such as sending out Avahi or Jabber messages).


[*d-feet*]("http://packages.ubuntu.com/maverick/d-feet") will help you view and test the UPower dbus interface before writing your code.

Hope that helps.

---

