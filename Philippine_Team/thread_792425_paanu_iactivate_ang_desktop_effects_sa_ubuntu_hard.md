---
title: "paanu iactivate ang desktop effects sa ubuntu hardy heron 2"
date: 2008-05-12
forum: Philippine Team
---

### Post by eryllex on 2008-05-12
gud day gus,,sori 'bout yesterday hnd n aq nkapagreply...but e2 ung result sa pagtype q ng lspci sa terminal/console.

ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge 
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge 
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge 
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge 
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge 
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller 
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device 
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge 
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80) 
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80) 
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge 
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c) 
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge 
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge 
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01) 
06:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10) 
ubuntu@ubuntu:~$ 

then wat nxt q pong gwin...tnx

---

### Post by loell on 2008-05-12
paliwanag :oops:

**maiksi:** di pa pwedeng mag enable nang desktop effects sa ngayon.


**mahaba:** ang graphics processor na gamit mo ay built in, ito ay ang 

**VIA Technologies, Inc. Chrome9 HC IGP ** , kaya nitong mag 3D , makaka laro ka nang linux games with accelerated graphics. 

 kaso di pa siya compatible sa **compiz** -- yung desktop effects.  hintay ka lang muna nang konti.

---

### Post by eryllex on 2008-05-13
sayang nman...wat do u mean sir na w8 lng aq ng konti?gus2 q p nman mag ubuntu...mybe ill have  to sell this laptop 2 buy a new 1,,can u suggest me or recommend me what specs should i choose so i can run ubuntu with its desktop effects,,how about if the graphic card is Intel Graphics Media Accelerator X3100? will this b ok?tnx...

---

### Post by loell on 2008-05-13
graphics na galing sa intel, oo pwede siguro yun- compatible naman yung compiz sa intel cards.   

ibig kung sabihin sa hintay, ay baka may improvements na sa driver nang VIA card mo pag lipas nang ilang buwan. pero kung gusto mo talaga nang desktop effects agad, bili ka na lang nag bago laptop o kundi video card.

---

### Post by eryllex on 2008-05-13
dbah kpag built in ang graphic dats means hnd n pwde i upgrade? can a later version of ubuntu would run its desktop effects in my laptop?

---

### Post by jepong on 2008-05-13
^ or atleast sana yung BIOS capable na increase yung shared na RAM. itong sa thinkpad ko 8MB lang pero wwork Compiz... Intel chip nito.  :) but i choose to disable it na lang.

---

