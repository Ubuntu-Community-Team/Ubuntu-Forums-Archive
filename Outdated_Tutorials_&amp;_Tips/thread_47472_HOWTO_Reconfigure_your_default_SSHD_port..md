---
title: "HOWTO: Reconfigure your default SSHD port."
date: 2005-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by dmccarney on 2005-07-08
For all you veterans this is a piece of cake and isn't worthy of a HOWTO but I figured since so many threads in the security forum are about SSH Dictionary attacks I figured I would write a quick howto for newbs.

This isn't a FIX for SSH Dictionairy attacks but if they bother you this really helps against the automated worm based ones that only aim for port 22.

This is my first real HOWTO so forgive me if I make any mistakes, I'm also fairly new to Ubuntu. 

Step 1)
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
``` 

Step 2)
```
sudo gedit /etc/ssh/sshd_config
``` 

Step 3)
Find this line in your sshd_config file:
> # What ports, IPs and protocols we listen for
Port 22 

Step 4)
Change it to:
> # What ports, IPs and protocols we listen for
Port XXX 
Where XXX is the number of the port you wish to use (You're best off choosing a high number and a number that isn't used for a wide-spread protocol like FTP etc)

Step 5)
Save the file.

Step 6)
```
sudo /etc/init.d/ssh stop
``` 
Wait for a second or two...
```
sudo /etc/init.d/ssh start
``` 

Voila! Couple this with the HOWTO for configuring SSHD to use Key Pair authentication URL: [http://www.ubuntuforums.org/showthread.php?t=30709&highlight=key+pair](http://www.ubuntuforums.org/showthread.php?t=30709&highlight=key+pair) , turning off password authentication and root login and you have a pretty secure setup.

---

### Post by szdavid on 2005-07-08
Good idea to have done this ; easy but necessary....

I think you should precise that to stop and restart the ssh service, you have to type sudo before /etc/.....

---

### Post by dmccarney on 2005-07-09
Ah thanks. I knew I probably forgot something. Its fixed now :)

---

