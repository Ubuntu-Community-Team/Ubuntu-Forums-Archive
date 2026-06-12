---
title: "Java MYSQL Connection Questions"
date: 2008-06-27
forum: Programming Talk
---

### Post by Black Mage on 2008-06-27
Hey, I'm writing a program in Java th connects to a MySQL Database over the internet and uses the standatard driver provided by MySQL. Now the questions I have is

1) Secure

Is doing this secure? Like is the username and password that connects to the database visible and easily sniffed or is it encrypted?

2)Speed

I'm using a gigaport switch but the connection is slow when I come through the internet even though my connection speed is12 Mbps provided by the ISP. Does connecting to a MySQL DB using the the MYSQL driver in Java require more than 12 Mbps to function at an acceptable rate? Because it takes like 30 seconds just to connect to the db externally, but is much faster when I keep it internal.

---

### Post by xlinuks on 2008-06-27
Hey, well, since you only mention that you write a Java program, we have no clue what's in and since _you_ write it - it's up to you whether it's secure or not - we cannot know.
I think you should write something like:
"Hey here's the code that I use to connect to the DB that is at such and such location.. - what should I do to make this code use a secure connection?"
Whatever that is I think you should google first, I'm pretty sure there's tons of info abou it..

---

