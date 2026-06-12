---
title: "How to bulk rename files using command line?"
date: 2016-09-02
forum: New to Ubuntu
---

### Post by walterwhite on 2016-09-02
this has been asked i guess but my question is a bit different , i just want to add suppose 'by walter' as suffix or Prefix of files ,

---

### Post by aromo2 on 2016-09-02
find is your friend.  use the -exec option and you'll be good.  man is your friend.

Sorry, find will need some tweaking to work.  Better use a for loop:

```
cd /home/mydir; for i in *; do mv ${i} prefix_${i}_suffix; done
```

---

