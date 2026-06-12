---
title: "Freeze Problem Error Log - Please Help!"
date: 2016-09-23
forum: New to Ubuntu
---

### Post by yithmas on 2016-09-23
Hi all,


I posted a question regarding a complete freeze of my screen a few days ago, and thanks to user mastablasta, I was able to check a few things, most notably the error log.
I found this, just before a freeze, the log records this:

Sep 23 21:56:11 [ComputerName] lightdm: PAM adding faulty module: pam_kwallet.so
Sep 23 21:56:11 [ComputerName] lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Sep 23 21:56:11 [ComputerName] lightdm: PAM adding faulty module: pam_kwallet5.so
Sep 23 21:56:11 [ComputerName] lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Sep 23 21:56:11 [ComputerName] systemd-logind[737]: New session c1 of user lightdm.
Sep 23 21:56:11 [ComputerName] systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Sep 23 21:56:16 [ComputerName] lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Sep 23 21:56:16 [ComputerName] lightdm: PAM adding faulty module: pam_kwallet.so
Sep 23 21:56:16 [ComputerName] lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Sep 23 21:56:16 [ComputerName] lightdm: PAM adding faulty module: pam_kwallet5.so
Sep 23 21:56:16 [ComputerName] lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "marcus"
Sep 23 21:56:31 [ComputerName] lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=marcus
Sep 23 21:56:33 [ComputerName] lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Sep 23 21:56:33 [ComputerName] lightdm: PAM adding faulty module: pam_kwallet.so
Sep 23 21:56:33 [ComputerName] lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Sep 23 21:56:33 [ComputerName] lightdm: PAM adding faulty module: pam_kwallet5.so


Apparently, pam_kwallet5.so (the key wallet log-in tool?) wants to do something even if I am not using a browser? I am just speculating. In any case, the screen freezes after the last log entry and I have to make a hard restart (pressing the power button for several seconds).

Can someone help me get rid of that problem or do I need to loook into another log?

Best,

Marcus:confused:

---

