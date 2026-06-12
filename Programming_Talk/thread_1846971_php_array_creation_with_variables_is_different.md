---
title: "php array creation with variables is different"
date: 2011-09-19
forum: Programming Talk
---

### Post by superalanliu on 2011-09-19
This code works:

```

$post_id = wp_insert_post( array(
'post_author'   => $user_id,
'post_category' => array(3) )
```


This does not

```
$post_id = wp_insert_post( array(
'post_author'   => $user_id,
'post_category' => array($category_id) )
```

Using echo, $category_id is indeed 3, so I don't get why this is not working. I'm guessing this has something to do with php and array creation but I couldn't figure out what is wrong.
What is the difference between array(3), and array($category_id) if $category_id is 3?

---

### Post by Bachstelze on 2011-09-20
What does it do instead of working?

---

### Post by lykwydchykyn on 2011-09-20
is $category_id a string or an integer?

---

### Post by superalanliu on 2011-09-20
I forcefully casted the value to int and it work. Turns out the cast location makes a difference.

Works:
$cat_id = (int) get_id();
array($cat_id)

Doesn't work
array ( (int) $cat_id ) //when cat_id hasn't been casted previously.

---

