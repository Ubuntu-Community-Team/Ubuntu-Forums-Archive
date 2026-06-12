---
title: "Ubuntu 11.10 &amp; SSDs - Will I have to monkey with fstat"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2011-09-21
I'll be buying a new pc in the next 2 months and want to install Ubuntu 11.10 as the only os.

I've read that for ubuntu 10.10 you had to manually edit fstab to enable trim for the ssd, is this still the case for 11.10.

Will any new 120 GB SSD I buy work out of the box with ubuntu 11.10.

My idea is to install ubuntu on the ssd and save my data multimedia onto a regular internal harddrive.

TIA

---

### Post by MacUntu on 2011-09-21
Yes, you still have to add that. However, not all SSD are influenced a lot by missing TRIM.

---

### Post by Col-1023 on 2011-09-21
Thanks for your reply MacUntu.

If I don't modify fstab, will future versions of ubuntu enable trim and therefore modify the fstab automatically, or is the fstab file never changed by os upgrades.

---

