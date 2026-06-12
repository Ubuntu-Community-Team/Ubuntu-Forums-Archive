---
title: "Run specific lines as root."
date: 2007-06-08
forum: Programming Talk
---

### Post by loathsome on 2007-06-08
Hi there,

How can I do something like this?

```

#!bin/bash

/usr/local/sbin/wifi # AS ROOT
/usr/local/sbin/mekk # **NOT** as root.

```

Thanks.

---

### Post by FuturePast on 2007-06-08
> **loathsome said:**
> Hi there,

How can I do something like this?

```

#!bin/bash

[COLOR="Red"]su -c[/COLOR] /usr/local/sbin/wifi # AS ROOT
/usr/local/sbin/mekk # **NOT** as root.

```

Thanks.

?

---

### Post by loathsome on 2007-06-08
Yeah, but if I initialize the script «sudo sh script.sh», everything will be run as root.

That's not what I want :)

---

### Post by FuturePast on 2007-06-08
Then don't run the script as root!

(Use the sudo in the script if you want)

---

