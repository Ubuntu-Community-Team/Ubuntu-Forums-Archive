---
title: "User Privoxy not found, but it works"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by gladgrind on 2013-01-18
I noticed in the system monitor that privoxy was not running even though tor was running.

So I ran the command:
sudo /etc/init.d/privoxy start

but got the reply:
2013-01-18 15:50:50.942 7f0bda3e6700 Fatal error: User 'privoxy' not found.

The odd thing, though, is that when I click on 'enable proxy servers' in Opera, tor is working - my ip is replaced with the tor proxy.

I assume privoxy is needed for this so it is a bit confusing. I'm guessing that privoxy is really running but since it is not a user any more, it can not be displayed, but who knows?

In any case, I don't like the 'user privoxy not found' message, and would like to get it fixed.

If it helps, I recently got rid of zeitgeist and whoopsie, following some threads here. I had to re-install a couple of zeitgeist modules because getting rid of them made gedit and nautilus not work.

There have been one or two other odd things since then, but easy stuff to fix.

But the user not found message is above my pay grade.

Can anyone give me a fix?

---

### Post by Daveth on 2013-01-19
have you waded your way through all the config stuff on here?

[http://www.privoxy.org/faq/misc.html#TOR](http://www.privoxy.org/faq/misc.html#TOR)

---

