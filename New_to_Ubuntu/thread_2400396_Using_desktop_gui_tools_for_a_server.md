---
title: "Using desktop gui tools for a server"
date: 2018-09-05
forum: New to Ubuntu
---

### Post by deepakdeshp on 2018-09-05
Hello,
I have Ubuntu 18 desktop as host and Ubuntu 18 server as client. Can I open a file on the client using hesitate which is available on the host? If so what would be the procedure or command?
TYAIA.

---

### Post by TheFu on 2018-09-05
Uh ... huh?
What? Please be more specific about what it is you are hoping to accomplish?

What client?
What server?
Which protocols?
>  Can I open a file on the client using hesitate doesn't make sense to me.

Normally, a client would connect to a server using a protocol like ssh or sftp or scp or nfs or CIFS (which is samba).  The "desktop" would always be the client and the server would be the server, but you can swap those around if you like. Most people wouldn't, but on Unix it only matters if you expect to use some GUI.  

Linux servers don't have GUIs.  If you want a GUI, and you shouldn't, then you've just added additional attack vectors against the server. Probably not a good idea, but people do it all the time.  GUIs don't work well when the server isn't on the same LAN, so if you ever plan to have a server running on Amazon or Azure or some other remote data center, learning without a GUI now is a very important step.

IMHO.

---

### Post by sporksrule on 2018-09-05
This is not recommended but you would have to enable x11 forwarding in /etc/ssh/sshd_config on the server and install a GUI.

---

### Post by travis-falkenberg on 2018-09-07
You could install "Webmin" on the server and access it. Works just like a GUI but in a web browser!

---

### Post by mastablasta on 2018-09-07
and if client /host is about virtualbox, then you just need to share the folder with the file to host (in vbox)

---

### Post by TheFu on 2018-09-07
> **travis-falkenberg said:**
> You could install "Webmin" on the server and access it. Works just like a GUI but in a web browser!

If you do use webmin, please only allow connections from localhost so an ssh tunnel with ssh-keys or ssh-certs for authentication is needed to access it. Allowing any unauthenticated http/s connection, even to the login page, is a huge security risk for any "admin" level tool like this.  Same would apply to wordpress, php-admins, and LDAP admin web tools. No need to make it easy for attackers.

---

