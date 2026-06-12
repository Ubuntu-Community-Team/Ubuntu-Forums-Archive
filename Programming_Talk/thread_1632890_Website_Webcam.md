---
title: "Website Webcam"
date: 2010-11-28
forum: Programming Talk
---

### Post by Sub101 on 2010-11-28
Hi all,

Ive been looking into creating a website that takes a photo from a clients webcam and uploads it to the webserver. Obviously many technologies exist for this sort of thing, however most examples are involved with the client viewing a webcam on the server end.

Is there a standard/preffered language to do website and webcam programming in? I know the main methods are using either a Java applet, or Flash. However my understanding is that using webcams in Java requires the JMF library, which must be installed on every clients pc. And I dont have any experience with Flash.

That being said, if the consensus is that Flash, or any other language, is the way to go with such a system then I would obviously start working towards expanding my knowledge.

Thanks for your time and thoughts.

---

### Post by PaulM1985 on 2010-11-29
I think another problem with this if you are going to use Java is that I don't think the applet will actually be able to access the clients webcam.

Applets run in a sandbox and so are very limited to what they can actually do.  I think you will need to have to make sure it is signed before you are able to do anything with the client's pc.

Paul

---

### Post by Sub101 on 2010-11-29
> **PaulM1985 said:**
> I think another problem with this if you are going to use Java is that I don't think the applet will actually be able to access the clients webcam.

Applets run in a sandbox and so are very limited to what they can actually do.  I think you will need to have to make sure it is signed before you are able to do anything with the client's pc.

Paul


So Flash would really be the only way?

---

