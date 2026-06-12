---
title: "&quot;Save&quot; button in &quot;editing connections&quot; greyed out"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by Jetro on 2012-02-09
So I'm quite new to 11.10, and have some issues with the wireless networking. 
It doesn't prompt to remember the password for the wireless network I'm using, so I have to type it in every time I log off/restart.

Then I found that you can solute the problem by adding a password to the connection (like key-ring manager or something?).

I go to **Edit Connections**, the Wireless tab and edit the connection I use. Up comes a few options, but unfortunately, the Save button down on the right is greyed out. So I can't really edit anything.

Anybody knows a fix for this? :popcorn:

---

### Post by duanedesign on 2012-02-11
Usually when the Save button is greyed out it is because a piece of information is missing. Your network may require different settings but I thought I would include the info I have filled in that lets me click Save.

Wireless tab
SSID: nameOfMyNetwork
Mode: Infrastructure

IPV4 Settings
Automatic(DHCP)

IPV6
Ignore

Wireless Security
WPA & WPA2 Personal
Password: mypassword

---

### Post by ikt on 2012-02-11
> **Jetro said:**
> Anybody knows a fix for this? :popcorn:

Try delete the connection and re-create, for me it allows me to save as soon as I put an SSID in, it may be as duanedesign said above that another option is checked but missing the information needed.

---

### Post by Jetro on 2012-02-17
Oh, dear. I hadn't put my password in in the 'Wireless Security' tab. When I did that, I was able to click Save. Thank you.

---

