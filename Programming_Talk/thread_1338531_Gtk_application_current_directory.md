---
title: "Gtk application current directory"
date: 2009-11-26
forum: Programming Talk
---

### Post by froggyswamp on 2009-11-26
Folks how can an app (executable) figure out what directory it lies in?
I thought one just has to call "g_get_current_dir()", but sometimes it doesn't work this way, i.e. I created a shortcut to my app on the upper (Gnome) panel and when launched from the panel g_get_current_dir() reports the home directory, not the directory the app is in. My app is in C & Gtk+.
Can anyone suggest some workaround/solution please?

---

### Post by alexmurray on 2009-11-26
g_get_current_dir() returns the directory the process is running in, not the location of the executable. The path to the executable is not so easy to determine - why do you need to know this from within your app?

---

### Post by Virtual Liberty on 2009-11-26
What's wrong with the [COLOR=Green]getcwd()[/COLOR] function ?

---

### Post by froggyswamp on 2009-11-27
@alexmurray
There's a resource folder in same dir as the executable. I know I there's the xdg spec, but.
Not easy? Can you give an URL to such a discussion please?

@Virtual Liberty
getcwd doesn't solve the issue.

---

### Post by froggyswamp on 2009-12-01
I found a workaround.
I created a bash script in the same dir as the executable and launch it instead. The script first does a "cd" to the dir it is in and then launches the app. Works fine.

Script contents (say "main" is the C executable):
```

#!/bin/bash
FILE_PATH="`readlink -f "$0"`"
cd "`dirname "$FILE_PATH"`"
exec "./main" "$@"

```

---

