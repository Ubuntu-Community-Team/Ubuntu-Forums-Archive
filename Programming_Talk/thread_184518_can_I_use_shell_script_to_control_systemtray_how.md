---
title: "can I use shell script to control systemtray? how?"
date: 2006-05-30
forum: Programming Talk
---

### Post by hydrogen on 2006-05-30
can I use shell script to control systemtray( such as add/del a network interface icon) ? how?

---

### Post by simplyw00x on 2006-05-30
Yes you can AFAIK. Zenity is the answer.
```
zenity --notification --window-icon=update.png
```

---

