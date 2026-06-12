---
title: "Bash: How can I use the Zenity progress window and keep the application's text output"
date: 2016-08-07
forum: Programming Talk
---

### Post by alexandrexavier on 2016-08-07
Hi everyone,

I have this code:

```
choice=$(top -n 3 | zenity --progress --pulsate --auto-close)
```

When it's done, the $choice variable is empty. Is there a way to keep the application's text output when using Zenity's progress window?

Thanks,
Alex

---

### Post by alexandrexavier on 2016-08-07
Found by myself after struggling with the "tee" command. 

```
OUTPUT="$(gksudo apt-get install $choice | tee >(zenity --progress --pulsate --auto-close))"
```

---

### Post by &amp;KyT$0P# on 2016-08-07
Seems zenity is just eating the stdout stream you're giving it.  Work around that using a temporary file -
```
tmp_store=$(mktemp)
top -n 3 | tee "$tmp_store" | zenity --progress --pulsate --auto-close
choice="$(cat $tmp_store)"
rm -fv $tmp_store
```

---

### Post by alexandrexavier on 2016-08-07
Thanks.

---

