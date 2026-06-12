---
title: "How can I connect to openoffice by programming code?"
date: 2010-10-11
forum: Programming Talk
---

### Post by hopelessone on 2010-10-11
Hi,

I've converted to linux for some years now, and now I need to write some simple database programming..

I used to write Basic in VB6 and SQL..via a helpful site for beginners called vbcity

I have 2 spreadsheets in openoffice...i can save them as databases..
what i want to do is this:
first spreadsheet
```
OEM		COMP	HCNO	MANUFACTYPE
0-0274-06652	NIKKO	191645	OEM

```
second spreadsheet
```
HCNO	VARE
191645	Starter Motor

```

Insert "VARE" where it's equal to "HCNO"

So it looks like:
```
OEM		COMP	VARE		HCNO	MANUFACTYPE
0-0274-06652	NIKKO	Starter Motor	191645	OEM
```

1. So what language should I use C or python do you think?
2. Is there any sites that can give help for beginners?

Thanks,
Hopelessone

---

### Post by juancarlospaco on 2010-10-11
I use Python-UNO for connecting with OpenOffice, it works nice.

If you want to try/study my program here's a .deb
[http://tecnicoslinux.com.ar/livecd/cvfacil2_0.5_all.deb]("http://tecnicoslinux.com.ar/livecd/cvfacil2_0.5_all.deb")
It makes elegant Curriculums Vitae to help people to get a job,
also do Menubar:Opciones--->Change to English, to get a *limited *English GUI
Python-Uno documentation is all i used so far.

---

