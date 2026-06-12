---
title: "Reading a serial interface async. with Boost::Asio"
date: 2008-10-04
forum: Programming Talk
---

### Post by meastp on 2008-10-04
I have an Arduino with an RFID reader. Whenever the reader registers an RFID, the Arduino sends this ID through the serial interface.

Therefore, I'd like to make an asynchronous function to process this ID from a serial interface. Like, do_something() whenever an ID is recieved.

I have read a bit about boost.asio[1], which treats a serial interface as a buffer, and can read asynchronously via async_read()[2]

Anyway, my question is if I am right in assuming that this is perfectly doable, and not that hard for a relative beginner like myself. Also, is asio packaged for ubuntu?


[2] [http://www.boost.org/doc/libs/1_35_0/doc/html/boost_asio/reference/async_read/overload1.html](http://www.boost.org/doc/libs/1_35_0/doc/html/boost_asio/reference/async_read/overload1.html)

[1] [http://www.boost.org/doc/libs/1_36_0/doc/html/boost_asio.html](http://www.boost.org/doc/libs/1_36_0/doc/html/boost_asio.html)

---

### Post by dwhitney67 on 2008-10-04
> **meastp said:**
> ...
Also, is asio packaged for ubuntu?

Yes, the Boost libraries are available for Ubuntu.

The "universe" repository needs to be enabled in your system's software sources.  If you have not already done this, it can be done via the gnome interface:  **System->Administration->Software Sources**

Afterwards, to get the Boost libraries, enter this on the command line:
```
sudo apt-get install libboost*
```

As for actually using Boost::asio, I have not.

---

### Post by meastp on 2008-10-05
> **dwhitney67 said:**
> Yes, the Boost libraries are available for Ubuntu.

The "universe" repository needs to be enabled in your system's software sources.  If you have not already done this, it can be done via the gnome interface:  **System->Administration->Software Sources**

Afterwards, to get the Boost libraries, enter this on the command line:
```
sudo apt-get install libboost*
```

As for actually using Boost::asio, I have not.

I'm sorry if I wasn't clear. The reason I asked is this bug:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg871472.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg871472.html)

---

