---
title: "Cannot print to printers on lubuntu machine from Vista Laptop"
date: 2014-10-26
forum: New to Ubuntu
---

### Post by James_Frayne on 2014-10-26
I have Lubuntu 14.04 installed with two printers connected to it via USB ports. I can print to both from the local machine and have shared them over the network. 

I have installed samba and added both printers to my Vista Laptop. When I try to print to either printer from the Vista laptop, the print job appears in the print queue on the lubuntu machine and it changes status to completed but nothing comes out of the printer.

Here is some debugging output from CUPS scheduler:
[ATTACH=CONFIG]257509[/ATTACH]

Regards,

James

---

### Post by cariboo on 2014-11-01
You don't need samba to share printers, if that's all you use it for. Start the cups web interface:

```
http://localhost:631
```

and make sure both your printers are shared. You should then be able to print from any system on your local network.

---

