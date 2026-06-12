---
title: "[SOLVED] Forgotten password"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by RefinersFire on 2008-05-18
Oops. I changed my passwords and forgot them :(. I need the root password so I could change the other passwords too. One possible problem is, I have some important files on the root desktop. I thought about using the live install CD, but I don't want to lose the files on my desktop.

Ouch, this lowers my IQ a few notches. I hope my friends don't find out about this or I will never hear the end of it.

May someone please help me get into my root desktop?

Thank you.

---

### Post by kellemes on 2008-05-18
> **RefinersFire said:**
> Oops. I changed my passwords and forgot them :(. I need the root password so I could change the other passwords too. One possible problem is, I have some important files on the root desktop. I thought about using the live install CD, but I don't want to lose the files on my desktop.

Ouch, this lowers my IQ a few notches. I hope my friends don't find out about this or I will never hear the end of it.

May someone please help me get into my root desktop?

Thank you.

Read this.. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
You don't need a rootpassword on Ubuntu, you better use "sudo".
Why have you created a root account to begin with?
Anyway.. just cd /root and work with it using "sudo"..
```
sudo mv file filebackup
sudo cp file /location/file
sudo rm -r directory

```etc..

Edit: In order to work graphically you can open nautilus using root privileges like so..
```
gksudo nautilus
```

---

### Post by RefinersFire on 2008-05-18
I am looking at a login screen and I can go no further.

The reason why I have a root login is because there were a couple of programs I could not install otherwise.

I need to get to a desktop.All of my passwords changed.

---

### Post by quelx on 2008-05-18
the suggestions here should serve you well, namely the 2nd post, once in revoery mode do a ```
passwd username
``` where username is your login

[https://answers.launchpad.net/ubuntu/+question/8906](https://answers.launchpad.net/ubuntu/+question/8906)

---

### Post by RefinersFire on 2008-05-18
Here is the issue. When I hit Esc at GRUB, I am eventually brought to a graphical interface that says,

Recovery Menu
[[img=http://img140.imageshack.us/img140/1259/080518000cs5.th.jpg]](http://img140.imageshack.us/my.php?image=080518000cs5.jpg)

Then when I select root and hit Enter, I see a message under the graphical interface that says,

Give root password for maintenance
(or type Control-D to continue):_


Either I am just not "getting it" or my GRUB is different then the instructions being given.

---

### Post by aysiu on 2008-05-18
You can only select the option to drop to a root shell if you never set a root password or if you know the root password you set.

What you'll have to do is boot a live CD, mount your Ubuntu partition, and then [manually edit the /etc/shadow file to allow your *sudo* user to temporarily have a blank password](http://ubuntuforums.org/showthread.php?t=513820&highlight=passwordless+account) (you can change this to a real password later).

---

### Post by RefinersFire on 2008-05-19
Praise God! It worked.

Thank all of you who posted a reply.

---

