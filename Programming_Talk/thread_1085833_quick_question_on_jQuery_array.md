---
title: "quick question on jQuery array"
date: 2009-03-03
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-03
How to display the text inside of a textbox? The input element is 
<input type='text' id='package_name' value='package name...' />

alert ($('#package_name').text()); does not seem to work... I get a popup box with nothing in it...

Thanks,

Tom

---

### Post by simeon87 on 2009-03-03
Try:

```
$("#package_name").get(0).value
```

---

### Post by qmqmqm on 2009-03-03
Thanks simeon87 but unfortunately this doesnt work...

---

### Post by qmqmqm on 2009-03-03
Does anyone have any suggestions?

---

### Post by qmqmqm on 2009-03-03
Figured out myself:

alert ($("#package_name").val());

---

