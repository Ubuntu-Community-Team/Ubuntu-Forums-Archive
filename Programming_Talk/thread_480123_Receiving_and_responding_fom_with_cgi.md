---
title: "Receiving and responding fom with cgi"
date: 2007-06-21
forum: Programming Talk
---

### Post by lrhaugen on 2007-06-21
Hi,
My secnario is that I have two scripts; one sender and one receiver. Both scripts are cgi and python.
The sender will make a request, where it posts a form. The receiver will receive the request, and based on the variables in the form, it will reply with a file. I think the easiest way to send the file back is with a new form. But how can I send a new form in the response? Whatever I am printing out on the receiver side, it is a part of the returning body and can easily be printed out on the sending side. But this time a print "" is not enough.

I have googled a lot, but it seems like I am the only one with this problem. 
Do you have any ideas? I have to make the 'file-response' in the same send/receive session. 

thanks!

---

### Post by pmasiar on 2007-06-21
> reply with a file

Easiest way to send file is send path to it. Both scripts are on same server, run as same user, so NP. If file needs be printed by receiver, send its URL.

---

### Post by lrhaugen on 2007-06-27
Hi, thanks for your reply.
The scripts should be running on different servers though.
I was so in to sending forms, that i forgot that this is actually a normal http get problem :-)

---

