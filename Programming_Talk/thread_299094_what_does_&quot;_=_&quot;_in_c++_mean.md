---
title: "what does &quot; |= &quot; in c++ mean?"
date: 2006-11-13
forum: Programming Talk
---

### Post by weatherman on 2006-11-13
The title pretty much says it all, I was reading through some code and found a bool variable which was assigned a value through "|=". What does this mean?

---

### Post by llonesmiz on 2006-11-13
variable|=whatever <=> variable=variable|whatever

the "|" operator means bitwise inclusive OR.

4|1:=5 <=> 0100|0001:=0101

4|6:=6 <=> 0100|0110:=0110

---

### Post by weatherman on 2006-11-13
> **llonesmiz said:**
> variable|=whatever <=> variable=variable|whatever

the "|" operator means bitwise inclusive OR.

4|1:=5 <=> 0100|0001:=0101

4|6:=6 <=> 0100|0110:=0110
great, thanks for the quick answer

---

