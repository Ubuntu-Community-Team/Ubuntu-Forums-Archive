---
title: "Having problems allowing remote hosts to see server"
date: 2008-12-14
forum: Programming Talk
---

### Post by MattJones on 2008-12-14
Howdy,

Any time I create a open socket in userland, it cannot be accessed by anything non localhost.

For instance, if I create a python socket, or ruby on rails webrick server on port 3000, and open the port using ufw(sudo ufw allow 3000/tcp), remote hosts on my network cannot access that server. Only local requests can.

External hosts can access ssh(port 22) and apache(port 80) just fine. Even if I run my rails webrick server on port 80, they still cannot see it. IE:
rails script/server -p 80

Is there something about regular user accounts that stop them from being able to create sockets that are externally accessible?

I've been looking for an answer to this for a month now, and see nothing on it.

---

### Post by geirha on 2008-12-14
Then you've probably set it to only listen on the loopback device (probably default if you don't specify an ip). Try listening on ip 0.0.0.0 port 3000, which should listen on all ethernet devices.

Also note that ports < 1024 can only be bound by root under linux.

---

### Post by MattJones on 2008-12-14
Woot.

I was using localhost(127.0.0.1). Then I changed it to 0.0.0.0 per your advice, and it worked! Thanks.

I never noticed the difference between 127.0.0.1 and 0.0.0.0. Always just assumed they were the same.

Super thanks.

---

