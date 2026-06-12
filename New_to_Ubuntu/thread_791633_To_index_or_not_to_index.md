---
title: "To index or not to index?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Sain on 2008-05-12
:)

I was just configuring Beagle search on my Kubuntu, and I set it to index my entire filesystem (/)... I'd like to have my entire hard drive indexed so I can find any file on the disk fast.

But was it a good idea? Will it get too slow? Or should I just set it to index where I keep my documents?

---

### Post by GPearce on 2008-05-12
If you're likely to be looking for files in the main filesystem regularly, then you should index the whole thing. If you're only really likely to use your own files in your own directory, just index that - it stops a lot of results coming from the system files that you don't need.

---

### Post by Oldsoldier2003 on 2008-05-12
> **Sain said:**
> :)

I was just configuring Beagle search on my Kubuntu, and I set it to index my entire filesystem (/)... I'd like to have my entire hard drive indexed so I can find any file on the disk fast.

But was it a good idea? Will it get too slow? Or should I just set it to index where I keep my documents?
Honestly after playing with beagle and tracker I've pretty well decided that they just eat cpu cycles without giving back enough in return. Some people may find them useful but in my book they are just a waste of resources and have removed them from my system.

---

### Post by tacutu on 2008-05-12
are you likely to look for content in the filesystem? Beagle is useful for searching the content of the files (documents, mails). On the filesystem you'll be probably looking for filenames, to see if you have a certain library, where that executable is located and so on. But for this, slocate is enough (updatedb is run daily by cron, AFAIK).

So personally I think it is a waste of CPU cycles to index the /

---

