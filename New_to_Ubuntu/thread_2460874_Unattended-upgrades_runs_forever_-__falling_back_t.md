---
title: "Unattended-upgrades runs forever -  falling back to adjusting .. dependencies recursi"
date: 2021-04-20
forum: New to Ubuntu
---

### Post by dmongan on 2021-04-20
New to Ubuntu.

Setting up unattended-upgrades.   When I run    unattended-upgrades --dry-run --debug
it runs forever, 

    Sample output:::

falling back to adjusting libnetplan0's dependencies recursively
adjusting candidate version: libnvidia-fbc1-450:i386=450.102.04-0ubuntu0.18.04.2
adjusting candidate version: libnvidia-common-450=450.102.04-0ubuntu0.18.04.2
adjusting candidate version: nvidia-kernel-source-450=450.102.04-0ubuntu0.18.04.2
adjusting candidate version: libnvidia-ifr1-450=450.102.04-0ubuntu0.18.04.2
adjusting candidate version: libnvidia-decode-450:i386=450.102.04-0ubuntu0.18.04.2

I did some Google searches, and it appears that it was a bug in the past, but I can't find a solution.

---

### Post by dmongan on 2021-04-21
I believe I found the fix.   [https://askubuntu.com/questions/792579/unattended-upgrades](https://askubuntu.com/questions/792579/unattended-upgrades)

Added this line to 50unattended-backups  file
Unattended-Upgrade::Remove-Unused-Dependencies "true";


The unattended-upgrades --dry-run --debug ran and completed in short order.

---

