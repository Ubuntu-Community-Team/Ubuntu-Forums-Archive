---
title: "How Do I connect to internet"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by nirakarsethy on 2008-04-24
I've a Motorola modem. My network icon shows that Network Connection is on. The problem is in Vista the netprovider's software runs and then it connects. (some PPPop software). How do i configure here in Ubuntu.

---

### Post by nirakarsethy on 2008-04-24
Because each time somebody help me I've to Logout, then test then comeback to windows to reply.

So kindly help

---

### Post by seshomaru samma on 2008-04-25
maybe [this]("https://help.ubuntu.com/community/ADSLPPPoE") will help

---

### Post by nirakarsethy on 2008-04-25
What does that mean ?

---

### Post by apostate on 2008-04-25
> **nirakarsethy said:**
> What does that mean ?

To clarify: Is this an ADSL modem or a dial-up modem?

---

### Post by seshomaru samma on 2008-04-25
> What does that mean ?
it means you have to click on the underlined word "this"

anyway -here is the link for you:
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by nirakarsethy on 2008-04-25
its ADCL

---

### Post by dokdoom on 2008-04-25
Are you directly connected to the modem? If so, that's bad but another problem. My brothers modem actually gave him an address, I can understand why others wouldn't. So, if you see you are connected but cannot connect I must ask, what have you tried so far? If you run 'ifconfig' you should see your interface(s). I'll assume eth0 is the interface you have linked and running. After you run ifconfig if I assume correctly eth0 should be up and running. Try running 'dhclient ethx' (where X = the interface number you have up and running.) Let me know if you have tried this already.

---

### Post by nirakarsethy on 2008-04-25
I've tried the seshomaru samma's way. But this was unsuccessful and this is the error message on the terminal

---

### Post by rajeev1204 on 2008-04-25
type in terminal sudo pppoeconf

Just enter username and password. see if this helps.

---

### Post by nirakarsethy on 2008-04-25
no it doesn.t work

---

### Post by rajeev1204 on 2008-04-26
> **nirakarsethy said:**
> no it doesn.t work


what message do u get ?

---

### Post by seshomaru samma on 2008-04-26
according to the error message the password you have put in is incorrect
can you repeat the whole procedure again ?

---

