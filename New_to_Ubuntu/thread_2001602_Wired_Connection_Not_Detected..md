---
title: "Wired Connection Not Detected."
date: 2012-06-11
forum: New to Ubuntu
---

### Post by rufus muturi on 2012-06-11
Hello, guys. I'm new to Linux (less than a week) and my ethernet adapter does not seem to be working. I cannot update Ubuntu or install applications, since I cannot connect to the internet. The network connection is not even detected. Please help me out here.

---

### Post by rufus muturi on 2012-06-11
I almost forgot, I'm running Ubuntu 12.04. Any help will be greatly appreciated.

---

### Post by timcowchip on 2012-06-11
Boot from the install media (the CD/DVD/USB that you used to install Ubuntu). Make sure the network connection is detected first, then re-install.

---

### Post by Inderpreet Singh on 2012-06-11
try this

sudo vi /etc/NetworkManager/NetworkManager.conf  and make sure that 

[ifupdown]
managed=true

if not than make it true
[B][COLOR=#000000][FONT=Arial]
Save, stop and start network manager:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**sudo service network-manager restart**[/FONT][/COLOR][/B]

now open network manger there must be a network card

---

### Post by rufus muturi on 2012-06-14
Thank you, I. Singh, for taking the time to help me out :)

---

### Post by rufus muturi on 2012-06-14
Thanks, Tim, for your help :)

---

### Post by rufus muturi on 2012-06-14
I found out it was a problem with my hardware, not the software or drivers. Thank you, guys, again.

---

