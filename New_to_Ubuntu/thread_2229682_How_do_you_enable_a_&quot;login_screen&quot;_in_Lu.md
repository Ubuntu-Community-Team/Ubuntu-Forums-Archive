---
title: "How do you enable a &quot;login screen&quot; in Lubuntu 14.04?"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by twalp on 2014-06-14
After installing the latest **Lubuntu **(14.04) in a re-purposed desktop PC *and *a VMware machine, both boot directly to Lubuntu's Desktop. (pardon if I use Windows terminology)  There's no Login screen or prompt despite the presence of a password, and in the **Users and Groups **| **Users Settings **window the setting for **Password **is "**Asked on login**".  

I would like to create a second password-protected User profile with an **account type **of "**Desktop user**".  The person using the physical PC will know only the "Desktop user" password so he'll have to choose that user at the Login screen (which I have yet to see but assume it's akin to Windows "Welcome" screen).

Please note that I created a second user in both systems, configured as "Desktop user", and set its password to "Asked on login"; but both systems still boot directly to the first user's Desktop. So I am asking *after *first having tried it. 

Is the current Lubuntu **Users and Groups **control panel faulty or at least partly impotent? How do I achieve my goal -- in *this *version of **Lubuntu **-- of having a Login screen with two users (the default/root one created during installation and another that has Desktop user" credentials)?

---

### Post by bapoumba on 2014-06-15
What are the outputs to :
```
sudo grep nopasswd /etc/gshadow
sudo grep nopasswd /etc/group
```

---

### Post by steeldriver on 2014-06-15
I'm pretty sure lubuntu now uses lightdm - so can you also post the outputs of

```

cat /usr/share/lightdm/lightdm.conf.d/50-autologin.conf

```

If no such file exists, try
```

cat /etc/lightdm/lightdm.conf.d/50-autologin.conf

cat /etc/lightdm/lightdm.conf

```

---

### Post by twalp on 2014-06-15
> **bapoumba said:**
> What are the outputs to :
```
sudo grep nopasswd /etc/gshadow
sudo grep nopasswd /etc/group
```

Thank you for replying bapoumba.

```
sudo grep nopasswd /etc/gshadow
nopasswdlogin:!::

sudo grep nopasswd /etc/group
nopasswdlogin:x:116:
```

---

### Post by twalp on 2014-06-15
> **steeldriver said:**
> I'm pretty sure lubuntu now uses lightdm - so can you also post the outputs of

```

cat /usr/share/lightdm/lightdm.conf.d/50-autologin.conf

```

If no such file exists, try
```

cat /etc/lightdm/lightdm.conf.d/50-autologin.conf

cat /etc/lightdm/lightdm.conf

```

Thank you for replying, also, steeldriver.

```

cat /usr/share/lightdm/lightdm.conf.d/50-autologin.conf
cat: /usr/share/lightdm/lightdm.conf: No such file or directory
cat: .d/50-autologin.conf: No such file or directory

cat /etc/lightdm/lightdm.conf
[SeatDefaults]
autologin-guest=false
autologin-user=jack
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

---

### Post by steeldriver on 2014-06-15
OK I suggest you edit your /etc/lightdm/lightdm.conf file to comment out the autologin-user parts - since I'm not familiar with the lubuntu GUI admin commands I can only suggest commandline methods - either

```

sudo nano /etc/lightdm/lightdm.conf

```

if you are comfortable editing system files in 'nano', or you can use this one-liner

```

sudo sed -i.bak 's/^autologin-user/#&/' /etc/lightdm/lightdm.conf

```

Then reboot (or just restart the lightdm service, if you prefer)

---

### Post by bapoumba on 2014-06-15
Just to say that outputs from #4 are normal, so not password setup problems here.
Thanks steeldriver :)

---

### Post by twalp on 2014-06-15
> **steeldriver said:**
> OK I suggest you edit your /etc/lightdm/lightdm.conf file to comment out the autologin-user parts - since I'm not familiar with the lubuntu GUI admin commands I can only suggest commandline methods - either

```

sudo nano /etc/lightdm/lightdm.conf

```

if you are comfortable editing system files in 'nano', or you can use this one-liner

```

sudo sed -i.bak 's/^autologin-user/#&/' /etc/lightdm/lightdm.conf

```

Then reboot (or just restart the lightdm service, if you prefer)

Merveilleux!  I now have control over the login screen in Lubuntu.  Any idea why **Users and Groups | Users Settings | Password_:Asked on login_** had no effect?

Thank you to steeldriver and bapoumba. \\:D/

---

### Post by bapoumba on 2014-06-15
Glad to see you got it to work :)
Please mark your thread as solved (under Thread tools), thanks.

---

