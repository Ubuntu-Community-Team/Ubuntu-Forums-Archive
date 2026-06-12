---
title: "Using Ubuntu As Root"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by JumpForJoy on 2008-11-13
Is there anything good/bad about using Ubuntu as the root?  I just installed a fresh copy and I was wonder.  As I said, a clean copy, so I don't have to worry about moving any files out of the root.  Thanks.

---

### Post by Tak11 on 2008-11-13
> **JumpForJoy said:**
> Is there anything good/bad about using Ubuntu as the root?  I just installed a fresh copy and I was wonder.  As I said, a clean copy, so I don't have to worry about moving any files out of the root.  Thanks.

root is just an administrative account, if you run everyday programs, *that don't require root* like xchat, etc. It can screw your sistem up, or become a security thret.

only run root when you need it, *ie to install a package etc.

---

### Post by beercz on 2008-11-13
Read [this]("https://help.ubuntu.com/community/RootSudo")

---

### Post by JumpForJoy on 2008-11-13
Ok, Thank you.  I will make a new account as soon as I can.

---

### Post by taurus on 2008-11-13
> **JumpForJoy said:**
> Ok, Thank you.  I will make a new account as soon as I can.

Didn't you create one during the installing process?

---

### Post by JumpForJoy on 2008-11-13
> **taurus said:**
> Didn't you create one during the installing process?
Ok.  I see, I assumed this was the root, because I caouldn't login as the root.  I see my large misstake here.  so is it safe to use the file I created during installation?  Thanks.

---

### Post by taurus on 2008-11-13
Yes, use the username and password that you created during the installing process.  That's your account to use.  And if you need root privilege to install, modify, or delete something, then put sudo in front of the command and use the same password that you log in with.  No need to create another account for you.

---

### Post by benhur99ph on 2008-11-13
Do not use the root account unless it is really needed. Using root account can cause damage to your system and become a security threat (as previously said).

That is why ubuntu disables the use of the root account by default. If you really want to use it then go to System>Administration>Login Window and under the Security tab, check the "Allow local Administrator login" checkbox. Then go to System>Administration>Users and Groups and set the password for the root account.

---

### Post by JumpForJoy on 2008-11-13
> **taurus said:**
> Didn't you create one during the installing process?

> **benhur99ph said:**
> Do not use the root account unless it is really needed. Using root account can cause damage to your system and become a security threat (as previously said).

That is why ubuntu disables the use of the root account by default. If you really want to use it then go to System>Administration>Login Window and under the Security tab, check the "Allow local Administrator login" checkbox. Then go to System>Administration>Users and Groups and set the password for the root account.

Thank You.  I will continue to use the acount set up when I installed Ubuntu.

---

### Post by Kellemora on 2008-11-13
Hi JFJ

IF you do reset-up your system, this is the best time to set up a SEPARATE PARTITION as your /home partition (home is where ALL of your user data and settings are stored).

Makes for easy backup and also, should you upgrade, you don't chance losing all your settings and data, nonetheless, you should still backup before doing an upgrade just to be safe.

TTUL
Gary

---

### Post by JumpForJoy on 2008-11-14
> **Kellemora said:**
> Hi JFJ

IF you do reset-up your system, this is the best time to set up a SEPARATE PARTITION as your /home partition (home is where ALL of your user data and settings are stored).

Makes for easy backup and also, should you upgrade, you don't chance losing all your settings and data, nonetheless, you should still backup before doing an upgrade just to be safe.

TTUL
Gary

I wasn't planning on, I could make a new empty partition, but how do I but my backup files in it?

---

### Post by taurus on 2008-11-14
If you have a new empty partition and you want to be able to write to it, the easiest way is to change the ownership of that directory from root to to your login name.  Then, you can write to it anytime you want without using sudo/gksudo.  

Where do you mount that new partition and what is the filesystem of it?

```
cat /etc/fstab
mount
```

---

### Post by JumpForJoy on 2008-11-14
> **taurus said:**
> If you have a new empty partition and you want to be able to write to it, the easiest way is to change the ownership of that directory from root to to your login name.  Then, you can write to it anytime you want without using sudo/gksudo.  

Where do you mount that new partition and what is the filesystem of it?

```
cat /etc/fstab
mount
```

I don't have an empty partition, but I can make one.(should I)  How do I change the ownership of a partition?  What's fstab?  What does mounting do?  I'm a newbie, thanks.

---

