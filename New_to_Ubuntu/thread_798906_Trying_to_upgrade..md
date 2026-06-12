---
title: "Trying to upgrade."
date: 2008-05-18
forum: New to Ubuntu
---

### Post by groeswenphil on 2008-05-18
Currently running Dapper....6.06

I'll be honest, I've thought about upgrading for some time but I thought it would be a bit more difficult than the forums tell me.....although I've got stuck at the first hurdle.


So, I went to this page.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

and tried this:-
gksu "update-manager -c" 

and got this:-

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Now........I know that I can upgrade one step at a time until I get to the current LTS version, but at the moment, I can't even get one step.
Any advice?
Thanks,
Phil

---

### Post by meborc on 2008-05-18
try this [https://help.ubuntu.com/community/HardyUpgrades#head-e7f287c730b93116f89de7ea7e05efbe95fa6dd1](https://help.ubuntu.com/community/HardyUpgrades#head-e7f287c730b93116f89de7ea7e05efbe95fa6dd1) scroll down for dapper -> hardy

;)

---

### Post by groeswenphil on 2008-05-18
Tried that..........got told that I had to be root.

Isn't that 'sudo' command? Can you remind me how that one goes?

Also it says [COLOR="Red"]Make sure the "dapper-updates" software channel is enabled.[/COLOR]

How do you do that?
Phil

---

### Post by meborc on 2008-05-18
although i prefer fresh installs to upgrades, i too did an upgrade to hardy... from 7.10 though...

i guess what it means is to be sure you have all the repositories enabled... after that upgrade your dapper to the latest by running **sudo apt-get update && sudo apt-get upgrade**

then run **gksu "update-manager -d"** in run (alt+F2)

or **sudo update-manager -d** in terminal

---

### Post by groeswenphil on 2008-05-18
[COLOR="Navy"]That worked. Huge thanks.
Phil[/COLOR]

---

### Post by groeswenphil on 2008-05-18
I hope that it takes into account that I'm running the AMD 64 version.

Phil

---

