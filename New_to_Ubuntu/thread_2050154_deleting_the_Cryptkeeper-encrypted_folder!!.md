---
title: "deleting the Cryptkeeper-encrypted folder!!"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-08-30
i created this (screenshot) encrypted folder in my desktop using Cryptkeeper!!
 and now it's not being unmounted nor being deleted! please help!

---

### Post by androssofer on 2012-08-30
> **tojonukokhadush said:**
> i created this (screenshot) encrypted folder in my desktop using Cryptkeeper!!
 and now it's not being unmounted nor being deleted! please help!

Nice font on the error box... i digress...

umount should do the trick for you, run this in the terminal:

```
sudo umount -f /home/bijay/Desktop/Encrypted!/Encrypted!
```

The filepath might be wrong, so double check, its just the filepath to the encrypted volume.

---

### Post by tojonukokhadush on 2012-08-30
yeah! thankyou very much for the help. that would have certainly helped but i did restart my pc at the first hand to find things normal and that unmounted volume gone!


and the font is hansa.ttf; you might love to use it as well! ;-)

---

