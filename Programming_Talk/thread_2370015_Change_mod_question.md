---
title: "Change mod question"
date: 2017-08-29
forum: Programming Talk
---

### Post by Herbon on 2017-08-29
Greetings All

Quick question, recently I created a bash script which creates folders for my avi movies.
When I sudo run the script (Ubuntu 16.06 Os), on the CLI, I'm seeing a "Lock icon" on the right corner of the newly created folder in the UI.


```
# Creates folder for movie files type
for f in *.mp4; do mkdir "${f/.mp4/}"; mv "$f" "${f/.mp4/}";done
for f in *.avi; do mkdir "${f/.avi/}"; mv "$f" "${f/.avi/}";done
for f in *.mkv; do mkdir "${f/.mkv/}"; mv "$f" "${f/.mkv/}";done

```

To correct this I simply do..
```

sudo chmod -R ugo+rw "new_file_here"

```

Is there a way to stop the permission change?

---

### Post by deadflowr on 2017-08-29
Do you need to run it with sudo?
Which is the reason it's setting it as read-only for you. 
(Lock icon equals read-only)

---

### Post by Herbon on 2017-08-29
> **deadflowr said:**
> Do you need to run it with sudo?
Which is the reason it's setting it as read-only for you. 
(Lock icon equals read-only)

Ok, so "*sudo*" isn't need to run this program. Thanks 
:oops:

---

