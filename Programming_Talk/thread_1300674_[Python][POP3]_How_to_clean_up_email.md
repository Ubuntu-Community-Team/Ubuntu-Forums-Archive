---
title: "[Python][POP3] How to clean up email?"
date: 2009-10-25
forum: Programming Talk
---

### Post by fiddler616 on 2009-10-25
Hello,

I've been trying to find a good way to clean up emails received via POP3--they come in like this:
> Delivered-To: *<address>* Received: by *<IP address>* with SMTP id k20cs48757rve;        Sun, 25 Oct 2009 06:04:53 -0700 (PDT)Received: by *<IP>* with SMTP id 6mr3370621ybg.261.1256475892668;        Sun, 25 Oct 2009 06:04:52 -0700 (PDT)Return-Path: *<address>*Received: from mail-yw0-f188.google.com (mail-yw0-f188.google.com [209.85.211.188])        by mx.google.com with ESMTP id 4si12671253ywh.47.2009.10.25.06.04.51;        Sun, 25 Oct 2009 06:04:51 -0700 (PDT)Received-SPF: pass (google.com: domain of [email]tsmacdonald@gmail.com[/email] designates 209.85.211.188 as permitted sen **etcetera**
and I haven't been able to make a foolproof regex to extract the actual message. Google has not revealed any good modules or other solutions, so what should I do?

PS: Is there any benefit to using IMAP instead?

Thanks.

---

