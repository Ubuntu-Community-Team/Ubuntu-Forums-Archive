---
title: "Can't apt-get upgrade?"
date: 2005-12-08
forum: Repositories &amp; Backports
---

### Post by wargames on 2005-12-08
I just did a "sudo apt-get update" and then went to the Update Manager and viewed the packages to be updated. But when I hit the Install button, it starts to download them and after about 3 seconds, it just stops and the download window just disappears. So I hit the Reload button in the Update Manager, and then it displayed the same packages, so I hit Install button again but this time it says that the packages "can't not be authenticated" and wants to know if I want to go ahead. I'm using just the official Ubuntu repositories also. I even "sudo apt-get clean" and rebooted and still the same thing happens. Is it a repository problem?

---

### Post by traherom on 2005-12-08
Try doing the upgrade through the command line (sudo apt-get upgrade) to see if you get any odd error messages.

---

### Post by wargames on 2005-12-09
Well, I decided to wait a day and I re-tried it today. It ran just fine from the Update Manager. Probably just a repository issue.

Thanks for your help. :)

---

