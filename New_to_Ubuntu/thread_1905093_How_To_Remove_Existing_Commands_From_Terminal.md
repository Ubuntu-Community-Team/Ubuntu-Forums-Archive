---
title: "How To Remove Existing Commands From Terminal"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by EDLIU on 2012-01-06
Hi,

How can I "remove existing commands(history) from the Terminal (command line)"?

Thanks.

Ed

---

### Post by sisco311 on 2012-01-06
```
history -d OFFSET
```
will delete the history entry at offset OFFSET.

---

### Post by EDLIU on 2012-01-06
> **sisco311 said:**
> ```
history -d OFFSET
```will delete the history entry at offset OFFSET.

Hi,

Got the fellowing message:

"bash: history: OFFSET: history position out of range"

Don't know what it means. Sorry, I'm new to Ubuntu(Linux).

Thanks.

Ed

---

### Post by malspa on 2012-01-06
Hm. I thought you (the OP) meant how to clear the terminal, like when you use the following:

```
$ clear
```

---

### Post by sisco311 on 2012-01-06
You have to replace OFFSET with the line number of the command you want to delete from the history list. To display the history list with line numbers, simply run:```
history
```

---

### Post by EDLIU on 2012-01-06
> **sisco311 said:**
> You have to replace OFFSET with the line number of the command you want to delete from the history list. To display the history list with line numbers, simply run:```
history
```


Hi,

But if I try to delete the 2nd command(for example) from the history list, there will be a new "history -d 22(or what ever number)" in the history list.

Besides that, can I "Delete All" commands from the history list?

Thanks.

Ed

---

