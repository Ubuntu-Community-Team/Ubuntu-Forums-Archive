---
title: "Is there a way to tell how long my script is running?"
date: 2011-01-28
forum: Programming Talk
---

### Post by rbishop on 2011-01-28
I am looking for a way to display how long an actual script is run.  I have a script that is in progress and at the beginning and end of the script it displays the time.  Is there any way to show this?

---

### Post by SeijiSensei on 2011-01-28
Write a log file:

```

#!/bin/bash

LOG=/path/to/logfile

echo "Script started at: $(date)" >> $LOG

[rest of script]

echo "Script ended at: $(date)" >> $LOG

```

---

### Post by AlphaLexman on 2011-01-28
```
#!/bin/bash

time {
 #body of your script
}

```

---

### Post by rbishop on 2011-01-28
Thank you for the responses.

[AlphaLexman]("http://ubuntuforums.org/member.php?u=810079") it looks like this is more of what I was wanting for the script.

---

### Post by AlphaLexman on 2011-01-28
If you are satisfied with our / my help, please mark your thread as [SOLVED] - this can be done from Thread Tools of threads you start.

---

