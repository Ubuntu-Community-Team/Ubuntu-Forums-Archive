---
title: "Trouble with Thunderbird 31.0"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by ray9 on 2014-07-28
I use "Wave Cable" for my internet provider.  Just recently Thunderbird 31 hasn't been downloading incoming email from the server.  Now it won't send either.  The error message I get when trying to send is "Sending of message failed.
The message could not be sent because the connection to SMTP server mail.wavecable.com was lost in the middle of the transaction. Try again or contact your network administrator."  I called Wave Cable and got no help.  I went to their web-site on how to set up e-mail and there was quite a change in the ports and authentication settings.  I changed everything back to the new settings but it still won't work.  They say it's T'Bird.  I'm thinking maybe to downgrading to an earlier version of T'Bird but don't know how to do that.

Any ideas?

Thanks

---

### Post by whitesmith on 2014-07-28
I don't think back-revving is the right approach. Try downloading Evolution. Once you get the settings right you can port them back to TB.

---

### Post by ray9 on 2014-07-28
Thanks for the reply.  I changed the port and Security settings back to the way they were on SMTP and left the setting on POP at the new settings and that seems to have worked.

---

### Post by ray9 on 2014-08-03
I thought I had this problem fixed but I have not.  I get this error when I try to send from thunderbird:  "Sending of message failed.
The message could not be sent because the connection to SMTP server mail.wavecable.com timed out. Try again or contact your network administrator."  So I click "send" about three or four more times and keep getting this message then it will finally send.  Any ideas?

---

### Post by Vladlenin5000 on 2014-08-03
You need to change the SMTP settings for the ones your service provider uses now. It won't work otherwise and it shouldn't be so hard to understand why.

Obs.: If you have IMAP available give it a try. POP3 is so XX century...

---

### Post by ray9 on 2014-08-03
"An error occurred while sending mail. The mail server responded:   your host [24.56.194.30] is blacklisted by sbl-xbl.wavecable.com. Send your questions to [email]blacklist-admin@wavecable.net[/email]. Please check the message recipient [email]xxxx@wavecable.com[/email] and try again."  Ever see an error like this?

---

### Post by ray9 on 2014-08-03
[http://www.wavebroadband.com/support/internet/email-help/](http://www.wavebroadband.com/support/internet/email-help/)  This is link to how they want it set-up.  But, it will only work with the 537 port and security set at  SSL/TLS and  authentication method set at NTLM.  It will work with repeated tries but  any changes, such as the way they say to use, I get the "blacklist" message or it won't send at all.

---

### Post by ray9 on 2014-08-28
I still have to try 3 times to send in thunderbird 31.  With the version ahead of 31 one click was all it took.  This is with Ubuntu and Linux Mint 17.  The exact same problem.  "Sending of message failed.
The message could not be sent because the connection to SMTP server mail.wavecable.com timed out. Try again or contact your network administrator."  The third time is literally the charm.

---

### Post by Erik The Pope on 2014-10-20
I use Windows 7 on one of my computers & I'm getting exactly the same message. I also am a Wavecable customer. I was on with them for an hour the other day & no joy. My settings were exactly what they said they should be. I thought of just deleting my account & then making a new one. Think that would work? Or just ask for the supervisor next time?

Thanks!

---

### Post by ray9 on 2014-11-02
Did you find an answer to this?  I'd call them but if I told them I was using Linux they run screaming!

---

### Post by buzzingrobot on 2014-11-03
The settings for a mail provider -- server names, ports, encryption method, authentication method -- will be the same for any user, regardless of OS or mail client. It's certainly possible for issues to come up with a client, but the posts in this thread indicate that probably isn't the issue here.

The blacklist notice from Wave is telling. If someone tries to run their own mail server on their own system, and tries to use it to relay mail to their mail provider, they often find that mail server blacklisted because it's easy to misconfigure it and leave it open to compromise by spammers.

It seems, though, that's not the case here. Possibly, then, misconfiguration at Wave's side of things?

Try using a free account with Google/Yahoo/Outlook, etc., and see if the problem exists there.

---

### Post by kurt18947 on 2014-11-03
buzzingrobot has a good idea with using an alternative email provider, or at least their SMTP server.  If you want to stick with Wave as your primary email address, you should be able to configure Thunderbird to use Google/Yahoo/whoever's SMTP server as default.  I'm concerned about using a free email provider and having my sent messages ending up in receipients' spam folder by default but at least using a different SMTP server might help to isolate the problem.

---

### Post by wolf2600 on 2014-12-21
> **ray9 said:**
> I still have to try 3 times to send in thunderbird 31.  With the version ahead of 31 one click was all it took.  This is with Ubuntu and Linux Mint 17.  The exact same problem.  "Sending of message failed.
The message could not be sent because the connection to SMTP server mail.wavecable.com timed out. Try again or contact your network administrator."  The third time is literally the charm.

My dad is getting the exact same error after upgrading to TBird 31.3.0 on Win7.  He has Astound.net as an ISP (which is also a Wave company).
Both for send and receive, it takes 3 attempts before the request goes through.

There's no error message when clicking Check Mail, but until you click it a couple times, nothing will come through.  For sending mail, he gets the SMTP Timeout message twice, then the 3rd time it sends.

I've tried increasing the mailnews.tcptimeout setting from 100 to 1000 with no affect.

After finally sending a message successfully, if you create/send another message, it goes through with a problem (maybe TCP connection is still open from the first message?)


I suspect my grandmother is also getting the same issue (comcast acct) after I upgraded her Thunderbird from something like 2.0 up to 31 over Thanksgiving.  But she just says "it won't send", not sure if the "3 sends" workaround will work in her case.

---

