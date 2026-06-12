---
title: "Small bash problem, driving me nuts"
date: 2006-07-01
forum: Programming Talk
---

### Post by Horizon on 2006-07-01
Ok, ok, ok, so...can someone tell me why cp keeps adding extra backslashes to this?

```
masao@Sayumi:~$ FPATH="/home/masao/college work/VM Files/AVG_CONFIG.png"
masao@Sayumi:~$ echo ${FPATH//' '/"\ "}
/home/masao/college\ work/VM\ Files/AVG_CONFIG.png
masao@Sayumi:~$ cp ${FPATH//' '/"\ "} ./
cp: cannot stat `/home/masao/college\\': No such file or directory
cp: cannot stat `work/VM\\': No such file or directory
cp: cannot stat `Files/AVG_CONFIG.png': No such file or directory

```

This is really driving me insane, especially because I know it's probably something silly...

I suddenly felt like learning a little bash today but I guess it doesn't like me :cry:

---

### Post by toojays on 2006-07-02
The way you are using echo doesn't show you the full story:```
toojays@fuzz:/tmp$ FPATH="/home/masao/college work/VM Files/AVG_CONFIG.png"
toojays@fuzz:/tmp$ echo ${FPATH//' '/"\ "}
/home/masao/college\ work/VM\ Files/AVG_CONFIG.png
toojays@fuzz:/tmp$ echo "${FPATH//' '/"\ "}"
/home/masao/college"\ "work/VM"\ "Files/AVG_CONFIG.png
```
Notice that in the second invocation of 'echo' here, there are double-quotes in the string which are not shown in the first invocation.

When the string is expanded by the shell before being passed to 'cp', the backslashes are quoted, and so they expand to double-backslashes.

To do what you wanted to do, you should have used '${FPATH//' '/\\ }' to avoid inserting quotes into the string.

Of course you can do the copy with 'cp "$FPATH" .', but I assume the purpose of this exercise is to learn advanced bash variable expansion.

Does this help?

---

### Post by Horizon on 2006-07-02
[QUOTE=toojays]The way you are using echo doesn't show you the full story:```
toojays@fuzz:/tmp$ FPATH="/home/masao/college work/VM Files/AVG_CONFIG.png"
toojays@fuzz:/tmp$ echo ${FPATH//' '/"\ "}
/home/masao/college\ work/VM\ Files/AVG_CONFIG.png
toojays@fuzz:/tmp$ echo "${FPATH//' '/"\ "}"
/home/masao/college"\ "work/VM"\ "Files/AVG_CONFIG.png
```
Notice that in the second invocation of 'echo' here, there are double-quotes in the string which are not shown in the first invocation.

When the string is expanded by the shell before being passed to 'cp', the backslashes are quoted, and so they expand to double-backslashes.

To do what you wanted to do, you should have used '${FPATH//' '/\\ }' to avoid inserting quotes into the string.

Of course you can do the copy with 'cp "$FPATH" .', but I assume the purpose of this exercise is to learn advanced bash variable expansion.

Does this help?[/QUOTE]


Perfect. I would have never figured that out myself. I guess if I really want to learn bash I should invest in a book or something. Cheers mate.

---

