---
title: "Storing binary data in MySQL using C API"
date: 2007-06-24
forum: Programming Talk
---

### Post by bluedalmatian on 2007-06-24
Hi

Just wanted to clarify this, if I've got some binary data in a C char array which I want to store in MySQL using mysql_real_query

Is it OK to do it by simply concatenating the char array into the query string at the appropriate place and then passing the whole string to mysql_real_query

Thanks
Andrew

---

### Post by aks44 on 2007-06-24
If you escape your binary data beforehand (mysql_real_escape_string or something like that, I don't remember precisely) then it is ok.

---

### Post by bluedalmatian on 2007-06-24
Thats great, thanks.

---

