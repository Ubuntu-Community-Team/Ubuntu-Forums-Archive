---
title: "Samba Passwords"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by andperry on 2012-05-08
I've just installed Ubuntu 12.04 Server to use on a home network where most of the computers are running Windows. Because of the idiosyncracies of Windows, there needs to be a Samba user with a matching username and password to all the other computers (otherwise Windows asks for the login credentials every time, which is not desirable in the given situation).

This has posed a problem because my main login name is the same on all computers, but I need to have a different password on the Ubuntu server from the other computers. I have tried setting up the Samba user with a password to match the Windows machines - this is fine until the next reboot, at which point the Samba password is changed to match the password of the main user account.

I thought that Samba users were managed separately from normal system users, but perhaps this is not the case.

Is there any way round this?

---

### Post by CharlesA on 2012-05-08
How are you adding the samba user?

I use:

```
smbpasswd -a username
```

---

### Post by andperry on 2012-05-08
Yes, I'm doing the same.

---

### Post by CharlesA on 2012-05-08
Do you have a system user of that same name? They don't need to have a password set.

---

### Post by andperry on 2012-05-08
Yes I do have a system user of the same name. I'm trying to have a system user and Samba user with the same name but different passwords. From what is happening, it appears that maybe that can't be done - if that is the case then I just need to know so that I can decide how to work round the situation.

---

### Post by Morbius1 on 2012-05-08
> I have tried setting up the Samba user with a  password to match the Windows machines - this is fine until the next  reboot, at which point the Samba password is changed to match the  password of the main user account.
See if you have the following package installed: **libpam-smbpass**

If it's installed remove it:
```
sudo apt-get remove libpam-smbpass
```
It's only function in life is to override whatever you set with smbpasswd with the Linux user's login password at every reboot.

---

### Post by CharlesA on 2012-05-08
Thanks for the tip Morbius. I checked my 12.04 box and it doesn't have that package installed. I installed samba via:

```
sudo apt-get install samba
```

---

### Post by Morbius1 on 2012-05-08
It used to be installed automatically ( together with samba ) the very first time someone used nautilus-share ( creating samba shared from Nautilus ). It's actually worse than I described it. What it does at every reboot is automatically assign a samba password that matches a login user's password automatically even if you had no intention of setting a samba password for that user. Insane.

Anyway it's the only thing I could think of that matches the OP's symptoms.

---

### Post by CharlesA on 2012-05-08
Oh nasty. I haven't used Nautilus for sharing in a long while, and I am glad I haven't.

Hopefully that clears up the OP's problem.

Thanks again!

---

### Post by andperry on 2012-05-08
Thanks for the hints. I've uninstalled libpam-smbpass and it seems to have sorted the problem. 

I've not had this problem previously with Ubuntu Desktop installations, but this will presumably be because Samba was installed with a simple "sudo apt-get install samba" command. This is my first Server installation and I installed Samba by selecting it when the list of add-ons is presented during the main installation sequence. The offending package is presumably slipped in at that point.

Anyway, many thanks.

---

