---
title: "best way to develop for iOS and Android?"
date: 2010-12-28
forum: Programming Talk
---

### Post by Molion on 2010-12-28
Ijust wondered, what is the best way to make apps for both iOS and Android, do I have to just make 2 apps, or is there some easier way?

---

### Post by idi0tf0wl on 2010-12-30
One way or another, yes, you do. The closest you'll get to a one-size-fits-all code base is going to be to develop your application entirely in html/css/javascript so you can just point each platform's individual implementations of web views to an assets folder. Designing your application in this way can be severely limiting, however, but in this way you'll be able to easily "port" any app you write to pretty much any platform. I've done this, so I can vouch for its effectiveness!:wink:

There is another effort to make cross-platform coding possible for the mobile environment, but there are some problems from Apple's side, because it eliminates the need to use a Mac for development (but not really, they're just meanie-faces), and, as fate would have it, it's built off of the exact same principle as above anyway, so you'll probably be best served to just write the framework (or at least so to speak) for yourself. You'll have better control over it that way anyway.

Cheers!

---

### Post by Tahakki on 2010-12-30
Probably not, unfortunately. However, once you have a decent knowledge of both Java and ObjC, porting isn't massively difficult. I'd start with Android in Eclipse.

---

### Post by PaulM1985 on 2010-12-31
Coincidentally, I was also looking into developing for Android yesterday.  I found these links and they got me off working ok:

[http://developer.android.com/guide/developing/eclipse-adt.html](http://developer.android.com/guide/developing/eclipse-adt.html)
[http://developer.android.com/sdk/eclipse-adt.html#installing](http://developer.android.com/sdk/eclipse-adt.html#installing)
[http://developer.android.com/sdk/installing.html#InstallingADT](http://developer.android.com/sdk/installing.html#InstallingADT)

Paul

---

