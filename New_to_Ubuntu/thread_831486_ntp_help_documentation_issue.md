---
title: "ntp help documentation issue"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by thinking2loud on 2008-06-16
The Ubuntu Help Center documentation for ntp suggests:

 To test that a server works, just type sudo ntpdate ntp.server.name and see what happens. 

I would suggest that is really not such a good idea.  It would be safer to use ntpdate -q ntp.server.name .

---

### Post by HalPomeranz on 2008-06-16
Or to get more detailed output, "ntpdc -p ntp.server.name"

---

