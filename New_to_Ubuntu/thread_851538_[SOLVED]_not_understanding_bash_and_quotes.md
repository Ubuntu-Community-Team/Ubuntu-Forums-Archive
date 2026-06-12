---
title: "[SOLVED] not understanding bash and quotes"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by il-luzhin on 2008-07-06
How can I get around this path name that has spaces?  I'm getting a 'too many arguments' error.

```

dest='/media/"Media and BU"/Music'

if [ -d $dest ]; 

```

Thanks folks

---

### Post by sdennie on 2008-07-06
Try "\ " instead:

```

dest=/media/Media\ and\ BU/Music

```

---

### Post by jpkotta on 2008-07-06
You need to quote the dollar-signed variable.


```

var="string with spaces"

func "$var"

```

---

### Post by il-luzhin on 2008-07-06
like a charm!

thnx vor, jpkotta!

---

