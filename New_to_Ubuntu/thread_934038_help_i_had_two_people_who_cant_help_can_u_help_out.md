---
title: "help i had two people who cant help can u help out"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by blake7 on 2008-09-30
W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A
thank you for your time

---

### Post by techstop on 2008-09-30
A search on this very forum would have found this thread;

[http://ubuntuforums.org/showthread.php?t=933896](http://ubuntuforums.org/showthread.php?t=933896)

...which has a link to this page;

[http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/](http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/)


...which tells you how to import a gpg key. The error message you are getting is telling you that apt-get can't tell that the digital signature for a package is valid because it doesn't have the public key to verify.

---

### Post by zxscooby on 2008-09-30
[https://help.ubuntu.com/community/SecureApt?highlight=%28public%29%7C%28key%29](https://help.ubuntu.com/community/SecureApt?highlight=%28public%29%7C%28key%29)

---

### Post by Elfy on 2008-09-30
There is no need to start another thread while people are trying to help in the other thread.

There is nothing wrong with the commands you have been given there - if you have errors after running the command - paste what you have run and the error you receive.

---

### Post by wilsong on 2008-09-30
Try 



```
wget -q http://apt.wicd.net/wicd.gpg
```

then try 

```
sudo apt-get add wicd.gpg 
```

then try to redo whatever you did to get that message

Let me know if this works or doesn't , it worked for me.

---

### Post by blake7 on 2008-09-30
it great that you know all that but i dont think you udersatand who is the aveage user out thier, which clean explaines why the world uses windows,
 becase the averager user does not give  a toss about all this crap they just want it to work, you have your jobs and i have mine it it does not include trying to learn a new world, my world is big and complicated as it is all ready. i need a great tool like this not to have to make a tool like this.

hope that is not to alinateing and i hope in some way you understand that postion

thank you for all that you do and long live ubuntu

---

### Post by Joeb454 on 2008-09-30
Please do not create duplicate threads.

You are receiving help in the other thread, why would you need to start another thread?

Original Thread: [http://ubuntuforums.org/showthread.php?t=934016](http://ubuntuforums.org/showthread.php?t=934016)

---

