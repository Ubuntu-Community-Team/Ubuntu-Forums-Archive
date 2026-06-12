---
title: "Strange error message"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-08-30
Aug 31 03:54:36 PJ NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.NoReply - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
Aug 31 03:54:57 PJ NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.LimitsExceeded - The maximum number of pending replies per connection has been reached 
Aug 31 03:55:26 PJ NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.NoReply - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
Aug 31 03:56:07 PJ NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.LimitsExceeded - The maximum number of pending replies per connection has been reached 
Aug 31 03:56:54 PJ NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.NoReply - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
Aug 31 03:57:22 PJ NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.LimitsExceeded - The maximum number of pending replies per connection has been reached 
Aug 31 03:58:12 PJ NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.NoReply - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
Aug 31 03:58:57 PJ NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.LimitsExceeded - The maximum number of pending replies per connection has been reached 


Anybody know what is going on here?

---

### Post by nicedude on 2008-08-30
Here is a debian netowrk manager bug report on this 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456363](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456363)

Hope that helps you figure out what is going on, network  manager works for me though so only thing I know to tell you is to start the system updater and see if there are some updates for your system as it could fix it ( it is marked as closed on the debian bug reports which should mean someone fixed the problem and I hope the fix made it to Ubuntu already as an update might fix it )


If you can't find the system updater then here is a command to do the same thing from a terminal

sudo apt-get update


hope this helps :-)

---

### Post by dunbrokin on 2008-08-30
> **nicedude said:**
> Here is a debian netowrk manager bug report on this 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456363](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456363)

Hope that helps you figure out what is going on, network  manager works for me though so only thing I know to tell you is to start the system updater and see if there are some updates for your system as it could fix it ( it is marked as closed on the debian bug reports which should mean someone fixed the problem and I hope the fix made it to Ubuntu already as an update might fix it )


If you can't find the system updater then here is a command to do the same thing from a terminal

sudo apt-get update


hope this helps :-)

Thanks, I will check it out...

---

