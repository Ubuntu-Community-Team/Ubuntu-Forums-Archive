---
title: "Concurrency handled in hibernate"
date: 2009-09-14
forum: Programming Talk
---

### Post by sthiranga on 2009-09-14
I'm Learning Hibernate and developing a web base hibernate project.I want know that hibernate can handle the data access concurrency correctly?

---

### Post by CptPicard on 2009-09-14
Yes... Hibernate integrates with the db quite nicely to guarantee transaction correctness. There is a lot of documentation available on both versioned, optimistic locking and pessimistic locking...

---

