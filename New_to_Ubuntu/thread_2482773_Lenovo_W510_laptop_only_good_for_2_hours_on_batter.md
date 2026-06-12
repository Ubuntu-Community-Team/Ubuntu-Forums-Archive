---
title: "Lenovo W510 laptop only good for 2 hours on battery ..."
date: 2023-01-10
forum: New to Ubuntu
---

### Post by cwmoser on 2023-01-10
My Lenovo W510 laptop is only good for 2 hours on battery.
I purchased a new 9 cell 70++ battery and got 2.5 hours when new, now after just a few months its down to 2 hours.
Is there a configuration I can make to extend my time on battery?

Lenovo has posted when these W510's were new that they should get 5-6 hours run time on battery.
I assume that was under Windows, but I use Ubuntu.  I'm wondering if there is technology in Windows that helps extend battery run time.

---

### Post by cwmoser on 2023-01-10
When I run ...

$  acpitool  -B

... it outputs Capacity loss = 20.77%

Battery is only 9 months old, but has a 1 year warrantee.  
Should I try to get a replacement?

---

### Post by MAFoElffen on 2023-01-10
I was a Certified Lenovo On-Site Warranty Tech... If it were me, get all your ducks in order before calling Lenovo Support.

[https://download.lenovo.com/pccbbs/thinkvantage_en/ldiag_4.46.1_linux.iso](https://download.lenovo.com/pccbbs/thinkvantage_en/ldiag_4.46.1_linux.iso)

That is a link to the Lenovo Linux Think Vantage Diagnostics tool ISO. Create a bootable Live-USB from it and test your battery. If it fails or if you think the results are too bad for a new battery, then you have the results from their tool set, to justify the support option. Make sense?

---

### Post by cwmoser on 2023-01-10
Thanks, but when I convert that iso file to bootable thumb drive it doesn't do anything.
It does a count down from default and just cycles doing nothing.
I used unetbootin to make the thumb drive.

---

### Post by MAFoElffen on 2023-01-10
Here is the instructions from Lenovo:
[https://support.lenovo.com/us/en/solutions/bootableusb](https://support.lenovo.com/us/en/solutions/bootableusb)

---

