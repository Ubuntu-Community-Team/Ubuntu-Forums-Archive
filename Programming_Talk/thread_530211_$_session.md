---
title: "$_session"
date: 2007-08-20
forum: Programming Talk
---

### Post by carteris21 on 2007-08-20
Hello, i would like to know, in which side server or client stored array's($_SESSION) information?

---

### Post by carteris21 on 2007-08-20
It's a php array.

---

### Post by LaRoza on 2007-08-20
$_SESSION variables are stored in cookies, if possible on the client and remembered by the server for that session.

---

### Post by merkur2k on 2007-08-21
not quite...
all session information is stored on the server (it would be a security risk to transmit it to the client).
only a unique identifier (PHPSESSID) is stored in the cookie on the client.

---

