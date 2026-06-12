---
title: "Ubuntu Postfix TLS check"
date: 2008-06-20
forum: Philippine Team
---

### Post by jmazaredo on 2008-06-20
I need to know how to check TLS (mail) if it is working. I know 

> $ telnet mail.example.com 25
Trying 192.168.100.11...
Connected to 192.168.100.11.
Escape character is '^]'.
220 scallop.seaglass.com ESMTP Postfix
EHLO localhost
250-scallop.seaglass.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-XVERP
250 8BITMIME
quit

But when both server talks how do they negotiate and how do i know if both has accepted tls . (zakame tell me :) )

Here is a header can you tell me where in that part where tls is

> Return-Path: <brandon.roppe@ge.com>
X-Original-To: [email]postmaster@agilys.com.ph[/email]
Delivered-To: [email]postmaster@agilys.com.ph[/email]
Received: from localhost (localhost [127.0.0.1])
     by mail.agilys.com.ph (Postfix) with ESMTP id EB1312502E9
     for <postmaster@agilys.com.ph>; Sat, 21 Jun 2008 07:14:30 +0800 (PHT)
X-Virus-Scanned: Debian amavisd-new at mail.agilys.com.ph
Received: from mail.agilys.com.ph ([127.0.0.1])
     by localhost (mail.agilys.com.ph [127.0.0.1]) (amavisd-new, port 10024)
     with ESMTP id 8LudbVkmmWqC for <postmaster@agilys.com.ph>;
     Sat, 21 Jun 2008 07:14:24 +0800 (PHT)
Received: from ext-cn0ut-4.online-age.net (ext-cn0ut-4.online-age.net [63.210.253.233])
     by mail.agilys.com.ph (Postfix) with ESMTPS id 23DA82502C6
     for <postmaster@agilys.com.ph>; Sat, 21 Jun 2008 07:14:23 +0800 (PHT)
Received: from int-cn0ut-4.online-age.net (int-cn0ut-4.online-age.net [3.159.252.73])
     by ext-cn0ut-4.online-age.net (8.13.6/8.13.6/20051114-SVVS-TLS-DNSBL) with ESMTP id m5KNEJUj018700
     for <postmaster@agilys.com.ph>; Fri, 20 Jun 2008 19:14:19 -0400
Received: from cinmlef03.e2k.ad.ge.com (int-cn0ut-4.online-age.net [3.159.252.73])
     by int-cn0ut-4.online-age.net (8.13.6/8.13.6/20050510-SVVS) with ESMTP id m5KNEIFc019203
     for <postmaster@agilys.com.ph>; Fri, 20 Jun 2008 19:14:19 -0400
Received: from CINMLVEM12.e2k.ad.ge.com ([3.159.214.56]) by cinmlef03.e2k.ad.ge.com with Microsoft SMTPSVC(6.0.3790.2499);
     Fri, 20 Jun 2008 19:14:18 -0400
X-MimeOLE: Produced By Microsoft Exchange V6.5
Content-class: urn:content-classes:mdn
MIME-Version: 1.0
Content-Type: multipart/report;
     report-type=disposition-notification;
     boundary="----_=_NextPart_001_01C8D32B.5D6A89D6"
Subject: Read: Test Mail Only
Date: Fri, 20 Jun 2008 19:14:18 -0400
Message-ID: <86EDF07DE71B444F9B0FA7F8EC8C12D5D2B7C3@CINMLVEM12.e2k.ad.ge.com>
X-MS-Has-Attach: 
X-MS-TNEF-Correlator: 
Thread-Topic: Test Mail Only
Thread-Index: AcjTK0oQ4A8jycF9RKKve/i8lWxajgAABNae
From: "Roppe, Brandon (GE Infra, Non-GE, US)" <brandon.roppe@ge.com>
To: <postmaster@agilys.com.ph>
X-OriginalArrivalTime: 20 Jun 2008 23:14:18.0742 (UTC) FILETIME=[5D98F960:01C8D32B]

TYVM :lolflag:

---

### Post by boyguapo on 2009-06-09
hi to all of you here,

ask you something, i need the code, for mail cofig on ubuntu 9.04 server.

---

