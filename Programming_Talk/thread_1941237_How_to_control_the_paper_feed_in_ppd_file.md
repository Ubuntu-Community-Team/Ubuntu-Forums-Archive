---
title: "How to control the paper feed in ppd file?"
date: 2012-03-15
forum: Programming Talk
---

### Post by Gurmeet Singh on 2012-03-15
Hi All,

I am developing a printer driver for 24-pin DMP using CUPS. when i install the ppd file on my system and print any document, after printing all the content of document, the paper is 25 cm feeded extra.
How i can control the paper feed from PPD file?

my code for Resolution in PPD file is 
```

*OpenUI *Resolution/Output Resolution: PickOne
*OrderDependency: 20 AnySetup *Resolution
*DefaultResolution: 180x180dpi
*Resolution 60x60dpi/60x60 dpi: "<</HWResolution[60 60]/cupsRowCount 8>>setpagedevice"
*Resolution 180x180dpi/180x180 dpi: "<</HWResolution[180 180]/cupsRowCount 24>>setpagedevice"
*CloseUI: *Resolution

```I have tried with below code
```
*Resolution 180x180dpi/180x180 dpi: "<</HWResolution[180 180]/cupsRowCount 24/cupsRowFeed 0/cupsRowStep 0>>setpagedevice"
``` but it is giving same result.

Please help me to sort out this.

Thanks in advance.

---

### Post by CynicRus on 2012-03-15
I think you need read [http://www.cups.org/documentation.php]("http://www.cups.org/documentation.php").

---

### Post by Gurmeet Singh on 2012-03-16
Thanks CynicRus for your reply.

> I think you need read [http://www.cups.org/documentation.php](http://www.cups.org/documentation.php). 	

That means i have to make some changes in cups filter?

Thanks.

---

### Post by CynicRus on 2012-03-16
You can do all that is described in the documentation for the development of drivers for &#1089;ups, as well as in the case of problems - there is a link to a forum -)

---

### Post by Gurmeet Singh on 2012-03-17
Thanks CynicRus for your response.

---

