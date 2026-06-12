---
title: "[SOLVED] Mp-bios bug:8254 timer not connected to io-apic"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by tuts69 on 2008-09-03
Hi there people i try to dual boot vista premuim 32 bit and ubuntu, but everytime i install it the installion stop and here's the message or error?
4294667.70400> MP-BIOS BUG: 8254 Timer not connected to IO-APIC
kernel panic-not syncing: IO-APIC+timer doesnt work boot with APIC=DEBUG and send report then try booting the NOAPIC option? 
 what is this means and how can i resolved this problem?
here some spec of my system:
CPU: CORE 2 DUO QUAD Q6600 2.4 @ OC TO 2.97
MOBO: EVGA 680i
MEMORY: CORSAIR DOMINATOR 1142 MHz 4GB
HDD: 2X 500 GB WD @RAID 0
thanks in advance.

---

### Post by porchrat on 2008-09-03
When you get to the menu press F6 and add "noapic" to the end of the line...then press the enter button

If that doesn't work then try the same F6 thing and add both "noapic" and "noacpi" to the end.

---

### Post by tuts69 on 2008-09-03
Thanks porchrat appreciate, i'm going to try this.

---

### Post by jacksmash on 2008-10-05
THis thread has been marked "Solved". What was the solution?!?

---

