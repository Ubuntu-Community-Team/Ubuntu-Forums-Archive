---
title: "firewall problem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by wordmaster on 2008-05-11
On Pogo I get the following error when I try to play Texas Holdem:

Explanation:
In order to play, the Java applet must open a network connection to our servers. The applet was unable to open this connection. This could occur if you are trying to connect through your company's firewall. Other things that might cause this error are that our servers may be temporarily down or that one of our other systems is currently unavailable. This problem might also be caused by Internet connectivity problems.

How to Fix the Problem:
There may be the possibility that one or more of our servers are not running. We typically try to keep the server downtime for maintenance and upgrades to under 15 minutes, and we apologize for the inconvenience.

If you don't think that it's a server issue, then there are several things that could have gone wrong:

The server just started up and is still initializing.
Try playing the game again to see if you are able to connect.

There is a network problem that is preventing you from reaching the game server.
If you know how to use traceroute, you can try to find where the problem in the network is. Otherwise, you should try to play again later. Sometimes, major routing points have glitches in their systems that cause intermittent outages. If the problem persists for 24 hours, you should contact your network administrator or ISP for support.

You are located behind a firewall or proxy server.
If you are located behind a firewall or proxy server, you will not be able to play the game. The firewall/proxy is preventing the applet from connecting with the server (that is what the firewall is designed to do). This is typically what happens if you try to play from work. All you can do in this case is to play the game from an account that is not behind the firewall (for example, a home account instead of a work account).


How do I get past the firewall? Pogo is at [http://www.pogo.com](http://www.pogo.com)

Any help appreciated.

---

### Post by wordmaster on 2008-05-14
Surely someone can tell me about any firewall or something similar that is set up when Ubuntu is loaded. Please help.

---

### Post by wordmaster on 2008-05-18
bump

---

### Post by BCtom on 2008-05-18
It sounds like you are having problems with the Java Applet. I tried it with Java 6 and hit the same problems as you described.

I went here and followed these suggestions from this thread.

[http://ubuntuforums.org/showthread.php?t=784384](http://ubuntuforums.org/showthread.php?t=784384)

The trick was un-installing the Java - 6 programs, and switching back to sun-java 5, or 1.5.... check the link to the thread for the full procedure.

Anyway, I managed to get pogo working with Hardy and FF3.

---

