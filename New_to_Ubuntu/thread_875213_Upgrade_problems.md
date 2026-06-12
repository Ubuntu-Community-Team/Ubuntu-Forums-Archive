---
title: "Upgrade problems"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by aja on 2008-07-30
Hello 

Can some please help me ??  I was upgrading ubuntu to Hardy Heron every thing was going great. Then the installation froze. I rebooted. Then ran the cmd   sudo dpkg --configure -a. I was then able to run apt-get install-f  which continued the installation till it got to this point "Generating locales...

  en_AU.UTF-8... 
"

Again it froze " left it for 10 hours " rebooted the computer. now I still get 

"me@me-desktop:~$ sudo apt-get install
[sudo] password for me: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
me@me-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
me@me-desktop:~$ sudo dpkg --configure -a
Setting up locales (2.7.9-4) ...
Generating locales...
  en_AU.UTF-8... 

And that is it . not to sure to do next

---

### Post by Rocket2DMn on 2008-07-30
Have a look at this bug report
[https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)
There are some descriptions there on how to continue the upgrade, but it is a known bug.

---

### Post by mac9416 on 2008-07-30
Same happened to me except I had some other error message. Can't quite remember what. I gave it a famous Linux R&R. 
Newb suggestion: Try apt-get install -f? I bet you get the same error though. Sorry.

---

