---
title: "Login Keyring and Administrators Password(s)"
date: 2014-10-30
forum: New to Ubuntu
---

### Post by David_C._Hallam on 2014-10-30
What is this keyring I am asked to login to when I first boot?  I have a password for it.  Also I have tried to do other things that ask for the administrators pasword (sudo).  I don't ever remember to set an aministrators pasword.  Where.how do I do that?

---

### Post by CantankRus on 2014-10-30
GNOME Keyring is integrated with the user's login, so that their secret storage 
can be unlocked when the user logs into their session.
If you use automatic login, the keyring is not unlocked at login.
When an application needs access to the keyring you are prompted for the password. Some web browsers and applications store your passwords here.

The admin and keyring password should be the same, and is what you entered in the install process.
[ATTACH=CONFIG]257626[/ATTACH]

You can either goto "User Accounts" and turn off automatic login

**[SIZE=3]or[/SIZE]**

goto "Passwords and keys", right click on the Login keyring and select change password.
Enter the current password then leave the new password fields blank.

The second option makes your system less secure.

---

### Post by David_C._Hallam on 2014-10-30
When I was asked for the administrator's password, I used the same one as for login keyring.  It was not accepted.

---

### Post by David_C._Hallam on 2014-10-30
When I was asked for the administrator's password, I used the same one as for login keyring.  It was not accepted.

---

### Post by CantankRus on 2014-10-31
> **David_C._Hallam said:**
> When I was asked for the administrator's password, I used the same one as for login keyring.  It was not accepted.

If you have forgotten your admin password you will need to do as in the following guide.
[**_[COLOR="#B22222"]How to reset your password in Ubuntu[/COLOR]_**]("http://psychocats.net/ubuntu/resetpassword")

If this is a fairly new install and depending on your Linux experience it may be easier for you to  backup and reinstall ...noting your password.
It's up to you what you do but following the guide is a good learning experience.

---

### Post by David_C._Hallam on 2014-10-31
How do I complete remove Linux from my computer?  I got a book on Ubuntu Linux but never seem to be able to find any reference to what I am looking for. I am not sure where in my computer Linux resides.  When I installed, I tried to partition my C: and install in the new partition.  That didn't happen.  It appears to have created a new partition my D: and installed itself there.  As I understand things Linux has written a new MBR and if Linux is removed I will not be able to open Windows because there is no MBR.

---

### Post by CantankRus on 2014-10-31
> **David_C._Hallam said:**
> How do I complete remove Linux from my computer?  I got a book on Ubuntu Linux but never seem to be able to find any reference to what I am looking for. I am not sure where in my computer Linux resides.  When I installed, I tried to partition my C: and install in the new partition.  That didn't happen.  It appears to have created a new partition my D: and installed itself there.  As I understand things Linux has written a new MBR and if Linux is removed I will not be able to open Windows because there is no MBR.
That's right you need to fix the mbr.
What version of Windows do you have?

See [**_[COLOR="#B22222"]RestoreUbuntu/XP/Vista/7Bootloader[/COLOR]_**]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader")

...and you may want to read this if you try again...
[**_[COLOR="#B22222"]A home user’s successful migration strategy from Windows to Ubuntu[/COLOR]_**]("http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/")

---

