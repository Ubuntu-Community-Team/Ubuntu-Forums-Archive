---
title: "Multiple  ubuntu installs"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by farrinux on 2012-04-06
Question Guys.  I would like to try LinuxCNC out on live cd and if I like it, would like to install it.  I know that the newest release is built around Ubuntu 10.04LTS.  The machine I would install it on is currently dual booting Win7 and Ubuntu 11.10.  Can I go ahead and install this alongside whats there  with out hosing Grub or is there going to have to be a pecking order.  By this I mean Loading Win 7 then linuxcnc (Ubuntu 10.04) and then Ubuntu 11.10.

---

### Post by gordintoronto on 2012-04-06
I have a similar setup. If you install 11.10 last using the normal approach, it will have control of the Grub. The only quirk is, if you get a new kernel in 10.04, you need to boot 11.10 and run sudo update-grub to make the new 10.04 kernel available. 

Or you can just wait until there's a kernel update in 11.10, at which point update-grub is run automatically.

---

### Post by Cheesemill on 2012-04-06
Or when you install LinuxCNC you can choose to install its bootloader to its own / partition instead of the MBR, then just run 'sudo update-grub' from your Ubuntu install to add it to the main grub menu.

Using this method each linux install looks after it's own grub settings which avoids the quirk mentioned above.

---

### Post by farrinux on 2012-04-06
Thanks Guys!  Appreciate the response was not sure just exactly what to do.  Better off getting a little help than hosing everything up just to learn! Again Thanks.

---

