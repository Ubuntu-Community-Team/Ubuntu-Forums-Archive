---
title: "Search only text files with 'find' command?"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Wakefield on 2012-09-08
I've been using this to search an entire directory recursively for a specific phrase in my code (html, css, php, javascript, etc.):

```
find dir_name -type f -exec grep -l "phrase" {} \;
```

The problem is that it searches ALL files in the directory 'dir_name', even binary ones such as large JPEG images. With a directory also containing large number of images dispersed everywhere, it dramatically reduces the efficiency. Sometimes it takes very long to get a response.

Is there any parameter I can easily use to make it only search text files?

---

### Post by diesch on 2012-09-08
You can use *file *to check the MIME-Type:

```
find dir_name -type f -exec sh -c 'file -ib "$0" | grep -q ^text' '{}'  \; -exec grep -l "phrase" '{}' \;
```

---

