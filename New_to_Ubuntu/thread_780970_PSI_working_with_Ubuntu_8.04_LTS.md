---
title: "PSI working with Ubuntu 8.04 LTS"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by lkraemer on 2008-05-03
I upgraded Ubuntu 7.10 to 8.04 LTS and PSI didn't work after the upgrade.

Here is how to get it working........WHEW I can't live without it!


Setup Psi Jabber for gTalk - Ubuntu 8.04 LTS

If PSI has been installed on 7.10 or 7.04 before the upgrade
remove the package qca-tls with Synaptic then:

1. Install:
   sudo apt-get install psi
   sudo apt-get install libqca2-plugin-ossl
   (also REMOVE your account from PSI ONLY not the server for upgrade)
2. Open Psi Jabber -- Under APPLICATIONS - INTERNET
3. (Menu bottom left) > Account Setup
4. Add a new account. Name the account whatever you'd like (this will be
   your gTalk account)  .ie....Larry

In the ACCOUNT TAB:
5. For your Jabber ID, enter your entire e-mail address
  (username@gmail.com).
6. Enter your PASSWORD
7. check all three boxes

In the CONNECTIONS TAB:
8. Check the top two boxes.
9. Uncheck the third box, then make HOST: talk.google.com  Port: 5223
   Encrypt Connection: Legacy SSL:
10. Check the third box after selecting: Ignore SSL Warning.
11. Set allow plaintext auth......to: over encrypted connection
12. Save
13. Go ONLINE - Connect to gTalk folks.

Also google "How to Install PSI on Ubuntu 8.04" for the BUG report,
[http://www.google.com/support/talk/bin/answer.py?answer=24074](http://www.google.com/support/talk/bin/answer.py?answer=24074)


LK

---

### Post by attila82 on 2010-02-21
> **lkraemer said:**
> I upgraded Ubuntu 7.10 to 8.04 LTS and PSI didn't work after the upgrade.

Here is how to get it working........WHEW I can't live without it!


Setup Psi Jabber for gTalk - Ubuntu 8.04 LTS

If PSI has been installed on 7.10 or 7.04 before the upgrade
remove the package qca-tls with Synaptic then:

1. Install:
   sudo apt-get install psi
   sudo apt-get install libqca2-plugin-ossl
   (also REMOVE your account from PSI ONLY not the server for upgrade)
2. Open Psi Jabber -- Under APPLICATIONS - INTERNET
3. (Menu bottom left) > Account Setup
4. Add a new account. Name the account whatever you'd like (this will be
   your gTalk account)  .ie....Larry

In the ACCOUNT TAB:
5. For your Jabber ID, enter your entire e-mail address
  (username@gmail.com).
6. Enter your PASSWORD
7. check all three boxes

In the CONNECTIONS TAB:
8. Check the top two boxes.
9. Uncheck the third box, then make HOST: talk.google.com  Port: 5223
   Encrypt Connection: Legacy SSL:
10. Check the third box after selecting: Ignore SSL Warning.
11. Set allow plaintext auth......to: over encrypted connection
12. Save
13. Go ONLINE - Connect to gTalk folks.

Also google "How to Install PSI on Ubuntu 8.04" for the BUG report,
[http://www.google.com/support/talk/bin/answer.py?answer=24074](http://www.google.com/support/talk/bin/answer.py?answer=24074)


LK

I followed you recipe on a laptop and everithing works properly.
I tried as well on a mini dell with  ubuntu 8.04 but psi cannot find the ssl plugins.

any suggestions?

---

### Post by lkraemer on 2010-02-21
Certainly.....Just use Synaptic Package manager to install
libqca2-plugin-ossl

lk

---

### Post by attila82 on 2010-02-23
I re-installed libqca2-plugin-ossl but when I ask for Legacy ssl in the tab connection, it complains about the missing plugin SSL/TSL.

what's going wrong?
Yesterday I tried also to re-install first libqca2-plugin-ossl and psi after deleting them from the system. :confused:

---

### Post by attila82 on 2010-02-23
ps.

I'm on a dell mini 9, with ubuntu 8.04.1

here where I found libqca-ossl

/usr/lib/qt4/plugins/crypto/libqca-ossl.so

---

### Post by lkraemer on 2010-02-23
The only thing I can think of, is maybe you are ONLINE and
trying to make a change to your account.  GO OFFLINE first then
compare your settings with these png's.  Change as necessary,
then go back ONLINE.

I've got PSI working on 7.10, 8.04, 9.10, and will have it working on
10.04 when it is released.

lk

---

### Post by lkraemer on 2010-04-30
PSI Setup for Ubuntu 10.04 LTS as per attached photos.

lk

---

