---
title: "CLI tool to beam things to PDAs"
date: 2008-05-09
forum: Programming Talk
---

### Post by slavik on 2008-05-09
I work in a college where we have terminals that are used to look up books. We have an in-house Firefox extension that generates a map of where a book is when you are at a page with the book's call number.

It was coded for windows. I was able to port it to Linux.

The second part that relates to this extension is that when the map is displayed, it allows you to 'beam' the map to your PDA (anything with an infrared receiver).

Does anyone by chance know of any tool/library that can be called from another script in order to accomplish this simple task?

---

### Post by heikaman on 2008-05-09
slavik try **obexftp** or **ussp-push** to push OBEX objects, you can call it from your script. 
Both are in the repository, also check out **irda-utils**.

---

### Post by slavik on 2008-05-09
thank you. will give them a try.

---

### Post by slavik on 2008-05-13
ussp-push fits the bill perfectly, but for some reason, the sigmatel usb-irda adapter fails to send things (I do see that it is communicating with the PDA through wireshark).

---

