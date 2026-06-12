---
title: "Wireless issue after updates installed"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by Homeroast on 2012-06-20
Hello everybody,

I installed some system updates this morning and now I can't get my computer on to the wireless network.  It was working fine before the updates (this is the first time this has happened).

I keep getting the authenticate message requiring my password.

And then I get the wireless network authentication required (it pops up with the correct password that has always worked before).

I just keeps cycling through these two messages.

I'm running Lubuntu 12.04

Any suggestions?

---

### Post by kc1di on 2012-06-20
first check and make sure your authentication method is correct for you router.  
right click on the network Icon and got to edit wireless wireless security and make sure you wpa wpa2 or other

---

### Post by Rex Bouwense on 2012-06-20
Hey I had this happen to me once and all I had to do was delete the network and then reaquire it.  I entered the appropriate passwork and bingo I was on.  Just updating your OS should not kick you off the network.

---

### Post by Homeroast on 2012-06-20
Thanks for the suggestions!  I'll try them and report back ...

---

### Post by Homeroast on 2012-06-22
Rex, 

I took your advice and now I'm back on.

Thanks for everything!

---

### Post by Rex Bouwense on 2012-06-22
Glad to help.

---

### Post by Turalyon on 2012-10-26
Hello Everyone,

**GOOD NEWS:**

I found a way to connect to my wireless router using Lubuntu 12.10.

**BAD NEWS:**

Step 1.  Disable **ALL** security on your wireless router (either by resetting it or through the configuration page)

Step 2. Login to your computer as you always would

Step 3.  Go to your wireless connection and choose your wireless network

Step 4. **Enter your login password from step 2 **when you are asked for a wireless athentication

I wouldn't really call this a "fix" for obvious reasons, but maybe it will help point someone more knowledgeable about Linux into the right direction for a real workaround. If anything this would offer a "quick fix" temporary solution for those needing to get a working infrastructure up and running in a hurry. 

[B]MAKE SURE:

[/B]You disable SSID Broadcast and make your network hidden if you think you might be using this solution for a short period of time.

---

