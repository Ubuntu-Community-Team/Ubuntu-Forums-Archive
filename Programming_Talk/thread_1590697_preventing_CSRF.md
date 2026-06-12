---
title: "preventing CSRF"
date: 2010-10-08
forum: Programming Talk
---

### Post by DanielWaterworth on 2010-10-08
I'm learning about preventing CSRF. One of the things I've seen recommended is to add a random string into each form that is stored in the session. What I'm wondering is, isn't it possible for a flash object to read the page that the form is in and parse it for the random-string and hence use that for the actual CSRF request.

In that case it seems better to create javascript code to read the session_id from the cookie and store that in a hidden value in the form on page load so that it gets sent in with the form and can be checked on the server.

My question is:

Is there another way of preventing CSRF without javascript?

---

