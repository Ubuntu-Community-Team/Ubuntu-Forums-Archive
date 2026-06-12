---
title: "Wireless Connection Problem"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by librandon12345 on 2012-01-27
I just bought a netbook with Ubuntu 11.10 installed on it from a friend. I don't know much about ubuntu so please bear with me. When I sign in as administrator, the wireless networks show up, but when I go to press my wireless network (any network for that matter) nothing happens (it doesn't prompt a password key, remains disconnected). I've tried connecting through hidden wireless and that didn't work. BUT when I signed into a guest session and pressed my wireless network, the password was prompted and I was able to connect. How can I connect when I'm administrator

---

### Post by WthIteh on 2012-01-27
Information about network connections are stored per-user. So it's possible that your admin user's settings learned something wrong preventing it from asking for correct info.
Click on networks icon and select "Edit Connections...", in Wireless tab find related network line, select it and click "Delete..." to remove it. Then click on "Add" and fill all correct info about that network from scratch.

---

### Post by anewguy on 2012-01-27
+1.  It seems that network manager remembers bad attempts, especially if it was the first attempt, at connecting to a network.  After that, it will always reject the connection.  As WthIteh mentioned, it's best to edit network connections and just delete everything there and start over.  Remember there is an option you can check to show the network password you are/have entered - highly recommended so you can verify you did get it right.


Dave ;)

---

