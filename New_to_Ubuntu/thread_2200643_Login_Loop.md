---
title: "Login Loop"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by hayloiuy on 2014-01-20
Hi guys, 

my Ubuntu 12.10 is stuck at a login loop. What happens is that after entering my creds and password, the screen turns black and I am back to the login screen. I am sure I entered the correct password because there were no messages that I have entered the wrong password.

I have tried this: 
[http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

but it still does not work. 

A thing to take note of though, I recently changed my Wireless NIC to D-Link DWA-525. I think the driver is not installed yet. I can't access internet from Ubuntu.

What is wrong?

---

### Post by whitesmith on 2014-01-20
Tell us if you can login from a terminal session. Do```
ctrl+alt+F1
```and attempt to login from there. To get back do```
ctrl+alt+F7
``` To reboot do```
shutdown -r 0
``` I suspect the NIC change is unrelated to your problem.

---

### Post by hayloiuy on 2014-01-21
Hey thanks for the reply!

Yeah I can login to the terminal session. I followed instructions in [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop).

However it doesn't work.

---

### Post by steeldriver on 2014-01-21
some other useful diagnostics

[LIST]
[*]can you log in to a different desktop session e.g. ubuntu-2d instead of the regular session?
[*]can you log in as a guest user?
[/LIST]

---

### Post by hayloiuy on 2014-01-22
What do you mean by ubuntu-2d?

Yes I can log in to the guest user with the login gui screen.

---

### Post by hayloiuy on 2014-01-25
Just something new. I recently changed the password because I forgotten the password. Could this have caused the login loop?

---

### Post by rburkartjo on 2014-01-25
yes that is probably the problem. see the post about re-setting your password or here is the link provide by dead

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

