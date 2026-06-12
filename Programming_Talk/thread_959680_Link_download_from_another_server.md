---
title: "Link download from another server"
date: 2008-10-26
forum: Programming Talk
---

### Post by Bradosia on 2008-10-26
Hello,
I have a download page on my website that currently links downloads to my files.
An example would be a link such as
[http://www.aisodar.com/download/file.zip]("http://www.aisodar.com/download/file.zip")

My server has run out of storage space, so I now store my files on another server. What I am trying to do is make a download link from my website to download a file from another website.
An example would be a link on my site like this:
[http://www.freewebs.com/osia/file.zip]("http://www.freewebs.com/osia/file.zip")

Can anyone help me with the coding to create a link or button that can download files from another server.

---

### Post by Ferrat on 2008-10-26
is there something special you need it to do? if not that it should just link to that place and you download from there? 

don't really understand what it is that you want to do?

---

### Post by Bradosia on 2008-10-26
the link i put on my download page is [http://www.freewebs.com/osia/file.zip]("http://www.freewebs.com/osia/file.zip")

For some reason it wont let me download, all it does is refreshes the page. Try clicking for yourself and it gives you no download, then type the same thing in your browsers address bar and it downloads.

But then the same file from my website downloads perfectly:
[http://www.aisodar.com/download/file.zip]("http://www.aisodar.com/download/file.zip")

---

### Post by StOoZ on 2008-10-26
hmmm , take a look at cURL library..

---

### Post by Bradosia on 2008-10-26
I solved the problem myself.
Seems freewebs doesn't let you download its files from links.
Thank you everyone for helping me.

---

