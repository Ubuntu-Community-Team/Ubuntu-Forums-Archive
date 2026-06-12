---
title: "join command issue with CSV files"
date: 2015-04-08
forum: Programming Talk
---

### Post by nagabhushan2 on 2015-04-08
HI,

Following are my file content

file 1 : [email]abc@gmail.com,"akfjas;gjg,",9833595094,2015-04-07T09:04:48.996Z,448996885,abc@gmail.com[/email]

file 2: [email]abc@gmail.com[/email]

command used join --nocheck-order -v 1 -t"," -1 6 -2 1 -o  1.1 1.2 1.3 1.4 1.5 core1.csv excore1.csv

As the i used field seprator as ,(-t,) it considers comma inside field "akfjas;gjg," as seprator.

Expected : [email]abc@gmail.com[/email],"akfjas;gjg,",9833595094,2015-04-07T09:04:48.996Z,448996885

OUtput : [email]abc@gmail.com[/email],"akfjas;gjg,",9833595094,2015-04-07T09:04:48.996Z

PLease help me  to fix it

---

