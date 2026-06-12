---
title: "Raw sockets: type not supported"
date: 2006-01-27
forum: Programming Talk
---

### Post by Durkheim on 2006-01-27
Hello,

 The thing I want to do is: declare myself an ip header, a icmp header (to redo a ping style command), and send them trough a socket.

 To do so, I've tried to compile something like this:

```

if (socket(PF_INET,SOCK_RAW,0) == -1)
   {
      cout<<"error"<<endl;
      perror ("socket");
   }
   else
   {
      cout<<"cool"<<endl;
   }
```

The answer at run time :

```

error
socket: Socket type not supported
```

I'm using breezy badger. I'm wondering if this is a os related problem, or if I have to specifiy a protcol at the end (if this is the case, wich ones are supported?)... I'm really lost here.

I've been eading man pages for a few days but can't find the answer... Ay help appreciated. Thanks in advance!

David

---

### Post by LordHunter317 on 2006-01-27
Are you root?  Regular users don't normally have the capacity to open raw sockets.

---

### Post by jerome bettis on 2006-01-27
i used this library once, [http://www.alhem.net/Sockets/]("http://www.alhem.net/Sockets/")

not the best thing in the world, but it was certainly the easiest way i found (days on google) to get data going back and forth.  plus the author was very helpful when i had some questions.  i guess the best thing though was the documentation on the website, that program used to generate that is pretty slick.

---

