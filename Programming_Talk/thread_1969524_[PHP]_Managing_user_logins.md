---
title: "[PHP] Managing user logins"
date: 2012-04-30
forum: Programming Talk
---

### Post by ki4jgt on 2012-04-30
What's the best way to manage user logins via PHP? I'm talking the whole shabang. I know how to give the users cookies and all but I don't know how to manage those cookies. What system do most php developers use to manage user logins?

---

### Post by Barrucadu on 2012-04-30
Generally you'll have some database containing usernames and passwords. When someone logs in, you will check the credentials and (if correct) use sessions to store some sort of authentication token. To check if a person is already logged in, you check if the token is set and that it is valid.

---

### Post by rg4w on 2012-04-30
PHP provides pretty good support for sessions as well, helpful for managing all sorts of session-specific data:
[http://www.php.net/manual/en/book.session.php](http://www.php.net/manual/en/book.session.php)

---

