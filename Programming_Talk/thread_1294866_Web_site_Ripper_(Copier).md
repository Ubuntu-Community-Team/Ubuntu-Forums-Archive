---
title: "Web site Ripper (Copier)"
date: 2009-10-18
forum: Programming Talk
---

### Post by mihnea.radulescu on 2009-10-18
Hello everybody!

I'm thinking of developing a web site ripper (copier) application. As I see it, it is not a very complicated task in terms of the overall picture. However, challenges may arise when developing particular features, at a finer level of granularity.

So, in large, I think I need to:
- get the required html document
- construct a document links tree
- recursively parse the initial document to find links to other documents and add them to the document tree
- once the tree is constructed, recursively get the desired resources (say, all the documents or just the images) and store them on disc
- modify the links in the locally stored html documents to point to the local disc structure

Is there anything specific that I should be careful with? What challenges may arise? Have I missed something important? I would welcome your feedback.

Best regards!

---

### Post by slavik on 2009-10-18
Shouldn't be very difficult, assuming you are using a language that makes text processing easy enough..

There is also wget that can do this.

---

### Post by Sub101 on 2009-10-18
It is a releatively simple thing to do... especially if everything is on the same server. ie.

```
wget -r **MY URL**
```

would copy everypage and image stored at My Url.

---

### Post by jessiebrownjr on 2009-10-18
Internet exploder used to have this(don't use it anymore) but you could download webpages for offline viewing, and set it up how many pages deep you wanted it to download..
 
Im learning programming so I can't be too much help with you coding it, but you might want to consider a way to block out spam links or certain links... like, if its a link to a porn site, don't click it and download all that crap..  90% of the sites I use on a daily basis seem to have a semi naked chick or dating site advert on there somewhere! Maybe make it take out certain types of script that would be used for adds as well :-)

---

