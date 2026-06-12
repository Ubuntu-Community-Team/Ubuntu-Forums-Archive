---
title: "Vidalia would not run Tor"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by pskeshu on 2014-07-25
I am not able to get vidalia running. I can run tor from terminal, but it's just vidalia that won't work. 

I have unchecked start tor in when Vidalia starts, set it to use TCP connection and added the current user to debian-tor usergroup. None of that seems to help.

I get this following error:
>       Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified.

I installed Vidalia from the Ubuntu repos using apt-get install vidalia.

I am on Lubuntu 14.04, if that helps.


I found the solution. The problem seemed to something to do with AppArmor.
By disabling it, fixed the problem.

> sudo ln -s /etc/apparmor.d/usr.bin.vidalia /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.vidalia



---

