---
title: "update manager not showing latest update release"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by bobmac on 2012-06-03
Folks,

I have a dual boot system. I have the update manager Settings|Software Sources|updates|Release upgrade set to Long Term Support Releases Only.

I have been expecting update manager to inform me that the new LTS release was now available for update but have not received that message.

Is there something I'm doing wrong or have I got something set incorrectly.

Any help appreciated.

regards,

Bob

---

### Post by synapsys on 2012-06-04
Try updating apt-get modules and see if it pops up:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If that doesn't work, you can upgrade your distribution from the command line.

---

### Post by Bucky Ball on 2012-06-04
> **synapsys said:**
> Try updating apt-get modules and see if it pops up:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If that doesn't work, you can upgrade your distribution from the command line.

NOTE: This will upgrade your system to 12.04 which might not be what you want.

Issue this in a terminal and then check your Update Manager. The new release should show:

```
update-manager -d
```

You can either upgrade or ignore. You should have an ethernet cable plugged in to upgrade rather than wireless. ;)

---

### Post by mcduck on 2012-06-04
If you are really still running 8.04 like your profile suggests, that would be the reason. 8.04 has already reached it's end-of-life for desktop last year, so there will be no update to the Update Manager to offer you the release upgrade.

...and also 8.04 can't be upgraded directly to 12.04 anyway, you'd have to upgrade to 10.04 first.

---

### Post by Bucky Ball on 2012-06-04
> **mcduck said:**
> If you are really still running 8.04 like your profile suggests, that would be the reason. 8.04 has already reached it's end-of-life for desktop last year, so there will be no update to the Update Manager to offer you the release upgrade.

...and also 8.04 can't be upgraded directly to 12.04 anyway, you'd have to upgrade to 10.04 first.

+1. Didn't notice that. If you are running 8.04 all bets are off. You will need to upgrade to 10.04 then 12.04 (if 8.04 is stall capable of the upgrade to 10.04).

Either that or a clean install of 12.04 if that's where you're going. ;)

---

