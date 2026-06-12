---
title: "PHP/HTML Newbies: find out if there is no frame or target?"
date: 2011-07-10
forum: Programming Talk
---

### Post by honeybear on 2011-07-10
Hello, 

In my site, somtimes some user get out of my frame by direct opening. How to detect if there is no  frame or target and then to impose to put frame back on main page? 

--------------
|   |        |
|   |        |
|   | target |
|   |        |
|   |        |
|   |        |
--------------

Thank you in advance

---

### Post by gingerkid101 on 2011-07-11
> **honeybear said:**
> Hello, 

In my site, somtimes some user get out of my frame by direct opening. How to detect if there is no  frame or target and then to impose to put frame back on main page? 

--------------
|   |        |
|   |        |
|   | target |
|   |        |
|   |        |
|   |        |
--------------

Thank you in advance

Don't use frames. They are way outdated IMO. I'd use div layers and css to accomplish the same thing. Use a PHP include to avoid repetitive code.

---

### Post by roccivic on 2011-07-11
+1 for what gingerkid said. 

If you really want to keep using the frames, try something along these lines:

Start a session in the main window and assign a random string to a session variable. Then append this variable to the url of the frame content (e.g: [http://www.example.com/page.php?var=123456](http://www.example.com/page.php?var=123456)).

When the frame content is being loaded, check the value of $_GET['var'] and see if it matches what you stored in the session variable. If it doesn't the frame content is definitely being loaded directly, so issue an error message.

N.B.: This is not fully thought though and there may be a whole bunch of issues with this approach (concurrent access, false positives, no cookies on user's browser, etc).

---

