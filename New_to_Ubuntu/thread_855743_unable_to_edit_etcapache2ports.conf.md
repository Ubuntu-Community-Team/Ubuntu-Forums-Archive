---
title: "unable to edit /etc/apache2/ports.conf"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by moekernel on 2008-07-10
Hi:
I am new to ubuntu, I have the desktop with lamp installed.
I also have the firewall install.

However, when I try to change the port.conf file to:

LISTEN 127.0.0.1:80 

with text editor or bluefish I am unable to save the edited file.
I keep getting a no permission warning.

How can I edit this file?


This is what I am doing.
I have LAMP installed on my desktop version, so I can still use my laptop as a regular computer while having a test environment for lamp.

My fear is that I do not want my laptop to be open and been seen thru the internet. I do not want any ports open or any holes.

I read that to prevent that I need to change the ports file, is this all I have to do to keep my laptop secure with the lamp installed and running as a test environment?

Many thanks for your help.

I am really excited and happy with ubuntu!

---

### Post by Xerp on 2008-07-10
try:

```
sudo gedit /etc/apache2/ports.conf
```

---

### Post by iaculallad on 2008-07-10
> **Xerp said:**
> try:

```
sudo gedit /etc/apache2/ports.conf
```

It will be a good practice to use:

```
gksudo gedit /etc/apache2/ports.conf
```

since you're opening a GUI-based application. Use **sudo** when using vi or nano to edit configuration files.

```
sudo nano /etc/apache2/ports.conf
sudo vi /etc/apache2/ports.conf
```

---

### Post by moekernel on 2008-07-11
Fantastic!

Thanks

:KS:KS:KS:KS:KS

---

### Post by adldesigner on 2008-07-11
> **moekernel said:**
> Fantastic!

Thanks

:KS:KS:KS:KS:KS

May I suggest marking the thread as SOLVED? :)

---

