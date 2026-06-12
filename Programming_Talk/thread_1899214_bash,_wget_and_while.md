---
title: "bash, wget and while"
date: 2011-12-23
forum: Programming Talk
---

### Post by kåring on 2011-12-23
Hi!

I need some help with a script. 

I'ts purpose is to download files from a spesific site every minute. But i want it to move the downloaded file after the download is complete. Move and overwrite if needed.

Can anyone help me?

```
#!/bin/bash

while [ 60 ]; do
wget --convert-links -r SITEADDRESS &
sleep 60
done

```

---

### Post by Bachstelze on 2011-12-23
Use the [font=monospace]-O[/font] flag of wget.

---

### Post by hakermania on 2011-12-23
Hey, also the
```

while [ 60 ]; do

```will be always true, so why not use
```

while true; do

```instead?

Plus, the
```

sleep 60

```could be
```

sleep 1m

```

---

### Post by kåring on 2011-12-23
Thanks! :)

---

