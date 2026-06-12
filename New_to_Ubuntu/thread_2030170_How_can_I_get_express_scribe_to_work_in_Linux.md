---
title: "How can I get express scribe to work in Linux?"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by Ubercook on 2012-07-20
I am currently using Ubuntu 10.4. 

I'm trying to work for Scribie as a transcriber and they want me to use express scribe. 

I used this site and many others in my attempts to fix my problem.
[http://www.nch.com.au/scribe/linux.html](http://www.nch.com.au/scribe/linux.html)

Every time I try to use Wine I get this message.

"Could not open the file /home/javon/.cache/.fr-GVvkkh/scribe using the Western (WINDOWS-1252) character encoding.
Please check that you are not trying to open a binary file.
Select a different character encoding from the menu and try again."

I tried a few different character encoders but none of them have worked so far.

I also tried the GTK native and I always get the same message or 

"The file '/home/javon/Downloads/scribe (1).tar.gz' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit." 

I wonder if the software,Transcriber would work as a substitute or would this fail?

I know this is a lot to ask for....so I'll greatly appreciate it.:)

---

### Post by anewguy on 2012-07-20
The tar-gz file is compressed - you'll need to decompress it first.  Make sure the files you are trying to open as executable have the Xecute bit set in the permissions:

chmod +x <your file here>

---

### Post by Ubercook on 2012-07-21
> **anewguy said:**
> The tar-gz file is compressed - you'll need to decompress it first.  Make sure the files you are trying to open as executable have the Xecute bit set in the permissions:

chmod +x <your file here>

I have it running now. Thank you!:)

---

