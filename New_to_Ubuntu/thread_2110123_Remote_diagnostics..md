---
title: "Remote diagnostics."
date: 2013-01-29
forum: New to Ubuntu
---

### Post by joco1500 on 2013-01-29
Hello

I am wondering if there is a program that will run diagnostics on a devise connected by a USB or Ethernet connection.

I want to know because i run a company that fixes hand-held things and other small electronics. 

Thank you for your help.

---

### Post by sudodus on 2013-01-29
> **joco1500 said:**
> Hello

I am wondering if there is a program that will run diagnostics on a devise connected by a USB or Ethernet connection.

I want to know because i run a company that fixes hand-held things and other small electronics. 

Thank you for your help.
You can log in via a network connection in many different ways, and once logged in, you can run most programs, also diagnostic programs.

One way is to run SSH, but it means that you need a secure connection and a static IP address is preferred (but not necessary). Another way is to run a remote screen program, which is possible with several programs.

Teamviewer is easy to use (even an inexperienced end user can set it up at her/his end). It is a commercial product, but as a private person you can evaluate it without any cost. Maybe you can convince the guys at Teamviewer to make a version, that runs in your hand-help devices.

---

### Post by TheFu on 2013-01-29
> **joco1500 said:**
> Hello

I am wondering if there is a program that will run diagnostics on a devise connected by a USB or Ethernet connection.

I want to know because i run a company that fixes hand-held things and other small electronics. 

Thank you for your help.

Every USB device has different capabilities. Testing these would be specific to each device.  There are some core features that most USB devices for each subset type must support, but those tests are fairly trivial.

For ethernet, again, it would depend on the remote device.  SNMP is a common way to monitor remote devices on a network, but there are others. The MIB is the core. Again, you would want to create and perform the tests for each device.  NMS and NMS-like tools would be a starting point.

Lots of programming tools have built-in testing techniques. In fact, something called TDD, Test Driven Development, has created some fantastic tools for test harnesses.  I use Perl and Ruby, but realistically, any language can be used.  There is a standard for test results that works across the different programming languages too.

There are other monitoring methods that could be extended to remote diagnostics too.  Hopefully, someone else will respond with smarter ideas.

The great news is that doing this stuff with most scripting languages (ruby, perl, python, etc...) would be almost trivial assuming your tests didn't also screw with the remote device's state or overload it from doing whatever work it should be doing.

---

