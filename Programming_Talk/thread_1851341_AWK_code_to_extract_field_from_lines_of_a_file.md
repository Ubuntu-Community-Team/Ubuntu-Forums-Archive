---
title: "AWK code to extract field from lines of a file"
date: 2011-09-28
forum: Programming Talk
---

### Post by haojam on 2011-09-28
Mr/Mrs.
Hello,
I would like to extract and print [COLOR="Red"]PharmGKB ID[/COLOR] field with its [COLOR="red"]relative value[/COLOR] in a column list using AWK command from the drug_links txt file. Could you please tell me the code for running this query. I have attached a text file plz see.

Regards,
Rocky

---

### Post by sisco311 on 2011-09-28
It seams to me that fields are separated by , (commas) and you want to print the 10th field.

```
awk -F, '{print $10}' filename
```

---

### Post by dethorpe on 2011-09-28
This will print the filed:
 
awk -F, ' {print $10}' drug_link.csv

---

### Post by Drenriza on 2011-09-28
This was what i came up with.
```
awk -F, '{print $10}' drug_links.csv |grep ^P
```
But i don't really get why the file is builded up the way it is. Seams unnecessary complicated. Maybe its just me.

---

