---
title: "After Updation from 14.04 to 16.04, encfs folder access lost"
date: 2016-07-30
forum: New to Ubuntu
---

### Post by vesa4 on 2016-07-30
After Upgrading from 14.04 to 16.04, i am unable to access my encfs folder.
The folder doesn't show any lock and there is no content in the folder.

I even tried the below
```
encfs ~/.encrypted ~/visible
```

I tried all the password that i use for encryption but its not working.

Is there any way i can retrieve the data stored in the folder.

---

### Post by gordintoronto on 2016-07-30
Do you use Cryptkeeper? I added an SSD and installed Mint 18 on it, then installed Cryptkeeper. It took some work, but I eventually tracked down my encrypted folder on the old hard drive, and opened it with Cryptkeeper. It's an encfs folder.

---

