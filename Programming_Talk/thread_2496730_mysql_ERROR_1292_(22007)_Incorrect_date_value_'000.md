---
title: "mysql: ERROR 1292 (22007): Incorrect date value: '0000-00-00'"
date: 2024-04-10
forum: Programming Talk
---

### Post by maketopsite on 2024-04-10
```
mysql> UPDATE some_table SET some_date_column='2024-04-10' WHERE some_date_column='0000-00-00' ;
ERROR 1292 (22007): Incorrect date value: '0000-00-00' for column 'some_date_column' at row 1
```

Server version: 8.0.26 MySQL Community Server - GPL

What is please optimal solution ?

---

### Post by ruwolf on 2024-04-20
Why do you post this question in multiple forums?
You have already got answer [here]("https://forums.debian.net/viewtopic.php?p=796739#p796739").

---

### Post by maketopsite on 2024-05-04
> **ruwolf said:**
> Why do you post this question in multiple forums?
You have already got answer [here]("https://forums.debian.net/viewtopic.php?p=796739#p796739").

Because I believe it increases probability of getting best answer (and faster). (I've posted it at same moment which I see is not apparent because this forum does not show exact time of posting)

---

### Post by maketopsite on 2024-05-11
solved by
```
UPDATE some_table SET some_date_column='2024-04-10'
WHERE some_date_column IS NULL;
```

---

