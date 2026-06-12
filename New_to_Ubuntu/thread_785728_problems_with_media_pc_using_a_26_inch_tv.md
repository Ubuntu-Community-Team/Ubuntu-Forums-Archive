---
title: "problems with media pc using a 26 inch tv"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by therealeggman on 2008-05-07
Hello,

I recently treated myself to a Goodmans 26 inch TV which has VGA and HDMI imputs. I assumed that if I built a PC that I could simply plug it into the TV and use it as a multimedia system.

It does work but with a resolution of 800x600.

I have got other resolutions to work by setting it on a normal computer monitor then plugging the TV in. However when I re-start the PC I get an 'Out Of Range' mesage on the TV screen and have to plug the monitor back in to cure the problem.

I have tried all the different cures available on these forums as well as in the documentation available on or from the Ubuntu website and they work until I restart the PC.

The TV is a Goodmans GTVL2W28HDF
The pc motherboard is an ASRock 939N68PV-GLAN with Nvida GeForce 7 graphics built in. (I am using the latest drivers for the board)

I have always used Windows (still do on the family PC) and am still trying to get up to speed with Linux which I find pleasantly suprises me and totaly frustrates me in equal measures!

Can anyone help me?

---

### Post by overdrank on 2008-05-07
> **therealeggman said:**
> Hello,

I recently treated myself to a Goodmans 26 inch TV which has VGA and HDMI imputs. I assumed that if I built a PC that I could simply plug it into the TV and use it as a multimedia system.

It does work but with a resolution of 800x600.

I have got other resolutions to work by setting it on a normal computer monitor then plugging the TV in. However when I re-start the PC I get an 'Out Of Range' mesage on the TV screen and have to plug the monitor back in to cure the problem.

I have tried all the different cures available on these forums as well as in the documentation available on or from the Ubuntu website and they work until I restart the PC.

The TV is a Goodmans GTVL2W28HDF
The pc motherboard is an ASRock 939N68PV-GLAN with Nvida GeForce 7 graphics built in. (I am using the latest drivers for the board)

I have always used Windows (still do on the family PC) and am still trying to get up to speed with Linux which I find pleasantly suprises me and totaly frustrates me in equal measures!

Can anyone help me?

HI and welcome, I am assuming that you are using Hardy the latest release of ubuntu. Have you tried using the nvidia-settings with the command ```
gksu nvidia-settings
``` Also have you tried screens and graphics?

---

### Post by therealeggman on 2008-05-09
Thanks, i did try to use the nvida program but had trouble running it, however Ubuntu (you are correct the latest Hardy version) has sorted it out on its own. 
Perhaps I should just stop mucking about with it and let it get on with doing its job!

Thanks for the reply

---

### Post by hylli on 2008-12-15
Hi,

a friend of mine has the same screen resolution problem with the same motherboard.

Could you get it to work with higher screen resolution? How did you get it to work? Can you post your /etc/X11/xorg.conf?

Hylli

---

