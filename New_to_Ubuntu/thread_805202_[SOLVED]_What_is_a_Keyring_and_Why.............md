---
title: "[SOLVED] What is a Keyring and Why............"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-23
I have idea what I have changed or what is going on.  But.... I dont leave my computer up 24/7 I turn it off in the morning and then back on at night. When I get home.  After it has been off during the day when I log back in at night and open Evolution (what I am using for email) Evolution keeps asking for a password - So it can access a "keyring" What the hell is a keyring??  :lolflag: And why is Evolution trying to access it..  Gunny enough I entered a password the first time it asked for this and as it turns out it was the right password. LOL. Once I have entered the password once each day it won't have to be entered anymore even if I close out of evolution and open it back up...

Can anyone help 

??
~D

---

### Post by anewguy on 2008-05-23
What is probably happening is that you have a protected connection - usually this is a wireless thing.  If you have WEP or WPA on your wireless router, each time you attempt to connect to that router it wants a password.  This password holding is done via a logical key ring manager in Ubuntu.  Basically, this logical key ring can hold the keys needed by all of your wireless connections (maybe others as well - I'm just familiar with it from using wireless).  The access to this logical key ring is password protected.  Whenever you attempt to go online the 1st time after a power up, the logical key ring needs to be accessed to provide the password to the router.  The password you are being asked for is actually the password to the keyring manager.  In most instances, you set this password to the same as your log in password and no questions will be asked.  It's possible you've done an update/upgrade that affected the keyring manager password, or perhaps you deleted the keyring itself.  Your best course of action might be to go into the keyring manager (system/administration/keyring manager) then delete your existing keyring.  This will force it to create a new key ring the next time you boot up and 1st try to access the net.  At that point in time it should ask for a keyring password - give it the password you use to log in.  If it doesn't ask for a key ring password, then that portion has been automated and should work (unless of course you change your log in password or your log in altogether.  :)

---

### Post by hufferd on 2008-05-23
HEy thanks for the reply I will try the things you have said here and see what happens :) 

Have a great long weekend :)

---

