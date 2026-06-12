---
title: "auth.log and proxy?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ub newb on 2008-08-25
Hi, 

Please let me know what this auth.log entry means where 
the xyzz is my user name. Is this an attempt to run a terminal command? Or is this just an attempt to run something that requires admin privileges? 

Aug 25 02:16:55 MDdesktop sudo:     root : TTY=unknown ; PWD=/ ; USER=xyzzz ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy 
Aug 25 02:16:55 MDdesktop sudo: pam_unix(sudo:session): session opened for user xyzzz by (uid=0) 
Aug 25 02:16:55 MDdesktop sudo: pam_unix(sudo:session): session closed for user xyzzz
Aug 25 02:16:56 MDdesktop sudo:     root : TTY=unknown ; PWD=/ ; USER=xyzzz ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host 
Aug 25 02:16:56 MDdesktop sudo: pam_unix(sudo:session): session opened for user xyzzz by (uid=0) 
Aug 25 02:16:56 MDdesktop sudo: pam_unix(sudo:session): session closed for user xyzzz 
Aug 25 02:16:57 MDdesktop sudo:     root : TTY=unknown ; PWD=/ ; USER=xyzzz ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port 
Aug 25 02:16:57 MDdesktop sudo: pam_unix(sudo:session): session opened for user xyzzz by (uid=0) 
Aug 25 02:16:57 MDdesktop sudo: pam_unix(sudo:session): session closed for user xyzzz

Thank you very much for your time. :)

---

### Post by ub newb on 2008-08-29
bumped...

if this is a question that would be better answered in another spot, please let me know? 

thanks

---

