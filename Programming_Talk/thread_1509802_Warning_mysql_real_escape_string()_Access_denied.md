---
title: "Warning: mysql_real_escape_string(): Access denied"
date: 2010-06-14
forum: Programming Talk
---

### Post by Rebajas on 2010-06-14
I'm pulling my hair out here - I have some code that cleans data, and it works fine on my dev box but on my live server I get the following:

```
Warning: mysql_real_escape_string(): Access denied for user 'www-data'@'localhost'
```

Any idea what might fix this? Is it a user permissions thing?

Both platforms are Ubuntu, dev is Ubuntu 8.10 - live is Ubuntu 10.04


Thanks in advance.

---

### Post by Kerubu on 2010-06-16
> **Rebajas said:**
> I'm pulling my hair out here - I have some code that cleans data, and it works fine on my dev box but on my live server I get the following:

```
Warning: mysql_real_escape_string(): Access denied for user 'www-data'@'localhost'
```

Any idea what might fix this? Is it a user permissions thing?

Both platforms are Ubuntu, dev is Ubuntu 8.10 - live is Ubuntu 10.04


Thanks in advance.

It does sound like a permission problem. Check the permissions of the users on your database - check from where access is allowed e.g. local or remote.

Might need to post a bit more code here if you're still struggling.

---

