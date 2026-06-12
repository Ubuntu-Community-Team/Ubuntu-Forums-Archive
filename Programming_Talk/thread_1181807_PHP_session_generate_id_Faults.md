---
title: "PHP session_generate_id Faults"
date: 2009-06-08
forum: Programming Talk
---

### Post by HornedBeast on 2009-06-08
Hello,

I am having trouble with the issue of visitors quickly reloading pages or double clicking on links and losing all their session data.

It's taken me ages to find the problem, but it defiantly stems from session_regenerate_id(true).

If a visitor quickly hits refresh or clicks on a link or form submit very quickly then all the session data is lost due to the browser not being able to keep up. It cannot move the old data to the new ID quick enough, so it losses it.

However, I like the security of the ever changing sessionid on every page request. Is there any way around this or a better way of protecting myself from Session Hijacking?

Regards,

Horned Beast

---

