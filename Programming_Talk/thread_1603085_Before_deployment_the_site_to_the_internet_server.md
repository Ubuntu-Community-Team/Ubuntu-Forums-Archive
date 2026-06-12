---
title: "Before deployment the site to the internet server"
date: 2010-10-22
forum: Programming Talk
---

### Post by medic2000 on 2010-10-22
Site is written in php. What should i do? Disable the error messages on php? And what after that?

---

### Post by v8YKxgHe on 2010-10-22
No, never ever ever turn off error messages on a production server, that's the worse thing you could do.

What you do want to do however, is to turn off the display of errors with the 'display_errors' directive, and instead log them to a file (see 'error_log').

However, why are there PHP errors/warnings/notices within your application to start with?

---

