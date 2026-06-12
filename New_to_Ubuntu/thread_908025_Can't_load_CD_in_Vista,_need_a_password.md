---
title: "Can't load CD in Vista, need a password???"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Redptc on 2008-09-02
I try to run the Hardy CD in order to install Ubuntu but I'm asked for a 'password'? It is not the password used in Vista, it must be an Ubuntu password.

Is it just me? Does any body know?

---

### Post by windozehater on 2008-09-02
are you talking about using wubi, or running the live system from a restart

---

### Post by pmlxuser on 2008-09-02
ubuntu live Cd password

username:ubuntu
password:ubuntu

but i would think that is not the case it must be windows password for admin to install something (are you sure you have the right to install something in windows as admin)

---

### Post by Redptc on 2008-09-02
When I put the CD in the drive and start the PC up again it goes directly to Windows Vista, it doesn't boot from the disk. The instructions included with the Ubuntu disk indicates that you can run it in Windows but when that is tried I get asked for a password. It is not the password used in Vista because that doesn't work it must be a password for the Ubuntu CD?

I really want to know how to get Ubuntu running on this Laptop!

---

### Post by sstusick on 2008-09-02
You need to go into your BIOS and make sure the CD-ROM is first in the boot order.

You can get into your BIOS by pressing one of the following keys as soon as the computer turns on: F1, F2, DEL, ESC, F10. It could be any one of these, so try them all. 

Good luck.

---

### Post by Redptc on 2008-09-02
Thanks mate! It seems to be doing the job.

---

### Post by merck906 on 2008-09-02
You might have a faulty disc. Make sure your bios lets you boot from a CD/DVD drive. If you want to install inside of vista, make sure you are logged on to the administrator account for vista first.

---

### Post by fidamehran on 2008-09-02
If you are completely new to Ubuntu &/or Linux, booting from Live CD and using disk partitioning might be a headache for you. In that case you might try the Wubi built in in the CD. Wubi is a Windows based installer for Ubuntu, which installs Ubuntu just like any other Windows program. You can even uninstall Ubuntu later through Add/Remove.

---

### Post by fidamehran on 2008-09-02
> **Redptc said:**
> I try to run the Hardy CD in order to install Ubuntu but I'm asked for a 'password'? It is not the password used in Vista, it must be an Ubuntu password.

Is it just me? Does any body know?

And I really think you were running the CD from within Windows and the Wubi started up. In that case, all you had to do is put in a user name and password of your choice. That username and password would be used as the user account for Ubuntu when it finally finished installing.

---

### Post by fidamehran on 2008-09-02
> **fidamehran said:**
> If you are completely new to Ubuntu &/or Linux, booting from Live CD and using disk partitioning might be a headache for you. In that case you might try the Wubi built in in the CD. Wubi is a Windows based installer for Ubuntu, which installs Ubuntu just like any other Windows program. You can even uninstall Ubuntu later through Add/Remove.

Oops, didn't see your profile. Looks like you've been around at the Ubuntuforum for quite some time now. So you should know by now all that I told you.

---

### Post by Redptc on 2008-09-02
Thanks for your interest, my first instal of Ubuntu was seamless and easy. I have a new, additional PC running Vista. I needed to be reminded how it is done!

I want to install Hardy in a dual boot situation and this means I will have to change the boot order in Vista's bios. So far i have not able to 'locate' the bios to change things.

I pulled out of a Wubi instal because I will not use Vista very much once I get Hardy up & running.

---

### Post by Muflon on 2008-09-02
Hi

You need to change the boot order of your PC in the computer BIOS.  There is no such thing as a Vista BIOS.

This link should help

[https://help.ubuntu.com/8.04/installation-guide/i386/pre-install-bios-setup.html#boot-dev-select](https://help.ubuntu.com/8.04/installation-guide/i386/pre-install-bios-setup.html#boot-dev-select)

Muflon

---

### Post by Redptc on 2008-09-03
Thanks, Muflon, all up and running and no obvious tweaking required just yet!

---

