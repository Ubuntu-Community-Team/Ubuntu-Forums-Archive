---
title: "[SOLVED] Help with vinagre"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by blaze41 on 2008-11-30
All im trying to do is access remote desktop between two computers that i have networked. Everytime i try it tells me connection closed. HELP please.

---

### Post by Bölvaður on 2008-11-30
what remote desktop protocols are you using and how did you set them up (programs)?
Is it possible that you allow each others ip to connect?

---

### Post by blaze41 on 2008-11-30
I used iptables and set 5900 on both computers for inbound. as far as setting anything else. I set up vinagre on both computers and made it so it needs a password.

---

### Post by Bölvaður on 2008-12-03
ok I do not know vinagre as Ubuntu used to rely on a CLI program only when I used it.
You do not need to open the ports in iptables as Ubuntu is set to open it automaticly (I think).

Make sure your computers have static ip.
Open for all connections and make sure the port for the vnc (I think it uses that protocol) is 5900.
Restart both computers and make sure the ips are still correct (this is just to be sure if everything is set correctly)
check if the computers connect for sure with ping 192.168.1.180 (as an example)
Connect with ip:port like this &#8594; 192.168.1.180:5900

If that fails there are CLI VNC programs in the repos if you wish to try some other programs.

---

