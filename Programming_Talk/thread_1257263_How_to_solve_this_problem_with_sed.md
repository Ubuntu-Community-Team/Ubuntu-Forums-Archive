---
title: "How to solve this problem with sed"
date: 2009-09-03
forum: Programming Talk
---

### Post by flylehe on 2009-09-03
Hi,
I have many such parts in my file
> 
main.o : main.cc defs.h \
    src/misc.h


I want to specify some prefix right before the object files, i.e.
> 
$(BIN_DIR)main.o : main.cc defs.h \
     src/misc.h


How to do it by sed?

Thanks and regards!

---

### Post by stroyan on 2009-09-03
Assuming that the targets that you want to change all consist of alphanumeric characters and periods followed by an optional group of spaces and a colon, use-
```
sed -e 's/^[[:alnum:].]\+ *:/\$(BIN_DIR)&/' Makefile > Makefile.new
```
That will put the "$(BIN_DIR)" in front of every line that starts with that pattern.
You may need to tweek the pattern to match only the lines that you want.

---

### Post by ghostdog74 on 2009-09-03
```

awk -F":" '/\.o /{ $1="${BINIR}"$1}1' file

```

---

