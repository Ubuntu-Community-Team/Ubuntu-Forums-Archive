---
title: "socket server with sub directories"
date: 2016-08-03
forum: Programming Talk
---

### Post by chuchi on 2016-08-03
Hi all!

 

 Let's say I have a simple TCP server socket listening on port 1234, with protocols AF_INET and SOCK_STREAM.
 

 If I type the address 'http://127.0.0.1:1234' in the browser the server gets an new connection.

 

 But if I type the address '[http://127.0.0.1/subdir:1234]("http://127.0.0.1/asdf:1234")' there is no connection at all.

 

 How can I configure my socket server to listen to sub-directories in the URL?

 

 Thanks a lot!!

---

### Post by Rocket2DMn on 2016-08-03
You need 'http://127.0.0.1:1234/subdir'.  The way you have it given now, 'http://127.0.0.1/subdir:1234', will try to open a connection to port 80 (the default http port) and try to access a subdirectory of your web server directory called 'subdir:1234'.  If you want different directories to be accessible on different ports, I believe you need different TCP server instances.

---

### Post by chuchi on 2016-08-04
Hi Rocket2DMn! Yes you are right, that's the proper syntax!

Thank you very much!

---

