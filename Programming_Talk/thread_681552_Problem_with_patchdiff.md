---
title: "Problem with patch/diff"
date: 2008-01-29
forum: Programming Talk
---

### Post by cudds on 2008-01-29
I'm trying to patch across a diff file that I've got from google's safebrowisng api which looks something like this

+000bd0e0987e3252177001ee6cb03b6d
+001b9d557d0bdc82e319e0839af597d3
+002af1f96eb0cac23c1620acbb6de966
+002df0577d0b50adf821f54398452e0c
+0034429ea4793ff23e76cf12532cca18
+0045efc982ca111ee77f1674ce819b5a
+006767a8818b2fcd70b7adbe9e4decf6
+0076885464388840480ce4b801d4677c
+007a6e4a9bfbddb7b28ec56bba927156
+007d8f401b4f6e1be30122526c26faaa
+0099079997574f312940d768a695df44
+009f44f815253ec9c8387bcef85776e6
+00a1f3b87727e14ecd53ac952bf95839
+00d439a3041b66a90a773768cc3e84ba
+00dc84863de491bacb29f51e0f0c39b2
+00dda740c7de0bda267e1d8e8bbf0a46
+00fd810d25bf1916770e6bf063444b69
+0103d55428da444cb785884b28980965
+011b11f03db9128aec07b081a1efcdda


nothing too complex there - in the unified format I can see

So I try 



sudo patch -u -i update\?client\=api\&apikey\=ABQIAAAAj_FbuB3KI4WcXQGhmQgN2xQWPDu-zgE5xBGilwtQRT4OjfDmKw\&version\=goog-black-hash\:1\:-1 -o testhold.url 

and I get...

patch: **** Only garbage was found in the patch input.

Garbage? It looks pretty good to me. Can anybody help me? Don't know where to turn.

---

### Post by cudds on 2008-01-29
Sorry I don't mean a problem with patch per-se - just my understanding of it! lol

---

### Post by cudds on 2008-01-29
ok so it looks like unified diffs have headers such as

```
-- original timestamp
+++ new      timestamp
@@ -1,3 +1,9 @@
+This is an important
```
[http://en.wikipedia.org/wiki/Diff](http://en.wikipedia.org/wiki/Diff)

However - my diff won't have a header I just want it to compare and add if it sees a + and subtrate if it sees a -. Nothing too complex I wouldn't of thought - how do I force this?

---

