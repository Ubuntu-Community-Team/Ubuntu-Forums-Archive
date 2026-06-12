---
title: "[SOLVED] HTTP using C++"
date: 2007-10-31
forum: Programming Talk
---

### Post by Humph on 2007-10-31
I'm new to C/C++ and, for my first "proper" project, would like to write a dynamic DNS update app.

I'm more than happy (and to be honest rather like the idea of the challenge!) to write my own HTTP sockets "driver", but I'm unable to find a resource that indicates how to do this. In Win32 VB I had the option of the Winsock control or using the internet browser component. I'm not going to be needing anything more than simple text processing of webpages.

Can anyone point me at an article or two on how to do/learn about this, as I seem to be Googling for the wrong terms?

Many thanks.

---

### Post by LaRoza on 2007-10-31
My wiki has a link named "Socket Programming", which is what you want. [http://laroza.pbwiki.com/CC++](http://laroza.pbwiki.com/CC++)

If you able to use other languages, Python's standard library has easy to use functions for what you want.

---

### Post by slavik on 2007-10-31
or if you want a language closer to C, there is Perl. :)

---

### Post by LaRoza on 2007-10-31
> **slavik said:**
> or if you want a language closer to C, there is Perl. :)

Do you have any good links/references for socket programming in Perl? The Perl part of my wiki is lacking, and I would appreciate any recommendations.

---

### Post by slavik on 2007-10-31
[http://www.perlfect.com/articles/sockets.shtml](http://www.perlfect.com/articles/sockets.shtml)

"perl socket tutorial" in google brings back many tutorials with simple code, basically it is:

simple script to read the index page from google.com
```

use IO::Socket;
my $sock = new IO::Socket::INET ( PeerAddr => "google.com", PeerPort => 80, Proto => "tcp") or die $!; #create a new socket or die ... pretty readable, no?
print $sock "GET /index.html HTTP/1.0\nFrom: slava!!!\nUser-Agent: wget_sortof by slava\n\n"; #the HTTP request
read $sock, $message;
print $message;
close $sock;

```

---

### Post by LaRoza on 2007-10-31
> **slavik said:**
> [http://www.perlfect.com/articles/sockets.shtml](http://www.perlfect.com/articles/sockets.shtml)

"perl socket tutorial" in google brings back many tutorials with simple code, basically it is:


Thanks for replying. I am well aware of the power of google. I have a wiki covering many languages, and do not have time to learn them all with equal proficiency at once. Perl is a language I have "learned", but can not effectively program with. 

Your experience with Perl would be more useful than my judgement of the millions of available material.

-EDIT that tutorial was not very useful, I guess I will have to find more complete material later when I have time.

---

### Post by slavik on 2007-10-31
you need only the code ;)

---

### Post by LaRoza on 2007-10-31
> **slavik said:**
> you need only the code

The wiki isn't for me...

---

### Post by Humph on 2007-11-01
> **LaRoza said:**
> My wiki has a link named "Socket Programming", which is what you want. [http://laroza.pbwiki.com/CC++](http://laroza.pbwiki.com/CC++)


Thanks, LaRoza, that looks like just what I'm after. Looks like I have a lot of reading ahead of me!

---

