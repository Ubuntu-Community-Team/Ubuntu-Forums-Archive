---
title: "tethering verizon vx6800 through USB in 8.10"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by sdp0et on 2008-11-09
I am trying to set up my vx6800 to tether as a modem in ubuntu.  I have seen many posts and articles that make it seem such a simple matter.  Each says to use dmesg to find the device the phone's modem is connected with, and continues with instructions for setup, but none offer advice on what to do when it is not found.

my phone is detected by the computer when I try "lsusb"
but when I try "dmesg" the modem is not found.  I do have the modem link active on the phone.  Every article/thread says I should have something like:
[  119.616081] cdc_acm 1-2:1.0: ttyACM0: USB ACM device

but nothing shows.  grepping the output of dmesg for "tty" only finds tty0, and ACM has no matches.

I would appreciate any suggestions or help in figuring this out.

thanks,

paul

---

