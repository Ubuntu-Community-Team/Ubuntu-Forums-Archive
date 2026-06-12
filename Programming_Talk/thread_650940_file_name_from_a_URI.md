---
title: "file name from a URI"
date: 2007-12-27
forum: Programming Talk
---

### Post by chamaracal on 2007-12-27
how i can extract file name from a URI using C?Is there any library for that?

---

### Post by Compyx on 2007-12-27
Perhaps libcurl will do what you want, although I suspect that might be overkill.

---

### Post by chamaracal on 2007-12-27
i have tried libcurl before .i'll try it thnx

---

### Post by MicahCarrick on 2007-12-27
GLib provides g_filename_from_uri() for that purpose.

---

