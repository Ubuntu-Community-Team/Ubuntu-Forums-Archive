---
title: "Java KeyListener Slow Response"
date: 2009-02-07
forum: Programming Talk
---

### Post by sjrf on 2009-02-07
Greetings,

I've just recently installed Ubuntu on one of my computers, and it seems that it's the only one that seems to have trouble with the response time of KeyListeners whilst running several threads simultaneously. I've come to the conclusion that it's probably on my side, and not Ubuntu's, as I've searched and nothing similar has come up on these forums, unless my search criteria wasn't general enough, which I highly doubt. My code works fine on Windows, and it worked fine on the computer that has Ubuntu currently, back when it was running Windows.

So, my question is, does anyone have a clue as to what my problem might be?

---

### Post by txcrackers on 2009-02-07
It may be the JVM you're running. For best results, make sure you're using the Sun JVM.

---

### Post by HotCupOfJava on 2009-02-07
> **txcrackers said:**
> It may be the JVM you're running. For best results, make sure you're using the Sun JVM.

I concur ... I'm not really having any issues with KeyListeners. Check out your virtual machine. I have noticed the best performance with Sun's stuff.

---

### Post by sjrf on 2009-02-07
I believe I am currently using the GVM, or something like that, so I will look into it, thanks for the help, both of you.

---

