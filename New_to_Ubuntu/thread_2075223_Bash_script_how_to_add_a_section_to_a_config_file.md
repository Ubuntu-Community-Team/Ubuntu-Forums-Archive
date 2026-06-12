---
title: "Bash script: how to add a section to a config file?"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by Houmie on 2012-10-23
I know how to find and replace a section in a config file like this:

    sudo sed -i "s/upload_max_filesize = 2M/upload_max_filesize = 3M/" /etc/php5/cgi/php.ini

But how do I add a whole new section to the end of the config file within the bash script?


Many Thanks,

---

### Post by Cheesemill on 2012-10-23
Use echo and >> to append text to an existing file:
```
echo "This is a new section" >> config.file
echo "option1 = yes" >> config.file
```

---

### Post by Lars Noodén on 2012-10-23
You can use >> to append to a file.

```

echo "upload_min_filesize = 1M" >> /etc/php5/cgi/php.ini

```

But wouldn't it make more sense to edit manually with a text editor?

Edit: Oh.  Too slow.  :)

---

### Post by Houmie on 2012-10-23
yeah that worked thanks.

---

