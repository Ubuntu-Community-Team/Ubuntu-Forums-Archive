---
title: "Firefox 33 doesn't store session after update"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by e-mail-4 on 2014-10-16
After last update Firefox to v 33.0 it start to lost sessions. I find what it happens because of pemissions problem.
How to solve this: **sudo chmod 666 ~/.mozilla/firefox/[your letter-phrase here].default/sessionstore.js**
It allow Firefox to read sessions file.

---

### Post by Impavidus on 2014-10-16
Something is not right there. I haven't got a sessionstore.js file there (some similar names exist). I don't think there should be any files with permissions 666 in .mozilla/firefox/. Permissions 600 should be OK. If you need sudo to change permissions there, you must have files not owned by you in your home directory, which is wrong. It could happen when you run firefox as root, which is a very bad idea BTW.

---

### Post by ajgreeny on 2014-10-16
That sessionstore.js file will now be owned by root.  Everything in the .mozilla folder in your home should be owned by you so check that with ```
ls -lR .mozilla | grep root
```which should not show any output.  If it does than something there is owned by root and will need you to change ownership back to yourself.

---

