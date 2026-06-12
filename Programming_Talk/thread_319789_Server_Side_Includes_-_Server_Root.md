---
title: "Server Side Includes - Server Root"
date: 2006-12-16
forum: Programming Talk
---

### Post by anthro398 on 2006-12-16
Does anyone know how virtual includes work when the site is hosted from a public_html directory in the user's home?  <!--#include VIRTUAL="/includes/banner.html" --> seems to work in some cases on not in others.  In this case, the includes directory is at /home/user/public_html/includes.  I'm not sure whether /var/www/ is still considered root or /home/user/public_html is considered root when determining where the virtual include path points?  I understand how include file works and it won't work in this situation.

This isn't really programming, but I didn't see a better place for it.

Thanks.

---

