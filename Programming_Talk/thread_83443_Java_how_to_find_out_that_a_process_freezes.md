---
title: "Java: how to find out that a process freezes"
date: 2005-10-28
forum: Programming Talk
---

### Post by Cyrus on 2005-10-28
Hi,

I opened an external process in my java application. Sometimes this process freezes so my program can't work on. Is there any way to find out the process is freezing?

So I can kill the process manually ...

---

### Post by jvictor on 2005-11-07
May sound weird, but this is what i can think of now

 u must run the line of code  taht executes this external process as a thread , now when u use Runtime.getRuntime.execXX u will be gettign a return value

init the var that will handle the retun value to some value taht the sytem will never return , after n seconds of executing the thread , chk the val of this var. if its the val that u have filled in during init ,then ur process msut have hung.. then 

System.err.println("BLAH BLAH BOOHOO BOOHOOO");

did u try this ?

I know its v wierd .. :)

---

### Post by Cyrus on 2005-11-07
Thank you - I actually use this solution now ...

---

