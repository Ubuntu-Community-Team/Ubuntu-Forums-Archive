---
title: "Fedex API: Stocktype error?"
date: 2012-04-18
forum: Programming Talk
---

### Post by fallenshadow on 2012-04-18
Hi guys/gals,

Im using the Fedex API and I almost have the shipping part of it working. However I am coming up against an error that does not seem possible to solve.

> Severity: ERROR
Code: 6025
Message: Invalid Stock Type
Source: ship

This is driving me insane, any ideas? You will probably need to have some experience with the API to help out. :D

---

### Post by fallenshadow on 2012-04-18
Seems to be a problem with this line:

```
labelSpecification.setImageType(ShippingDocumentImageType.PNG);
```

BUT if I comment that out I get this error! -_-

> Severity: ERROR
Code: 2241
Message: Label Image type can not be empty
Source: ship

Also I have tried all the enums available at the end of "ShippingDocumentImageType.".

---

