---
title: "Preparing customized object to send over the network."
date: 2011-07-03
forum: Programming Talk
---

### Post by akshay.sulakhe on 2011-07-03
Hello guys,
            I am working on some code,in which i have to prepare custom network packets to send over the network and get the reply,which will mainly be of data. I am using a middleware called as ariba for this purpose. Ariba is actually a middleware,the main framework is called SpovNet. I want to prepare 2 types of packets,one is interest packet,which needs to be broadcasted,and shud jst contain what data i want. Second is data packet,which should contain the data,and the address of the reciever. Can u tell me which API's i would need,and how to make such a packet,i can send normal text messages,i have that much ready. The link for all api's is:-
[https://i72projekte.tm.uni-karlsruhe.de/trac/spovnet-base/doxygen/Ariba_0.7.0/html/modules.html](https://i72projekte.tm.uni-karlsruhe.de/trac/spovnet-base/doxygen/Ariba_0.7.0/html/modules.html)

---

### Post by akshay.sulakhe on 2011-07-03
I just dont know the API's..once i know them,i can implement. Kindly let me know. Thanks.. :-)

---

### Post by juancarlospaco on 2011-07-03
I dunno, but Broadcast are deprecated on IPv6, just in case...
good luck.

---

### Post by akshay.sulakhe on 2011-07-03
The API"s have everything needed,dont know frm where i should start.Thats my problem.

---

### Post by doas777 on 2011-07-03
I'm getting a browser security warning on that link. not interested.

---

### Post by akshay.sulakhe on 2011-07-03
I know that....its a secure site from germany...if u can check the name,its written kalsruher..its a german university...u can always check it online...kindly add an exception...Plz dont worry,its no spam,scam,etc.m a student,and i am using that framework...thanks... :-)

---

### Post by nvteighen on 2011-07-04
> **doas777 said:**
> I'm getting a browser security warning on that link. not interested.

Not me (using the latest Chromium). It's the Karlsruher Institute for Technology, a more-or-less well-known German scientific institution.

Now about the OP's issue.

Let's see, API docs aren't tutorials, they're specifications and documentation for a certain interface. Take a look on the rest of the Documentation section for more information, but I think the developers of this framework assume that you know networking basics.

---

