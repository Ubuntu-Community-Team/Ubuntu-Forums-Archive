---
title: "[SOLVED] how do i avoid having to enter my keychain password on login?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by leemajors on 2008-09-15
hey,

whenever i log in, the wireless network connection requires me to enter my keychain password before it will properly connect.

any way i can just have it connect without needing my input?

thanks

---

### Post by y-lee on 2008-09-15
I don't know if this will help but you might want to see [Wireless password keychain]("https://answers.launchpad.net/ubuntu/+question/5643"), it is a bit dated but should still work.

---

### Post by MegaJim on 2008-09-15
If your deafuault keyring has the same password as your user account you only need to grant the application access to your keyring rather than type your password each time.

Launch the encryption and passwords manager by hitting alt+f2 then typing:
```
seahorse-preferences
```
now select the "login" keyring and change the unlock password to match your login password.

Now it should no longer ask you for your password when connecting to the wlan, as long as you give network manager (or whatever program you use to connect) access to your keyring.

**NOTE:** this won't take effect until your next login.

---

### Post by leemajors on 2008-09-17
great! now how do i give network manager access to my keyring?

---

### Post by lisati on 2008-09-17
> **leemajors said:**
> hey,

whenever i log in, the wireless network connection requires me to enter my keychain password before it will properly connect.

any way i can just have it connect without needing my input?

thanks
Have a look [here]("http://ubuntuforums.org/showthread.php?t=748934")

---

### Post by leemajors on 2008-09-19
Yeah, I had seen that post when I searched for answers. It sort of doesn't really help -- seems like it installs another piece of software to bypass something I should just be able to do with some permissions.

MegaJim's post suggesting I give network manager access to my keyring sounds perfect -- but I've been looking through all my settings trying to figure out how to do this and it's not apparent....

---

### Post by MegaJim on 2008-09-19
Seahorse should prompt you to allow it access, however if it doesn't you can launch seahorse and go to the passwords tab, one of the items in that list will be your wireless password; right click -> properties, switch to applications tab and nm-applet should be listed with read/write/delete access.

As long as everything else is configured as a standard 8.04 install with the login keyring having same password as your user account and selected as the location for application passwords, it should not ask for your password (but it might ask permission to save a new key).  It will also ask for the password again after resume from hibernate as keys are purged from ram on hibernate to avoid a potential security breach.

---

### Post by crjackson on 2008-09-19
I change mine to a blank (i.e. no password) and save.  Works for me on Hardy.

---

### Post by aysiu on 2008-09-19
> **leemajors said:**
> Yeah, I had seen that post when I searched for answers. It sort of doesn't really help -- seems like it installs another piece of software to bypass something I should just be able to do with some permissions.

MegaJim's post suggesting I give network manager access to my keyring sounds perfect -- but I've been looking through all my settings trying to figure out how to do this and it's not apparent....
I believe that's what libpam-keyring does, though.

Alternatively, you can use WICD instead of Network Manager. That's the only way on an autologin that I've been able to not have a prompt for a keychain password.

---

### Post by MegaJim on 2008-09-20
That raises a good point aysio, If the opo is using automatic login, he will still need to enter his password at least once.

---

### Post by leemajors on 2008-10-03
so how then is that an automatic login??

---

### Post by leemajors on 2008-12-14
having searched for a way of doing this, i've found a cool replacement for the network manager, which despite all of your help and my searching never actually let me sign in automatically without entering my keychain password.

it's Wicd, a third party network manager; apparently it'll be in the official repos for jaunty but until then, go here:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

thanks everyone for your advice!

---

### Post by clive littlewood on 2008-12-14
Hi

Just quick note for future ref.

On initial install the keyring will ask for network permission.

Just enter without putting in a password, it will advise of security issues, agree and enter, you will not be asked for password again.   :p

Hope this helps.

Clive

---

