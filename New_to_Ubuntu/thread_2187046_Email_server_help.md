---
title: "Email server help?"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by caleb12134 on 2013-11-10
Hi, I have a dell power edge running zpanel. I am behind verizon router so they blocked 25. I am unsure how to setup my email server in zpanel admin area. It has options for wether to use tls ssl or none, outgoing email server ( I put my External IP) and wether to use auth or not (with user and pass fields). I can receive mail but not send? I get this error message when it says "Delayed Mail". On a side note I also have the option to send mail using (SendMail, PHP, or SMTP) I had smtp selected. Thank you so so much for any help. I am a noob :)




*********
[COLOR=#333333][FONT=Lucida Grande]This is the mail system at host control.yourdomain.com.

####################################################################
# THIS IS A WARNING ONLY.  YOU DO NOT NEED TO RESEND YOUR MESSAGE. #
####################################################################

Your message could not be delivered for more than 4 hour(s).
It will be retried until it is 5 day(s) old.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<[EMAIL="calebputnammac@gmail.com"]calebputnammac@gmail.com[/EMAIL]>: connect to
    alt2.gmail-smtp-in.l.google.com[2a00:1450:4013:c00::1b]:25: Network is
    unreachable
[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Reporting-MTA: dns; control.yourdomain.com
X-Postfix-Queue-ID: 64946190232A
X-Postfix-Sender: rfc822; [EMAIL="test@balnazzar.com"]test@balnazzar.com[/EMAIL]
Arrival-Date: Sat,  9 Nov 2013 13:54:27 -0500 (EST)

Final-Recipient: rfc822; [EMAIL="calebputnammac@gmail.com"]calebputnammac@gmail.com[/EMAIL]
Original-Recipient: rfc822;[EMAIL="calebputnammac@gmail.com"]calebputnammac@gmail.com[/EMAIL]
Action: delayed
Status: 4.4.1
Diagnostic-Code: X-Postfix; connect to
    alt2.gmail-smtp-in.l.google.com[2a00:1450:4013:c00::1b]:25: Network is
    unreachable
Will-Retry-Until: Thu, 14 Nov 2013 13:54:27 -0500 (EST)
[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Return-Path: <[EMAIL="test@balnazzar.com"]test@balnazzar.com[/EMAIL]>
Received: from 192.168.1.8 (localhost [127.0.0.1])
	by control.yourdomain.com (Postfix) with ESMTPA id 64946190232A
	for <[EMAIL="calebputnammac@gmail.com"]calebputnammac@gmail.com[/EMAIL]>; Sat,  9 Nov 2013 13:54:27 -0500 (EST)
MIME-Version: 1.0
Content-Type: multipart/alternative;
 boundary="=_ce5249ff4c9256294b3bff91a2b483da"
Date: Sat, 09 Nov 2013 13:54:27 -0500
From: [EMAIL="test@balnazzar.com"]test@balnazzar.com[/EMAIL]
To: [EMAIL="calebputnammac@gmail.com"]calebputnammac@gmail.com[/EMAIL]
Subject: Apple
Message-ID: <[EMAIL="bb09d6a23b8b297af8283b2522ead884@balnazzar.com"]bb09d6a23b8b297af8283b2522ead884@balnazzar.com[/EMAIL]>
X-Sender: [EMAIL="test@balnazzar.com"]test@balnazzar.com[/EMAIL]
User-Agent: Roundcube Webmail/0.9.2[/FONT][/COLOR]

---

### Post by SeijiSensei on 2013-11-10
If you cannot send out port 25, it doesn't matter how you configure the server.  You won't be able to exchange mail with remote servers.  You might be able to relay your mail through a server Verizon provides, but if you are on a residential account, you should be aware that the VZ [Terms of Service]("http://my.verizon.com/central/vzc.portal?_nfpb=true&_pageLabel=vzc_help_policies&id=TOS") prohibit servers on those accounts.

"You also may not exceed the bandwidth usage limitations that Verizon may establish from time to time for the Service, or use the Service to host any type of server."

---

