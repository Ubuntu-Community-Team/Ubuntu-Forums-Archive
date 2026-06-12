---
title: "Saving images from a website with Java"
date: 2010-11-02
forum: Programming Talk
---

### Post by Mike128 on 2010-11-02
Howdy all I was wondering if some kindly person might be able to help me out with the following:

I wish to run a program that will download a number of images from a website. All the images are at addresses of the form [http://[website](http://[website) address]/[folder]/[file.jpg].

I have a file already with a list of all the file names and of all the addresses in total so I want to be able to connect to each link, save the file there and then connect to the next link and so on. 
Possible bump in the road is that some of the images may not exist (though the vast majority do, I'm not blindly looking for anything) so it would need to be able to skip over these missing images and go on to the next line

currently the file I have is just a .txt with a list like:
[http://[website](http://[website) address]/[folder]/[file1.jpg]
[http://[website](http://[website) address]/[folder]/[file.2jpg]
[http://[website](http://[website) address]/[folder]/[file.3jpg]
[http://[website](http://[website) address]/[folder]/[file.4jpg]


I realize it's a lot to ask but I'm trying to get ahead of myself and actually do something useful rather than all the silly programs I've done so far.

---

### Post by spjackson on 2010-11-02
> **Mike128 said:**
> Howdy all I was wondering if some kindly person might be able to help me out with the following:

<snip>

I realize it's a lot to ask but I'm trying to get ahead of myself and actually do something useful rather than all the silly programs I've done so far.
What sort of help are you looking for? There will be plenty of examples available on the internet that show how to do this, e.g [http://download.oracle.com/javase/tutorial/networking/urls/readingURL.html](http://download.oracle.com/javase/tutorial/networking/urls/readingURL.html) This particular example is for a text file (it uses readLine()), but the same sort of principle applies for binary data. You need to create a java.net.URL with the URL of the file, open it for read (using java.io), open a local file for write, and copy the bytes using read() and write().

---

### Post by Some Penguin on 2010-11-02
Apache Httpclient is often used for this sort of thing.

That said, things to think about:

- how/whether to handle redirects
- how to handle case where server refuses to tell you how large a fetch will be (-1 content length)
- how to handle possibly transient failures like 500s
- whether the server will reject crawls from unknown user-agents or the like

---

