---
title: "vi copy buffers"
date: 2010-03-01
forum: Programming Talk
---

### Post by PeterL777 on 2010-03-01
(Not sure if this is the right forum - please advise if I've got it wrong. Thanks)

I have what I thought was a simple &quot;vi&quot; question, but I can't seem to find the answer. vi (and vim) have multiple copy buffers - at least 36 by my count - and I can have stuff in them all. Only problem is I can't remember which snippet I put in which buffer. How can I get a list or an index to all the (occupied) copy buffers? Say just the first line or 20 chars or so of each.  

Thanks all for your help  Peter

---

### Post by falconindy on 2010-03-01
:reg

Short for :registers

---

### Post by PeterL777 on 2010-03-04
Thanks, that works a treat. Found some new buffers I didn't know about, too ;).
For others info, :dis[play] also works

---

