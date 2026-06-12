---
title: "SSH from Script not recognizing password.  Ok from terminal with same command"
date: 2015-11-27
forum: Programming Talk
---

### Post by Marwynne_Kuhn on 2015-11-27
I .can run the script it works until i enter the password.  It fails with the password.   I can run the following and it works every time.  "scp pxfer.sh pi@192.168.254.8:/home/pi" logs in no problem  It only fails when I run the script.  
It appears to be the packets are changed when I send it from the script.  Any ideas , I have searched the web with know success. I run both with debug and only find sending packets from the script does not authenticate.   Thanks in advance for any assistance.


#!/bin/sh

clear

echo "                    Pi  Transfer"
echo
echo
echo
echo "Type the name of the file you want to transfer."
echo
read NAME
echo
echo $NAME
echo
scp -vvv $NAME kitfox@192.168.254.8:/home/pi 
echo

---

### Post by Irihapeti on 2015-11-28
*Thread moved to **Programming Talk**.*

---

### Post by Lars Noodén on 2015-11-28
Can you provide the output of the script when using scp -v (instead of -vvv) ?

---

