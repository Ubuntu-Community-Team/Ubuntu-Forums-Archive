---
title: "Ruby error"
date: 2006-03-23
forum: Programming Talk
---

### Post by icyisamu on 2006-03-23
I had ruby installed via the respository.

Then i went crazy and install ruby 1.8.4 and used make install to install it.

Problem is, I can't uninstall it via make uninstall. So I went crazy again and uninstall ruby via synaptic (the respository one) and went to delete everything that has ruby.

Now after I install ruby via synaptic and run ruby in terminal, I get this error.

```
serph@desktop:/lib$ ruby
ruby: error while loading shared libraries: libruby1.8.so.1.8: cannot open shared object file: No such file or directory
```

I know i screwed things up, so is there any way to solve this error?

---

### Post by icyisamu on 2006-03-23
I solved this by installing libruby again.

---

