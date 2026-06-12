---
title: "How would you approach this webdev problem? (LAMP)"
date: 2008-08-18
forum: Programming Talk
---

### Post by rianjs on 2008-08-18
Scenario is this:

1) User uploads an image
2) Image is cropped, resized to highlight a specific feature (think selecting your face for a thumbnail for a dating site or something)
3) User clicks "finished"
4) Edited image is saved. Original, uncropped image is deleted.
5) The edited image should be saved (or saved locally and then moved) to a different physical server immediately.
5) URL of the new, modified image is put into the database, along with its meta information (user, timestamp, EXIF, etc.)

I've built the upload stuff, have a good idea of how to implement the image editing bits -- though I wouldn't mind your suggestions there, either -- but I am at a complete loss for how to move the image from its temporary location to a permanent home.

Suppose I wanted to move the image to a different physical server, on its own subdomain: image is edited, user clicks finished, and behind the scenes, the image is shoved off to a different physical server where its URL will is something like [http://media1.example.com/directory/filename.jpg](http://media1.example.com/directory/filename.jpg)

Once that physical server gets filled, the image would be written to media2.example.com/directory/filename.jpg, ad nauseum. So I can keep adding physical servers as each gets full.

I have no idea how to implement something like that using the LAMP stack. And since I don't really have any idea how to accomplish it, I'm having trouble doing useful web searches to move forward.

---

### Post by pdwerryhouse on 2008-08-18
The easiest way to do it would be to spawn off an scp process to copy the file. Set up ssh keys between the two hosts so that it doesn't need a password. The disadvantage to this method is that you'll need to call it with system() or exec() and some people consider this unclean/impure.

You could also have the destination directory NFS mounted onto the source server, and then just copy the files. Not really recommended, it's best to avoid NFS if you don't need it.

Another way to do it is to have the destination server running a program that accepts images via HTTP in the same way that your first server does, and then send them across with an HTTP POST.

---

### Post by pmasiar on 2008-08-18
Since PIL was added to Google App engine, you can develop and host all this for free at GAE, under one condition: Python.

---

### Post by rianjs on 2008-08-19
> **pmasiar said:**
> Since PIL was added to Google App engine, you can develop and host all this for free at GAE, under one condition: Python. Yeah, I've got nothing against Python at all, but this entire project was born as a way for me to learn the LAMP stack (less Linux, but it's a bonus), so I'm not super interested in doing it this way. In fact, once I've got a good handle on PHP, Apache, and MySQL, Python's next on that list for a couple of reasons. Perl's probably better for text parsing, but I have a data-mining project in mind that I think I could apply Python to pretty effectively.

If I ever decide to sell it, being tied to Google isn't a particularly desirable thing. (Unless I were selling to Google, of course.)

---

### Post by rianjs on 2008-08-19
> **pdwerryhouse said:**
> The easiest way to do it would be to spawn off an scp process to copy the file. Set up ssh keys between the two hosts so that it doesn't need a password. The disadvantage to this method is that you'll need to call it with system() or exec() and some people consider this unclean/impure.

You could also have the destination directory NFS mounted onto the source server, and then just copy the files. Not really recommended, it's best to avoid NFS if you don't need it.

Another way to do it is to have the destination server running a program that accepts images via HTTP in the same way that your first server does, and then send them across with an HTTP POST. Thanks for your input. I was hoping to avoid system calls, but if I can't, it's nice to know this before I go haring off down the wrong path. I didn't think there was a way I could do it with Apache+PHP without needing to go down to the system level. For some reason SCP didn't even occur to me... Thanks again, I'll look into it.

---

### Post by doas777 on 2008-08-19
> **rianjs said:**
> Thanks for your input. I was hoping to avoid system calls, but if I can't, it's nice to know this before I go haring off down the wrong path. I was thinking some kind of file-transfer thing, but wasn't sure. Was thinking rsync initially, but obviously that wasn't what I really needed. For some reason SCP didn't even occur to me... Thanks again, I'll look into it.

there may be another option, but I've never tried it with mysql so i can't swear it'll work for ya. just store the resultant byte stream in a binary field in your database.

usually at work I just point to a folder share on the network.

good luck,
Franlin

---

### Post by rianjs on 2008-08-19
> **doas777 said:**
> there may be another option, but I've never tried it with mysql so i can't swear it'll work for ya. just store the resultant byte stream in a binary field in your database.

usually at work I just point to a folder share on the network.

good luck,
Franlin Yeah, I'm trying to avoid that for scalability and server setup reasons. Right now I'm building with the idea of a beefy DB server, and a couple of stripped down servers running Apache+Squid for image serving. Highly-accessed files (CSS, icons, other static files like header and footer text) will be served from a CDN (Cachefly).

So yes, I did think of that. But with millions of entries, I'd rather not have each served from the DB. :)

---

