---
title: "SOAP java server calling client methods."
date: 2009-11-26
forum: Programming Talk
---

### Post by MCBTunes on 2009-11-26
I am making a program in java with SOAP web services, it is my first time using SOAP so it is going a little rough.

Basically I want to be able to have a client proxy object on my server and call client methods on it from the server. So when the client sends a message it will also need to send all the information required for the server to contact it(just the WSDL's location I believe). Then the server can send messages back to the client whenever it chooses.

So assuming my server gets a string of the WSDL's location how would I then get the WSDL and create the proxy? 

I am using wsimport while compiling my client.

---

