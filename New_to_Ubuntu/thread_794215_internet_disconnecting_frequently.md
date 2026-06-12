---
title: "internet disconnecting frequently"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by koundinya on 2008-05-14
hi
I configured my internet connection in ubuntu. But I noticed that it disconnects almost every five min or so or if I dont browse for 5 min. Why is it so? I have to type pon dsl-provider every time. When I checked using plog it returned lot of lines but the last one sometimes is modem hanged. Also the downloads get paused in between. What is the solution for this??

---

### Post by koundinya on 2008-05-15
pppd[5645]: remote IP address 59.93.112.1
 pppd[5645]: primary   DNS address 218.248.240.24
 pppd[5645]: secondary DNS address 218.248.240.135
pppd[5817]: No response to 4 echo-requests
 pppd[5817]: Serial link appears to be disconnected.
pppd[5817]: Connect time 3.0 minutes.
 pppd[5817]: Sent 16719 bytes, received 436564 bytes.
 pppd[5817]: Connection terminated.
pppd[5817]: Modem hangup

This is what plog returns

---

### Post by koundinya on 2008-05-15
pppd[5645]: remote IP address 59.93.112.1
 pppd[5645]: primary   DNS address 218.248.240.24
 pppd[5645]: secondary DNS address 218.248.240.135
pppd[5817]: No response to 4 echo-requests
 pppd[5817]: Serial link appears to be disconnected.
pppd[5817]: Connect time 3.0 minutes.
 pppd[5817]: Sent 16719 bytes, received 436564 bytes.
 pppd[5817]: Connection terminated.
pppd[5817]: Modem hangup

This is what plog returns

---

### Post by mrdosa on 2008-05-15
I got the same error when my ISP's server was down. Well, I've a dual boot with xp, so checked with xp and found my connection to be broken!

---

### Post by koundinya on 2008-05-15
Ya I did check with xp but my connection is ok

---

