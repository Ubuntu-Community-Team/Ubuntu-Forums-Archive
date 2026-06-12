---
title: "[SOLVED] Javascript to modify HREFs"
date: 2008-07-18
forum: Programming Talk
---

### Post by billynomates on 2008-07-18
Hi, I'm writing this little script to search through all the HREFs on a page and if it contains the string "Settings//", it replaces it with "Settings/" (with one backslash).

Here's what I've got so far.
```

	var as = document.getElementsByTagName("a");
	for (var i = 0; i<as.length; i++){
		as[i].href.replace("Settings//","Settings/");
	}
```

It doesn't work. Any ideas why? 
Thanks in advance!

---

### Post by [h2o] on 2008-07-18
I think string.replace() returns a new string with the replacements done, and does not modify the original string.

Try:

```

var as = document.getElementsByTagName("a");
for (var i = 0; i<as.length; i++){
  as[i].href = as[i].href.replace("Settings//","Settings/");
}

```

---

### Post by billynomates on 2008-07-18
Yeah, that fixed it. Thanks a lot!

---

