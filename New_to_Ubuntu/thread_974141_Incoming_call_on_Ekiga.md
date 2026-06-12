---
title: "Incoming call on Ekiga"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by shah_vm on 2008-11-07
Hello 

I am new to ubuntu. I was trying to setup ekiga with voxalot. However am unable to receive incoming call on ekiga. I am able to make call. Is it am missing any setup. My current setting is as below

Under Preference-->Protocols-->Network Settings-->NAT Settings
   NAT Traversal Method: None
   STUN Server: voxalot.com

Under Preference-->Protocols-->SIP Settings-->Misc Settings
   outbound Proxy: <blank>
   Forward URL: <blank>

Under Preference-->Protocols-->SIP Settings-->DTMF Mode
   Send DTMF as: RFC2833

Under Preference-->Protocols-->H.323 Settings-->Misc Settings
   Default gateway: <blank>
   Forward URL: <blank>

Under Preference-->Protocols-->H.323 Settings-->Advance Settings
   Enable H.245 tunneling is checked
   Enable early H.245 is checked
   Enable fast start procedure is checked

Under Preference-->Protocols-->H.323 Settings-->DTMF Mode
   Send DTMF as: String

---

### Post by brian_p on 2008-11-07
> **shah_vm said:**
> Hello 

I am new to ubuntu. I was trying to setup ekiga with voxalot. However am unable to receive incoming call on ekiga. I am able to make call. Is it am missing any setup. My current setting is as below

Under Preference-->Protocols-->Network Settings-->NAT Settings
   NAT Traversal Method: None
   STUN Server: voxalot.com 

It may not solve your problem but the stun server should be stun.voxalot.com and NAT Traversal Method: possibly shouldn't be 'none'.

You're behind a router?

---

### Post by shah_vm on 2008-11-08
> **brian_p said:**
> It may not solve your problem but the stun server should be stun.voxalot.com and NAT Traversal Method: possibly shouldn't be 'none'.

You're behind a router?

Thanks brain for the response. I changed to stun.voxalot.com and NAT traversal method to stun but still dont receive incoming call.

---

### Post by shah_vm on 2008-11-08
> **shah_vm said:**
> Thanks brain for the response. I changed to stun.voxalot.com and NAT traversal method to stun but still dont receive incoming call.

It is solved now. I can now receive incoming call on ekiga. I had to update preferences-->protocols-->sip settings-->misc settings-->outbound proxy: us.voxalot.com

---

