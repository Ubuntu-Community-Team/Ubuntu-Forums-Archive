---
title: "LightDM + unity-greeter with huge passwd file"
date: 2011-10-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rhoads on 2011-10-13
Hi,

I am trying to make the unity-greeter to behave nicely with our /etc/passwd with ~33000 entries. So far I can make it to not traverse the passwd when displaying the greeter, so that is well and good.

But as soon as I type in a username and hit enter, it wants to load the list. So a login takes too long time (roughly 15 minutes).

Have I missed some obvious options?

Also is there a way to change 'Other...' to 'Login' when the user listing is disabled?

I am on unity-greeter 0.1.1-0ubuntu1
and lightdm 1.0.1-0ubuntu6

I have not changed anyting in unity-greeter.conf

lightDM.conf has the following:

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
greeter-hide-users=true
allow-guest=false
load-users=false

[UserManager]
load-users=false

[GuestAccount]
enabled=false

[xdmcp]
enabled=false

---

