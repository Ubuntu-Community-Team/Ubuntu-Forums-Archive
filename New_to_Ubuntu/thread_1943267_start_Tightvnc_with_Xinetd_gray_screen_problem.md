---
title: "start Tightvnc with Xinetd gray screen problem"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by SeDonk on 2012-03-19
When I try to start Tightvnc with Xinetd, all I see in vncviewer is a grey screen with a black X.
 
 When I start Tightvnc by typing vncserver in a terminal everything works fine.
 
 Does anybody know why Tightvnc doesn't work with Xinetd in my configuration?
 
 Thanks in advance for your help,
 Sem
  
 Ubuntu 11.10
 Tightvnc 1.3.9


xstartup:
                  
```

#!/bin/sh   
unset SESSION_MANAGER 
   
xrdb $HOME/.Xresources 
xsetroot -solid grey  
  
export XKL_XMODMAP_DISABLE=1 
exec gnome-session & 

```service defined in xinetd.conf: 
```

service Xvnc  
 {  
     type = UNLISTED  
     disable = no  
     socket_type = stream  
     protocol = tcp  
     wait = no  
     user = sem  
     server = /usr/bin/Xvnc  
     server_args = -inetd -httpd /var/www  
     port = 5901       
 }
```

---

