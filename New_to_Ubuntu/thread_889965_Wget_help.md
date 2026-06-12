---
title: "Wget help?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Wiebelhaus on 2008-08-14
Thanks , I'm fighting with my limited knowledge of wget more so than the tool itself , I can't figure out how to download only the .exe files from a website without all the html directories.

from here:
[www.filehippo.com](www.filehippo.com)
> 
wget -r -np -a exe,bin,zip [www.filehippo.com](www.filehippo.com)

any suggestions?

Thanks.

---

### Post by t0p on 2008-08-14
You want the -A flag to define the type(s) of files you want.

---

