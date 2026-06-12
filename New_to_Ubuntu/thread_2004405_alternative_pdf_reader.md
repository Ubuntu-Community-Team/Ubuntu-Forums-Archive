---
title: "alternative pdf reader"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by unibroker on 2012-06-15
I am running Ubuntu 12.04.  I have downloaded 2 large maps and viewed them in the default document viewer which I presume is evince; that's what Dash says.  Both times the maps were not sharp even to the point of not being able to read the street names.  I have looked for an alternative reader but a 2 year old Ubuntu forum recommended evince.  Any suggestions?

---

### Post by BBQdave on 2012-06-15
> **unibroker said:**
> I am running Ubuntu 12.04.  I have downloaded 2 large maps and viewed them in the default document viewer which I presume is evince; that's what Dash says.  Both times the maps were not sharp even to the point of not being able to read the street names.

ePDFViewer works well for me. Often you have to adjust the size and view percentage of the pdf, for clearer detail.

Currently, Adobe is not developing it's Reader for Linux. So, your best choice will be an Open Source pdf reader.

---

### Post by N0oki3 on 2012-06-15
Yup, as BBQDave said. But if you want Adobe reader you can still install it via wine

---

### Post by unibroker on 2012-06-15
> **BBQdave said:**
> ePDFViewer works well for me. Often you have to adjust the size and view percentage of the pdf, for clearer detail.

Currently, Adobe is not developing it's Reader for Linux. So, your best choice will be an Open Source pdf reader.
Thanks for the response.  I downloaded your suggestion from the Software Center but when I try to open the file with it all I get a flash "Loading" and then nothing.  Is it possible this graphics-intensive map is too much for it?

---

### Post by kanikilu on 2012-06-15
Acrobat Reader in wine? I can't imagine that's going to work well, but whatever floats your boat ;)

BTW, there's no harm in trying the native Adobe Acrobat Reader for linux, the package is in the partner repo, I think: ```
sudo apt-get install acroread
```

---

### Post by unibroker on 2012-06-15
> **kanikilu said:**
> Acrobat Reader in wine? I can't imagine that's going to work well, but whatever floats your boat ;)

BTW, there's no harm in trying the native Adobe Acrobat Reader for linux, the package is in the partner repo, I think: ```
sudo apt-get install acroread
```
I get:  ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package acroread
```

---

### Post by unibroker on 2012-06-15
Success!  I was able to download acroread direct from launchpad and then had to download acroread-common in order to install it.  I used it on a map that I couldn't read last night and it was crystal clear! Thanks for the suggestion kanikilu.

---

