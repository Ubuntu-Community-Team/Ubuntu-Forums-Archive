---
title: "Open a file within an ISO in python."
date: 2008-05-04
forum: Programming Talk
---

### Post by Danikar on 2008-05-04
Is there a way to open a file that is inside of an ISO in python?

Say I have an ISO file, danikars.iso and on the iso there is a file called information.txt

I want to be able to do something like this.

```
iso_h = openiso("danikars.iso")

file_h = iso_h.extract("information.txt")

contents = file_h.read()
```

Is there anything that will give me that functionality? Or close?

Thanks,

Danikar

---

