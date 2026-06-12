---
title: "Gmail fails to connect in Pidgin"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2011-09-30
Some time back I was advising someone about Pidgin.  Well, now I have a weird situation.  I use Pidgin for instant messages and since I have kids and grandkids that use MSN and Gmail (jabber I think), it just works.  I haven't been on Pidgin for almost a week but now I cannot connect to my Gmail account.  
I have deleted the account and then added it back.  No luck. I did a search on the forums and have come up empty.  As far as I know there have been no recent updates to Pidgin.  Hot mail works.  Any ideas.

---

### Post by LinuxRocks713 on 2011-09-30
What is the specific error message that you are getting? It might help us to help you on your situation.

---

### Post by Rex Bouwense on 2011-09-30
[email]xxxxxxx@gmail.com[/email]/
disconnected
Unable to connect
Not much in the way of error messages.  When it did that before I just tapped the reconnect button and it always (usually) connected.  I am using a different WIFI system here in Charleston than I was using in North Carolina last week.  Perhaps it has something to do with the provider.  We will be moving in three days so if it is the IP, I will probably find out then.  It is just a weird situation.

---

### Post by LinuxRocks713 on 2011-09-30
> **Rex Bouwense said:**
> [email]xxxxxxx@gmail.com[/email]/
disconnected
Unable to connect
Not much in the way of error messages.  When it did that before I just tapped the reconnect button and it always (usually) connected.  I am using a different WIFI system here in Charleston than I was using in North Carolina last week.  Perhaps it has something to do with the provider.  We will be moving in three days so if it is the IP, I will probably find out then.  It is just a weird situation.

Looks like an ISP/Router problem, at least according to [bug #13120](http://developer.pidgin.im/ticket/13120).

In the meantime, try this workaround mentioned in the bug report:

> You can try using talk.google.com as the value for the Connect Server field on the account's advanced tab.

---

### Post by Rex Bouwense on 2011-09-30
Thanks LinuxRocks713,  Although I am using a different (earlier) version (2.6.6), the bug has been around for 9 months and is supposedly fixed, I tried the work around that you mentioned and that is mentioned on their site and it works.  It is probably the provider and will switch back on Monday when I get down to Georgia just to see.  Thanks again.

---

