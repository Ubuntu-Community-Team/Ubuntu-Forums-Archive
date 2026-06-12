---
title: "New rasperry pi user"
date: 2021-10-16
forum: New to Ubuntu
---

### Post by dantpi on 2021-10-16
Hi how's all? I'm a new user of raspberry pi 4 8gigs and using the latest version of ubuntu on it.
My goal is to make a nas connection to a 4tb drive i have and also host my own website from.
Being tottally new to all this i would proberbly need somme tips along my journey.
Glad to be here.

---

### Post by ActionParsnip on 2021-10-16
You can use nginx or apache for the Web server. If you have SSH access then you can connect your users to the SFTP service that you get by default. Use your Ubuntu credentials as you expect. The Ubuntu and Mac OS file manager can connect to the service without issue. Windows isn't very good and will need a client like Filezilla. You could alternatively setup a Samba share and Windows can access that using the default file manager.

---

