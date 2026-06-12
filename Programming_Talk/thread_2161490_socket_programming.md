---
title: "socket programming"
date: 2013-07-10
forum: Programming Talk
---

### Post by jairoh_ on 2013-07-10
hi everyone, i'm built a chat program and it worked but i don't wanna be limited on sending message only, but i want to send files like images, .docs and etc. Anyone have an idea how to do it? tnx

Language: JAVA

---

### Post by 1clue on 2013-07-10
What language?

---

### Post by 1clue on 2013-07-10
I guess it doesn't really matter what language.  You can send objects through the wire from one language to another, as long as both sides agree on what it is that's being transferred.

Back when I learned this people were writing both sides of the socket, so you had control of what exactly was going on.  Now, we have things like Representative State Transfer (REST) and pass data in standard formats.  JSON is an example.  If both sides have a standards-compliant parser for the sort of data being passed, then you have valid transfers.

This works for anything, you can basically take any object and either break it down into an array of bytes or you can turn it into something like a map, with key-value pairs.

All this requires a basic agreement on what's being transferred.  A PDF for example needs a standard writer on one side, then you pass the bytes, then you have a standard reader on the other.

---

### Post by jairoh_ on 2013-07-11
updated i'm actually using java sir

---

### Post by 1clue on 2013-07-11
I can help more then.  What's the application?  Are you making a web application inside an app server, or some other kind of socket.  Do you have any details?

---

### Post by jairoh_ on 2013-07-12
> **1clue said:**
> I can help more then.  What's the application?  Are you making a web application inside an app server, or some other kind of socket.  Do you have any details?

just desktop app. i already made chat program when a server can chat to many clients and a client back to server or a client to another client. I don't wanna be limited on just sending a message. i want to send a file like images, word documents and etc. you might wanna share some idea sir? that would be so helpful for me learning things.

---

### Post by 1clue on 2013-07-12
OK well since this is Java, pretty much all of this stuff has been thought of and solved.  Look at ObjectOutputStream and work from there.

---

### Post by mni on 2013-07-13
> **jairoh_ said:**
> just desktop app. i already made chat program when a server can chat to many clients and a client back to server or a client to another client. I don't wanna be limited on just sending a message. i want to send a file like images, word documents and etc. you might wanna share some idea sir? that would be so helpful for me learning things.

Hi Jairoh,

What is your protocol for sending message, http or xmpp..?. I use xmpp just for send text,emoji, and stamp, but for send image, audio and video, **Do not use xmpp**, but use http and use multipart for send image. For your information, use smack openfire as the **xmpp **library if you want to developing chat app for desktop. Smack is build for android and desktop,



**Iqbal**

---

