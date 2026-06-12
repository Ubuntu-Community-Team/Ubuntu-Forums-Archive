---
title: "Firefox says, &quot;Insecure Connection&quot; when going to download Ubuntu"
date: 2017-12-29
forum: New to Ubuntu
---

### Post by anon24 on 2017-12-29
Is this something that I should be concerned about?   "The owner of releases.ubuntu.com has configured their website improperly. To protect your information from being stolen, Firefox has not connected to this website. mirror.picosecond.org uses an invalid security certificate. The certificate expired on Friday, November 10, 2017, 5:00 PM. The current time is Friday, December 29, 2017, 12:00 AM."

---

### Post by vasa1 on 2017-12-29
I'm not seeing that on [http://releases.ubuntu.com/](http://releases.ubuntu.com/). Which link in there did you click on?

---

### Post by ajgreeny on 2017-12-29
I'm not seeing a problem either.

Show us the full url of the link you used by right clicking it and selecting "Copy link location" and then post that back here.
I am wondering if the link is for a mirror rather than the ubuntu site itself?

---

### Post by VMC on 2017-12-29
I see a warning:
[https://ibb.co/kC546b](https://ibb.co/kC546b)

---

### Post by slickymaster on 2017-12-29
Chrome is also displaying that warning.

[ATTACH=CONFIG]277955[/ATTACH]

---

### Post by vasa1 on 2017-12-29
Okay, I didn't click on the little "i". But when I do, I see what VMC sees. Isn't that just because the site is http and not http_s_?

---

### Post by slickymaster on 2017-12-29
> **vasa1 said:**
> Okay, I didn't click on the little "i". But when I do, I see what VMC sees. Isn't that just because the site is http and not http_s_?

That would be my bet.

Just set up a VM with 18.04 ISO and the Firefox Detailed information states exactly that

[ATTACH=CONFIG]277956[/ATTACH]

---

### Post by vasa1 on 2017-12-29
But I don't see "... To protect your information from being stolen, Firefox has not connected to this website. mirror.picosecond.org uses an invalid security certificate. The certificate expired on Friday, November 10, 2017, 5:00 PM. The current time is Friday, December 29, 2017, 12:00 AM." which is reported by the OP :???:

---

### Post by slickymaster on 2017-12-29
> **vasa1 said:**
> But I don't see "... To protect your information from being stolen, Firefox has not connected to this website. mirror.picosecond.org uses an invalid security certificate. The certificate expired on Friday, November 10, 2017, 5:00 PM. The current time is Friday, December 29, 2017, 12:00 AM." which is reported by the OP :???:

Yep, me neither

---

### Post by deadflowr on 2017-12-29
Myself, I would only be slightly concerned about the cert issue, but the image is still hashed and you can still verify it:
[https://help.ubuntu.com/community/VerifyIsoHowto]("https://help.ubuntu.com/community/VerifyIsoHowto")

You can go contact the mirror admins to see if something is off:
[https://launchpad.net/~picosecond-mirror-admins]("https://launchpad.net/~picosecond-mirror-admins")

The mirror itself is currently listed as up-to-date, so...

Edit:
when in doubt, torrent the iso.

---

### Post by quasimodo69 on 2018-01-01
> **anon24 said:**
> Is this something that I should be concerned about?   "The owner of releases.ubuntu.com has configured their website improperly. To protect your information from being stolen, Firefox has not connected to this website. mirror.picosecond.org uses an invalid security certificate. The certificate expired on Friday, November 10, 2017, 5:00 PM. The current time is Friday, December 29, 2017, 12:00 AM."

Every time I have come across this error it was a bad date on my computer....a motherboard battery going bad...or a glitch of some other kind changed my date causing the date from the website security certificate to be out of date...maybe.

---

