---
title: "Tomcat Requests"
date: 2010-05-03
forum: Programming Talk
---

### Post by jtrulen on 2010-05-03
I have a tomcat server that I am trying to get information about the requests on. How do I go about doing this? We have an instance of BIRT doling out reports. We have had over 41000 hits already, and I need to be able to see which of these are being hit the hardest.

The request in Server Status looks something like: POST /birt/run?__report=02-03001.rptdesign&__format=pdf&  HTTP/1.1

I need to know if there is some way to capture every request and store it, or if tomcat already does this.

Thank you for your help.

---

### Post by myrtle1908 on 2010-05-04
[http://wiki.apache.org/tomcat/FAQ/Logging](http://wiki.apache.org/tomcat/FAQ/Logging)

---

