---
title: "[SOLVED] Receiving HTTP POST with Java"
date: 2008-02-28
forum: Programming Talk
---

### Post by spupy on 2008-02-28
Hello. I need some help with understanding HTTP and POST requests.
There is a program that sends notifications via POSTs to a servlet (or any kind of script) on a server. I wrote a Java program to act as some kind of simple http server, receive this POST message, parse it and do other stuff. 
In my Java program i have a Server socket that accepts the connection from the other program, then reads lines from the new socket. 
1. The first problem is that when i want to do readLine() on the last line from the content of the request, my Java program stalls. As if there is no end line delimiter on the end of  message.  I guess i should use the content-length http header to know when the message is over? 
2. And another thing: in this kind of relationship - a program makes a POST request - which side should close the connection - the client or the server (my program)?
3. One last question: When receiving the POST request and reading the whole message, should i send back some kind of response? HTTP 200 OK?

Many thanks for any tips/answers! :)

---

### Post by pmasiar on 2008-02-28
You are writing HTML header parser to process CGI request? Why not use some from existing solutions instead of reinventing a wheel? And why doing it in Java if so many superior solutions exist in more flexible languages like Perl, Python, PHP, Ruby?

---

### Post by lnostdal on 2008-02-28
i don't have time to answer properly, but: [http://www.jmarshall.com/easy/http/](http://www.jmarshall.com/easy/http/)

---

### Post by spupy on 2008-02-28
> **lnostdal said:**
> i don't have time to answer properly, but: [http://www.jmarshall.com/easy/http/](http://www.jmarshall.com/easy/http/)

Thanks! I have stumbled on this link, but discarded it then. Don't know why, seems useful.

[QUOTE=pmasiar]You are writing HTML header parser to process CGI request? Why not use some from existing solutions instead of reinventing a wheel? And why doing it in Java if so many superior solutions exist in more flexible languages like Perl, Python, PHP, Ruby?
[/QUOTE]

It should be a simple program - the source of the requests comes from only one source. I discard the headers because they have nothing i need (apart from the content-length header). I just need the content.
It's in Java because of some other tools i use with the program.

---

### Post by a9bejo on 2008-02-29
> **spupy said:**
> 1. The first problem is that when i want to do readLine() on the last line from the content of the request, my Java program stalls. As if there is no end line delimiter on the end of  message.  I guess i should use the content-length http header to know when the message is over? 


Yes, use content-length or transfer-encoding headers to check if the request is valid and how much you have to read.  

> **spupy said:**
> 
2. And another thing: in this kind of relationship - a program makes a POST request - which side should close the connection - the client or the server (my program)?


The connection needs to be closed on both ends.  The client is responsible for ending the conversation by closing its connection after sending the message. However, the server must not rely on that to happen.  A server should close the connection itself after a certain time.  Java socket classes already offer timeout properties to do this.

> **spupy said:**
> 
3. One last question: When receiving the POST request and reading the whole message, should i send back some kind of response? HTTP 200 OK?


Yes. Exactly. But only if the request was valid and there were no errors of course.

---

### Post by spupy on 2008-02-29
Yeah, i figured it out. I was using BufferedInputReader, which messed up the InputStream that I'm using later on, because it's buffered. Now i just read everything in chars and it works ok.

---

