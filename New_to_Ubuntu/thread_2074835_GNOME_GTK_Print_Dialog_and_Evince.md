---
title: "GNOME GTK Print Dialog and Evince"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by codyn on 2012-10-22
I'm currently working on building an Ubuntu 12.04 image for kiosk/POS type usage scenarios.  So far, everything appears to be working fantastic.  However, I am having an issue with printing as it pertains to PDF documents.  I have observed the Adobe plugin crashing when opening multiple PDFs (Basically a black screen after several attempts).  This is the current acroread installation.

As an alternative, I have started using Evince as an inline alternative, which works great.  However, with this image, I have two different printers which would require distinctly different settings.  One is a label printer and the other is your standard inkjet.  This requires different paper sizes for both printers.  I have observed Evince uses the GTK printer dialog and does not use lpoptions to read in the default printer settings.  As a result, it stores different settings.

Does anyone know if there is a way to store settings for multiple printers in Evince or configure it to read in the default printer options from lpoptions?

---

