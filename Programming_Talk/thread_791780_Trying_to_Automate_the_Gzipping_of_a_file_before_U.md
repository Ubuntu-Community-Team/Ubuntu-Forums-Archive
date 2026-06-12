---
title: "Trying to Automate the Gzipping of a file before Uploading via HTTP"
date: 2008-05-12
forum: Programming Talk
---

### Post by ExtremeClean on 2008-05-12
Essentially here is my dilema

I have a page to upload a single file to a server that processes the information in the file. It is all done in one click.

What I want to do is gzip the file before uploading it (the files get pretty big)

How can I set it up to gzip the file THEN upload to the server, im having trouble with the upload portion because I only know how to upload using the standard <input type=file name=file1 > type stuff then handling it as a multi-part request.

Is there any way that when the user selects his file and clicks upload It can gzip and upload that file?

My current idea is to just gzip the file then create my own POST header from scratch in a String then passing the string through the output stream to the server, where the file contents in the header is just the byte array of the gzip file.

Any help is appreciated

---

### Post by Verminox on 2008-05-12
I'm confused whether you are just a client wanting to upload a bunch of files to a remote server or if you are the server wanting users to upload files to your script.

If it's the first case:
It would be impossible to send a gzipped file to a server if the server does not have a mechanism to automatically detect this format and decompress it.

For the latter case:
If you want to compress a file before uploading then obviously you have to tell the browser to perform this action. Now, as you cannot rely on any third party browser add-ons for such an activity you will have to rely on client side scripting ---> Javascript.

Unfortunately, for security measures, Javascript cannot access local files on the client computer, so even if you do end up making a wild algorithm to perform a GZIP compression on a string using Javascript it is pointless because you won't be able to access the contents of the file to be uploaded in the first place.

If you know Java you could try building an applet to do this though. I'm sure it's possible through an applet but this comes with all the disadvantages a Java applet brings, so keep that in mind.

---

### Post by ExtremeClean on 2008-05-12
the server does handle gzip files fine, at the moment I just gzip manually prior to uploading, however i am trying to create it on the Client side where when they select the file they wish to upload, it gzips it before uploading.

---

### Post by Verminox on 2008-05-12
If it is to be implemented on the client side, it has to be implemented in the browser. As I mentioned above, Javascript cannot read files so it's not possible with that. 

I can't think of any other way to access local files and process them before upload other than a Java applet or a browser modification (eg. Firefox add-on).

You can however make your own script in a different language that automates this process. But every user who wishes to use this would have to launch that script separately, and not through the original HTML web page interface.

---

