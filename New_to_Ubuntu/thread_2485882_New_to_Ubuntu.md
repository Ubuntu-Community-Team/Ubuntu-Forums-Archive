---
title: "New to Ubuntu"
date: 2023-04-12
forum: New to Ubuntu
---

### Post by edensearch on 2023-04-12
Hello.. I am a newby to ubuntu and trying to get an ssh remote server access setup/established so I can have remote access for software installation/updates while working from my office computer.
I have successfully installed Ubuntu and setup OpenSSH and have confirmed the system is "listening".
I am able to remote access through "Putty" while on the same LAN/WAN (router), but continue to be "timed out" when trying to connect from outside of my network (router). 

Any detailed directions/recommendations would be very much appreciated.:confused:

---

### Post by SeijiSensei on 2023-04-12
You can't see device behind your router from outside unless you set up something called "port forwarding." Most firewalls block all incoming traffic unless specifically enabled. See if you can figure out how to pass port 22 on the router to port 22 on the server. In most cases you can pick any other port >1023 on the router, like 22222, and pass that back to the server for a little bit of added security.

---

### Post by edensearch on 2023-04-12
Great! I will give that a try.. Thank you

---

### Post by ActionParsnip on 2023-04-13
Nothing to do with Ubuntu. This is your router doing it's job. It'll be called "port forwarding" or "Virtual server" in the web interface of your router. Once setup you can access your WAN IP on the port you specify and access the internal server. Please use SSH keys as the ONLY method of authentication and disable SSHing in as root. I also suggest you install and configure fail2ban to protect the service. Your SSH port will be brute force attacked a LOT

---

