---
title: "Is there any software that tells me which packages and applications I do not use?"
date: 2022-03-20
forum: New to Ubuntu
---

### Post by esso10 on 2022-03-20
Is there any software that tells me which packages and applications I haven't used for a long time just like android does?

---

### Post by MAFoElffen on 2022-03-20
Yes, in a round-a-bout way: [WhatPulse]("https://www.whatpulse.org/")

[I]It will show you when you used an application, how much time spent in, where you clicked, how many mouse clicks, etc... Then go to the end of to see what you haven't used recently. It would be up to you to look up which package that application is a part of. 

For application never used, you would need to list packages installed (by you or defaults) to find applications that you have never used. Since never used, they would not be any stats on them.[/I]

---

### Post by wyattwhiteeagle on 2022-03-23
WhatPulse is a snap package.
Is there something that isn't a snap?

---

### Post by Impavidus on 2022-03-23
Or, assuming the filesystem has been mounted without the noatime option, use stat to see when you last accessed the executable.

---

