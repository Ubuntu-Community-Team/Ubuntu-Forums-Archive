---
title: "Aspell problem with currency symbol"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by MaxVK on 2008-04-22
Hi there, I'm having a little problem with aspell:

I am calling aspell to spell check a document and pipe the results to another document with the following command line:

```
aspell pipe < File1 > File2
```

This works exactly as expected and the resulting file contains a series of lines that are either a * to show that the word is spelled correctly, or a line which includes the word, its position in the file, and a list of suggested corrections.

However, if I type "£2" into the document to be checked (Just in case you cant see that symbol correctly it is a GBP (British Pound) symbol) all subsequent spelling mistakes *after* that symbol are reported to be one character position before they really are

So for example, in the phrase "bad spilling", the start of the badly spelled word is in position 4. However, if a GBP symbol had been used before the badly spelled word, it would be reported as being in position 3, which is incorrect.

Is this a bug of some kind with aspell, or am I missing some option or switch that will make this work. Iv tried setting the language to en-GB etc, but this doesn't seem to make any difference.

Any help is much appreciated.

Regards

Max

---

### Post by MaxVK on 2008-04-23
No command line gurus?

---

