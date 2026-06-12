---
title: "Intrepid ThinkFinger"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by rossjman1 on 2008-11-13
In Hardy ThinkFinger worked perfectly, but when I upgraded to Intrepid I had to add a 3rd party source to solve the carriage return issue. However, Intrepid completely broke my internet, so I just did a clean install of Intrepid. Here is my problem, I have followed this tutorial:
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Intrepid](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Intrepid)
Here's a bug report about the --add-user problem:
[https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/203973](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/203973)

The bug report says to use
```
sudo /usr/lib/pam-thinkfinger/pam-thinkfinger-enable
```
But I don't have this file. GDM and all other password prompts still ask for my password when they should ask for my password "or swipe finger".

---

### Post by rossjman1 on 2008-11-13
bump

---

### Post by rossjman1 on 2008-11-13
bump

---

### Post by beercz on 2008-11-13
[http://ubuntuforums.org/showthread.php?t=760018&highlight=finger+print+reader](http://ubuntuforums.org/showthread.php?t=760018&highlight=finger+print+reader)

---

### Post by rossjman1 on 2008-11-13
Any suggestions to get ThinkFinger to work. I'm using Fprint - which works, but has issues. In Fprint GDM doesn't ask for password after entering the user name, it just says enter user name still. Gksudo (for like Synaptic) will ask for a password, and I can swipe my finger which works, but the window doesn't go away.

---

### Post by rossjman1 on 2008-11-13
bump

---

### Post by rossjman1 on 2008-11-14
anyone?

---

### Post by rossjman1 on 2008-11-15
So no one got ThinkFinger working in Intrepid?

---

### Post by bigbrovar on 2008-11-15
i added this repo to my sources.list 
deb [http://ppa.launchpad.net/jon-oberheide/ubuntu](http://ppa.launchpad.net/jon-oberheide/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/jon-oberheide/ubuntu](http://ppa.launchpad.net/jon-oberheide/ubuntu) intrepid main
 ran an update
sudo apt-get update

then updgraded my system 

sudo apt-get upgrade

rebooted and it worked just like it did in hardy

---

### Post by rossjman1 on 2008-11-15
No it doesn't. Exactly what I did.

---

### Post by rossjman1 on 2008-11-16
bump

---

### Post by rossjman1 on 2008-11-17
Ok. I am probably waisting my time since I never seem to get a lot of responses to my threads. Fprint is no good. How can I activate ThinkFinger? I already have it all set up. I already edited /etc/pam.d/common-auth.
Half the time Fprint doesn't work and half the times that it does work it does so very sloppily. I think Fprint is freezing Update Manager, so I have to update using the terminal. PLEASE HELP. I will keep bumping this.
```
jeff@jeff-laptop:~$ sudo apt-get update
fp:error [fp_dev_open] device initialisation failed, driver=upekts
[sudo] password for jeff: 
```

---

### Post by rossjman1 on 2008-11-17
bump

---

### Post by rossjman1 on 2008-11-17
bump

---

### Post by rossjman1 on 2008-11-18
bump

---

### Post by rossjman1 on 2008-11-18
bump, is anyone even looking at this thread?

---

### Post by rossjman1 on 2008-11-18
bump
module uinput is already loaded and it still wont work...
Here is my /etc/pam.d/common-auth
> #
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#

# fingerprint device
#auth	sufficient	pam_fprint.so

#auth	sufficient	pam_unix.so try_first_pass nullok_secure
#auth	optional	pam_smbpass.so migrate missingok
auth    sufficient      pam_thinkfinger.so
auth    required        pam_unix.so try_first_pass nullok_secure

---

### Post by rossjman1 on 2008-11-18
bump

---

### Post by rossjman1 on 2008-11-19
bump

---

### Post by aliencam on 2008-11-26
There are a lot of resources with the information you need, and thinkfinger is installed similarly to the way it was installed in hardy. 

here is a guide that I wrote on installing thinkfinger in intrepid: 

[http://blog.aliencam.net/2008/11/thinkpad-fingerprint-reader-in-ubuntu-810-intrepid/](http://blog.aliencam.net/2008/11/thinkpad-fingerprint-reader-in-ubuntu-810-intrepid/)

I tried fprint and i agree with you, it only works sometimes, is sloppy, and freezes update-manager.

---

### Post by undoIT on 2008-11-26
> **aliencam said:**
> There are a lot of resources with the information you need, and thinkfinger is installed similarly to the way it was installed in hardy. 

here is a guide that I wrote on installing thinkfinger in intrepid: 

[http://blog.aliencam.net/2008/11/thinkpad-fingerprint-reader-in-ubuntu-810-intrepid/](http://blog.aliencam.net/2008/11/thinkpad-fingerprint-reader-in-ubuntu-810-intrepid/)

I tried fprint and i agree with you, it only works sometimes, is sloppy, and freezes update-manager.

Thanks for the excellent guide. This also fixed two other issues I was having:

1. Update Manager and Synaptic not working with thinkfinger installed.
2. More than one request for password

---

### Post by jcdyer on 2008-11-29
I just got thinkfinger working on my Lenovo T43.

Contrary to the instructions at [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger) you have to install both thinkfinger-tools and libpam-thinkfinger.  (The instructions mention libpam-thinkfinger for hardy, but not for intrepid).  With libpam-thinkfinger installed, you can run:

```
sudo /usr/lib/pam-thinkfinger/pam-thinkfinger-enable
```

to enable pam to regocnize thinkfinger.  

At this point, I still didn't have the promised "--add-user" option for tf-tool, so I ran 

```
tf-tool --acquire 
tf-tool --verify && \
   sudo cp ~/.thinkfinger.bir /etc/pam_thinkfinger/$USERNAME.bir
```

(make sure /etc/pam_thinkfinger/${USERNAME}.bir is owned by root, and only readable/writeable by owner.)

Then modify the pam configuration files as recommended in the tutorial, log out and swipe yourself in.  This only addresses login.  Dunno if it fixes the rest of the issues.  I haven't gotten that far yet.

Good luck.

Cheers,
Cliff

---

### Post by jcdyer on 2008-11-29
Just discovered: on intrepid, if you have ~/.thinkfinger.bir, you don't need an /etc/pam_thinkfinger/${USERNAME}.bir

The thinkfinger module searches for ${HOME}/.thinkfinger.bir first, and if that's not found, looks in /etc/pam_thinkfinger.

Cheers,
Cliff

---

### Post by philgenius on 2009-01-04
*post deleted*

---

### Post by cottoncloth on 2009-01-05
i followed aliencam's excellent guide & TF is working properly on my x61t.  nm-applet is no longer bothering me for a keyring password either.

Except for one weird thing on resume/unlock from gnome-screensaver:

if I **type** my password, the prompt says "checking," pauses, and then prompts for password *again* before letting me in.

if I use the fingerprint reader, i'm only asked once.  it only happens with gnome-screensaver, not initial login at startup, su, etc.

is there something i'm missing or duplicating in these /pam.d files?

/common-acount
```
account	[success=1 new_authtok_reqd=done default=ignore]	pam_unix.so 
```

/common-auth
```
account     requisite	pam_deny.so
account     required	pam_permit.so
```

/gdm
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
```

---

