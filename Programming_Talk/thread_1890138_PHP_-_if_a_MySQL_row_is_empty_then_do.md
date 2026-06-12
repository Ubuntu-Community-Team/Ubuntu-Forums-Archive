---
title: "PHP - if a MySQL row is empty then do"
date: 2011-12-02
forum: Programming Talk
---

### Post by Kolusion on 2011-12-02
How can I make it so if a MySQL row is empty, then do? I tried this, but it didn't work.  **$query = &quot;SELECT * FROM products WHERE availability = 'yes' AND categorydir = 'belts' AND fordir = 'menswear'&quot;;**    The problem is that there are matches to my MySQL query, but the **($row == &quot;&quot;)** stringis taking effect and causing nothing to display.  Sorry for the page layout. I am using a web proxy that has been coded badly.

---

### Post by Kolusion on 2011-12-02
Its cool, I solved it:  if (!$row['id'] == "") {

---

### Post by Kolusion on 2011-12-03
That actually didn't solve it, all it did was skip the string all together. This is is what I actually needed. All I had to do was add it to the end of the code. Bloody hell!  [PHP]if ($listing == 0) {echo "";}[/PHP]

---

### Post by Petrolea on 2011-12-03
> **Kolusion said:**
> Its cool, I solved it:  if (!$row['id'] == "") {

If your query doesn't return a column with name 'id', then this statement will fail. It will also fail if only 'id' is empty. 

Use a loop to check all elements in a row.

```

foreach($row as $r)
{
    if(empty($r)) //do something to later tell whether its empty or not
}

```

---

### Post by dazman19 on 2011-12-09
if(mysql_num_rows($resource) === 0) {
     //true (no results) do this... 

}

---

