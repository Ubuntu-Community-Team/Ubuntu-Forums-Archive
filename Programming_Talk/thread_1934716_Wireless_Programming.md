---
title: "Wireless Programming"
date: 2012-03-02
forum: Programming Talk
---

### Post by mikaelcrocker on 2012-03-02
I want to get into programming/communicating with wireless devices and such.  I've programmed and am most familiar with C++ and C# but also familiar with Ruby and Java as well.

I understand that certain devices or apps have an api to interface with, just looking for a place to start with something basic.  Any suggestions??

---

### Post by surfer on 2012-03-02
maybe i misunderstand, but all you have to learn is how to do tcp/ip programming. wireless (if you mean wifi and  not bluetooth or alike) devices look the same way as an ethernet cable once they have an ip address.

---

### Post by r-senior on 2012-03-02
Are you thinking of Bluetooth devices?

---

### Post by mikaelcrocker on 2012-03-02
> **surfer said:**
> maybe i misunderstand, but all you have to learn is how to do tcp/ip programming. wireless (if you mean wifi and  not bluetooth or alike) devices look the same way as an ethernet cable once they have an ip address.

Yea, Wifi is what I'm going for, I was just wanting to know what a good language is for programming or communicating via wifi.  i have looked into Ruby, but dont' know if there is a better way.  Thanks

---

### Post by Tony Flury on 2012-03-03
As previous people have said - unless you intend to re-write your wifi hardawre drivers, it shouldn't matter if your network connection is ethernet or wifi.

You need to look at a socket library - i know C/C++, python and a number of other languages have socket libraries - not sure about Ruby.

---

### Post by surfer on 2012-03-03
[twisted]("http://twistedmatrix.com/trac/") should let you do a lot of what you need if you want to program in python.

python has also a built-in socket module that could get you started.

---

