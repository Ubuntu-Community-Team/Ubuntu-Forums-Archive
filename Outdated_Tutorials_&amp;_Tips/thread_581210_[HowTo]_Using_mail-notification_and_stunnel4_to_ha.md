---
title: "[HowTo] Using mail-notification and stunnel4 to have SSL/TLS support"
date: 2007-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by chrroessner on 2007-10-19
Hi,

mail-notification was not compiled with SSL/TLS support, because of some licensing problems that, in my option, is really idotic, at least for us users.

First I went on and recompiled mail-notification with ssl support, but then after switching from feisty to gutsy, same old story again.

Now I have done a very simple solution:

I installed stunnel4 and configured it in client-mode, so mail-notification is connectiong to localhost on different ports and stunnel is doing the ssl stuff.

What to do:

```

sudo aptitude install stunnel4

```

Go to /etc/stunnel and edit stunnel.conf

```

sudo gedit /etc/stunnel/stunnel.conf

```

```

; stunnel configuration file

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/run/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
compression = rle 

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Some debugging stuff useful for troubleshooting
;debug = 7
;output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes 

; Service-level configuration

[imaps1]
accept = localhost:1143
connect = mail.roessner.it-zahner.de:993

[imaps2]
accept  = localhost:1144
connect = imap.some.other.server:993

; vim:ft=dosini

```

Then you need to edit /etc/default/stunnel4:

```

# /etc/default/stunnel
# Julien LEMOINE <speedblue@debian.org>
# September 2003

# Change to one to enable stunnel
ENABLED=1
FILES="/etc/stunnel/*.conf"
OPTIONS=""

# Change to one to enable ppp restart scripts
PPP_RESTART=0

```

There I have set ENABLED to 1.

Now you can start stunnel4 and go on to the mail-notification setup

```

/etc/init.d/stunnel4 start

```

You can configure mail-notification and point to localhost, in this example ports 1143 and 1144

Advantage:

- You will not miss any security updates on mail-notification
- You never will need to recompile mail-notification again

Disadvantage:

- This is working perfectly on a single-user desktop, but might be problematic on multi-user scenaries. But, ask your local admin :-)

---

### Post by racmar on 2007-10-29
@chrroessner

Thanks, I just followed your howto and it worked  beautifully on gutsy!

---

### Post by Cris(c) on 2008-09-17
Hi guys...I followed all the instructions in the post but my mail-notification is not working...can someone help me? 

Thanks,

Cris.

---

### Post by chrroessner on 2008-09-17
Can you please give more detailed information, what exactly is not working?

---

### Post by Cris(c) on 2008-09-17
Hi chrroessner....thanks for the reply! I tried with stunnel but it did not work. I kept saying it could not connect to the server. Anyways, I finally succeeded following the tips in this [how to]("http://ubuntuforums.org/showthread.php?t=589115")...

Cris.

---

### Post by chrroessner on 2008-09-18
> **Cris(c) said:**
> Hi chrroessner....thanks for the reply! I tried with stunnel but it did not work. I kept saying it could not connect to the server. Anyways, I finally succeeded following the tips in this [how to]("http://ubuntuforums.org/showthread.php?t=589115")...

Cris.
Well, I know that using stunnel does push a little more complexity, but I can not confirm the posters opinion.

Setting on hold is IMHO a bad solution. Next dist-upgrade or security fix and I think you are out of luck with manuualy rebuilt packages. So for me, stunnel still is the better solution than recreating mail-notification.

If I may speak honestly, I can not understand, why ssl or gnutls still is missing in mail-notification; even in intrepid!

Christian

---

### Post by Cris(c) on 2008-09-19
> **chrroessner said:**
> Well, I know that using stunnel does push a little more complexity, but I can not confirm the posters opinion.

Setting on hold is IMHO a bad solution. Next dist-upgrade or security fix and I think you are out of luck with manuualy rebuilt packages. So for me, stunnel still is the better solution than recreating mail-notification.

If I may speak honestly, I can not understand, why ssl or gnutls still is missing in mail-notification; even in intrepid!

Christian

Yup...I do agree with you in this last point: I can't understand why ssl is not included in mail-notification...it is pretty much non-sense since you can recreate it by rebuilding the package yourself....(or using stunnel as you suggested).

Cris.

---

### Post by Pegasus_from_UA on 2008-10-28
chrroessner, Thanx a lot for the HowTo. 
I have an one question. 
My  mail-notification are working with the stunnel4 but there's 2 troubles. The  mail-notification always show more messages then there're ones. And after mail-notification showed about new messages it change tray icon to the envelope picture , I go to the FireFox , read the messages but the  mail-notification doesn't change icon back, so I think some new messages have received. Can anyone help me to fix it ?

---

### Post by ctothej on 2009-01-11
Thank you for this. This worked perfectly. Very useful tool.

---

### Post by Naaktgeboren on 2010-01-29
There is also a PPA with mail-notification packages built with SSL support:

[https://launchpad.net/~mail-notification-ssl/+archive/ppa](https://launchpad.net/~mail-notification-ssl/+archive/ppa)

---

