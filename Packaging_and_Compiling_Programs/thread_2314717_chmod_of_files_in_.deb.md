---
title: "chmod of files in .deb"
date: 2016-02-23
forum: Packaging and Compiling Programs
---

### Post by WolfDogDesigns on 2016-02-23
Hi all.

As I mentioned in a post about another issue I'm pretty new to debian packaging. I'm trying to distribute files around the file system in my .deb archive. I have a file structure in the package folder which is copying all the right files to the right places but I need one of them to be executable (/usr/bin/packagename). I've read about [FONT=courier new]DEBIAN/rules[/FONT] being a runnable script so I've tried making [FONT=courier new]DEBIAN/rules[/FONT] a bash script to make it executable:

```
#!/bin/bash
chmod +x /usr/bin/packagename
```

If I then install that package, the file isn't executable and so the package doesn't run from it's command without me manually chmodding the run script.

Can anyone suggest what I'm doing wrong or failing to understand?

Many thanks.

---

