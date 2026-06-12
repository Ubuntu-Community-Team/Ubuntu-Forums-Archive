---
title: "how can sort as number of character"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by say2sky on 2008-11-04
In unix lensort can be used to  sorts lines from shortest to longest.

How I can do the same thing by use linux command ie. sort according to the number of character in a line or in a field.

Thanks for help!

---

### Post by tatsuno on 2008-11-04
```

awk '{print length($0), $0}' input_file | sort -n | cut -d" " -f2-

```

---

### Post by say2sky on 2008-11-04
> **tatsuno said:**
> ```

awk '{print length($0), $0}' input_file | sort -n | cut -d" " -f2-

```

great, thank you very much.

---

