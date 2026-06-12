---
title: "In package list, what does [security] mean"
date: 2006-02-10
forum: Repositories &amp; Backports
---

### Post by billtom on 2006-02-10
In the package list, it shows the component, then on some items it also says [security]. I understand that this means that the package is available in the security repository.

But what I don't understand is what that means in terms of the management/updating of the package. 

What's the difference (in management/updating) between a package that says "[universe]" and a package that says "[universe][security]" or between one that says "" (meaning main component) and one that says just "[security]"?

I tried to search for the answer to this, but the word "security" is just too overloaded in meaning.

---

### Post by jasmuz on 2006-02-10
"Secutity" packages are usually security upgrades added both to security and universe repositories for further upgrading.

Each time a bug/flaw is corrected, a new "security" package is uploaded in order to replace the faulty one.

---

### Post by billtom on 2006-02-10
Sorry, still not entirely getting it.

Is this correct: if a package says "[universe][security]" does that mean that there are two versions of this package (one in the universe repository and one in the security repository) and I have to pick which one I want and that they will be upgraded separately based on different criteria?

And a package that only says "[security]" is only available in the security repository?

---

