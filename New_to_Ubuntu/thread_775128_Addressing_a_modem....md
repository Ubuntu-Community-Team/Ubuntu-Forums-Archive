---
title: "Addressing a modem..."
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Larken on 2008-04-29
I have a system running Edubuntu.  I need it to be able to dial up to an Internet provider.  I have installed Gnome PPP.  My modem is being detected as FA82537EP 56K V.92 Data/Fax Modem PCI.  When I try to address it with Gnome PPP, it fails to respond.  I switched between the various ttyS01-S04 but still no go.  Can anyone help me out?

Thanks

Larken

---

### Post by Mark_in_Hollywood on 2008-04-29
You haven't said what brand and model of modem you have. It could make a significant difference. And while I had a dial-up modem for a while, I'm not a computer geek as some on these forums are.

A quick search of the info you provided showed your modem as being semi-compatible with linux, but in need of patches. I'm not able to help you with patches.

Please see:

[http://hardware4linux.info/component/21739/](http://hardware4linux.info/component/21739/)

and

[http://pci-ids.ucw.cz/iii/?i=80861080](http://pci-ids.ucw.cz/iii/?i=80861080)

If you are in a hurry about this, I recommend you get a used external modem from a thrift store or e-bay. All external modems "just work". I'll continue to monitor this thread and maybe two heads will be better than one.

---

### Post by mgranet on 2008-04-30
If you can compile source
(see [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware))

Then you should be able to obtain drivers for that modem here:

[http://downloadcenter.intel.com/filter_results.aspx?strOSs=39&strTypes=DRV&ProductID=1230&OSFullName=Linux*&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strOSs=39&strTypes=DRV&ProductID=1230&OSFullName=Linux*&submit=Go)!

If you have trouble, you know where to find us!

---

