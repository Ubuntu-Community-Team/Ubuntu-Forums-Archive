---
title: "Link &quot;selected&quot; status with PHP?"
date: 2007-12-13
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-12-13
I'm redesigning my website, and one thing I could definitely use is a technique to place a "selected" class on the current page's link. Is there a way to do this? Right now, I include a header, navigation, and footer. For example, a page title is passed to the header from the specific page.

---

### Post by geirha on 2007-12-13
You want to set a class attribute on an html element based on the url? Have a look at $_SERVER['PHP_SELF'] at [http://www.php.net/manual/en/reserved.variables.php](http://www.php.net/manual/en/reserved.variables.php)

---

### Post by LaRoza on 2007-12-13
The client side script on my site: [http://laroza.freehostia.com](http://laroza.freehostia.com) has that.

It only highlights it however, not disables.

---

