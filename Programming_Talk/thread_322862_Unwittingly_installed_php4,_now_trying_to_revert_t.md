---
title: "Unwittingly installed php4, now trying to revert to php5"
date: 2006-12-21
forum: Programming Talk
---

### Post by mcai6in2 on 2006-12-21
Hi,

I have the LAMP server setup and it was all working fine.  However, i've tried to install a package which required a lesser version of php (package is called FPDF); after this php no longer processes on the server.

When i try to connect via a web browser to the server, the php doesn't parse, instead, just throws up an "what do you want to open with" message.

I think my question is how can i get PHP 5 back (which libraries) and how do i configure it to parse again...

Regards,

Imran.

---

### Post by lnostdal on 2006-12-21
> **mcai6in2 said:**
> Hi,

I have the LAMP server setup and it was all working fine.  However, i've tried to install a package which required a lesser version of php (package is called FPDF); after this php no longer processes on the server.

When i try to connect via a web browser to the server, the php doesn't parse, instead, just throws up an "what do you want to open with" message.

I think my question is how can i get PHP 5 back (which libraries) and how do i configure it to parse again...

Regards,

Imran.

something like:
```
aptitude install libapache2-mod-php5 
```

..it should configure apache automatically..

---

### Post by mcai6in2 on 2006-12-22
Thanks for reply,

I've already done that via synaptic, but it hasn't configured apache.  i wonder if the php.ini files need configuring? Any ideas on that one?

---

### Post by lnostdal on 2006-12-22
> **mcai6in2 said:**
> Thanks for reply,

I've already done that via synaptic, but it hasn't configured apache.  i wonder if the php.ini files need configuring? Any ideas on that one?

maybe deleting the config-files would trigger it to install stuff properly again .. aptitude has a command `purge' that does this

---

### Post by mcai6in2 on 2006-12-23
SOLVED!!!!

Thanks a lot for your help.  I persevered (was tempted just to do a complete OS reinstall as it only takes 15 mins), but basically removed (including configuration) the following libraries:

libapache2-mod-php5
php5
php5-mysql
php5-mysqli

had to reboot, then reinstalled completely again, reboot.  Now working.

By the way, used synaptics.

Regards,

Imran.

---

### Post by maddog39 on 2006-12-23
Well if you use LAMPP just run:
```
sudo /opt/lampp/lampp php5
```
Then if you want to switch back:
```
sudo /opt/lampp/lampp php4
```

If that doesnt work, you have an old version of LAMPP, just download and install the new version.

---

