---
title: "sqlite query help"
date: 2010-02-26
forum: Programming Talk
---

### Post by GOwin on 2010-02-26
Could anyone help me with this sqlite query please? I have these tables:

cities (id string, name string)
neighbors (center string, adjacent string)

neighbors.center and neighbors.adjacent are foreign keys of the cities.id primary key.

cities.id, cities.name
1	city 1
2	city 2
3	city 3
4	city 4
5	city 5
6	city 6

neighbors.adjacent
1	2
1	3
2	1
2	4
3	1
3	4
4	2
4	3
4	5
5	4

what is the query to list all cities and its neighboring cities like this?

cities.id, cities.name, neighboring cities (id), number of neighbors
1|city 1|2,3|2
2|city 2|1,4|2
3|city 3|1,4|2
4|city 4|2,35|3
5|city 5|4|1
6|city 6||0

or; cities.id, cities.name, neighboring cities (name), number of neighbors
1|city 1|city 2, city3|2
2|city 2|city 1, city 4|2
3|city 3|city 1, city 4|2
4|city 4|city 2, city 3, city 5|3
5|city 5|city 4|1
6|city 6||0

---

