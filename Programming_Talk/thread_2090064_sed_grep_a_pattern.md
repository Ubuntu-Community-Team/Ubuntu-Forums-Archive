---
title: "sed grep a pattern"
date: 2012-12-01
forum: Programming Talk
---

### Post by MikeCyber on 2012-12-01
Hi
I want to extract from a *.txt and write to another file.
It consists of 12 numbers and/or letters without spaces or anything else between. 
Those numbers are on each line and I only want those to extract to another file also each on a line.
Many thanks
Michael

---

### Post by Lars Noodén on 2012-12-01
Well your answer will probably use grep or awk to redirect to a file.  But first, can you provide some sample data along with the detailed selection criteria?  Without seeing the data, it is very hard accurately guess.

---

### Post by MikeCyber on 2012-12-01
Hi Lars
 some lines only have an email and the number/letters:

[email]asom@sme.com[/email]   3232B232323232vNvV

Other lines look alike:

"05/05/2007"    "16:15:48"    "MESZ"    "Fredric"    "Zahlung f&#65533;r Warenkorb empfangen"    "Abgeschlossen"    "EUR"    "9.00"    "-0.70"    "8.30"    "Arld@al.com"    "mich@gm.ch"    "3232B232323232vNvV"    ""    ""

And I want to extract only: 3232B232323232vNvV
to a new txt file/line.
Many thanks

---

### Post by Vaphell on 2012-12-01
try
```
grep -Eo '\b[a-zA-Z0-9]{18}\b'
```

---

### Post by MikeCyber on 2012-12-02
Great, many thanks.

---

