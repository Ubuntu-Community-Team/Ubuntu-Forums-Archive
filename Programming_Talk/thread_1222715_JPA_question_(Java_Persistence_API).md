---
title: "JPA question (Java Persistence API)"
date: 2009-07-25
forum: Programming Talk
---

### Post by froggyswamp on 2009-07-25
Folks, 
has anyone noticed that between transactions there's a 50 offset between last transaction's last entity and next transaction's first entity IDs?
Does it mean those IDs in between will never get used?

example:
If last transaction's entity was assigned ID 150, next transaction's first entity gets ID 201.

PS: TransactionType.IDENTITY is not an option because of its side effect.

---

