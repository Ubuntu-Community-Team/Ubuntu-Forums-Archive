---
title: "[SOLVED] socket in database.yml"
date: 2007-11-06
forum: Programming Talk
---

### Post by frietzieey on 2007-11-06
is there any difference if i remove the socket in the config/database.yml?.

```

development:
  adapter: mysql
  database: bookmarker
  username: root
  password: s3cr3t
  host: localhost
  socket: /var/run/mysqld/mysqld.sock

```

---

### Post by ThinkBuntu on 2007-11-07
If you remove that line, your app won't be able to connect with the MySQL database.

---

