---
title: "printer problem"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by fred hoth on 2008-06-23
problem setting up brother 210c printer
printer set as default printer (type cups:mfc-210c)
when print command is sent a error message appears "error while printing"
version 8.04 ubuntu
Pc-Compaq Presario
Processor-Intel Celeron D
Processor 360
Memory 512

can someone please help
fred

















9

---

### Post by plucky on 2008-06-23
> problem setting up brother 210c printer
printer set as default printer (type cups:mfc-210c)
when print command is sent a error message appears "error while printing"
version 8.04 ubuntu
Pc-Compaq Presario
Processor-Intel Celeron D
Processor 360
Memory 512



How did you set up the printer driver?

Which driver have you selected?

To install the **Brother printer driver** open Synaptic Package Manager (System > Administration > Synaptic Package Manager) and search for [color=red]Brother extra[/color]

There are two packages to install

1) Brother-cups-wrapper-extra
2) Brother-lpr-drivers-extra

Select both and mark for install and apply.

After they are installed open System > Administration > Printing and Select New printer.It should then search for and find the new printer and give you a choice of drivers.Select the MFC210C driver and print a test page.


Good Luck

---

### Post by fred hoth on 2008-06-23
To:plucky
Many Thanks For The Help
You Made My Day

Fred
Pearlington Mississippi Usa
June 23, 2008

---

