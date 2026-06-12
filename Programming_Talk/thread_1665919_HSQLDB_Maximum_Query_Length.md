---
title: "HSQLDB Maximum Query Length"
date: 2011-01-13
forum: Programming Talk
---

### Post by pcman312 on 2011-01-13
I'm using embedded HSQLDB in a J2EE application and I'm attempting to run a single insert query with one value being inserted. This query happens to be approximately 2600 characters long (it's a very large table - a little over 100 columns, we haven't refactored it to be a more appropriate size yet). I've tried to find what the maximum length of a query can be with no luck. Does anyone know the maximum length of a query can be in HSQLDB? If not, does anyone have any suggestions on how I could potentially split up the query into multiple queries? My only idea is to split a query like this:

INSERT INTO tableA (ID, A, B, C) VALUES (id_val, a_val, b_val, c_val);

converted into this:

INSERT INTO tableA (ID) VALUES (id_val);
UPDATE tableA SET A = a_Val WHERE ID = id_val;
UPDATE tableA SET B = b_Val WHERE ID = id_val;
UPDATE tableA SET C = c_Val WHERE ID = id_val;

I can do some optimization like putting multiple sets in a single update, but that's the basic premise.

---

