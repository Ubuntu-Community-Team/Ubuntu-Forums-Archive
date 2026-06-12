---
title: "HTTP methods"
date: 2010-08-16
forum: Programming Talk
---

### Post by hakermania on 2010-08-16
Ok, so, let's say we have a foroum in which there are several topics.
Each topic says beside its name how many views it has.

When you view a topic an extra "view point" is added. 
Although, when you wget this page (e.g. [www.foroum.com/posts/Hello-All.html](www.foroum.com/posts/Hello-All.html)) there is not added a view.
So, there is another method that the server understands how many have viewed the page, and it does not count how many times he has given the HTML page to persons. 
So, how does it do it?

---

### Post by Hellkeepa on 2010-08-17
HELLo!

The view counter is implemented in a server side language, which the pure html page does not use. It's as simple as that.

Happy codin'!

---

### Post by hakermania on 2010-08-17
Can you please tell me where to start ? In which language it is written?

---

### Post by PaulM1985 on 2010-08-17
It could be written in one of many server side languages.  JSP and Java Servlets have the ability to do this.  I believe that PHP would be able to do this aswell (although I do not personally have any experience in PHP).

Paul

---

### Post by hakermania on 2010-08-18
So,with the help of these languages, can I send specific signals to the server and add views to a specific post?

---

### Post by Bachstelze on 2010-08-18
You need to ask the forum owners how they implement that, no one here has a crystal ball to guess it.  There are several ways to do that, one would be to check the referer headers, and increment the counter only if it's another forum page.

---

