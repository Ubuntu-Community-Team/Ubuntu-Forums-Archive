---
title: "Log any output from shell script to txt file"
date: 2013-02-17
forum: Programming Talk
---

### Post by CrusaderAD on 2013-02-17
Hello all. I'd like to log any output on the screen to a text file in my shell script. Any ideas on how to accomplish this?

---

### Post by CrusaderAD on 2013-02-17
This seemed to be what I needed.

[http://stackoverflow.com/questions/2410628/send-output-to-file-from-within-shell-script]("http://stackoverflow.com/questions/2410628/send-output-to-file-from-within-shell-script")

```
exec &> output.txt
```

---

