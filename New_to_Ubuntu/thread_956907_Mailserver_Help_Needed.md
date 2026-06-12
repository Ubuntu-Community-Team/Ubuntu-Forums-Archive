---
title: "Mailserver Help Needed"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by insub2 on 2008-10-23
Hello,

I have a working Apache2/MySQL/PHP server on my laptop for testing out websites that I'm building but I need email support!  I only need it to send email from PHP scripts.  No webmail client (like squirrelmail) or anything.

Everything I've found so far is so complicated and has way too much stuff.

---

### Post by Dr Small on 2008-10-23
All you should have to install is the package 'mailutils' with:
```
sudo apt-get install mailutils
```

---

### Post by prematurebaby on 2008-10-23
Is it an outgoing sftp server you need? If so just use the gmail one.

---

### Post by insub2 on 2008-10-23
> **prematurebaby said:**
> Is it an outgoing sftp server you need? If so just use the gmail one.

How?

---

### Post by insub2 on 2008-10-23
> **Dr Small said:**
> All you should have to install is the package 'mailutils' with:
```
sudo apt-get install mailutils
```

This didn't work.  Do I need to restart anything?  or do some configuration?

---

### Post by Dr Small on 2008-10-23
> **prematurebaby said:**
> Is it an outgoing sftp server you need? If so just use the gmail one.
What does SFTP have to do with a mailserver?

---

### Post by insub2 on 2008-10-23
> **insub2 said:**
> This didn't work.  Do I need to restart anything?  or do some configuration?

Had to install Postfix also.  Just did it through Synaptic.
It seems to be working now.

---

