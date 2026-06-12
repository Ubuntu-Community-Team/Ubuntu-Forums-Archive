---
title: "Communication between android device and linux device"
date: 2013-08-05
forum: Programming Talk
---

### Post by lion87 on 2013-08-05
Hello guys,
In my network there are several (embedded linux powered, c++) devices which are connected via Wifi. Now i want to control the devices over the network from an android smartphone (and later on, from other platforms).
In the end i want to have a library which others can use on Android to easily control the network devices.
So i need to develop some kind of "protocol" to communicate with the devices. What would you suggest to use for communication?
For finding the devices in the network i use UDP multicast, which seems so work fine. 
Since on every device there is running a http server, i thought of implementing some kind of REST interface which the android device can call to control the device, sending commands to the device, receiving data back....
Later on the communication should also be possible from outside the local network (from the internet). 

What approaches and technologies do you recommend?

regards

---

### Post by TheFu on 2013-08-05
> **lion87 said:**
> Hello guys,
In my network there are several (embedded linux powered, c++) devices which are connected via Wifi. Now i want to control the devices over the network from an android smartphone (and later on, from other platforms).
In the end i want to have a library which others can use on Android to easily control the network devices.
So i need to develop some kind of "protocol" to communicate with the devices. What would you suggest to use for communication?
For finding the devices in the network i use UDP multicast, which seems so work fine. 
Since on every device there is running a http server, i thought of implementing some kind of REST interface which the android device can call to control the device, sending commands to the device, receiving data back....
Later on the communication should also be possible from outside the local network (from the internet). 

What approaches and technologies do you recommend?

regards

ssh. Secure. ssh has been implemented on pretty much every platform. With keys, no logins needed.  It means that whatever you want to run, is just a shell script away. Much lighter too, than running a full web/app server in embedded devices.  Scripts can easily return JSON and you can treat those just like any other REST web service - except this way, you absolutely KNOW which client is connecting - not just anyone from anywhere will have the SSH keys, right?  On the LAN or from around the world - it doesn't matter. ssh is secure.

UDP isn't secure, so I'd avoid that.
HTTPS isn't secure. CAs and DNS providers have proven that they cannot be trusted.

Don't forget to implement WoL ... though over WiFi - I don't think that will work.

Interesting plans.

---

### Post by lion87 on 2013-08-06
sounds interesting, what kind of libraries would you suggest on the c++ side as well as on the android side?

---

### Post by TheFu on 2013-08-06
The devices you have will limit which libraries can be used. Clearly, **not** something like Boost. Too bloated.

---

### Post by lion87 on 2013-08-07
after thinking about this approach i think that this is too complicated for my needs, do you have other suggestion how this can be implemented?
I think that xml-rpc would also be a possibility.

---

### Post by TheFu on 2013-08-07
rpc has ZERO security.  Either you care about security that works over the internet or you don't.  If you can guaranty that connections from the internet will always be through a secure tunnel or VPN, then use whatever lightweight communication method you want.

I'm honestly surprised that you believe ssh is too complex.  It is much simpler than running a web server that handles any sort of request - perhaps 100x easier.
Have you never run a remote program from an ssh request?

Try this:
```
$ ssh user@server ls /bin/
```

The returned data is displayed on the local server. That means it could easily be captured and used just alike any JSON you like. Complicated?```
$ ssh user@server my-fancy-server optionA optionB .... optionZ
```
The requests can be made with an XML or JSON input too.  Very simple, very "RESTful", very secure.

---

