---
title: "corrupted password file"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by zaatlob on 2008-09-22
In some way it seems that i did corrupt my password for root.
I ain't able to start programs (firewall, add applications).

I treid to change the password with passwd root in the recovery mode. If i try that, i get a message: autherication information cannot be recoverd.

Is there a way to change/reset the password?

---

### Post by spiderbatdad on 2008-09-22
```
sudo passwd -l root
```to relock your root password...as it should be. Use sudo for administrative actions. 
Or have I misunderstood? Is your user password lost?

---

### Post by zaatlob on 2008-09-22
I unlocked en changed my password in the recovery mode.
I get the message that the password is changed. 

But when I try to start firewall with the new password i stil get a message that the password isn't correct. 
I am now getting a little bit confused

---

### Post by Iowan on 2008-09-22
Which password did you change - user or root?  Ordinarily, you (should) use **sudo** to start/restart  programs (eg. **sudo /etc/init.d/networking restart**) The requested password would be for your user.
[Here]("http://www.psychocats.net/ubuntu/resetpassword") is a good How-To on resetting password. Right next to it is one on [sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by zaatlob on 2008-09-23
Thank you very much.
I changed them both and now everything works.
I probaly did switch the two passwords inside my internal computer.
;)

---

