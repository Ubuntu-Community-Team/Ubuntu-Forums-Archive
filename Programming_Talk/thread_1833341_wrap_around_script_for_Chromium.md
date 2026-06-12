---
title: "wrap around script for Chromium"
date: 2011-08-25
forum: Programming Talk
---

### Post by troymius on 2011-08-25
I noticed that Chromium starts and runs quite a bit faster than Firefox. However, it does not have a setting that would delete browsing history upon closing the application. Is it feasible to write a wrap-around script that would start Chromium and then, when Chromium closes, it would go into the ~/.config/chromium folder and delete the history files?

---

### Post by hakermania on 2011-08-26
Short answer:
Yes it is
Long Answer:
Yes it is, you can create a script and place it to /usr/bin/ which will execute the chromium without appending to it:
```

chromium-browser&

```
and then in a while loop you will delete the history if there's no pidof chromium:
```

while [[ $(pidof chromium) != "" ]]; do
   sleep 10;
done
#here chromium has closed because we are out of the loop
rm /path/to/the/history

```

---

### Post by juancarlospaco on 2011-08-26
Because you dont need it, use Incognito Mode, everything goes when you close the window.
Plus, go to Tools--->Clear Browsing Data

---

### Post by troymius on 2011-08-26
The script should do it... nice! Let me give it a try. Thanks!

As for the incognito mode... yes it seems you are right too! I just have to change the launcher command to "chromium-browser --incognito". However this can make some websites difficult to use (like on-line banking perhaps - don't they need to drop some cookies?).

Thanks to you both.

---

