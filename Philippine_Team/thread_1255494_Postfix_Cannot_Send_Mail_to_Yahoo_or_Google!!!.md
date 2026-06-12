---
title: "Postfix Cannot Send Mail to Yahoo or Google!!!"
date: 2009-09-01
forum: Philippine Team
---

### Post by jmazaredo on 2009-09-01
Hey! You have configured postfix + mysql and suddenly got problem? ginawa mo nalahat ayaw padin! 

I got this problem on my postfix server. It is working perfectly fine all can send receive mails out going and incoming. 

Then suddenly I cannot send to yahoo, gmail!

The problems maybe the following:

1. the isp that the client is using is blocked by rbl's or some sort check it
2. the server is hacked compromised or the configuration is broken with unknown reason check main.cf

What if all is good still cannot send???!!!!

Check this out!

you have miss configured the client

if you are using outlook check for the option server needs authentication if you are using sasl or other sort of login

add the ip address of the client for example the public ip is 203.77.77.77 then add to postifx to allow 203.0.0.0/8 in networks this will fix your error

---

