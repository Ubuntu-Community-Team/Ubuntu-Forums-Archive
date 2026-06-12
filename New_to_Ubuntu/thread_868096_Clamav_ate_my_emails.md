---
title: "Clamav ate my emails"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by sydbat on 2008-07-23
I decided to check out clamav to see if it would be useful to detect windows viruses so I would not spread them. I ran it manually and it gave me "7 viruses found". So I checked them to see what they might be. I found it strange that a few were in archived email files, and thought maybe when I was using Windows in the past, the anti-virus program I used missed them somehow. Coming from that Windows background, I figured 'quarantine' meant individual files that may be infected were, well, quarantined. I was wrong.

Clamav has destroyed my email inboxes and now I do not know how to recover them. I went into the 'quarantine' dialog and only found 3 "viruses" (although, as I mentioned above, there were 7). There is an option to let clamav know if the "virus" is a false positive, so I clicked that and it said the file was put into my /home folder. OK. What I realized when I got into my /home folder was the ENTIRE EMAIL DATABASE FILE was there...but only one...and I have no idea which one, or if it is all the email db's put together. 

This is extremely not good as I work from home and these are business emails. Sure, I know that I do not need an antivirus program in Ubuntu GNU/Linux, but as I mentioned at the start, I was trying to be a good citizen.

So, how do I (or can I) recover my email database. I use Thunderbird.

EDIT - The one email db is restored...thankfully. But this still leaves me without any emails in 3 other accounts. The screen is blank in 2 and one has the emails "listed", but no actual emails to view. Yes, I do have backups, but they are about 2 weeks old and there have been several emails in the meantime.

---

### Post by sydbat on 2008-07-23
Bump. This is extremely important. If I have posted this in the wrong area, please direct me to the appropriate board(s).

Thank you.

---

### Post by dca on 2008-07-23
I've never seen that happen, you can try here if nobody is able to help on this side...
 
[http://www.clamav.net/support/ml](http://www.clamav.net/support/ml)

---

### Post by sydbat on 2008-07-23
Thanks. I'll look into it.

---

### Post by sydbat on 2008-07-23
Nothing related on the Clamav site I could find. I may have to simply suck it up.

What I figure happened (for future reference to those thinking of using unnecessary anti-virus programs in GNU/Linux) is Clam found something in one email, but linked it to the entire "Inbox" folder, so when I 'quarantined' what I thought was an individual file, it removed the entire Inbox folder...then overwrote it with the next Inbox, etc. This is why I was able to recover one such folder, but have lost 3 others. DOH!

I'll keep searching via Google...but I'm not going to hold my breath because I'll pass out long before I find the solution.

---

### Post by dca on 2008-07-23
On the ClamAV site, there should be a mailing list you can apply (add yourself to) to and send them an email with your issue.  I'm still trying to figure if this is by design or something not added/changed to the clam config file in the /etc directory

---

### Post by LowSky on 2008-07-23
Are you running you own email client or using something like google mail or yahoo mail and then using thunderbird to read them? 

Thunderbird has a setting to keep emails on the server and not delete them unless you want to with a few option of when and how. So if your email are comming from a POP or IMAP server like google mail then you have this option, and can have a back up of all your emails

---

### Post by sydbat on 2008-07-23
@dca - I've sent the email. I don't think they can help.

@LowSky - My own email from my website host/server. It defaults to downloading everything to reduce online overhead.

EDIT - My web host does not keep backups of emails...which I figured, but confirmed. I guess I am SOL!

---

### Post by sdowney717 on 2008-07-23
I use hotmail, totally online webmail so I can only lose them if I delete them myself.
Can you forward link emails from another site to post on a hotmail type of email account?

---

### Post by sydbat on 2008-07-23
Something I might try to set up...maybe in my Gmail account...

---

### Post by stevoo on 2008-07-23
Most probably those emails are lost. 
You can try and look if the AV has actually archived the deleted files but i still doubt it

---

### Post by sydbat on 2008-07-23
I've looked...and looked...and...well you get the idea. Just a reminder to backup often!

Thanks to everyone who helped!

---

### Post by frogotronic on 2008-12-03
Hi,

  Just got "bit" by this one - didn't realise that quarantining a message wipes the folder - luckily it was on small subfolder.  If I find the solution, I'll post back.

- CH

---

