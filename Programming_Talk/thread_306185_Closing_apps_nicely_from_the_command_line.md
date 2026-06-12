---
title: "Closing apps nicely from the command line"
date: 2006-11-24
forum: Programming Talk
---

### Post by musther on 2006-11-24
I want to set up a cron job to close amule at a given time.  

If I close amule nicely (graphically) then it saves all of the part files, but if I kill it, or shut the machine down while it's running it looses a little of what it has downloaded.  So what I need is a command to close it nicely, I can then schedule this with cron.  How can I do this?

Thanks

---

### Post by cilynx on 2006-11-24
I hate to give RTFM as an answer, but it's the best bet in this case:

```
man kill
```

'kill' can send a bunch of different signals.  How aMule interprets them is another question.  If aMule doesn't have a signal hook that shuts down nicely, then there isn't much else that I know of to do.

---

