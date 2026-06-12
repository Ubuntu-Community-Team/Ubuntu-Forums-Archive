---
title: "Reinstall?"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-16
1. Can one reinstall Ubuntu by just formatting the root partition & not checking the /home?

2. Have 3 partitions, /30 GiB, /home 263 GiB & swap 5 GiB.

3. So that data in the home doesn't get deleted.

4. Will I have to reinstall all updates too along with apps?

Thanks.

---

### Post by Elfy on 2013-01-16
That is correct. Using Soemthing Else and setting mountpoints for / and /home, but not formatting /home will do that.

Yes you will need to reinstall apps and update again, however there's nothing to stop you copying the debs from /var/cache/apt/archives and then putting them back in the new install, you'll need root nautilus to do that. Assuming that the new install is the same version.

---

### Post by Yezinki on 2013-01-16
Thanks again Elfy.

---

