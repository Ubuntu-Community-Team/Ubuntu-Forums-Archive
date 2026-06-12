---
title: "Question about encrypted /home."
date: 2012-11-08
forum: New to Ubuntu
---

### Post by Unity User on 2012-11-08
I have ubuntu 12.04 installed on a VBox. During the install I selected to encrypt the /home folder. I noticed when I started creating extra user account that is does not offer to encrypt those accounts. Does this mean that all of the Home folders are encrypted with the same key?

Thanks!

---

### Post by Popenuj on 2012-11-09
For adding a user with an encrypted home
```
sudo adduser --encrypt-home (new user's name)
```

Or have you already added them and would now like to edit them?

---

### Post by Unity User on 2012-12-20
Thanks for the input. I was just wandering why the GUI didn't offer to do this for new accounts.

---

### Post by zombifier25 on 2012-12-20
> **Unity User said:**
> Thanks for the input. I was just wandering why the GUI didn't offer to do this for new accounts.

If you feel that this is something they should add, then file a bug report :) It'll get the developers' attention.

---

