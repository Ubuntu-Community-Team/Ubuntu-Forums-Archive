---
title: "Secure file/directory path"
date: 2011-02-07
forum: Programming Talk
---

### Post by dawwin on 2011-02-07
Hello,
I wrote simple http server and I've got following question: What should I do to make path to directory/file secure? String ".." (parent directory) is already forbidden but I'm not sure it's all.
My server creates full path like this
www_dir + / + path_from_http_header
www_dir = '/var/www' by default

---

### Post by Some Penguin on 2011-02-08
You could always run the server with a user account that has very few permissions.

---

