---
title: "How can I set cookie in PHP for Internet Explorer"
date: 2011-01-31
forum: Programming Talk
---

### Post by The_Aegidius on 2011-01-31
I have this code for setting cookie in PHP

```

define("COOKIE_EXPIRE", (time() + (60 * 60 * 24 * 7)));
[...]
setcookie("country_iso", $location["country"], COOKIE_EXPIRE);

```

But it does not work for Internet Explorer 8. I realized that the function *setcookie* even does not return false, as it actually set the cookie.

How can I fix it?

---

