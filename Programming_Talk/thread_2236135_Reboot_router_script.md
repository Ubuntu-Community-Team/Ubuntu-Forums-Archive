---
title: "Reboot router script"
date: 2014-07-24
forum: Programming Talk
---

### Post by ian-goodchild on 2014-07-24
Hi

I have a one line script that I was using to reboot my router(cheapy from my very cheap ISP). Since yesterday the script does not work. It's a one liner curl script which calls the routers reboot webpage with basic authentication and I had to run it a couple of times (cookies) to bounce the thing but it no longer works. It is a really cheap router and I need to reboot it all the time so this script was really useful. Any ideas

The script is with relevant variables set in the header

curl   -u ${username}:${pssword} $routerip/reboot.html



A Lot of thanks in advance
Ian

---

### Post by steeldriver on 2014-07-25
I would start by adding a '-v' option to get verbose output from the curl command

```

curl   -**v**u ${username}:${pssword} $routerip/reboot.html

```

---

### Post by bapoumba on 2014-07-25
*Thread moved to **Programming Talk**.*

---

### Post by tgalati4 on 2014-07-25
Was this router provided by your ISP?  It's possible that they sent an update to your router (to fix a security vulnerability) and when you rebooted, it closed the reboot feature.  What was the version of the router firmware when you wrote the script?  What is the firmware version now?

Can you manually reboot the router through the web page?

---

