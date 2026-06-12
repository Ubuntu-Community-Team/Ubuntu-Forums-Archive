---
title: "Error in postrm script"
date: 2008-10-01
forum: Packaging and Compiling Programs
---

### Post by Nonno Bassotto on 2008-10-01
I was playing around with dpkg-deb to learn how it works, so I created a dummy package to test the postinst and postrm scripts.

This is my postinst
```

#! /bin/sh

touch /home/andrea/working

```

and this is postrm
```

#! /bin/sh

rm /home/andrea/working

```

The postinst script gave no problem, but when I removed the package, the postrm script returned an error, complaining that "/home/andrea/working" doesn't exist. Still it correctly removed it. So I created the file and then I could remove the package.

What did I get wrong? I thought that maybe the created file was automatically removed when I purged the package, before postrm, but I'm not sure. Is dpkg that intelligent? If so, how far can it go in unwinding the changes made during the postinst phase?

(By the way, I know I should use idempotent scripts, it was just a simple test)

---

