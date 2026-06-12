---
title: "Forum view count logic. How it works?"
date: 2010-06-26
forum: Programming Talk
---

### Post by aklo on 2010-06-26
Alright i'm making a forum as a school project and I want to know how "number of views" works.

Right now getting the number of views to increase is no problem but if it is within the page, the view count will increase everytime the page refreshes, I'm almost certain this is not the way how "number of views" works. 

So questions are:

Is the view count unique for every visitor? 10 views means 10 different users.
How long does this unique counter last? If i view a thread now, it +1 to the view count, will it increase again if i visit the same thread like 2 days later?



If it is unique, how can I do that without it increasing every time the page reloads?

---

### Post by simeon87 on 2010-06-26
Store the IP address and the time in a database and increment the counter. Only increment the counter again when at least x hours of minutes have passed (and store the time again when doing so).

---

### Post by aklo on 2010-06-26
Thanks ! It makes sense.

---

### Post by lavinog on 2010-06-26
You might want to use a cookie.
What if there are multiple users that use the same ip address?

---

### Post by DanielWaterworth on 2010-06-26
If you're doing this as a school project, then you're likely to all be on the same IP address, the cookie approach is better in this case. Check for the cookie, increment it's not there and add the cookie, (make sure the expire time is set right too).

---

