---
title: "How to check if networking is attempting to connect"
date: 2012-02-17
forum: Programming Talk
---

### Post by Bufke on 2012-02-17
Is there any way to check if networking is in the process of connecting? I know many ways to check if a computer is connected to a network or not. I specifically want to know if it in the process of connecting.

Why? I'd like to implement a good way to let users log in via ldap when networking might not be instantly available, such as wifi. 

```

start networking
start gdm/lightdm
user enters credentials
if using ldap related login method:
  while network_trying_to_connect:
    sleep 1
```

It's annoying to have the user wait for networking if they have cached credentials or maybe don't even want to login as a domain user. lightdm should start and the user can start typing in their password while networking in still working. Upon hitting enter it should pause and wait for for networking but if networking is fully down and not waiting on dhcp or something it should give up instantly.

---

