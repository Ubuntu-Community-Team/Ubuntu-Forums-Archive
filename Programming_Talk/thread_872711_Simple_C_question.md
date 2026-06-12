---
title: "Simple C question"
date: 2008-07-28
forum: Programming Talk
---

### Post by blooddrunk on 2008-07-28
Is there a command in C which checks for an Internet connection?

---

### Post by LaRoza on 2008-07-28
Pinging google is one of the best ways to check.

C doesn't have "commands". It has keywords, and no keyword for that. And it has standard functions (and macros) and there isn't an Ansi C function for that.

---

### Post by lordhaworth on 2008-07-28
Just out of curiosity, why do you want to check for an internet connection in C? I'd be quite interested to hear the application in mind

---

### Post by blooddrunk on 2008-07-28
> **LaRoza said:**
> Pinging google is one of the best ways to check.

C doesn't have "commands". It has keywords, and no keyword for that. And it has standard functions (and macros) and there isn't an Ansi C function for that.


Yeah, I thought about the ping, but the problem is that you have to do it with system(). Unfortunately, system() somehow always returns 0 and I am interested in the return value of ping in order to find out whether there is a connection or not

---

### Post by lordhaworth on 2008-07-28
Not sure how well this work (i.e. i havnt tested it) but heres a link, it seems by the end this guy has achieved what you want to do. 

[http://cboard.cprogramming.com/archive/index.php/t-41635.html](http://cboard.cprogramming.com/archive/index.php/t-41635.html)

---

### Post by blooddrunk on 2008-07-28
Well, it says that it's a ping imitation program. I don't know, there has to be an easier way.

---

### Post by lordhaworth on 2008-07-28
If there are people building elaborate programs to imitate ping i doubt there are any built in or easily designed ways of doing it. I'd recommend finding (possibly a better) ping imitator, it should do the same thing, and then referencing to that in your program (i.e. use it as a module or subroutine). 
All you should have to do is copy and paste it and then referr to it - a reliable imitator should get you the same results

---

### Post by nvteighen on 2008-07-28
I've found a library for C and C++ that enables you to use the ICMP protocol. It's even in the repos! 

(EDIT: Ah, it's licensed under GPL not LGPL, so your application will have to be GPL'ed too if you are going to publish an application using this library...)

```

sudo apt-get install liboping0-dev

```

(Website: [http://verplant.org/liboping/](http://verplant.org/liboping/)).

---

### Post by lordhaworth on 2008-07-28
lol ok so maybe there is an easier way, this is pretty cool if it works, i never knew about that

---

### Post by nvteighen on 2008-07-28
> **lordhaworth said:**
> lol ok so maybe there is an easier way, this is pretty cool if it works, i never knew about that
Neither I... just curious and went to Google (and Synaptic).

It's not about "easier", but "saner". If your application will be pinging just to perform a connection check to afterwards do something else, then why bother to reimplement the whole thing?? Any reimplementation will have to conform to the ICMP specs! (or it won't be a ping).

But, of you're creating an application just to check your internet connection, maybe a shell script would be more appropiated?

---

### Post by LaRoza on 2008-07-28
> **nvteighen said:**
> 
It's not about "easier", but "saner". If your application will be pinging just to perform a connection check to afterwards do something else, then why bother to reimplement the whole thing?? Any reimplementation will have to conform to the ICMP specs! (or it won't be a ping).


Actually, I don't think a ping is probably needed. If this app relies on an internet connection, it will soon be obvious if one exists (like a web browser, it doesn't give errors until they happen)

---

### Post by Felson on 2008-07-28
Why not just try and open a remote socket on port 80 to a known location? If the socket fails, you have no internet...

---

### Post by LaRoza on 2008-07-28
> **Felson said:**
> Why not just try and open a remote socket on port 80 to a known location? If the socket fails, you have no internet...

Gee. I wish I thought of that...

---

### Post by slavik on 2008-07-28
> **Felson said:**
> Why not just try and open a remote socket on port 80 to a known location? If the socket fails, you have no internet...
or to the location you need to be able to connect to. :)

if you are looking for a network connection, you probably need to connect to someone, and if you don't, why check for a network connection?

---

### Post by blooddrunk on 2008-07-29
Thank you, Felson. Worked like a charm

---

### Post by Felson on 2008-07-29
@LaRoza
LOL Sorry. Just reread your answer, and realize that you said about the same thing I did. I somehow miss read it the last time.

---

### Post by LaRoza on 2008-07-29
> **Felson said:**
> @LaRoza
LOL Sorry. Just reread your answer, and realize that you said about the same thing I did. I somehow miss read it the last time.

That alright. Slavik just reworded my other suggestion also (if you are using the network, you don't need to check for it before hand)

---

### Post by sq377 on 2008-07-29
This is how I've always done it.  I just resolve the domain, and assume internet works if that does.  It's a really quick and simple check.

[PHP]#include <netdb.h>
#include <stdio.h>

int main(int argc, char **argv)
{
     if( gethostbyname("www.google.com") != NULL )
     {
          printf("Internet works\n");
     }
     else
     {
          printf("Internet doesn't work\n");
     }

     return 0;
}[/PHP]

---

### Post by Felson on 2008-07-29
That works depending on your purpose. If you are writing an app to tell you when and what is wrong with your internet, that is awesome for finding out if your DNS is down, but doesn't tell you if you are totally off line.

---

