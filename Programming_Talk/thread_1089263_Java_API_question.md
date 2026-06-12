---
title: "Java API question"
date: 2009-03-06
forum: Programming Talk
---

### Post by andrew222 on 2009-03-06
Does anyone know what the differences are between ConcurrentHashMap and HashMap in the Java API...

---

### Post by shadylookin on 2009-03-06
looks like concurrentHashMap is thread safe and HashMap is not.

Most data structures in java have a thread safe type and one that is not.

---

### Post by DocForbin on 2009-03-07
Use ConcurrentHashMap if your app is multi-threaded and it's possible to have multiple threads operating on the map at the same time (e.g. one enumerating it while another is updating it).

---

### Post by andrew222 on 2009-03-07
Thank you...that was a recent interview question...

---

