---
title: "How do I turn off ALL requests for passwords?"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by davidc60 on 2012-01-31
Hi,
 I am presently running Ubuntu 11.10 (from a USB) as the Administrator. I routinely receive messages asking for 'authentication' with my password, sometimes even for the most routine/mundane tasks. I need to be able to use the system without all of these requests for passwords during routine usage. Can I amend the settings in order to achieve this (I have already turned off the log-in password in the User Accounts program but I still continue to receive requests for my password!) Thanks,
 davidc

---

### Post by snowpine on 2012-01-31
Can you give an example of a specific task for which you don't feel a password is necessary?

---

### Post by philinux on 2012-01-31
> **davidc60 said:**
> Hi,
 I am presently running Ubuntu 11.10 (from a USB) as the Administrator. I routinely receive messages asking for 'authentication' with my password, sometimes even for the most routine/mundane tasks. I need to be able to use the system without all of these requests for passwords during routine usage. Can I amend the settings in order to achieve this (I have already turned off the log-in password in the User Accounts program but I still continue to receive requests for my password!) Thanks,
 davidc

Please read all of this [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

And this.  [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Before you make any changes.

---

### Post by Dngrsone on 2012-01-31
I'm thinking you might want to switch to a different Linux distribution; one where you can log in as root.

---

### Post by davidc60 on 2012-01-31
Thanks for your reply. Normally I would do so but I only have a couple of USB's to boot from and work with at the moment (I had to clear my HDD a couple of days ago due to a problematic extended partition) and I am not sure what I need in Ubuntu or Linux Mint to be able to 'install' ISO's on to an USB (in anticipation of a full install to the HDD). I do have USB Creator, Unetbootin and USB Universal Installer on another USB but they won't run in either Ubuntu or Linux Mint - at least I can't get them to run. Thanks for your consideration anyway.
davidc

---

### Post by Dngrsone on 2012-01-31
[Damn Small](http://www.damnsmalllinux.org/)

[Creating bootable USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by restorator on 2012-01-31
> How do I turn off ALL requests for passwords?

Use Windows XP

Please read the post by philiunx

> Please read all of this [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

And this. [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Before you make any changes. 

---

### Post by Kixtosh on 2012-01-31
I'm wondering if davidc60 is using the Chromium or Chrome browsers. When I was using Chromium, I would keep getting messages asking me to unlock the keyring. This stopped (mostly, if not completely, I think) if I forced my computer to boot to a login screen instead of booting directly to the default user desktop. Otherwise, I'd keep having to unlock the keyring every time I visited a website that required a password to log in, such as e-mail websites. With Firefox, I don't get any of this behavior.

During normal use, I only have to use a password if I'm using the update manager, or synaptic package manager, and that isn't all that cumbersome (certainly a lot less so than keeping my Windows 7 installations up to date).

Is this the issue you're describing, davidc60? If not, please describe clearly when you are getting asked for passwords exactly.

---

### Post by Cheesemill on 2012-01-31
> **Kixtosh said:**
> I'm wondering if davidc60 is using the Chromium or Chrome browsers. When I was using Chromium, I would keep getting messages asking me to unlock the keyring. This stopped (mostly, if not completely, I think) if I forced my computer to boot to a login screen instead of booting directly to the default user desktop. Otherwise, I'd keep having to unlock the keyring every time I visited a website that required a password to log in, such as e-mail websites. With Firefox, I don't get any of this behavior.

During normal use, I only have to use a password if I'm using the update manager, or synaptic package manager, and that isn't all that cumbersome (certainly a lot less so than keeping my Windows 7 installations up to date).

Is this the issue you're describing, davidc60? If not, please describe clearly when you are getting asked for passwords exactly.

If you have set up auto logon you can remove prompts to unlock the keyring by setting a blank keyring password.

---

### Post by Dngrsone on 2012-01-31
The OP wants to work as root (in his words 'Administrator') and can't be bothered to put in a password every fifteen minutes or whatever.

He is assuming that Ubuntu works like Windows, which we all know is not the case, and that has been explained to him.

---

### Post by sanscents on 2012-01-31
> **Cheesemill said:**
> If you have set up auto logon you can remove prompts to unlock the keyring by setting a blank keyring password.

Is it possible to reset my Keyring password after-the-fact?  I'd like to make it blank.

---

