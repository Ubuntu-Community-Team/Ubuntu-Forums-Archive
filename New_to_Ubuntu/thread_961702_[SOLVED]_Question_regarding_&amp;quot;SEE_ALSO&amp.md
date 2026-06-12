---
title: "[SOLVED] Question regarding &amp;quot;SEE ALSO&amp;quot; in application files"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by boof1988 on 2008-10-28
When I'm looking at info files from Terminal after typing *application_name* preceeded by "info" like this:

```
info network-admin
```

there is often a "SEE ALSO" area the has some other files listed... like this:

```
services-admin(1)
```

How so I "SEE ALSO" these other files?  What does the number mean?

I noticed that the file that is currently being viewed has this "*style*" of formatting for it's "*title*" at the top of the page.  So I assume I could view the current info file a different way than *info app_name*?

---

### Post by boof1988 on 2008-10-28
<Update>

I've been able to find some stuff similar to this in the "Ubuntu Help Center" (the big question mark at the top of the screen) but I'd like to learn where the 'help' files are located in the directory.

---

### Post by tCarls on 2008-10-28
> 
How so I "SEE ALSO" these other files?

Move the cursor on to them and press enter. Alternatively, you could exit and run "info services_admin".

> 
What does the number mean?

Man pages are divided into sections. See [http://en.wikipedia.org/wiki/Man_page#Manual_sections](http://en.wikipedia.org/wiki/Man_page#Manual_sections). Occasionally there is more than one command with the same name. In that case, you may need to specify the section to view the right page. (e.g. "man 1 printf" or "man 3 printf", sorry I couldn't figure out how to specify the section with info, only man.)

> 
but I'd like to learn where the 'help' files are located in the directory. 


They're in /usr/share/man, among other places. They're in the troff format, so while they are human readable, they're not pleasant to read directly.

---

### Post by boof1988 on 2008-10-28
Thanks tCarls.

:KS

---

