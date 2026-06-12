---
title: "Update manager?"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-04
Though it's set to check for updates daily it doesn't, have to check manually, can this be fixed?

Thanks.

---

### Post by NikTh on 2012-10-04
> **Yezinki said:**
> Though it's set to check for updates daily it doesn't, have to check manually, can this be fixed?

How are you sure about that ? 

Ubuntu updates are not available everyday. 

You can check if you have right (or wrong) with terminal. 

If you give ```
sudo apt-get update ; sudo apt-get upgrade
```and you receive updates , and update-manager has not a notification for you, then you have right.  (OR you have not set correctly the options)

Try to change it with 
```
gksudo software-properties-gtk
``` go to "Updates" and check if 

```
**Automatic check for updates : _Daily _**
When there are security updates : immediately
**When there are other updates:_ immediately _**
```
Thanks

---

### Post by Yezinki on 2012-10-04
Thanks NikTh for replying & posted commands.

I had in settings> Updates> other updates weekly rest daily.

Now it's fixed.

Thanks again for your expert assistance.

---

