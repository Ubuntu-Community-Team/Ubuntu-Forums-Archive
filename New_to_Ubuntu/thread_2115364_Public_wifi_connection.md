---
title: "Public wifi connection"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by jagdefalke on 2013-02-12
Bear with me....
I'm staying with family for a while and there's no internet at the house so I've been finding wifi at the local coffee shops.   I found a favorite coffee shop and it was working great until a couple weeks or so ago when I allowed some software updates to install and now my computer won't connect to their wireless.  It'll connect anywhere else just not this one.   I noticed it's a WEP and everyone else around seems to be WPA2, I don't know if that means anything...  I'm fairly stupid about this stuff.    So I'm wondering if there's any little packages that will fix the problem?    I'm running 12.04 on an Aspire D270, with Ubuntu on one half and the factory Win 7 on the other.   I really don't like having to use Windblows just so I can sit at the coffee shop I like.. :(


Michelle

---

### Post by jagdefalke on 2013-02-12
Bump..  :)


ok, so I did some general searches on the issue and am seeing alot about linux (debian esp) having issues with WEP.   I don't have access to the router so there's nothing I can do at that end, but since this happened immediately after installing some software updates I'm sure it's just a matter of software/driver.   I'm terrible in kernel as well.    Hopefully I won't have to find a new favorite coffee shop...  :(

---

### Post by Mark Phelps on 2013-02-12
> **jagdefalke said:**
> ...I noticed it's a WEP and everyone else around seems to be WPA2, I don't know if that means anything... 

These are two very different wireless security schemes.  WEP is an older version and (generally) considered insecure.  WPA2 is newer, and better, and you would have to change your wireless config setting to use WPA2 -- and provide the correct passphrase.

---

### Post by jagdefalke on 2013-02-12
Is the passphrase the same as the password that they give their patrons, which is the stores phone number? Or is it the some other key?  I was under the impression that the router had to be changed to WPA2, can I just change to it in my connection settings?  I know I sound childish about this.. I need to take a linux class..  :p

---

### Post by squakie on 2013-02-12
If you open network manager while at the hotspot and select the network, ubuntu should automatically know the encryption type - in this case wep.  It should, however, ask you for the passkey/passphrase/password to connect to that network - that's where you would use the password they give you.  Click the "show" button below the space where you put in the password so you can be sure you entered the correct password.  This is independent of any other connections you might use at other times.

---

### Post by jagdefalke on 2013-02-12
Ah.  See, thats the problem is it won't even get to the point of asking for the passcode anymore.  It recognizes that the signal is there but just can't seem to communicate with it at all.

---

### Post by unheeding on 2013-02-12
Try removing it from Network Connections (click on the wifi icon, edit connections, click on the wireless tab, select the connection for the coffee shop, delete) and reconnecting.

---

### Post by jagdefalke on 2013-02-12
I'll try that next time.  Thankyou.

---

### Post by squakie on 2013-02-12
> **unheeding said:**
> Try removing it from Network Connections (click on the wifi icon, edit connections, click on the wireless tab, select the connection for the coffee shop, delete) and reconnecting.

+1.  If you have ever tried to connect to a network and entered a passphrase/passkey/password, it seems the "remembered" connection information is used no matter what - even when you try to specify a new passphrase/passkey/password.  To start clean, always delete the network if it shows in network manager when you edit connections.

---

