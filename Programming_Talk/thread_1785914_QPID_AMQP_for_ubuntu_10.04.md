---
title: "QPID AMQP for ubuntu 10.04"
date: 2011-06-18
forum: Programming Talk
---

### Post by biovore on 2011-06-18
I have recently built some debs for Ubuntu 10.04 that implement the QPID AMQP broker and client stuff.  I did this because I could not find a compiled implementation of the needed packages to install.

[AMQP]("http://www.amqp.org/confluence/display/AMQP/About+AMQP") is the first open standard for Enterprise Messaging.
Enterprise Messaging systems let programs communicate by exchanging messages, much as people communicate by exchanging email. Unlike email, enterprise messaging systems provide guaranteed delivery, speed, security, and freedom from spam. Until recently, there was no open standard for Enterprise Messaging systems, so programmers either wrote their own, or used expensive proprietary systems. 

I have found a nice high level talk about what AMQP is, and how it is used.
[http://mutlix.blogspot.com/2007/09/amqp-in-10-mins-part0.html"]AMQP in 10 mins tutorial](http://mutlix.blogspot.com/2007/09/amqp-in-10-mins-part0.html"]AMQP in 10 mins tutorial)

The debs are located in my ppa and contains the cpp/python/qmf/tools packages that should include everything to get started.
These packages probably could use some cleaning up and polish, but there good enough to get people going with QPID AMQP implementation on Ubuntu.

ppa:kb3gtn/qpid

deb [http://ppa.launchpad.net/kb3gtn/qpid/ubuntu](http://ppa.launchpad.net/kb3gtn/qpid/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/kb3gtn/qpid/ubuntu](http://ppa.launchpad.net/kb3gtn/qpid/ubuntu) lucid main

I might post more information if there is interests.

---

