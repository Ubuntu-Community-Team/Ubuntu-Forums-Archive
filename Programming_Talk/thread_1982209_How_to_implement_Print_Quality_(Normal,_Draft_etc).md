---
title: "How to implement Print Quality (Normal, Draft etc) in rastertoepson filter?"
date: 2012-05-18
forum: Programming Talk
---

### Post by Gurmeet Singh on 2012-05-18
Hi Experts,

I want to implement Print Quality feature (Draft, Normal, High) in rastertoepson filter.
I have written below mentioned code in ppd file:
```
*OpenUI *cupsPrintQuality/Print Quality: PickOne 
*OrderDependency: 10 AnySetup *cupsPrintQuality 
*DefaultcupsPrintQuality: Normal 
*cupsPrintQuality Draft/Draft: "3" 
*cupsPrintQuality Normal/Normal: "4" 
*cupsPrintQuality High/Photo: "5"
*CloseUI: *cupsPrintQuality
```

I have to pass some commands  to printer from rastertoepson filter depending upon which print Quality  has been selected by the user.
How i can get the information about selection of print Quality by user in printer properties?

Thanks in advance.

---

