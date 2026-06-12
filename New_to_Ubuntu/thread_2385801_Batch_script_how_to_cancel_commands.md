---
title: "Batch script how to cancel commands?"
date: 2018-02-25
forum: New to Ubuntu
---

### Post by brianww on 2018-02-25
So if i for example write the following **printf "-b test"** printf will see **-b** as a flag. I want to be able to print **-b** without **printf** viewing it as flag

---

### Post by steeldriver on 2018-02-25
You can use `--` (two dashes) to denote the end of options

```

printf -- '-b test'

```

(this is a convention adopted by many GNU utilities)

---

### Post by sisco311 on 2018-02-25
```
printf %s "-b test"
```
or
```
printf -- "-b test"
```

EDIT: steeldriver beat me to it. Did not refresh the page before posting.

NOTE: -- (end of options) works with many utilities, but there are some exceptions like **echo**

---

