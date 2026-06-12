---
title: "Problem connecting to Jabber with Empathy"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by BoZenKhaa on 2012-03-06
Hello everyone, 
I have a problem with my Jabber account in Empathy. 

Each time I enter my password, it connects for about 5 seconds (at least I can see people who are online). After that the account disconnects with this message:
"Connection has been replaced by a new connection using the same resource"

I am clueless as to what that means, I tried googling this error but it turns up posts related to msn accounts that go unanswered and translation notes.
I also have to confirm the certificate each time i try to log in, but searching the forums I didn't find anybody else having the same problem as I do. 

This jabber account is working fine on my phone. 
I tried google talk account in empathy and it works fine as well.

Empathy version 3.2.0.1
I am running Ubuntu 11.10 from AMD64 alternate cd with xfce 4.8.

I would be happy for any ideas as to what this problem is related to, empathy, jabber, my account or the server?

Thank you!

Ok, I actually found out what resource is (as i understand, it is a specification of how or from where you are connecting that allows you to be signed in in more than one location), so I turned my phone off and selected a resource in empathy but nothing has changed.

---

### Post by Jon Monreal on 2012-03-08
I don't use empathy, so I'm not able to even try to figure out what the problem might be.

Have you considered trying another program, such as Pidgin, with jabber support?

---

### Post by bill.albertson on 2012-12-18
The problem is with expected behavior of XMPP.  The Empathy client has an API, called Telepathy.  Telepathy doesn't support XMPP ping/keepalive.  The problem is that the GNOME dev is basically saying that it isn't his problem if you can't stay connected, even if an XMPP/Jabber server admin a) expects client side keep alive to exist, b) doesn't know about the setting, or c) doesn't want to run a bunch of keepalive processes that would bog the hell out of the jabber server.  If there is no client side keep alive, then the client will die as described, according to the defaults of how many XMPP servers are configured.  When the XMPP ping fails, the connection gets closed.

The Empathy developer sees no issue with not having a client side keep alive, even though whether an XMPP server does keep alive or not is wholly up to the server admin and not the client.  The Ubuntu dev team has no control over the GNOME dev, and also hasn't seen fit to produce their own fix nor switch to a client that actually does do XMPP ping.  Like Pidgin does by default.  I've commented in the bug for this issue.

Now, as for Pidgin, there is an open bug with them regarding how their XMPP ping isn't working correctly, but I'm not sure if a) there is a fix yet; b) or if there is a fix, whether Ubuntu has pulled from the upstream for this issue.  I can verify that Pidgin continues to have this issue under Ubuntu 12.10, because unlike Empathy, I have a handy dandy debug window under Pidgin, and I'm watching the ping issue being reproduced as I type this... randomly.  However, my performance under Pidgin is tolerable, compared to being completely broken under Empathy.  I am now looking for another option for keeping sessions alive, as my daughter uses Ubuntu and I need to keep in touch with her while I'm at work and on the road, but so far having a mostly working client is, well, ok...

---

