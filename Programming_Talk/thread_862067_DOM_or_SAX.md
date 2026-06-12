---
title: "DOM or SAX?"
date: 2008-07-17
forum: Programming Talk
---

### Post by rivalslayer on 2008-07-17
DOM or SAX? Which one is comparatively easier to learn? I need to know, as I will be starting to learn XML Manipulation with Python, if anyone can help me please do so...

I Googled out, and found that DOM is better for complex documents, but SAX is better in large documents with little amount of processing. And another thing is that SAX use less memory that DOM. 

So, which one to choose as a novice. I will be working with simple documents, that's all.
:confused:

---

### Post by archivator on 2008-07-17
Well, those are two tools for two different tasks. 

If you need direct access to the n-th child of the 3rd element in the document, go with DOM. If you, however, only need to parse 2 or 3 types of nodes and do no care that much about relationships (parents and children), I'd say SAX is a safe choice.

What I did in my last XML-parsing project was to use SAX. Then, in the middle of the project discovered that I'd been reimplementing DOM functionality on top of SAX and then just started anew with DOM. Trial and error is sometimes an inevitable approach.

---

### Post by pmasiar on 2008-07-17
... and the answer is: Python with ElementTree, which is much simpler than DOM or SAX.

SAX makes sense only if your file is really huge and you need just a small part.

---

### Post by LaRoza on 2008-07-17
About the memory, the DOM has to have the entire document read, and SAX doesn't. For most things I think, like webpages, the entire document is loaded anyway.

They are both easy. The DOM has only a handful of methods that need to be used a lot, and a reference will help with the rest. I can't imagine SAX being any more complicated and if the other solution is simpler still...

---

### Post by Yannick Le Saint kyncani on 2008-07-17
Yeah, don't use sax unless you're memory-constrained.

---

