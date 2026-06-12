---
title: "good tutorials on expect scripting"
date: 2011-11-07
forum: Programming Talk
---

### Post by Drenriza on 2011-11-07
I'm trying to connect to a psql database and get it to output one of the tables.

I have tried so far with the code below, and it execute with 0 errors. But it docent create the output file. What am i doing wrong?

```
#!/usr/bin/expect -f

spawn psql stbinfo stbinfo
sleep 1
expect "stbinfo=> "

send "\o /home/nice/test_sql.csv"
sleep 1
send "select stb_version from stbinfo;"
sleep 1

send "\q"
```

---

