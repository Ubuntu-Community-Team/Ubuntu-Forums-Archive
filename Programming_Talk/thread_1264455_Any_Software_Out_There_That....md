---
title: "Any Software Out There That..."
date: 2009-09-12
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-09-12
... Can allow me and others to get forwarded mail from a single email account? My friend and I have formed a club and we both switch off on checking the group's email but is there any program out there or email provider that can forward mail to two separate accounts and possibly even let both of us know if one of us has already responded to an email?

If not, I would like to attempt programming something to do this. Any pointers on how to go about this and where to start? Thanks!

---

### Post by soltanis on 2009-09-12
This is a roundabout way to do it.

(1) Create a mailing list, and place yourself and your friend on it.
(2) Have all incoming emails forwarded to your mailing list.
(3) When responding to emails, cc: the list to notify everyone else that you replied.

---

### Post by donkyhotay on 2009-09-12
> **soltanis said:**
> This is a roundabout way to do it.

(1) Create a mailing list, and place yourself and your friend on it.
(2) Have all incoming emails forwarded to your mailing list.
(3) When responding to emails, cc: the list to notify everyone else that you replied.

That would be the easiest solution I can come up with. Only other solution would be to have a 'shared' pop3 Email account and make certain that messages are not deleted on download. Course, I can't think of anyway from that point to find out if a message has been replied which brings us back to the mailing list solution.

---

### Post by StunnerAlpha on 2009-09-13
Thanks for the replies guys. That roundabout way is not a bad idea I think I will try that. But if I happened to want to program something to do this automatically I would need to get an SMTP server to which I would forward all emails from the club account, then that SMTP server would have to send those emails to two separate accounts(mine and my friend's). Then whenever one of us replies it would have to send the email to the other as well so that we know if one of us replied... any way to do this automatically without me or my friend explicitly CCing the other? Am I close or completely and utterly lost? I know a bit about how email works and if I were to program something I would use python. I appreciate any ideas and input, thanks.

---

### Post by CptPicard on 2009-09-13
Google Groups?

---

