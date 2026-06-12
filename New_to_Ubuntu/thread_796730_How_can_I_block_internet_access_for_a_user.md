---
title: "How can I block internet access for a user?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by KIAaze on 2008-05-16
How can I block internet access for a user?
Or just deactivate network stuff by default, so that only a user with root permission can activate it?

---

### Post by tompickles on 2008-05-16
youve probably tried it - but have you tried unchecking the - connect to internet using modem box in their user properties?

---

### Post by KIAaze on 2008-05-16
Yes, but that didn't work for the ethernet/wifi connections.

---

### Post by PinkFloyd102489 on 2008-05-16
Are you wanting to limit certain programs for connecting to the internet, or the connection in general?

---

### Post by KIAaze on 2008-05-16
The connection in general.

---

### Post by tompickles on 2008-05-16
does removing them from the dhcp group do anything?

---

### Post by PinkFloyd102489 on 2008-05-16
> **tompickles said:**
> does removing them from the dhcp group do anything?

Im the admin of my system and Im not even listed beside of the dhcp group. I dont think that will help.

---

### Post by KIAaze on 2008-05-16
Indeed, it doesn't help. :/

Otherwise, is it possible to do a blanket IP block using iptables?
(I currently have no idea how to use iptables however. So any specific details on this are welcome.)

---

### Post by PinkFloyd102489 on 2008-05-16
Firestarter is a GUI to iptables, try that?

---

### Post by loldrup on 2008-05-16
Try installing firestarter. You can block stuff using that, and it requires root access for editing

---

### Post by PinkFloyd102489 on 2008-05-16
Problem with Firestarter and iptables in general is you cant block certain users.

---

### Post by KIAaze on 2008-05-16
And block all users?

---

### Post by PinkFloyd102489 on 2008-05-16
It blocks all users from whatever you choose to block, whether it be by ip, hostname, or port.

---

