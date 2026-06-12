---
title: "libcurl help/autoconf script"
date: 2006-02-06
forum: Programming Talk
---

### Post by zootreeves on 2006-02-06
Hi, I'm trying to use libcurl functions in my C program, however 

If I add: #include <curl/curl.h>
It doesn't chuck up any erros and compiles, however it says curl_global_init() is undefined.

Am I going wrong here? Is there something else I need to do to load libcurl. There is an autoconf .m4 script provided on the curl site, but I don't have a clue how to include it in the build process, can anyone help? Thanks

---

### Post by hod139 on 2006-02-07
are you linking against the curl library?  ```
gcc foo.c -lcurl
```

---

