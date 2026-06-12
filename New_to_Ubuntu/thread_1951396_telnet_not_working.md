---
title: "telnet not working"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by rishiar4 on 2012-04-02
my ubuntu is not responding to telnet http requests for a web page.why???

---

### Post by CSNate on 2012-04-02
Why are you trying to telnet google?

---

### Post by SeijiSensei on 2012-04-02
The OP is initiating an HTTP session directly.  I do this from time to time myself for diagnostic purposes.  However unlike the OP, I get the expected result:

```

seiji@host:~$ telnet www.google.com 80
Trying 173.194.70.106...
Connected to www.l.google.com.
Escape character is '^]'.


```

Now the OP's request is poorly worded, or he or she hasn't actually explained what the intent is.  It's not "ubuntu" that isn't responding, but [www.google.com](www.google.com).

My guess is there's a firewalling or routing issue somewhere along the way.  If you open a web browser on this machine, can you connect to Google?  Can you ping the address you posted in the attachment?

---

