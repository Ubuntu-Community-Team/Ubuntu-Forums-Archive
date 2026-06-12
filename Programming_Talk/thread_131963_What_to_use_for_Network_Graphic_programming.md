---
title: "What to use for Network Graphic programming"
date: 2006-02-17
forum: Programming Talk
---

### Post by EstevaoSoares on 2006-02-17
Hi folks...

Firt, thanks a lot for your time here. 


My doubt is what laguage and where to start. 

I need to make a program that will log into various server (Solaris, Suse, Redhat Enterprise) and them I'll be able to see and manage disk space, edit files etc... 

I just a need to make this under a visual interface, wxpython, gtk, I really don't know and don't have a clue where to start, what to do. 

Could someone, please, help me? 

(ps. don't worry about my program level, this won't be an issue)

---

### Post by healychan on 2006-02-17
If I were you, I will use Java.

1. Java can make GUI easily with the swing package.
2. Java has a rich lib for network programming.

Are you trying to make something like telnet/ssh ???

---

### Post by toojays on 2006-02-17
Are you familiar with the concept called "X Network Transparency"?

As long as you have the right program on the server, you can just use the program you would normally use, but run it on the server. For example "ssh -X user@server konqueror" or "ssh -X user@server nautilus".

Alternatively, you can take advantage of the fact that most KDE applications have network transparency built in, and just load a local konqueror and login to a remote server using sftp:// or fish://.

---

### Post by healychan on 2006-02-18
[QUOTE=toojays]Are you familiar with the concept called "X Network Transparency"?

As long as you have the right program on the server, you can just use the program you would normally use, but run it on the server. For example "ssh -X user@server konqueror" or "ssh -X user@server nautilus".

Alternatively, you can take advantage of the fact that most KDE applications have network transparency built in, and just load a local konqueror and login to a remote server using sftp:// or fish://.[/QUOTE]

He is right.

If your target server provides X Window service, you can have your GUI run on the server side but display locally. It is not worth to create a new program because there are already many of them available.

---

### Post by EstevaoSoares on 2006-02-20
[QUOTE=healychan]He is right.

If your target server provides X Window service, you can have your GUI run on the server side but display locally. It is not worth to create a new program because there are already many of them available.[/QUOTE]


Thanks for you answers, all of you. 


The remote servers dos not provides X Window service and for sure, this is not an option in my enviroment. That's actualy the main reason to make such a program. 


Answering the second post. 

Yah, is somenthing like ssh but graphical interface and more powerfull too. 

Java could be an option I really didn't think about it before.
Someone could point me some direction, where to start, what library or somenthing like that, a tuto, book in somewhere. 


Thanks a lot guys!

---

### Post by toojays on 2006-02-21
Hehe . . . sorry, but describing the kind of program you're talking about as "more powerful than ssh" doesn't make any sense. SSH is essentially an enabling technology, like Emacs or zero. It's comparing the sublime with the mundane . . . it just doesn't make sense.

I still think your best bet is to get an X client library onto the server. If you can run arbitrary programs, you should be able to X11 over ssh. You don't need root access for that.

---

### Post by EstevaoSoares on 2006-02-21
[QUOTE=toojays]Hehe . . . sorry, but describing the kind of program you're talking about as "more powerful than ssh" doesn't make any sense. SSH is essentially an enabling technology, like Emacs or zero. It's comparing the sublime with the mundane . . . it just doesn't make sense.

I still think your best bet is to get an X client library onto the server. If you can run arbitrary programs, you should be able to X11 over ssh. You don't need root access for that.[/QUOTE]


Sorry, I have to admit, it really makes no sense :D 

My "more powerfull" was something graphical programmed by me. I missed the point. 


Even so, I would like to do it by myself and no to install or depend of anytning to connect, that`s the ideia, got it ?


Thanks again.

---

