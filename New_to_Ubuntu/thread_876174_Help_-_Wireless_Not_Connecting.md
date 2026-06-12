---
title: "Help - Wireless Not Connecting"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by iHaVEnOmMrS on 2008-07-31
Hey all,
I have a wireless built-in to my Compaq V6000 notebook. I'm trying to connect to my wireless router, and it hangs on "Waiting for network key", and then asks me for the password again...and again...and again. My password is WEP with Shared Key for Auth. Any help? Thank you.

//ihavenommrs

---

### Post by anewguy on 2008-07-31
I had a small problem like that, and in my case it was just an error in the network manager connection screen - specifically be sure to watch the key definition - 128 vs 64 bit, ascii vs hex.  I think the default is 128 bit hex, and with my old router I just had 64 bit hex.

Also remember:

= case sensitive
- no spaces in password/passphrase
- no quotes

:)

---

### Post by iHaVEnOmMrS on 2008-07-31
I already checked, it's 128 bit ASCII. The password is 100% correct, too. So I really don't know what's wrong... =S

//ihavenommrs

EDIT: Also I installed the driver following the instructions here:
   --> [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by saj0577 on 2008-07-31
Are you selecting HEXadecimal(2nd option on the drop down menu) when it asks for the WEP code?

Even if you think its wrong give it a go just to be sure.

Saj

---

### Post by iHaVEnOmMrS on 2008-07-31
> **saj0577 said:**
> Are you selecting HEXadecimal(2nd option on the drop down menu) when it asks for the WEP code?

Even if you think its wrong give it a go just to be sure.

Saj

I'm not able to type in my password, if I select it.

//ihavenommrs

---

### Post by anewguy on 2008-08-04
If you are using network manager with 8.04, the options is now a 128 bit for WEP passphrase, 64/128 bit (all one option) for WEP hex, and 64/128 bit (all one option) for ASCII.  As soon as you select one of those the appropriate box for a passphrase/password should appear in the new connection box.  On my new connection screen from network manager, WEP ASCII is the THIRD option down.  If you selected HEX, you probably won't be able to enter anything beyond 0-9 and A-F.

If need be, we can try connecting via the command line and seeing if you can ping, etc..

---

