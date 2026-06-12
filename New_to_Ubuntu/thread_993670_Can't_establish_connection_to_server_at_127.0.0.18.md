---
title: "Can't establish connection to server at 127.0.0.1:8080"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Motion_Noob on 2008-11-26
I've restarted Motion, and I'd like to control it now. In Firefox, using the same box that Motion is installed on, and into which the webcam is plugged, both [http://localhost:8080](http://localhost:8080) and [http://127.0.0.1:8080](http://127.0.0.1:8080) return a "can't establish connection to the server" error. 

Does restarting Motion automatically restart the webserver that Motion uses? 

If not, how do I restart that webserver?

---

### Post by jemate18 on 2008-11-26
> **Motion_Noob said:**
> I've restarted Motion, and I'd like to control it now. In Firefox, using the same box that Motion is installed on, and into which the webcam is plugged, both [http://localhost:8080](http://localhost:8080) and [http://127.0.0.1:8080](http://127.0.0.1:8080) return a "can't establish connection to the server" error. 

Does restarting Motion automatically restart the webserver that Motion uses? 

If not, how do I restart that webserver?


I'm not familiar with motion but you can start a service like thise..

example, to start service named XXSERVICE

```
sudo /etc/init.d/XXSERVICE start
```

where XXSERVICE is the service you like to start.

To check if the service is running

```
ps ax | grep XXSERVICE
```

---

### Post by Motion_Noob on 2008-11-26
OK, thanks. But what is the name of the webserver service that Motion uses?

---

