---
title: "[SOLVED] Irc"
date: 2007-09-02
forum: North Carolina Team - US
---

### Post by markthecarp on 2007-09-02
HI All,

I was on the #ubuntu-northcarolina channel until my system rebooted today due to power problems. Now when I try to join the channel the Freenode server gives me the following message...

```
#ubuntu-northcarolina :You need to be identified to join that channel
```

I have not registered my nick on Freenode. Is that what is required? I'm using Xchat on Fiesty.

Edit:

Duh, yeah that's it.

-mark

---

### Post by ddrichardson on 2007-09-03
Glad its working, can you mark it solved?

UAResolved

---

### Post by mark_k on 2007-09-05
So, for all us complete and utter irc minor-leaguers, how does one register a nic on freenode?

I ran across a series of commands at [http://freenode.net/faq.shtml#nicksetup](http://freenode.net/faq.shtml#nicksetup) but how does one issue all the commands they mention without posting them to the discussion? My biggest fear is issuing the wrong command a dozen times, and having the irc channel get spammed with my mistakes!

Also, the last couple days I don't seem to be able to connect to #ubuntu-northcarolina with irc.freenode.net. Are other folks having similar problems, or am I just special?

- MarkK

---

### Post by Siph0n on 2007-09-05
Type this:
/msg Nickserv register <password you choose> <your email address>
than whenever you log onto Freenode type:
/msg Nickserv identify <your password you chose>

do not include the < or >.

/msg is the command to send a private message to someone, so the rest of the channel wont see it. And Nickserv is the bot that registers your nickname.

---

### Post by markthecarp on 2007-09-05
> **mark_k said:**
> So, for all us complete and utter irc minor-leaguers, how does one register a nic on freenode?

I ran across a series of commands at [http://freenode.net/faq.shtml#nicksetup](http://freenode.net/faq.shtml#nicksetup) but how does one issue all the commands they mention without posting them to the discussion? My biggest fear is issuing the wrong command a dozen times, and having the irc channel get spammed with my mistakes!

Also, the last couple days I don't seem to be able to connect to #ubuntu-northcarolina with irc.freenode.net. Are other folks having similar problems, or am I just special?

You are special ;-))

After following the steps SiphOn describes.

I've done this maybe three times in ten years. Issue the commands for nick registration in the server tab, not the channel tab. That is XChat specific.

My XChat does not require the password once I've registered; i.e. ```
/join #ubuntu-northcarolina
``` does not require me to enter my passwd. 


-mark

---

### Post by mark_k on 2007-09-24
Thanks for all the pointers.

I was using gaim, and the steps I ended up taking were:

(1) start up gaim. It pops up a 'freenode-connect' dialog that I left open.
(2) /msg Nickserv register _password_ _email_
  popped up another window talking to the Nickserv, which complained to me about having the wrong command. I dutifully correct myself!
(3) /msg Nickserv register _password_
  then it tells me to add a password (grr. that's what I tried to do!)
(4) /msg Nickserv set email _email@address_

After all that, I'm able to get back in to the chat room.

Again, thanks for giving me a hand. I only hope I'll be able to return the favor in the future.

- Mark

---

