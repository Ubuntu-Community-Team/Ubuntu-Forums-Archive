---
title: "Optimum Setup for VPS to run several Joomla sites (PHP 5.5 question)"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by brad16 on 2014-03-26
I've messed around with VPSs for a bit but I'm rather green.  I can get my way around but I'm still learning the how's and why's and what to do.  

I'm setting up a VPS that will run about 15 small Joomla sites.  I've setup Ubuntu 13.10 with most of the defaults and the required additions for Joomla.  

I want to setup PHP to run as FCGI (unless there's a reason I shouldn't) and also setup suExec.  This is per the Joomla security guidelines.  But I'm not sure if PHP 5.5 will run with the opcache or not when it's run as FCGI.  I used APC in the past with pretty good results so I was interested in keeping caching fuctioning.

So my questions are: 

[LIST=1]
[*]will PHP 5.5 run as FCGI still include the opcode caching by default?
[*]do I want to use fcgi or is there something similar that is better?
[*]is that the right setup for what I'm trying to do?
[*]is there anything else I need to know about setting up suExec with that?
[*]Are there any obvious recommendations you have based on my current plan?
[/LIST]

Thanks for the help in advance.

---

