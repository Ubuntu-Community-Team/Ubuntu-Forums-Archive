---
title: "Making An ISO file from a CD"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by Paper Pusher on 2012-09-29
I am running Ubuntu 12.4 DTE LTS.

I have a CD that I want to turn into an ISO file so I can attach it to an e-mail message.  How do I do that?

---

### Post by cbanakis on 2012-09-29
You should be able to just use Brasero.

Should already be installed.  (If not, its in the software center)

Select "Disk Copy" (second option from the bottom, on the left)

Select the disk you want to copy.

Click on properties, so you can enter a file name, and location for the iso.

Click on "Create Image"

---

### Post by NikTh on 2012-09-29
> **Paper Pusher said:**
> 

I have a CD that I want to turn into an ISO file so I can attach it to an e-mail message.  How do I do that?

You can do that 4 ways ,at least.

1 . Brasero as @cbanakis said 

2. k3b program , you can find and install in Software Center

3. AcetoneIso program. Software Center again . 

4. genisoimage (from generating iso image) program. This is command line tool. 

Thanks

---

### Post by cbanakis on 2012-09-29
On another note...

Just noticed you intend to email this iso?

Depending on the size, it is very unlikely that the file will be small enough to email.

If you don't already know, you will have to use a file hosting site, so you can upload the file there, then paste a link to it in your email.

Sites like sendspace, yousendit, dropbox...

There are hundreds.

---

### Post by NikTh on 2012-09-29
Ubuntu ONE offers 5GB of free space in any new User. [https://one.ubuntu.com/](https://one.ubuntu.com/)

---

### Post by HermanAB on 2012-09-29
Hmm, a CD *is* an ISO file.  So you don't need any special software to copy it to a hard disk. The good old kitty cat will do it for you just fine:
$ sudo cat /dev/cdrom > mycd.iso

You could also use data definition:
$ sudo dd if=/dev/cdrom of=mycd.iso

Or you could use any number of overly complicated programs like Brasero.

La voila!

---

### Post by black veils on 2012-09-29
when you upload to a file sharing website, there will be a file size limit, i think windows live skydrive is 100mb, and dropbox is 300mb.

---

### Post by TheMTtakeover on 2012-09-29
> **black veils said:**
> when you upload to a file sharing website, there will be a file size limit, i think windows live skydrive is 100mb, and dropbox is 300mb.

True, You may able to send it directly though something like Skype? I know AIM used to send directly but not it hosts the file instead.

---

### Post by cbanakis on 2012-09-29
I use torrents, but that is a bit complex for people who aren&#8217;t already doing it.

---

### Post by NikTh on 2012-09-29
> **black veils said:**
> when you upload to a file sharing website, there will be a file size limit, i think windows live skydrive is 100mb, and dropbox is 300mb.

I recently uploaded a file 1.2 GBs and shared with a friend of mine. 

Use Ubuntu One and enjoy the benefits (like integration to the Desktop)  and the big free cloud space of 5GB , and SHARE Everything  :)

---

### Post by Paper Pusher on 2012-09-29
Thank you very much for the excellent suggestions.  I ended up using the Barsero utility to create my ISO file.  It worked in the end but there were some funky aspects of Brasero that didn't make it too obvious.

---

