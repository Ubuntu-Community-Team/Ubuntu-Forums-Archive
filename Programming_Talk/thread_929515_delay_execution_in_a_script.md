---
title: "delay execution in a script"
date: 2008-09-25
forum: Programming Talk
---

### Post by insert_name_here on 2008-09-25
While I apologize for using ubuntuforums.org as my personal coding agency, I don't have the expertise to do this myself: What I want to do is to be able to set my firefox shortcut to execute firefox five minutes AFTER I click the shortcut.

(Purpose: To cut down on procrastination.  I have a paper due about 14 hours, and I'm spending my time procrastinating, rather than writing...  the way I figure it, most procrastination is totally impulsive.  If I can cut down on the instant procrastinatory gratification, I'll get my stuff done more quickly.)

So, guys, how would I do this?

Much thanks.  You're getting me better grades!

---

### Post by slavik on 2008-09-25
```
#!/bin/sh

sleep 600
firefox
```

---

### Post by dwhitney67 on 2008-09-25
```
#!/bin/bash

sleep 300      # 5 minutes = 5 * 60 seconds = 300 seconds

firefox &      # launch firefox in the background

exit 0
```

Save the script, make it executable (chmod 744 script.bash), then create a launcher (shortcut) for it.

P.S.  Now why in pray-tell do you want this script?

---

### Post by insert_name_here on 2008-09-25
Much thanks guys.

I want this script to cut down on my impulsive procrastination while I do my damn homework.  I figure if firefox doesn't open immediately, I won't be able to procrastinate, and when it pops up 600 seconds later, it'll just be a distraction and I'll close it.

---

