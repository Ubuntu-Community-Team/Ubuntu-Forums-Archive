---
title: "wait for 1 of list of processes"
date: 2010-06-28
forum: Programming Talk
---

### Post by glederfein on 2010-06-28
I want to write a bash script which calls 2 processes in the background, and when **one** of them finishes, calls a third processes. Here's what I've got so far:
```

process1 &
id1=$!
process2 &
id2=$!
wait $id1 $id2

```

However, "wait" waits for **both** processes to finish.

How do I accomplish this?

---

