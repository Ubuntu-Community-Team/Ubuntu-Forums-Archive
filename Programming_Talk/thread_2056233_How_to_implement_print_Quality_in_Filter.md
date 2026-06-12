---
title: "How to implement print Quality in Filter"
date: 2012-09-11
forum: Programming Talk
---

### Post by Gurpreet123 on 2012-09-11
Hi Experts,

I want to implement Print Quality feature (Draft, Normal, Quick) in rastertoepson filter.
I have written below mentioned code in ppd file:
     Code:
 >     *OpenUI *PrintQuality/Print Quality: PickOne
*DefaultPrintQuality: None
*OrderDependency: 150 AnySetup *PrintQuality
*PrintQuality Draft/Draft:  "<< /PrintQuality Draft>> setpagedevice"
*PrintQuality Roman/Roman: "<< /PrintQuality Roman>> setpagedevice"
*PrintQuality Quick/Quick: "<< /PrintQuality Quick>> setpagedevice"
*CloseUI: *PrintQuality 
I have to pass some commands  to printer from rastertoepson filter  depending upon which print Quality  has been selected by the user.
How i can get the information about selection of print Quality by user in printer properties?


Thanks in advance.

---

