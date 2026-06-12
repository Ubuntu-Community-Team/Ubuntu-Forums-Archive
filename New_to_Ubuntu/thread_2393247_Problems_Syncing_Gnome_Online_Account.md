---
title: "Problems Syncing Gnome Online Account"
date: 2018-05-31
forum: New to Ubuntu
---

### Post by binchois on 2018-05-31
Hello All,

I'm new to using Ubuntu (16.04) as my main OS.  I'm using Gnome for my desktop and am having problems syncing my work Microsoft Exchange account with Gnome Online Accounts.  When I first set things up everything was working perfectly, then one day I started getting messages about my credentials being expired.  Re-entering my credentials gave an error something to the effect of "Error Code 10: Unexpected Response from Server".  I removed the account and tried to set it up again, and now when I go to create the new account I get a "Failed to find ASUrl and OABUrl in autodiscover response" error.

I also tried adding the account directly in Evolution.  There during the account creating it seems to find URLs for "Host URL" and "OAB URL" automatically but when I continue trying to create the account Evolution hangs and I eventually have to do a force kill. 

Any tips on what might be the issue or how to get started troubleshooting this?

Thanks.

---

### Post by mrdc76 on 2018-06-03
I had a similar problem in 16.04 but upgraded to 16.10 and so on. I used this workaround to restart the daemon when the problem occurred:

/usr/lib/gnome-online-accounts/goa-daemon --replace &

---

### Post by binchois on 2018-06-19
Thanks for the reply.  Restarting the daemon doesn't seem to do anything.  At some point things just magically started working again and I could recreate the account in GOA.  It worked for about 2 weeks, but today I started getting errors in Evolution saying: "The reported error was 'Source 'mymail@mydomain.com' doesn't support prompt for credentials".  I can delete and recreate the account in GOA, but Evolution just keeps giving this error.

---

