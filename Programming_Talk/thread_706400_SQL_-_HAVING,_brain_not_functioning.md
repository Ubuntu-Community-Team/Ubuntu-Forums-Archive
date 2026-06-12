---
title: "SQL - HAVING, brain not functioning"
date: 2008-02-24
forum: Programming Talk
---

### Post by wrightee on 2008-02-24
Hello.. sorry, remedial question from brain malfunction.

I have tbl.transactions with columns id, buyer, product.  I need to find products that have been sold to a distinct buyer more than once.  So if my data looked like this, my query should return 5 as that one's been purchased by buyer #1 more than once.

(id, buyer, product)

1 1 5
2 1 5
3 2 5
4 2 6

I'd be most grateful if someone can remind me how to walk.  Thank you!

---

### Post by aks44 on 2008-02-24
From the top of my head (untested):

```
SELECT buyer, product, COUNT(id) AS num
FROM transactions
GROUP BY buyer, product
HAVING COUNT(id) > 1
```

---

### Post by volanin on 2008-02-24
Tested one:

SELECT buyer, product, COUNT(product) AS total
FROM transactions
GROUP BY buyer, product
HAVING total > 1;

You will get a table with the specific buyer, specific product and the total number of this product.

---

### Post by wrightee on 2008-02-24
Thank you both, saved me much brain ache.

---

