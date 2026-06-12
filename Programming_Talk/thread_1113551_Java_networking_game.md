---
title: "Java networking game"
date: 2009-04-01
forum: Programming Talk
---

### Post by TCSnyder on 2009-04-01
I know Java very well, and i am wanting to make a Desktop app ( no i dont want an applet ) that we can play a card game. what is a good tutorial on sending data over the internet to another computer.

My Thoughts:
   all of my firends are using ubuntu (Thanks to me!), and i do have a server, i could write it to ssh login. when they log in, i could have the game write to a xml file or some sort, and each persons computer reload the file every second and read the last move. 

thats all i could think of to do it but i know there is a better way.

Thanks

---

### Post by simeon87 on 2009-04-02
I would write a server that can accept connections from other players using sockets and threads. One thread would handle the incoming connections and the communication with each player is handled using a single thread per player.

---

### Post by Choad on 2009-04-02
i've got to write a threaded network class for a game i'm making too so any tips on how to do this would be hugely apprieciated 

i've never done threads before. i know the theory, but i also know they're a right pain in practice.

---

### Post by TCSnyder on 2009-04-02
here i found a good guide
[http://http://www.cafeaulait.org/slides/sd2003west/sockets/Java_Socket_Programming.html]("http://http://www.cafeaulait.org/slides/sd2003west/sockets/Java_Socket_Programming.html")

---

