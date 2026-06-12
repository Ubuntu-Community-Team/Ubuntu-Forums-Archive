---
title: "[php] looping through this data"
date: 2009-07-06
forum: Programming Talk
---

### Post by ELD on 2009-07-06
Okay say i have this back from some sql:

```

id   |  name            |  parent |   is_cat
1    |    Category 1    |    0      |    1
5    |    Category 2    |    0      |    1
2    |    forum 1         |    1     |       0
6    |    forum 2         |    5     |       0
7    |    forum 3         |    5      |       0

```

I want to first loop through where "is_cat" = 1, then for each of those loop through where the "parent" = their "id"

So it would end up like:
Category 1
--forum 1
Cateogry 2
--forum 2
--forum 3

I know it is probably using some foreach loop but i am unsure?

---

### Post by credobyte on 2009-07-06
Pardon me if it doesn't work as expected - I'm at work and can't test it ;)

[PHP]<?php

$query = mysql_query("SELECT * FROM somewhere");

while ($data = mysql_fetch_array($query)) {
    if ($data['is_cat'] == 1) {
        echo "<b>" . $data['name'] . "<b> <br />";
        $sql_findparent = mysql_query("SELECT * FROM somewhere WHERE parent='{$data['id']}'");
        while ($parent = mysql_fetch_array($sql_findparent)) {
            echo "-- " . $parent['name'] . "<br />";
        }
    }
}

?>
[/PHP]

---

### Post by ELD on 2009-07-06
I'm doing it in one query, i have since learnt i need to do the sorting in the query.

[http://forums.devshed.com/showpost.php?p=2289918&postcount=2](http://forums.devshed.com/showpost.php?p=2289918&postcount=2)

---

### Post by masux594 on 2009-07-06
the "tree" structure is perfect for recursive methods.. A recursive method is a little bit hard to create, but is more flexible and smarter!
i think that you can build with a single query, but when you create the query, you're "fixed" with the example that you show.. I'm a developer and by the experience i know that "a fixed thing, in the future, it will come changed!"

Sysc, A

---

### Post by ELD on 2009-07-06
It is fine the way i linked to on devshed, i only need that many.

---

### Post by masux594 on 2009-07-06
i don't understand.. do u need the query for your db?

Sysc, A

---

### Post by ELD on 2009-07-06
It's just a simple output to show categorys, forums and then their subforums no deeper than that for the frontpage, it's sorted now :)

---

