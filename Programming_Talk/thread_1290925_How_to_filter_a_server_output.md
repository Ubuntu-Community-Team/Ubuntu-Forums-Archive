---
title: "How to filter a server output?"
date: 2009-10-14
forum: Programming Talk
---

### Post by satwien on 2009-10-14
Hi m8s,

One more noob is stressing you ... :)
I'm running a server application in a terminal and I would like to filter the output messages, to forward all the security related messages in a separate terminal. These messages are something like that:
"Illegal user abc is trying to access the server from IP 1x5.2x1.22x.1x"
In the main terminal should remain only the "normal" messages (requests and server answers).
I have no ideea from where should I start. :confused:
Could you please help me with an idea?

---

### Post by ubuser_7 on 2009-10-14
Do you have rules that you can use to filter out the security related messages? 

Perhaps you should use something like logsurfer or logwatch to keep track of these things.

---

### Post by satwien on 2009-10-15
Thx, I will have a look to logsurfer and logwatch to check if I could apply the filter rules.

---

