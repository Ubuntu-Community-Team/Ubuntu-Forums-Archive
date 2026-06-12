---
title: "Sending registration data *without* a browser"
date: 2007-09-03
forum: Programming Talk
---

### Post by Acglaphotis on 2007-09-03
Hlow would i go and send registration data over the internet with python or a shell script?

-Thanks

---

### Post by ryno519 on 2007-09-03
> **Acglaphotis said:**
> Hlow would i go and send registration data over the internet with python or a shell script?

-Thanks

I suppose if you used a shell script you could just send a query string to the registration validation address using lynx. If you did it with python you could probably find an http library that would be able to do this kind of thing pretty easily.

---

### Post by Mirrorball on 2007-09-03
Registration or login? Also you are not trying to create a spam script, are you?

---

### Post by Acglaphotis on 2007-09-03
im trying to see if it can be done and how much it would impact a server, since im planning on mounting a website and i wanna see how apache would take something like that, because the server isnt exactly a top computer and i know some people who would like to spam my server if they had a chance. Sorry for not being clear.

---

### Post by Mirrorball on 2007-09-03
It definitely can be done.

---

### Post by ryno519 on 2007-09-03
> **Acglaphotis said:**
> im trying to see if it can be done and how much it would impact a server, since im planning on mounting a website and i wanna see how apache would take something like that, because the server isnt exactly a top computer and i know some people who would like to spam my server if they had a chance. Sorry for not being clear.

As I said, something like

lynx [http://url.com?username=foo&password=bar&email=foo@bar.com](http://url.com?username=foo&password=bar&email=foo@bar.com)

will send the request. Just stick that inside of a loop in a bash script and that might do the trick. This of course assumes that your registration script uses GET queries instead of POST. You could still do the post queries with lynx, but it might just be easier to change the type of queries you use for the purpose of testing.

---

### Post by nanotube on 2007-09-03
for python, you can look into the Browser class from the "mechanize" module. (google it)

but... about your server and stuff - if you suspect you'll be spammed a lot, that's why you put up a captcha for registration.

---

