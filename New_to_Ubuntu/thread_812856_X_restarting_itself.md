---
title: "X restarting itself"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by gardara on 2008-05-30
Since I have upgraded to ubuntu 8.04 X has been restarting itself, every now and then....

Today I turned on my laptop, opened pidgin, amarok and xchat and then X restarted itself.
I re logged in and opened the same applications again, and the same thing happened.

Looking at /var/log/daemon.log I can see some errors about this.

```
May 30 04:40:16 glappi gdm[5994]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 30 04:40:31 glappi hcid[5926]: Default passkey agent (:1.53, /org/bluez/passkey) registered
May 30 04:40:31 glappi hcid[5926]: Default authorization agent (:1.53, /org/bluez/auth) registered
May 30 04:43:25 glappi gdm[10131]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 30 04:43:43 glappi hcid[5926]: Default passkey agent (:1.89, /org/bluez/passkey) registered
May 30 04:43:43 glappi hcid[5926]: Default authorization agent (:1.89, /org/bluez/auth) registered
May 30 06:20:34 glappi hcid[5926]: link_key_request (sba=00:16:CF:FE:CF:F5, dba=00:1D:28:2A:1E:2F)
May 30 13:40:15 glappi gdm[11684]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 30 13:40:31 glappi hcid[5926]: Default passkey agent (:1.206, /org/bluez/passkey) registered
May 30 13:40:31 glappi hcid[5926]: Default authorization agent (:1.206, /org/bluez/auth) registered
May 30 13:40:54 glappi gdm[31534]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 30 13:41:16 glappi hcid[5926]: Default passkey agent (:1.238, /org/bluez/passkey) registered
May 30 13:41:16 glappi hcid[5926]: Default authorization agent (:1.238, /org/bluez/auth) registered
May 30 13:43:05 glappi gdm[32159]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```

How can I prevent this from happening again?

---

### Post by gardara on 2008-06-03
This problem hasn't gone away... And now always when I open amarok, x restarts itself... Really annoying since I love amarok so much...

Any advices?

---

### Post by Shazaam on 2008-06-03
Do you have desktop effects turned on?
It might be related to this bug.....
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130325](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130325)
Google search results....
[http://www.google.com/search?hl=en&as_q=&as_epq=WARNING%3A+gdm_slave_xioerror_handler%3A+Fatal+X+error+-+Restarting+%3A0&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=&as_epq=WARNING%3A+gdm_slave_xioerror_handler%3A+Fatal+X+error+-+Restarting+%3A0&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)

I have the same problem. Turning off desktop effects is the only cure (except living with it) that has worked for me.

---

### Post by gardara on 2008-06-03
I use compiz, compiled from git.

Tried disabling it and starting amarok.. Was able to start amarok that way, and then I re-enabled compiz with no problems... I find it strange that they can run together with no problems but I cannot start amarok if I have compiz running.
Running amarok has been no problem until about a week ago. I have a intel graphicscard and I think it hasn't been updated or anything for a long time.

this is really strange...

---

