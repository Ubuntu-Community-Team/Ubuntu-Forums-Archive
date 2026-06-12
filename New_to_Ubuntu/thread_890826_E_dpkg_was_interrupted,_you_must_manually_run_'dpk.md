---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by teenzonez on 2008-08-15
Hi,
when i try to open synaptic pakage manager i get an error:E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
when i try to give the dpkg --config it asks for super user password. i gave the password for the id i logged in. but it says authentication failed. i am administrator.
im very new to ubuntu or linux itself. could anyone help me?
Thanks,
Teena

---

### Post by Crafty Kisses on 2008-08-15
Try running the following in Terminal:
```
sudo dpkg --configure -a
```

---

### Post by teenzonez on 2008-08-15
Thanks for the reply.i got a blue window package configuraion. inside it i got a message saying :Local security certificates must be replaced                            &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474; A security certificate which was automatically created for your local   &#9474;   
  &#9474; system needs to be replaced due to a flaw which renders it insecure.    &#9474;   
  &#9474; This will be done automatically.                                        &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474; If you don't know anything about this, you can safely ignore this       &#9474;   
  &#9474; message. 

could you please tellme what is the next step to do?

---

### Post by teenzonez on 2008-08-15
Hi i pressed ok and it is done i think.i didnt know which key to press. i pressed spacebar and it workd. but could you please tell me what the message means? will it have some effect on my os operations?

---

### Post by Elfy on 2008-08-15
Have you recently(ish) instaleld and just got the first updates - I think it maybe was to do with the updates a sort while ago, dns could have been.

Nothing to worry about afaik - I did the same thing.

---

### Post by decoherence on 2008-08-15
The message about the security certificate has to do with an OpenSSL vulnerability that was found a little while ago. We all got the same message -- most users don't need to worry about it.

---

### Post by teenzonez on 2008-08-15
thanks a lot for your responses. yes i installed it one week before. but didn install all in the synaptic fully. do i need to do that?

---

