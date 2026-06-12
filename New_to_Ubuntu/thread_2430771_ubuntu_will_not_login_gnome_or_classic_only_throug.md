---
title: "ubuntu will not login gnome or classic only through xcfe"
date: 2019-11-07
forum: New to Ubuntu
---

### Post by dylan-thomas on 2019-11-07
Hi everyone,

 I am new to ubuntu and have an issue logging into ubuntu using either gnome, ubuntu or ubuntu classic, 
though for some reason do not have an issue logging in using xfce.I have had a look through some forum 
answers though cannot seem to find what the solution is for this specific problem.


Following instructions from this link [https://www.maketecheasier.com/fix-ubuntu-login-loop/](https://www.maketecheasier.com/fix-ubuntu-login-loop/)
I  logged into terminal (prior to the login page) to check the Permissions of Xauthority and using the command

ls -lah | grep -i Xauthority

it did not appear to be owned by root so it didn&#8217;t appear to be an ownership issue
I also checked the tmp permissions and these were correct.

The logged into xfce and used synaptic to check if there were any errors with repositories or duplicates 
which may be conflicting, whether this is related or not, there seemed to be no issue upon reloading packages either. 

I was noticing a bit of freezing up prior to the issue, I may have installed something prior that has caused the issue. 
The last thing I was installing was LaTex presentation software and I shut this down before it had finished installing.

Any thoughts on how to test this would be appreciated, maybe there is a way to roll back or check if something has caused a 
conflict that stops me logging in.

Thanks

Distro Ubuntu Studio 18.04.3 LTS

---

### Post by deadflowr on 2019-11-07
> no issue upon reloading packages either.

What packages?

---

### Post by dylan-thomas on 2019-11-07
I just meant that when I click reload in synaptic and the message comes up "checking for new, removed or upgraded software packages" - that no error message comes up.

---

### Post by dylan-thomas on 2019-11-09
I managed to find a solution to this problem within another thread

[https://askubuntu.com/questions/1059458/ubuntu-18-04-on-login-loop-even-with-correct-password](https://askubuntu.com/questions/1059458/ubuntu-18-04-on-login-loop-even-with-correct-password)

Using the command to uninstall flatpak has fixed this error, 

apt purge flatpak && apt autoremove

I don't recall installing this, though I have been tinkering a bit so anything is possible.

---

