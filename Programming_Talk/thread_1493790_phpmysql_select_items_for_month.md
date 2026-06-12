---
title: "php/mysql: select items for month"
date: 2010-05-26
forum: Programming Talk
---

### Post by Johnsie on 2010-05-26
In the mysql 'dateOrdered' field the dates are dd/mm/yyyy (i didnt create the table)

I'm trying to select the accountsQuantity for everything that was ordered in April but the following query wont work: 

> SELECT accountsQuantity FROM customer_envelope_orders_psort WHERE company='$company' AND dateOrdered BETWEEN '01/04/2010' AND '30/04/2010'


Anyone know how I can do this?

---

### Post by januzi on 2010-05-26
Could You add something like:
```

echo $query.' '.mysql_error() ;

```
after the line with mysql_query( $query ) ?

---

### Post by DaithiF on 2010-05-26
Hi,
use: 
```
between '20100401' and '20100430'

```

---

