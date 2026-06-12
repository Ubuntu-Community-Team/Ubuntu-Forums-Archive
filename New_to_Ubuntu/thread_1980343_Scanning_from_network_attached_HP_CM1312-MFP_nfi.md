---
title: "Scanning from network attached HP CM1312-MFP nfi?"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by n3mmr on 2012-05-15
Running simple scanner (and a few others), the HP scanner seems to be assumed by the software to be there, but scanning always fails, unable to connect to scanner.

Scanner connection configuration seems not to be done in the scanning application, so I am stumped.

The CM1312 is network attached.

Printing works well, using hplip.

---

### Post by n3mmr on 2012-05-15
Solution: run hp-plugin-ubuntu AFTER installing the printer itself.

Now things work purrfectly!

---

