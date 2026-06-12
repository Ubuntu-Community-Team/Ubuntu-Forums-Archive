---
title: "Problem with dkpg due to postfix config"
date: 2017-11-02
forum: New to Ubuntu
---

### Post by mimtoki on 2017-11-02
I installed Ubuntu via Bootable usb and I'm new to this OS.

I've encountered the following error after trying to remove rkhunter:

```
Setting up postfix (3.1.0-3ubuntu0.1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).


After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.


Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: nthink-ThinkCentre-M58e..name
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: nthink-ThinkCentre-M58e..name
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.


dpkg: error processing package bsd-mailx (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 postfix
 bsd-mailx
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

When I encountered this before, I reinstalled the OS because of Ebury from Chkrookit result.

Since there's no tutorial on it, I was confused.

Can anyone help me? I'm very, very new to Ubuntu. Thank you.

---

### Post by DuckHook on 2017-11-03
Welcome to the forums, mimtoki.

I'm not sure if I understand your issue, but you mention rkhunter and then postfix, which is a separate package. You also state that you are very new to Ubuntu. I am taking the liberty of assuming that this means you are also new to Linux?

If you are brand new to Linux in general, then my first piece of advice is to perhaps become more comfortable and familiar with Linux before trying to install such heavyweight apps. Both rkhunter and postfix are rather high octane programs and require a fair amount of knowledge to properly install and maintain.

I don't use rkhunter, so can't help you there. I've installed postfix only once a long time ago, so can't be of much help for you there either.

Perhaps one of the more technically proficient forum members can help you with either, but my more general advice would be to refrain from using either app until you are more seasoned with Linux, then experiment with them in a VM first, so you roll back to a good snapshot if/when things go wrong. In the meantime, since it appears that you don't have a lot invested in this installation, the easiest way to get back to a pristine system with a working dpkg is simply to reinstall again. This time, I recommend refraining from experimenting with your base system, and installing a VM right away to play with the things you want to learn about. And, as a beginner, don't use a low-level tool like dpkg because of the danger of breakage. Apt should work in practically all circumstances.

---

