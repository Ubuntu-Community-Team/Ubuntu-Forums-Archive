---
title: "Hosting Code Online"
date: 2013-07-07
forum: Programming Talk
---

### Post by red willow on 2013-07-07
Hi, I'm interested in hosting code online. For example, how do people host games written in Java online? What is the HTML code needed to do this? Also, how is this done with C++ code?
Thanks

---

### Post by dazman19 on 2013-07-07
A java applet can be embedded in HTML page? Is this what you are getting at?
Obviously the person wont be able to use it unless they have the JRE installed.

---

### Post by trent.josephsen on 2013-07-07
Define "host" and "online". When I think of hosting code I'm usually thinking of stuff like Git or FTP. When you say "host games" I might think of games with a server multiplayer component. But neither of those implies HTML and your C++ comment suggests you may not be talking about simply embedding games in Web pages. What is it you really want to do?

---

### Post by red willow on 2013-07-07
Dazman's response is part of what I'm looking for. I googled 'java applet' and found some stuff on those, and embedding them. I'll have to try to make that work.
So simply embedding games into web pages is a lot of what I want to do. Is it possible to do that with C++? Also, how would I do that with Action Script 3 (flash)?

---

### Post by nvteighen on 2013-07-08
C++ and Flash have nothing to do with this: a Java applet is a program written in Java that is embedded using a tag in HTML (I don't remember if it's <embed> or <object>...). The user is required to have the Java Runtime installed (nearly everybody has it) with the Java browser plugin activated (nearly everyone has it). Be aware that Java is also a general purpose language that is able to create desktop applications, not only browser applets.

---

