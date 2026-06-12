---
title: "Ubuntu 20.04 automaticaly command before login"
date: 2022-02-12
forum: New to Ubuntu
---

### Post by nyunity on 2022-02-12
Hello @all!

I installed Ubuntu 20.04 on my HP T630. Works fine, WoL activated and also works fine.

So, when I wakre up my Thin-Client from LAN, I do not want to login in. Is it possible to make a command line automaticaly when boot is finished and it is ready to login?

Do you know what I mean?

thx,

Erik

---

### Post by him610 on 2022-02-12
You can "ssh user@ip_address" which will open up up a terminal with command line.

---

### Post by MAFoElffen on 2022-02-13
On server:
```

sudo systemctl edit getty@tty1.service

```
This will  create a drop-in file (if neccessary) and open it an editor. Add the following, replacing 'myusername' with your username:
```

[Service]
ExecStart=
ExecStart=-/sbin/agetty --noissue --autologin myusername %I $TERM
Type=idle

```
On boot, will login automatically to the named user, in vtty1...

---

### Post by Jaxilian on 2022-02-15
> **nyunity said:**
> Hello @all!

I installed Ubuntu 20.04 on my HP T630. Works fine, WoL activated and also works fine.

So, when I wakre up my Thin-Client from LAN, I do not want to login in. Is it possible to make a command line automaticaly when boot is finished and it is ready to login?

Do you know what I mean?

thx,

Erik

You can add code at the bottom of the file /etc/gdm3/PreSession/Default
It runs as root though

---

### Post by MAFoElffen on 2022-02-15
> **nyunity said:**
> I installed Ubuntu 20.04 on my HP T630. Works fine, WoL activated and also works fine.

So, when I wake up my Thin-Client from LAN, I do not want to login in. Is it possible to make a command line automatically when boot is finished and it is ready to login?

He didn't say which Edition of Ubuntu 20.04 he installed, but does say it is thin client, and is started via WOL...

> **him610 said:**
> You can "ssh user@ip_address" which will open up up a terminal with command line.
For a passwordless ssh login into, you would copy over the rsa fingerprint of the source computer to the target, so it would not ask for the password for that user...

> **Jaxilian said:**
> You can add code at the bottom of the file /etc/gdm3/PreSession/Default
It runs as root though
That would not log him/her in as a user... The first post, though the OP did not say which Edition they were running did not mention if they were running a GUI Desktop...

You mention GDM, which would mean a Graphical Desktop would need to be there... It here was, the correct way to do that would be to edit the /etc/gdm3/custom.conf file... Go to the section "# Automatic Login" and uncomment the next two lines, then edit the user line with the correct username...
```

# Automatic Login
      AutomaticLoginEnable = true
      AutomaticLogin = MyUserName

```
But in the first post, he said WOL, which would be sending a remote wakeup packet to a remote computer to wake it up. Then he mentions both thin client, and a commandline type of solution to automatically login... This leads me to an assumption that it might not have a GUI, and they want a console solution, which console boots to vtty1...

I admit, the first post did not get into many details... The ssh solution above, with the addition of a RSA Key copied to the target thin-client image may work just fine... As WOL does imply that it is woken up remotely, and may just be connected remotely also. No one has to be logged in 'locally' for that to work.

But now the OP has 3 solutions...

---

