---
title: "Log-in Password requested?"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by James_Horvath on 2014-04-13
Hi,

I choose AUTO Login, so I did not enter a Password, yet now when I try to log in I'm asked for a password? 

Note: this was a new clean install of Ubuntu 12.04.4 LTS.

Help Please!

---

### Post by buzzingrobot on 2014-04-13
If you log out manually, you will be asked for the password when you log in again.

If you reboot and autologin is set correctly, you should not be asked for your password.

---

### Post by James_Horvath on 2014-04-13
Hi,

Thanks for the reply. My keyboard was having a problem during Install, My name I now see is spelled wrong, I tried all my passwords I use and still no luck. I going to do another Install. I will put in a Password that way I will know it.

---

### Post by deadflowr on 2014-04-13
No need to reinstall, and chuck the sponge.
Follow this to set/reset your password
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Make note to follow the mount command exactly, or it might not take hold to change from read-only to read/write.
Also note that the password field will probably be empty when filled, so don't think it's not working.
It's just invisible.

---

### Post by James_Horvath on 2014-04-13
Hi Deadflowr,

Thank you, I bookmarked the URL, I did a reinstall and now all is well. :P

---

### Post by trag on 2014-04-14
In order to remove the Unlock Login Keyring dialog set the password for the keyring to an empty password. This prevents being prompted for a password. 


[LIST=1]
[*]Open Applications --> Accessories -->Password and Encryption Keys
[*]Right-click on the "login" keyring
[*]Select "Change Password"
[*]Enter your old password and leave the new password blank
[*]Press ok, read the security warning, think about it and if you still want to get rid of the Unlock Login Keyring dialog, choose "use unsafe storage"
[/LIST]
As the message states: This will expose all passwords saved in the keyring (e.g. email passwords) to anyone using your computer or having access to your files and is not recommended.

---

### Post by deadflowr on 2014-04-14
> **trag said:**
> In order to remove the Unlock Login Keyring dialog set the password for the keyring to an empty password. This prevents being prompted for a password. 


[LIST=1]
[*]Open Applications --> Accessories -->Password and Encryption Keys 
[*]Right-click on the "login" keyring 
[*]Select "Change Password" 
[*]Enter your old password and leave the new password blank 
[*]Press ok, read the security warning, think about it and if you still want to get rid of the Unlock Login Keyring dialog, choose "use unsafe storage" 
[/LIST]
As the message states: This will expose all passwords saved in the keyring (e.g. email passwords) to anyone using your computer or having access to your files and is not recommended.

Of course the rub is knowing the old password, or having a password.
Which is what this thread is/was actually about.

Mangling your security by disabling the keyring settings is something of a different story.

---

