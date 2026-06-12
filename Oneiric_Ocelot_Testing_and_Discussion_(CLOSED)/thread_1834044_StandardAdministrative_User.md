---
title: "Standard/Administrative User?"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by scradock on 2011-08-26
In Oneiric, I noticed that my user account was set as "Administrator", which seemed contrary to what I understood was the norm in Ubuntu - a user account is not administrative, but acquires admin privileges by using "sudo".

So I tried setting it to "Standard".

Big mistake. That takes me off the sudoers list, so I can't now use my password to authenticate for anything - including changing the user account back to "Administrator".

There must be a simple CL command to rectify this - anyone willing to enlighten me? Do it privately if this info is not to be shared widely.

But WHY the heck is the (only) user account now set to be "Administrator" - exactly the behavior we've all scoffed at Widnows for doing all these years?

---

### Post by aysiu on 2011-08-26
This should help you fix the problem:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

*Administrator* means you run as a regular user most of the time but have the option, after password authentication, to temporarily escalate to root privileges.

When you're a regular user, you can't escalate even with *sudo*.

I submitted a Brainstorm idea on this a while ago, and I thought it'd already been implemented:
[Idea #11107: Users and Groups should always make sure at least one user is in the admin group](http://brainstorm.ubuntu.com/idea/11107/)

---

### Post by scradock on 2011-08-26
> **aysiu said:**
> This should help you fix the problem:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

*Administrator* means you run as a regular user most of the time but have the option, after password authentication, to temporarily escalate to root privileges.

When you're a regular user, you can't escalate even with *sudo*.

I submitted a Brainstorm idea on this a while ago, and I thought it'd already been implemented:
[Idea #11107: Users and Groups should always make sure at least one user is in the admin group](http://brainstorm.ubuntu.com/idea/11107/)

Thanks, pal.

---

