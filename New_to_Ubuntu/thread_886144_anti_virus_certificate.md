---
title: "anti virus certificate"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by sqela on 2008-08-10
i have an issue and i hope this would be the correct section to post this. if not i appoligies. anyway i'm a very happy ubuntu user and use ubuntu everyday including using it for work. one of my side jobs includes working for a lawyer and submiting legal documents to the court's site. however the clerk is asking for a anti-virus certificate. Now how do i go about either providing one or in non noob terms explain that i don't need one?

---

### Post by lisati on 2008-08-10
Doesn't their incoming email scanner provide one for them?

Perhaps some kind of signature on your email from within your email client.....

---

### Post by Yannick Le Saint kyncani on 2008-08-10
> **sqela said:**
> however the clerk is asking for a anti-virus certificate. Now how do i go about either providing one or in non noob terms explain that i don't need one?

You could install clamav. It has a frontends both for gnome (avscan) and kde (klamav).

---

### Post by freak42 on 2008-08-11
I would try to educate him (in a friendly way though):

Tell him/her:

- That one should not rely on anything received including lines that
tell that the email has been virus scanned.

- Such a line can be easily faked by anybody.

- That, not surprisingly, malware that emails itself and/or malware distributors like to add such a notice that the email is malware-free.

- Even if the line was written by an antivirus software, this software might not have recognized the virus for various reasons: It might be out of date, the virus might be really new, the antivirus-software might have been manipulated by malware.

- They should rely only on protection they use, which they certainly do. He/She should ask their system administrator about what their organization security measures are and if their incoming email is scanned for malware (which it hopefully is).

- That you take great care of your system and are not very likely to distribute a virus. That you are using Linux, and despite that it is possible for your system to have a virus, chances are extremely low because Linux is designed to be secure and because Linux's low distribution profile doesn't make it a target for major virus/malware distributors.


hth

---

### Post by hyper_ch on 2008-08-11
> **freak42 said:**
> I would try to educate him (in a friendly way though):

Tell him/her:

[...]


hth

The only problem is that this is a court and the courts are always right ;) You can't really make them listen to you, you will have to adjust to them.

---

### Post by mcduck on 2008-08-11
..so you can just make a certificate of your own and configure your email application to use it as signature.. It's worth just as much as any other antivirus certificate attached by the _senders_ server, and everybody is happy. :D

---

