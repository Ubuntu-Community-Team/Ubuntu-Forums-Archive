---
title: "failed to lock /var/...../lock?"
date: 2008-11-10
forum: Philippine Team
---

### Post by adredz on 2008-11-10
got the error after fresh install and attempted install updates. i changed the ownership to mine and it worked. the question is, was my workaround appropriate?

---

### Post by loell on 2008-11-10
i guess, if the previous apt forgot to unlock it. as long as there is no current apt running when you do this, then its fine.

---

### Post by adredz on 2008-11-10
i think you misunderstood me. i had the error prior to installing the updates. i had to change the onwnership to enable updates. is the lock dir/file supposed to have a root permission? should i change it back? guess i have to find it out come the next update...

---

### Post by loell on 2008-11-10
nope i did not, the lock occurs only because apt was working on something, it doesn't need to be a prior update, it could be that you were installing a software from the repo? or anything that triggered APT, prior to installing an update. 

apt will recreate the "lock" file anyway, everytime you install/uninstall. so no need of reverting it back.

---

### Post by adredz on 2008-11-10
aw, thanks poh..:)

---

### Post by loell on 2008-11-10
np.. :)

---

