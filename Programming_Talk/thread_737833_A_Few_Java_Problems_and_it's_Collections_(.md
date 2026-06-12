---
title: "A Few Java Problems and it's Collections :("
date: 2008-03-28
forum: Programming Talk
---

### Post by The3rdhero on 2008-03-28
I have a Class called WebPageData and a Class Called Finder - I'm trying make a little search engine type app which will search through a Set for text and display how many words it finds.

In Finder, I have tried to assign WebPageData to a Set called searchedSites.

I get the following error:

cannot find symbol - method add(WebPageData)

Any idea what i've done wrong please? :)


```
   

private Set<String> scannedSites = new HashSet<String>();

public void addSite(WebPageData webpageData)
   {
      this.scannedSites.add(webpageData);
   }

```

Thank you.

---

### Post by CptPicard on 2008-03-28
Well, HashSet<*String*> scannedSites does not have a method "add" that takes the type WebPageData, does it :)

(I don't think toString() automagically works here, if that is what you're trying to achieve)

---

### Post by The3rdhero on 2008-03-28
So what shall I do?

---

### Post by themusicwave on 2008-03-28
Not knowing exactly what you are going for here, but I am assuming WebPageData is a class you made?

The problem is your HashSet only accepts String objects and you sent it a WebPageData object.  This is an error.

You have 2 options.

1) Don't use a HashSet of Strings, instead make a HashSet of WebPageData objects like so:

private Set<WebPageData> scannedSites = new HashSet<WebPageData>();

You now have a collection of all your WebPageData objects

2) Implement a getString() or getHashData() or whatever method in the WebPageData class to return a string to store in your HashSet.  This way you define what you need to store and save it in the HashSet.

Which one to do depends on what you are trying to do really.

---

