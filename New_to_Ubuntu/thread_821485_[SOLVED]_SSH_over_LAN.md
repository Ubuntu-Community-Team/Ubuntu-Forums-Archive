---
title: "[SOLVED] SSH over LAN"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by michaljohn86 on 2008-06-07
I have a wireless network at home.  I have recently added two more computers both running Ubuntu Hardy.  

I would like to get the two of them talking to them using SSH but I have no idea how.  I can see the computer I want to connect to in Place->Network if that helps.

---

### Post by Monicker on 2008-06-07
Have you installed the openssh server package on the remote computers?


[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by michaljohn86 on 2008-06-07
I have installed openssh-server and can ssh into the computers using username@ipaddress.  However, I need to find the ip address of the server each time I do this using ifconfig.  Is there a way around this?

---

### Post by Monicker on 2008-06-07
> **michaljohn86 said:**
> I have installed openssh-server and can ssh into the computers using username@ipaddress.  However, I need to find the ip address of the server each time I do this using ifconfig.  Is there a way around this?

Assign static ip addresses to the computers, or use dhcp reservations to make sure they always get the same ip address from the dhcp server.

---

### Post by DBrocks on 2008-06-07
To assign static IP, check this site out. 
[URL="http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html"]http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html
[/URL]

---

### Post by michaljohn86 on 2008-06-07
Thanks a lot seems to be working really well.

---

### Post by DBrocks on 2008-06-07
Don't forget about the 'thanks' feature! Lol I'm bein vain agian.

---

