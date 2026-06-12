---
title: "System updates still showing for removed software (Evolution)"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by mingle on 2008-07-19
Hi,

Yesterday the system update notifier told me that there were 16 software updates available (all of which appeared to be for the Evolution email client). However, since I was planning on removing Evolution, I didn't install the updates.

Later on, I removed Evolution from my system by using the following command:

sudo apt-get remove evolution

And it worked fine, no errors and Evolution was now gone.

But when I booted up this morning, the system update notifier is still telling my there are 16 updates available, all of which are for Evolution.

Is there any simple way of stopping it from displaying updates for software that is no longer installed on the system, or hiding updates that I don't want to install?

Cheers,

Mike.

---

### Post by phidia on 2008-07-19
Try sudo apt-get update or use synaptic to update. Your system should sync then.

---

### Post by cariboo on 2008-07-19
If you don't want evolution updates just lock the version you have now. Open synaptic package manager, search for evolution, highlight when it is found then got Package-->Lock Version.

Jim

---

