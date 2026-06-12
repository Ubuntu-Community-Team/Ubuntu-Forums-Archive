---
title: "Chromium web browser"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by mrrog on 2013-04-11
1. started with lubuntu a few days ago, problem (?) now is that I have had to roll back the web browser from the 25etc version to the 22etc version, the 25 version just hands after a few seconds while apparently trying to load the google home page (google.co.uk)

any ideas?

2. also, can anybody point me at a good overall tutorial/help documentation facility?

thanks

sorry, should have also said problem has only occurred since I upgraded lubuntu from 12.04 to 12.10

---

### Post by Frogs Hair on 2013-04-11
2. [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)

---

### Post by Rex Bouwense on 2013-04-11
1.  Why did you decide to use Chrome instead of Chromium which is the default browser for Lubuntu?  Does it have something that you need that Chromium doesn.t have?

---

### Post by mrrog on 2013-04-11
Ahh'TE=Rex Bouwense;12598453]1.  Why did you decide to use Chrome instead of Chromium which is the default browser for Lubuntu?  Does it have something that you need that Chromium doesn.t have?[/QUOTE]


Ahh, mean't chromium

---

### Post by Rex Bouwense on 2013-04-11
Give us a little bit more to go on.  Version 25 of Chromium we browser is in the repositories so it has been tested and approved.  When you moved to 12.10 from 12.04, did you upgrade or do a clean install?  Upgrades occasionally bonk something.  If you current version is working, can you upgrade from it?

---

### Post by ikt on 2013-04-11
> **mrrog said:**
> 1. started with lubuntu a few days ago, problem (?) now is that I have had to roll back the web browser from the 25etc version to the 22etc version, the 25 version just hands after a few seconds while apparently trying to load the google home page (google.co.uk)

any ideas?

Try running 'chromium' from terminal, and see if it spits anything interesting out.

---

### Post by maglinu on 2013-04-11
Do you by any chance have the default apparmor profile for Chromium set to enforce? 
If so you may need to add a line or two for Chromium 25 - I did.

---

### Post by mrrog on 2013-04-11
> **maglinu said:**
> Do you by any chance have the default apparmor profile for Chromium set to enforce? 
If so you may need to add a line or two for Chromium 25 - I did.


does this mean anything:-

 apparmor module is loaded.15 profiles are loaded.
15 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
3 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (1806) 
   /usr/sbin/cupsd (637) 
   /usr/sbin/ntpd (1904) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

?

---

### Post by mrrog on 2013-04-11
> **ikt said:**
> Try running 'chromium' from terminal, and see if it spits anything interesting out.


ok, so upgraded back to latest version, (by the way I have previously done both upgrade and clean install of the browser) to try running in terminal and it now boots up with the following warning:-

'Your profile could not be opened correctly.


Some features may be unavailable.  Please check that the profile exists and you have permission to read and write its contents.'

the chromium settings menu is also telling me I have a 'sync error: sign in again' which I am loath to do while the latest version is working for me apparently fine, but I would like to get to the bottom of this?

---

### Post by maglinu on 2013-04-12
> **mrrog said:**
> does this mean anything:-

 apparmor module is loaded.15 profiles are loaded.
15 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
3 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (1806) 
   /usr/sbin/cupsd (637) 
   /usr/sbin/ntpd (1904) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

?
Well it's not really what I was expecting to see, but then I don't run Lubuntu.

If you want to see what I had to do to get Chromium working on Ubuntu have a look here.
[http://ubuntuforums.org/showthread.php?t=2125553&page=2](http://ubuntuforums.org/showthread.php?t=2125553&page=2)

You could look in /var/log/kern.log to see if apparmor is denying anything to do with chromium when you open it.

Probably best to wait for more advice from a Lubuntu user.

---

### Post by howefield on 2013-04-12
> **annaharris said:**
> why do you want to install chrome in Ubuntu ? It already provides mozilla firefox web browser.

Read the thread and you'll find the answer to your question.

---

### Post by maglinu on 2013-04-12
> **annaharris said:**
> why do you want to install chrome in Ubuntu ? It already provides mozilla firefox web browser.

If your question was for the OP - they are running Lubuntu, and Chromium is the default browser.

If your question was for the previous poster - me - a few reasons:
(i) I find Chromium faster than Firefox
(ii) I am led to believe that with its SECCOMP sandboxing it is out-of-the box more secure than Firefox (though if you add NoScript to Firefox I don't know where the balance would lie)
(iii) I use both browsers - in separate user accounts. In one account used only for sensitive transactions I use only Firefox. In another account used only for general browsing I use only Chromium.

I realise this is all well off topic - so if any passing moderator wants to delete it - feel free[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

