---
title: "Facing 2 Problems on Ubuntu 13.10 on Lenovo W530"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by abhishes on 2013-12-10
I finally decided to take the plunge and formatted my windows 8.1 (could not tolerate the new metro UI anymore) and replaced it with Ubuntu 13.10

Last 2 days have been spent with only 3 hours of sleep and merciless googling. but the bring side is that I have configured vmware, citrix receiver, chrome, skype and even fingerprint-ui on my machine.

It works great but I am facing two problems (and I have done alot of googling before posting here).

1. when i do finger print login. I get an password prompt saying I need to enter password for login keyring.

I have searched the web and most solutions say that I need to go to "passwords and keys" and then either use the same password for login keyring or blank password. The problem is that most solutions are for old versions of ubuntu and the new version does not have the same UI options.

They say "right click on the folder called Passwords" .... but in 13.10 there is nothing in "passwords and keys" called the password folder. See attached.

there is nothing to right click. Also I clicked on + sign and saw two options. when I click on "password keyring" it asks me the name of a keyring. I tried putting the name of "login" and "gnome-ring" and I tried blank password and same password as my account. I also tried selecting "stored passwords" and then tring to enter a blank password... and the same password as my login id... 

But nothing seems to make the password prompt go away... nothing.

Can anyone give me the exact steps for "13.10" version because most blogs talk about older versions.

2. When I put down the lid of my machine, the fan keeps running. Again, the internet is full of this complain but everything is talking about old versions of Ubuntu. I want to know what are the steps for 13.10 to ensure that the fan shuts down when I put the lid down.

Thanks for your help and not "immediately" closing this as duplicate or flaming me for being ignorant. (i have done so much of googling on ubuntu in the last few days that google's revenue must have gone up).

Other than this... thanks to so many utilities on ubuntu. I have successfully configured skype, citrix receiver, vmware workstation, chrome, and everything is working very well for me.

---

### Post by sandyd on 2013-12-10
> **abhishes said:**
> I finally decided to take the plunge and formatted my windows 8.1 (could not tolerate the new metro UI anymore) and replaced it with Ubuntu 13.10

Last 2 days have been spent with only 3 hours of sleep and merciless googling. but the bring side is that I have configured vmware, citrix receiver, chrome, skype and even fingerprint-ui on my machine.

It works great but I am facing two problems (and I have done alot of googling before posting here).

1. when i do finger print login. I get an password prompt saying I need to enter password for login keyring.

I have searched the web and most solutions say that I need to go to "passwords and keys" and then either use the same password for login keyring or blank password. The problem is that most solutions are for old versions of ubuntu and the new version does not have the same UI options.

They say "right click on the folder called Passwords" .... but in 13.10 there is nothing in "passwords and keys" called the password folder. See attached.

there is nothing to right click. Also I clicked on + sign and saw two options. when I click on "password keyring" it asks me the name of a keyring. I tried putting the name of "login" and "gnome-ring" and I tried blank password and same password as my account. I also tried selecting "stored passwords" and then tring to enter a blank password... and the same password as my login id... 

But nothing seems to make the password prompt go away... nothing.

Can anyone give me the exact steps for "13.10" version because most blogs talk about older versions.

2. When I put down the lid of my machine, the fan keeps running. Again, the internet is full of this complain but everything is talking about old versions of Ubuntu. I want to know what are the steps for 13.10 to ensure that the fan shuts down when I put the lid down.

Thanks for your help and not "immediately" closing this as duplicate or flaming me for being ignorant. (i have done so much of googling on ubuntu in the last few days that google's revenue must have gone up).

Other than this... thanks to so many utilities on ubuntu. I have successfully configured skype, citrix receiver, vmware workstation, chrome, and everything is working very well for me.

1.Go to
Passwords & Keys ->VIew (menu) -> by Keyrings

Now, right click on Login and default and change the password on both to your login password.

---

