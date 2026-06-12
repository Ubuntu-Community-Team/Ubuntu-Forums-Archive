---
title: "Wireless router,  I have admin password but not network password"
date: 2009-10-28
forum: Programming Talk
---

### Post by tc101 on 2009-10-28
I have a Netgear Rangemax Wireless router that was set up by someone else.  I have the admin login and password.  I do not have the password for the wireless network.  There is one laptop that is set up to get on to the wireless network and it works fine.  How can I get the password for the wireless network so I can make other connections to it?

---

### Post by albandy on 2009-10-28
Connect it to your computer by a network cable, enter the admin zone and change the wifi key.

---

### Post by tc101 on 2009-10-28
> Connect it to your computer by a network cable, enter the admin zone and change the wifi key. 

OK, I'm in the admin zone.  I  see the Security Encryption (WEP) Key.  There is a button there to generate passphrase.  If I just  push that button will it give me a password for that key? Is the passphrase the same as a password?  I would rather not change the key because I am afraid I might mess up something on the laptop that already connects to the wifi network.

---

### Post by albandy on 2009-10-28
> **tc101 said:**
> OK, I'm in the admin zone.  I  see the Security Encryption (WEP) Key.  There is a button there to generate passphrase.  If I just  push that button will it give me a password for that key? Is the passphrase the same as a password?  I would rather not change the key because I am afraid I might mess up something on the laptop that already connects to the wifi network.

make and screenshot and put it here

---

### Post by tc101 on 2009-10-28
deleted

---

### Post by tc101 on 2009-10-28
I need to go out.  Will check back in a few hours.  Thanks for your help.

---

### Post by albandy on 2009-10-28
I think the wifi key is "key 1" value, but I see that you're using 64 bit WEP encryption. This is so dangerous, crack this kind of encryption it's about seconds or minutes.

I recommend you to use wpa2-psk[aes]

---

### Post by tc101 on 2009-10-28
That was it.  Thanks.

---

### Post by tc101 on 2009-10-29
> I see that you're using 64 bit WEP encryption. This is so dangerous, crack this kind of encryption it's about seconds or minutes.

I recommend you to use wpa2-psk[aes]

If I make that change, do I have to change anything on the lap top that uses that connection?

If I make that change, will the connection be slower?

---

### Post by albandy on 2009-10-29
Probably it will ask you for the new wpa key. 
I don't think it will be slower.

---

