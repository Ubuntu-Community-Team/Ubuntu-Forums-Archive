---
title: "is there any other way wget can check newer file besides timestamp?"
date: 2007-09-03
forum: Programming Talk
---

### Post by Hopeless on 2007-09-03
hi,

is there any other way wget can compare file size instead of timestamp? i download .asp pages where there is no timestamp on them...so it's always downloading ALL pages even if unchanged...

thanks..

---

### Post by aks44 on 2007-09-03
AFAIK there's hardly a way to determine if a dynamic page has changed, since it is generated on the fly.

Moreover, most dynamic pages explicitely set nocache headers to force the client reloading the page.

If you have some control on the ASP pages (which I guess isn't the case) you could output a timestamp header. But this is quite impractical since most of the time it implies to store timestamps in (almost) every record of the database.

EDIT: another technique is the eTag header, but again you are dependent on whether the site developper implemented it (which is quite burdensome for dynamic pages, it is easier to implement timestamps)

---

