---
title: "Can't Connect To School Wifi"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by paranoidsuperhero on 2013-01-23
Hi I'm running 12.04 LTS on a Thinkpad Edge 13 (Intel). I installed using the certified image. I'm having trouble getting into my school's wifi. It worked fine on my phone (Nexus 4, Android 4.2 stock) but it never connects on my laptop.

Here's what the settings on my phone say. (All I had to do was input my username as my identity and password I use to log into school computer lab desktops and it worked fine.) I'm hoping someone can help me understand what I should input in the setup for when I try to access from my computer.

> SSID: STJ-WiFi
Security: 802.1x EAP
EAP method: PEAP
Phase 2 Authentication: None
CA certificate: (unspecified) <-- it literally says that there
User certificate: (unspecified) <-- it literally says that there
Identity: (this is where I put my regular username in)
Anonymous Identity ___________ (left it blank)
Password: (this is where I put my regular password in)

STJ-WiFi is picked up by the computer. I changed the security to the one above and input PEAP as well. There was no room for whatever Phase 2 Authentication means and if I try to pick something for CA/User certificates it takes me to a folder so I left those blank as well. I put in my username for my identity and password for password (just like I did for my phone). Anonymous was left blank. When I try to connect, after about 30 seconds it asks for credentials where I basically re-enter my username and password and tries to connect but never does.

Appreciate any help possible, thank you!

---

### Post by HunterDX77M on 2013-01-23
I am having a similar problem. Do you dual boot? If so, how is Wifi on your other OS?

---

### Post by paranoidsuperhero on 2013-01-23
Nope, no dual boot.

---

### Post by fdrake on 2013-01-23
see if this helps: [http://www.nowiressecurity.com/articles/configure_8021x_authentication_in_linux.htm](http://www.nowiressecurity.com/articles/configure_8021x_authentication_in_linux.htm)

if you can't use dual boot then try to use the thetering with android.

---

