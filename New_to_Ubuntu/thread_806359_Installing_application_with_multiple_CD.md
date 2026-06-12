---
title: "Installing application with multiple CD"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-24
hi guys

can anyone help me to over come this. i am trying to install LOTR that has 4 CD's and it installs CD1 good and ask for CD2 but when i try to edject it says that cannot be unmounted as its being used. i try unmounting it but still same error..
attach is screenchot

any idea? please help:confused::confused::confused::confused::confused::confused:

---

### Post by HotShotDJ on 2008-05-24
> **appoloin said:**
> can anyone help me to over come this. i am trying to install LOTR that has 4 CD's and it installs CD1 good and ask for CD2 but when i try to edject it says that cannot be unmounted as its being used. i try unmounting it but still same error.I have no idea what you are trying to install.  I've never heard of a Linux application that installs in this manner.  Where did you obtain this application?  What does it do?  Is it a Linux application?

---

### Post by appoloin on 2008-05-24
Its Lord of the Ring Game Original. using wine. it comes with 4 CD's to install

---

### Post by HotShotDJ on 2008-05-24
> **appoloin said:**
> Its Lord of the Ring Game Original. using wine. it comes with 4 CD's to installOk.  When the system asks for the next cd, open Applications --> Accessories --> Terminal and type ```
wine eject

```Insert the next CD and WAIT for a bit before continuing.  Wash, Rinse, Repeat for each cd.

---

