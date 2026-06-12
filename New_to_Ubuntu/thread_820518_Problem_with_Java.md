---
title: "Problem with Java"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by jjblackfox on 2008-06-06
Hello, thanks for taking the time to try to help me with my problem. Everytime I try to view a Java appellate online I get the following error:

Unable to connect : java.security.AccessControlException : access denied (java.net.SocketPermission 

I have Java 6.0 installed so it's not out of date. A box popped up and asked if I wished to trust this publisher and I clicked allow, but now the appellate doesn't load.

---

### Post by The Cog on 2008-06-06
Java only allows applets to connect back to the server they came from. Your applet is trying to connect to somewhere else. An applet that can connect to other places could impersonate you doing anything and make all kinds of trouble for you. So java is doing the right thing. You should not trust an applet that tries to talk to servers other than the one it came from.

---

### Post by jjblackfox on 2008-06-06
> **The Cog said:**
> Java only allows applets to connect back to the server they came from. Your applet is trying to connect to somewhere else. An applet that can connect to other places could impersonate you doing anything and make all kinds of trouble for you. So java is doing the right thing. You should not trust an applet that tries to talk to servers other than the one it came from.

It is an IRC from a website that I trust. Is there anyway to allow it?

---

### Post by The Cog on 2008-06-06
I think it might work if you run it from your own PC (local files). But the idea of an IRC applet in java is bizarre, because the java security model just doesn't allow for that kind of behaviour.

---

