---
title: "Shell Script FTPing Problems"
date: 2012-03-21
forum: Programming Talk
---

### Post by CrusaderAD on 2012-03-21
I have a shell script that does this via ftp:

```
mget *.txt
mdelete *.txt
```

I'm downloading batches of invoices all at once. Problem is that FTP is unreliable and sometimes just halts after a few downloads... stopping the script when this happens will delete everything up there and only get a few invoices. Any ideas? Is there an auto-retry option or something?

---

### Post by Lars Noodén on 2012-03-21
[ncftpget](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ncftpget.1.html) has the ability to resume interrupted transfers.  See the -z option.   I'm not sure how good the error checking is but it is a step in the right direction.

---

### Post by CrusaderAD on 2012-03-21
Looked super promising. I just tried it. It died after 12 transfers:

> Could not read reply from control connection -- timed out.
ncftpget /Invoices/*.pdf: timed out while waiting for server response.

I used -z in the command, but it just died. Any ideas?

---

### Post by Lars Noodén on 2012-03-21
Are you using passive mode?   You could try forcing it with -F

I have to admit I use FTP very little now and have become rusty.  I normally do small transfers with SFTP and large ones with rsync.

---

### Post by CrusaderAD on 2012-03-21
I did it with -zDD in the command, so now I can download and delete after a successful transfer. Even if the connection dies, I won't be downloading duplicate files which is what I was afraid of. I can run this as much as I want which is cool. I think this is working out pretty well... THANK YOU!

---

