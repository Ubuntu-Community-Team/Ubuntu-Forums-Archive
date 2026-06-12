---
title: "Running client script from browser"
date: 2009-07-12
forum: Programming Talk
---

### Post by tc101 on 2009-07-12
This questions relates to MS products, but I know lots of programmers here are working in the MS world and have helped me in the past, so here goes:

I need to run a vbscript on client computers in the most user friendly way possible.  This is all in house stuff.  My boss would prefer that we start it from a browser, since many of the users are not very computer literate but are used to using our company wide web app.

Is there a way to do this?  I know normally you couldn't because of security reasons but I can set security on the client machines any way I want.

Our web app is classic asp in vbscript, and client side javascript, all running in Internet Explorer.  How can I start client side VBScript from there?

---

### Post by tc101 on 2009-07-13
No answers on the question on running vbscript on client from the browser.  I guess short of creating an activeX to do it, there is no way because of security.  Is that correct?

---

### Post by pokerbirch on 2009-07-13
It all depends on what the script needs to do. Even complicated Flash and Java Applets have restricted access and cannot save files to the hard drives, etc. I'm no expert, but i don't think you can do this *safely*.

---

### Post by tc101 on 2009-07-13
Thanks.  I've come to the same conclusion.  It will take me a minute to put a shortcut on the desktop.  It is not worth the slight extra convenience to spend hours figuring out how I might do it from a browser.

---

### Post by soltanis on 2009-07-13
That or have the script be downloaded then run an installer of some kind (hopefully your users understand how that works). Blowing the security hole necessary to do this automatically is completely possible (especially with Internet Explorer) but will leave your computers vulnerable and very quickly infected if anyone ever wanders from your intranet.

---

