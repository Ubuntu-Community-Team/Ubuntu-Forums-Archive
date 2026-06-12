---
title: "Tough to describe permissions problem on windows domain"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by trivialpackets on 2013-03-14
So, this is the problem. I have a freshly installed 12.10 on a dell laptop for work. I am able to join the domain with no issues utilizing centrifydc. Before rebooting, and before logging out, I make some changes to the sudoers file to allow particular users to have sudo power on the box. 

This works great. The initial user I set up though at this point does not work but I can log in with my domain user.  The problem is that when I'm in the system in a gui, such as adding a network connection and I try to make a change that requires me to provide the sudo password, it's still prompting for the initial user's (by name) password, which no longer works. I can work around this by starting the gui from the command line, but I would much rather solve this so that it is asking for the current user's password, as he is in the sudoers group.

---

