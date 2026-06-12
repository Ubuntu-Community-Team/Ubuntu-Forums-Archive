---
title: "file in home folder named  linux_signing_key.pub"
date: 2016-12-02
forum: New to Ubuntu
---

### Post by joelrio on 2016-12-02
I'm not sure if this flags a problem but I just found a file in the root of my home folder named  linux_signing_key.pub

I don't remember it being there before. Is it an orphaned file that has lost its home or is it just fine?

Hope this isn't a stupid  question

Thanks joel

---

### Post by oldrocker99 on 2016-12-02
.Pub files can be opened by LibreOffice, by the way. Not a stupid question, either.

---

### Post by mcduck on 2016-12-02
Sounds like a PGP key. I'd guess you have at some point installed a new piece of software, and the install process included configuring a new software source, downloading the signing key for that source and then importing the key. Probably you did it by copy/pasting some terminal commands? The .pub file you are looking at is the key you downloaded, and assuming it imported without problems you don't need the file any more feel free to delete it.

Software repositories uses PGP keys to verify that the programs you download actually come from the sources you have configured on you computer, and nobody has messed around with the files.

---

### Post by joelrio on 2016-12-03
That makes sense as i have just set up a lamp stack to run wordpress on my localhost with a fair bit of copy and paste etc. I was worried that I might need it at some point but not know where it lived. I'll mark as solved
Thanks Joel

---

