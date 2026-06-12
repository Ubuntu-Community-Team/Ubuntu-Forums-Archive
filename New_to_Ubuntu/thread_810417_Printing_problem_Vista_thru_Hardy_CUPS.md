---
title: "Printing problem Vista thru Hardy CUPS"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by GarethA on 2008-05-28
Hi

I'm using hardy on a dell workstation connected (USB) to a Lexmark Z605.
Local print from that workstation works fine.

CUPS is running and I have shared the printer on the network.

My vista laptop can see the printer and has connected to it successfully - in the vista print manager screen I can see when jobs from the ubuntu box get submitted and processed.

However....  when I submit a print job from the vista machine it just sits there and does not get picked up (if I connect the vista machine directly to the Z605 it's fine)

I'm completely new to linux - so sorry if this is a daft question but I'm stuck.

Thanks

---

### Post by nebu on 2008-05-28
> **GarethA said:**
> Hi

I'm using hardy on a dell workstation connected (USB) to a Lexmark Z605.
Local print from that workstation works fine.

CUPS is running and I have shared the printer on the network.

My vista laptop can see the printer and has connected to it successfully - in the vista print manager screen I can see when jobs from the ubuntu box get submitted and processed.

However....  when I submit a print job from the vista machine it just sits there and does not get picked up (if I connect the vista machine directly to the Z605 it's fine)

I'm completely new to linux - so sorry if this is a daft question but I'm stuck.

Thanks



chk this out....
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by GarethA on 2008-05-29
Thanks... I've been through that but still not working.

My vista (and XP) laptops connect fine to the printer on:
http://<machinename>:631/printers/<printername>

but when they submit jobs they are not picked up by cups

I've tried creating a queue for my printer as a 'generic postscript printer' and a generic 'raw' printer ... and my windows machines can connect to both these 'printers' but still not print.

Any ideas?

---

