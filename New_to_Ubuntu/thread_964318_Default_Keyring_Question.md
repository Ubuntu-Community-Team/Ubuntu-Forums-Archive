---
title: "Default Keyring Question"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by fdepinto on 2008-10-30
Newbie here.  I just installed 8.10 today and when I boot up the computer, here's the message I get:

"Enter password for default keyring to unlock.  The app 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked"

When I enter my password, everything works fine. 

Here's my question:  Is there any way to bypass this request for my password, or do I have to enter it every time I boot up?

Thanks in advance.

---

### Post by clancymf on 2008-10-30
I get it too...

Its for access to your wireless router.  I havent looked for a way around it since its one password when you start up.

edit...
check this out= [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

---

### Post by dlodge on 2008-10-30
> **fdepinto said:**
> Newbie here.  I just installed 8.10 today and when I boot up the computer, here's the message I get:

"Enter password for default keyring to unlock.  The app 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked"

When I enter my password, everything works fine. 

Here's my question:  Is there any way to bypass this request for my password, or do I have to enter it every time I boot up?

Thanks in advance.
The PAM method didn't work for me. The easiest solution is to set a blank password for the default keyring.  The method of doing this varies by Ubuntu version. Prior to 8.10 you went through System->Preferences->Encryption and Keyrings or typing 'gksudo seahorse&' in a terminal (without quotes). This didn't work for me in 8.10, so I did the following instead.

Delete the default keyring files in ~/.gnome2/keyrings/ and restart - you will have to re-enter your wireless password, then you will be prompted to set a new password for the default keyring. Click ok without typing a password when prompted and agree that you want to use an unsafe password.

I expect a more elegant solution can be found through System->Administration-Authorizations->network-manager-settings, but I could not get this to work.

---

### Post by dahlenw on 2008-11-08
> **dlodge said:**
> The PAM method didn't work for me. The easiest solution is to set a blank password for the default keyring.  The method of doing this varies by Ubuntu version. Prior to 8.10 you went through System->Preferences->Encryption and Keyrings or typing 'gksudo seahorse&' in a terminal (without quotes). This didn't work for me in 8.10, so I did the following instead.

Delete the default keyring files in ~/.gnome2/keyrings/ and restart - you will have to re-enter your wireless password, then you will be prompted to set a new password for the default keyring. Click ok without typing a password when prompted and agree that you want to use an unsafe password.

I expect a more elegant solution can be found through System->Administration-Authorizations->network-manager-settings, but I could not get this to work.

Just wanted to say thank you.  Installed 8.10 about a week ago and haven't been able to get that stupid password keyring request to go away.  The above finally worked for me.  Thank you!

---

