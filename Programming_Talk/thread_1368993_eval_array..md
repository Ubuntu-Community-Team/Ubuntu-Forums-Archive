---
title: "eval array."
date: 2009-12-31
forum: Programming Talk
---

### Post by J05HYYY on 2009-12-31
sorry to keep litter bombing this forum, I seem to find myself coming across niggley mistakes... any suggestions much appreciated.

```
#!/bin/sh
i=0
text="why wont spaces work? how can I get them to work?"
eval array${i}="$text"
eval echo "\$array${i}"
```

---

### Post by Arndt on 2009-12-31
> **J05HYYY said:**
> sorry to keep litter bombing this forum, I seem to find myself coming across niggley mistakes... any suggestions much appreciated.

```
#!/bin/sh
i=0
text="why wont spaces work? how can I get them to work?"
eval array${i}="$text"
eval echo "\$array${i}"
```

Shouldn't you have /bin/bash instead of /bin/sh?

---

### Post by J05HYYY on 2009-12-31
no, I want to use sh.

got it now:

```
#!/bin/sh
i=0
text="why wont spaces work? how can I get them to work?"
eval array${i}='$text'
eval echo "\$array${i}"
```

ta :)

---

