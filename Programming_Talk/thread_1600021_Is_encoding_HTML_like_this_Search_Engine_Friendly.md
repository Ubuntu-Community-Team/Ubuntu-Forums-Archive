---
title: "Is encoding HTML like this Search Engine Friendly?"
date: 2010-10-18
forum: Programming Talk
---

### Post by adeee on 2010-10-18
For example the string "Download Best Media Player" can be encoded as 

```
&#38;&#35;&#54;&#56;&#59;&#38;&#35;&#49;&#49;&#49;&#59;&#38;&#35;&#49;&#49;&#57;&#59;&#38;&#35;&#49;&#49;&#48;&#59;&#38;&#35;&#49;&#48;&#56;&#59;&#38;&#35;&#49;&#49;&#49;&#59;&#38;&#35;&#57;&#55;&#59;&#38;&#35;&#49;&#48;&#48;&#59;&#38;&#35;&#51;&#50;&#59;&#38;&#35;&#54;&#54;&#59;&#38;&#35;&#49;&#48;&#49;&#59;&#38;&#35;&#49;&#49;&#53;&#59;&#38;&#35;&#49;&#49;&#54;&#59;&#38;&#35;&#51;&#50;&#59;&#38;&#35;&#55;&#55;&#59;&#38;&#35;&#49;&#48;&#49;&#59;&#38;&#35;&#49;&#48;&#48;&#59;&#38;&#35;&#49;&#48;&#53;&#59;&#38;&#35;&#57;&#55;&#59;&#38;&#35;&#51;&#50;&#59;&#38;&#35;&#56;&#48;&#59;&#38;&#35;&#49;&#48;&#56;&#59;&#38;&#35;&#57;&#55;&#59;&#38;&#35;&#49;&#50;&#49;&#59;&#38;&#35;&#49;&#48;&#49;&#59;&#38;&#35;&#49;&#49;&#52;&#59;
```
Is it search engine friendly?

I want to encode all on my text inside HTML page into this format, but only if it has no drawbacks.

Please help.

---

### Post by Reiger on 2010-10-18
Pointless.

---

### Post by schauerlich on 2010-10-18
Is this supposed to be some form of encryption so someone doesn't "steal" your page? Protip: if your browser can render it, it can easily be reverse engineered.

---

### Post by adeee on 2010-10-18
> **schauerlich said:**
> Is this supposed to be some form of encryption so someone doesn't "steal" your page? Protip: if your browser can render it, it can easily be reverse engineered.

I just want to protect my site from xss. htmlspecialchars() is another solution but the encoding i mentioned above is a quick way to check if everything on my page has been escaped. When i look at source i cannot guess whether a part of output has all special characters escaped. If i use this encoding, it will not only escape all special characters but also all other characters will be encoded and i would be able to check whether i forgot to escape any output, by having just an overview of the page's source.

---

### Post by Reiger on 2010-10-19
You don't understand XSS: [http://en.wikipedia.org/wiki/Cross-site_scripting](http://en.wikipedia.org/wiki/Cross-site_scripting) 

Read the opening sentence carefully: XSS is about injected code. So escape your code all you want, but a determined attack will be able to un-escape your code, analyze it, find an XSS vuln if one exists and exploit it as usual. 

So you are exactly as vulnerable to XSS with or without rewriting content to needlessly use character entities: the code is already injected before the escape routines run.

---

