---
title: "A strange issue with serial ports on Ubuntu 10.04"
date: 2011-07-29
forum: Programming Talk
---

### Post by dimentiy2k on 2011-07-29
Hello, 

now I'm working on the project where the serial ports used.
I encountered an annoying thing under Ubuntu 10.04.
When I open port (doesn't matter onboard uart or USB adapter) everything works fine, but after a short period of time ~1-10 minutes aproximately the code stops receiving data from the port. 

I used boost::asio. On Windows code works fine but on Ubuntu the issue occurs. I thought it's an issue of the asio. So, recently I changed the code to use native Linux api instead of boost::asio and I get the same behavior, unfortunately.

I also found post describing similar issue on the Ubuntu's forum. 
Here is one of them [http://ubuntuforums.org/showthread.php?t=1526906](http://ubuntuforums.org/showthread.php?t=1526906)

Thank you.

---

