---
title: "Glassfish v3.0 Virtual Servers not working."
date: 2010-02-01
forum: Programming Talk
---

### Post by salman4u on 2010-02-01
I made a simple webapplication named MyFirstWebApp and i am trying to configure Virtual Server but it's not working. Here is a list of what i did :

Under Virtual Servers node i created a new Virtual server
id: jacc
Host : [www.jacc.com](www.jacc.com)
Default Web Module: MyFirstWebApp
Clicked Ok to create Virtual Server

Then went to Network Listener and added a new Network Listener

Name: MyListener 
Protocol: MyListener-protocol 
Port: 8888
Address: 0.0.0.0
Selected Default Web Server : jacc

Then again went to jacc Virtual server and selected Network Listener as MyListener

Then went under Applications node and for MyFirstWebApp selected Default Virtual Server as jacc

Lastly, restarted the server and went into hosts file and added entry
127.0.0.1 jacc.com

Then i went into browser and typed :

[www.jacc.com](www.jacc.com)
jacc.com
localhost:8888
localhost:8888/MyFirstWebApp

for all of the above i get webpage cannot be displayed. What can be wrong here?
Another thing is if removed Default web module (MyFirstWebApp) then i go in browser and type

localhost:8888
it shows one page "your server is up and running"

Please help me. It's now almost 2 days trying to solve this.

---

