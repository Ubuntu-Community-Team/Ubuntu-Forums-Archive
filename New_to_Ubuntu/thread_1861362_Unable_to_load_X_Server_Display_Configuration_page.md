---
title: "Unable to load X Server Display Configuration page:  Failed to query NoScanout for sc"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by mikee55 on 2011-10-15
Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

Guys/Gals, couldn't run Unity in 11.04, thought 11.10 would fix it, but alas no, can you help? I got a ASROCK N68C-S UCC mobo with an nVidia GeForce 7025/ nForce 630a chipset. I just need the correct Resolution for my monitor at 1024 by 768.
Where do I begin?

Thank you
Mike :)

---

### Post by Rumpty on 2011-12-01
I had that problem on Lubuntu 11.10 because I was using a fairly old nvidia card, FX5200, hence an old driver, nvidia-driver 173. The version of nvidia-settings in 11.10 (280 something) looks for "NoScanout", but that is not present in the 173 driver.

So I uninstalled the nvidia-settings in 11.10, and installed an old version nvidia-settings_177.87-0ubuntu2_i386.deb that I found on the web. No dependency problems. Now the X Server Display Configuration panel can be accessed with no error message.

Thanks to Tom Russo, I think, for the above solution.

---

