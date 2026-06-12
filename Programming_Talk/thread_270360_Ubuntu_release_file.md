---
title: "Ubuntu release file?"
date: 2006-10-03
forum: Programming Talk
---

### Post by linux2512 on 2006-10-03
I was wondering if there's a good way for my app to determine the Ubuntu release of the PC the app is running on other than /etc/issue?
On RedHat/Fedora there the /etc/redhat-release and SuSE there's /etc/SuSE-release.

Any help is appreciated.

Thanks

---

### Post by nemin on 2006-10-03
> **linux2512 said:**
> I was wondering if there's a good way for my app to determine the Ubuntu release of the PC the app is running on other than /etc/issue?
Hm, perhaps you could use apt's sources.list? Though there should be a better way...

---

### Post by linux2512 on 2006-10-04
> **nemin said:**
> Hm, perhaps you could use apt's sources.list? Though there should be a better way...

The sources.list file doesn't have any version information.  I agree, there really has to be a better way.

---

### Post by Engnome on 2006-10-04
# Are we running on Dapper?
if ( ! grep "Ubuntu 6.06" /etc/issue >/dev/null 2>&1); then
    echo "This script is only intended for Ubuntu 6.06 Dapper Drake"
    exit 1
fi

code taken from "faster dapper" (GPL 2)

---

### Post by linux2512 on 2006-10-04
> **Engnome said:**
> # Are we running on Dapper?
if ( ! grep "Ubuntu 6.06" /etc/issue >/dev/null 2>&1); then
    echo "This script is only intended for Ubuntu 6.06 Dapper Drake"
    exit 1
fi

code taken from "faster dapper" (GPL 2)

Thanks Engnome, that's what I'm currently doing, but the problem with that is a lot of people (my self included) modify the /etc/issue and /etc/motd files to customize the login prompt and when you login remotely so it's not that reliable.

---

