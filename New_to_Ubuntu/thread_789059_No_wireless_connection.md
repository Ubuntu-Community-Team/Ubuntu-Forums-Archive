---
title: "No wireless connection"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-10
I did a fresh install and got the wired working again. Now I click on network manager, click on wireless, I see my network, click on it and it brings up a box: wireless network key required, I fill in all the boxes and it tries to connect but can't. Then when I go back to network manager we start all over. What in the world am I doing wrong here? I have the restricted drivers installed and fwcutter.

---

### Post by cmnorton on 2008-05-10
You are probably doing this correctly. The only problem I have ever had connecting, once I got the box to put in the WEP key was putting in the hex key while being prompted for the passphrase. I was confused thinking that meant the translated hex key. Suggest you look at what you are prompted for and makesure it matches what you are entering.

---

### Post by Anatasia on 2008-05-10
In may case it was different.My wireless network only use MAC filter,doesn't use any security mode.It did see my network but when I try I can't connect at all.

---

### Post by cmnorton on 2008-05-12
The only other thing I can think of is to look at logs under /var/log. messages and syslog may contain some diagnostic information along with the output of dmesg.

---

