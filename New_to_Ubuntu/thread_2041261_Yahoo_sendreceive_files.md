---
title: "Yahoo send/receive files"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by Georgescu1 on 2012-08-12
I have ubuntu 12.04
Tried:
-pidgin-only can receive file, can't send(the file doesn't appear to the person i send it to).
-empathy-can't connect to id-failure to connect error
-gyache-can't send/receive file
-kopete-can't send file

Very frustrating.
I am not even looking for a video/audio call since that is a fantasy in linux, I just want to talk and send/receive files and hope that in the next 200 years when cars will start flying ubuntu will actually have a audio call function which seems as basic as having a wallpaper, for a windows user.

---

### Post by llamabr on 2012-08-12
I can't quite make out your question.  You want to chat via an instant messenger, and also send/receive files?

Mine works fine, using pidgin, but of course there are dozens of other way to do so.  I like google chat.  You might benefit from getting the plugin right from google:

[http://www.google.com/talk/](http://www.google.com/talk/)

---

### Post by Georgescu1 on 2012-08-12
> **llamabr said:**
> I can't quite make out your question.  You want to chat via an instant messenger, and also send/receive files?

Mine works fine, using pidgin, but of course there are dozens of other way to do so.  I like google chat.  You might benefit from getting the plugin right from google:

[http://www.google.com/talk/](http://www.google.com/talk/)

1.
Mine doesn't work to send files.
Friends don't see the request to accept or decline the files I send them.
I've seen alot of people having my problem,they didn't get a reply that actually helps them , that's why I asked.

2.
I need something for yahoo not other protocols else Skype works perfectly fine at sending/receiving files and video/audio functions , desktop share ect

---

### Post by TheFu on 2012-08-12
It is possible that you have a firewall enabled that is blocking all the requests? Since all the programs you have tried are failing, I'd think it was something like that.

What do the log files in /var/log show related to this issue?  I would start my research by opening a terminal and typing:
```
 sudo egrep -i error /var/log/*log | more
```It might be useful to search for the specific program you are running instead of "error" to see what that program is having trouble doing too.

To check the firewall status, I would start with 
```
sudo iptables -L | more
```I'm pretty certain there are other ways to accomplish these things - perhaps through the GUI, but this was easier to type here.

These connections could also be blocked by a hardware firewall on your network. I don't know anything about transmitting files through chat clients, sorry. 

Anyway, we'd like to help if we can.

---

### Post by llamabr on 2012-08-12
> **Georgescu1 said:**
> 1.

I need something for yahoo not other protocols else Skype works perfectly fine at sending/receiving files and video/audio functions , desktop share ect

What does that mean for yahoo?  Are you using pidgin or emphathy?

---

### Post by mastablasta on 2012-08-12
> **Georgescu1 said:**
> 
2.
I need something for yahoo not other protocols else Skype works perfectly fine at sending/receiving files and video/audio functions , desktop share ect

Gyachee improved is what you are looking for. It's kind of opensource yahoo messanger.: [http://sourceforge.net/projects/gyachi/](http://sourceforge.net/projects/gyachi/)

---

### Post by wh1zz0 on 2012-08-12
I'm having this same issue with Pigdin (on Yahoo). 

Ever since 11.10 I've been unable to send files via chat window, although I can receive files sent to me. 

I'm now on 12.04 but still haven't found a fix.

---

