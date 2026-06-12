---
title: "print from dosbox"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by paul1945 on 2012-07-08
Is there a Linux command I can use in a ".sh" file that would allow me to print either a ".prn" file automatically, or a command or Ubuntu utility such as Windows "Dosprint" that will capture the printing port of Dosbox and redirect this to a printer of my choice? Any help would be appreciated.

---

### Post by sanderj on 2012-07-08
Dos-box? I think you mean terminal? If so: "lpr".

---

### Post by paul1945 on 2012-07-18
Hi, I have managed to get a RAW file printed to the network printer by the following command:
lp -d HP-LaserJet-m2727-MFP /home/paul/dosdrive/document/UNNAMED.RAW
I placed this in a "print.sh" file and it works a treat.
But it needs to be manually executed each time I have printed something, which is a pain.
What I was looking for is whether there is a way to get Ubuntu or CUPS for that matter to poll a particular directory at certain intervals and pick up any new .RAW file and send it to the printer automatically.

---

