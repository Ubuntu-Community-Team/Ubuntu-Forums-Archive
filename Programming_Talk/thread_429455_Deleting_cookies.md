---
title: "Deleting cookies"
date: 2007-05-01
forum: Programming Talk
---

### Post by LaRoza on 2007-05-01
I am having trouble with cookies and PHP, I want to delete a cookie I set, but all the tutorials and books say something different, and none of them seem to work.

I have tried:

1. Resetting the cookie to a null value.
2. Resetting the cookie with a negative expiration date.
3. Changing the expiration on the original cookie, to a session and to 5 hours.
4. Every combination of the above methods.

Am I missing something?

Thanks.

---

### Post by scottious on 2007-05-03
setcookie('user','',time()-3600) 

Have you tried that approach?  That's all I can think of for setting a cookie to expire.

---

### Post by LaRoza on 2007-05-03
I did resolve it, that method is the way to do it, but I was doing it from a different page.

---

