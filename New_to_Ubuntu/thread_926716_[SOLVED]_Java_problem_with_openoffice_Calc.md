---
title: "[SOLVED] Java problem with openoffice Calc"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by mr wilson on 2008-09-22
I am having problems with OpenOffice's Calc spread sheet. I have only just started to use it and cannot seem to use macro on it. The follow error came up:

   “OpenOffice.org requires a Java Runtime Environment (JRE). Please install a JRE and restart  OpenOffice. Please install the open openoffice-java-common package for this functionality”.

 I am pretty certain I have a JRE installed – is there any way to check? Or is there something else I should do. I am a fair novice with ubuntu. 

 I also find that Calc tends to struggle a bit with large sheets. Is this just Calc? Is there a way to optimize it or something? Or is there superior spread sheet out there (that runs on linux)?

Cheers

---

### Post by tangibleorange on 2008-09-22
> **mr wilson said:**
> I am having problems with OpenOffice's Calc spread sheet. I have only just started to use it and cannot seem to use macro on it. The follow error came up:

   “OpenOffice.org requires a Java Runtime Environment (JRE). Please install a JRE and restart  OpenOffice. Please install the open openoffice-java-common package for this functionality”.

 I am pretty certain I have a JRE installed – is there any way to check? Or is there something else I should do. I am a fair novice with ubuntu. 

 I also find that Calc tends to struggle a bit with large sheets. Is this just Calc? Is there a way to optimize it or something? Or is there superior spread sheet out there (that runs on linux)?

Cheers

try installing the package it's asking for:

```
sudo apt-get install openoffice.org-java-common
```

and see if it solves the problem

---

### Post by mr wilson on 2008-09-22
Well that's embarrasing. Sorry to waste your time and thanks.

---

### Post by tangibleorange on 2008-09-22
> **mr wilson said:**
> Well that's embarrasing. Sorry to waste your time and thanks.

hehe no problem! glad I could help :)

---

