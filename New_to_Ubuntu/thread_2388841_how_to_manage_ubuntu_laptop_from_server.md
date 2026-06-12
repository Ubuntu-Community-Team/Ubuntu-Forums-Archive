---
title: "how to manage ubuntu laptop from server"
date: 2018-04-08
forum: New to Ubuntu
---

### Post by rashedayyash on 2018-04-08
dears
please your help ,how to manage ubuntu laptop from server "how to have full control " 
br

---

### Post by SeijiSensei on 2018-04-08
If you don't need a GUI, install openssh-server on the laptop and connect with SSH.  Since Server does not come with a GUI, you must have some experience with using the command prompt.

---

### Post by rashedayyash on 2018-04-10
ok but i want system as ltsp server

---

### Post by Tadaen_Sylvermane on 2018-04-11
Which system. Need to know which you want to be the ltsp server before can give further advise. I'd recommend the server and use the laptop as a client personally. The server needs to be available 24/7. Not good for laptops to run that way unless properly ventilated... at least here in the desert where I live. 

LTSP is quite easy to set up. I have a single server in my home serving 2 client images currently. One for desktop, another for my remote media centers. I can share some config examples if needed. I've hacked together a good workable environment for myself over the last couple years with lots of research and googling. 

I will say this though. LTSP is very use specific. It may not be the best choice for whatever you are trying to deploy. Need to know why you want to use LTSP.

---

### Post by rashedayyash on 2018-04-12
ok , but can you help me to manage laptop client from server not LTSP

---

