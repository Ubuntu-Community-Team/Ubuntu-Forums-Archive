---
title: "To check the status of online user at my server"
date: 2015-10-02
forum: New to Ubuntu
---

### Post by Danial_Rana on 2015-10-02
Kindly let me know if there is any command in ubuntu that would allow me to monitor the status of online users logged in to my web-server?

---

### Post by TheFu on 2015-10-03
Every webapp does logins differently - so if there are 5000 different webapps, there are 5000 different ways they handle logins. 

If you are just using the simple-auth module built into apache, then a grep of the apache log files would be needed.

The 2nd answer here [https://stackoverflow.com/questions/3539430/http-basic-authentication-maximum-allowed-trial-times](https://stackoverflow.com/questions/3539430/http-basic-authentication-maximum-allowed-trial-times) provides some other ideas for php, python and perl webapps.

---

