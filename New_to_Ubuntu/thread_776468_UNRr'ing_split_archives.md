---
title: "UNRr'ing split archives"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by iSplicer on 2008-04-30
Hello all

I have a 6.6GB file that is split-rar archived in windows into 50MB chunks. I am trying to unrar it in ubuntu by installing "unrar", using this command:

sudo apt-get install unrar

However, although it works, it is dead slow. I have been unraring this archive for the last 20  minutes and it is still going. The annoying thing is that there is no progress bar displayed, and I have another 100GB of archived stuff to burn.

Can anyone kindly suggest an alternative to "unrar"?

Thanks

---

### Post by Monicker on 2008-04-30
If it was compressed using maximum compression, it may take a while, depending on the total number of files and their size.  I do not think using another package is going to be significantly different.

7zip has a module for handling rar files.

```
sudo apt-get install p7zip-rar
```


You could also get the linux binary from the rarlabs web site and try that.

---

### Post by iSplicer on 2008-04-30
Thankyou for the reply.

If I install the p7zip-rar, do I have to do any additional configuration, or willi t automatically use that when I right click the archive and select "extract here"?

I will try the linux version from rarlabs, hopefully I can get that working.

---

### Post by Monicker on 2008-04-30
> **iSplicer said:**
> Thankyou for the reply.

If I install the p7zip-rar, do I have to do any additional configuration, or willi t automatically use that when I right click the archive and select "extract here"?

I will try the linux version from rarlabs, hopefully I can get that working.


It should be automatic.  I would uninstall the original unrar package first.  I am not sure how it would handle it if multiple packages for decompressing rar files are installed.

---

### Post by iSplicer on 2008-04-30
> **Monicker said:**
> It should be automatic.  I would uninstall the original unrar package first.  I am not sure how it would handle it if multiple packages for decompressing rar files are installed.

OK, thanks once again. I will try it soon after I do my homework :guitar:

And the linux binaries from rarlabs should work on split archives, right?

---

### Post by abhiroopb on 2008-04-30
Even files of about 1gb take 3-5 minutes, you'll have to be patient I'm afraid.

---

### Post by iSplicer on 2008-04-30
> **abhiroopb said:**
> Even files of about 1gb take 3-5 minutes, you'll have to be patient I'm afraid.

Hmm.. Maybe its just my brain, since there is no progress bar. I will extract it in windows and measure the time, and I will do it in ubnutu and measure the time also. The placebo effect will nicely come into being when one method has a progress bar and the other one doesnt.

---

