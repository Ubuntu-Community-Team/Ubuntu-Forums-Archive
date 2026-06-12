---
title: "write custom modules for webmin"
date: 2007-10-13
forum: Programming Talk
---

### Post by Krijk on 2007-10-13
I've created a number of bash scripts and run them with cron or from  a terminal. 

It might be necessary to execute these scripts from a webinterface because ssh traffic is not allowed from the network you're working on or because it is not allowed to ssh to the internal network.

In webmin custom commands can be defined, but these can only start the scripts. 

In some cases the scripts require user input.  How can I do that with webmin?

I thought about storing these in a seperate input file which can be modified from the webinterface. How can I do that or is there a better way to do this?

A custom module might be better, but I'm not sure where to start. I've checked webmin forums, but couldn't find any nice tutorials for newbies in programming which I am. Any pointers or advice would be  very helpful.

---

