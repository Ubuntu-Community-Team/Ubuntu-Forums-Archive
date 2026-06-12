---
title: "[SOLVED] How to use pidgin with a gmail account?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by bhadotia on 2008-05-21
There is no default option for gmail (there are yahoo, msn , etc. ,etc.....). So to configure pidgin with a gmail account?

Can anyone please help?

---

### Post by bhadotia on 2008-05-21
Sorry for that ........just found it.


reallllllllllyyyyyyyyyy very sooooooooorrrrrrrrryyyyy (clumsy me!).:(:(:^o:oops::oops:

---

### Post by bhadotia on 2008-05-26
Well I did this:

```
Basic
protocol:google talk 
Screen name: "my gmail user name"
Resources:Home


Advanced
proxy type:Use GNOME proxy settings
```


But I am getting the following error:

"my gmail username"@gmail.com/Home disconnected
```
Could not establish a connection with the server:
Access denied: HTTP proxy server forbids port 5222 tunneling
```


We use our University's Wi-fi network to connect to the net. So some of the ports are blocked .  
But my friends at the hostel with windows (with google talk installed) are able to connect to gtalk using our university's proxy settings.  And the "GNOME Proxy settings" above, are the same as my university's proxy settings.

Any idea where am I going wrong?
I have tried using the port 443, but the same error comes.

Also after getting this error , when I click on "modify account" option , I find that the protocol is changed to XMMP, whereas I formerly selected "Google Talk" as the protocol.

---

### Post by bhadotia on 2008-07-18
I think it was all network problem only (the closed network port in my University's network). I am at home at present and pidgin is working just fine.

---

### Post by bhadotia on 2008-11-20
[This ]("http://ubuntuforums.org/showthread.php?t=847947")link solved the problem even on the University network.

---

